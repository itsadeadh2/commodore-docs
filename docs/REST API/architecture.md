---
sidebar_position: 3
---

# Architecture

Breakdown of the API architecture

## Layered Architecture

The project follows a **[layered architecture](https://cs.uwaterloo.ca/~m2nagapp/courses/CS446/1195/Arch_Design_Activity/Layered.pdf)** approach, divided into four layers: **Setup, Database, Infrastructure, and Domain**.

## Setup

This layer is responsible for bootstrapping the application. Initially part of the **Infrastructure** layer, it was separated due to growing size and complexity. Components in this layer interact directly with the Flask `app`, adding functionality before the app is served.

Key components include:
- **Configurations**
- **CORS**
- **Logger**
- **Dependency Injector**
- **Blueprints Registration**

## Database

This layer contains components responsible for persistence actions.

Key components include:
- **Models**
- **Database client**
- **DAOs (Data Access Object)**

## Infrastructure

The Infrastructure layer contains base components required for domain functionality.

Key components include:
- **Custom Errors**
- **Services**
- **Schemas**
- **Blueprints**

## Domain

The Domain layer handles the actual business logic for specific resources. Components in this layer act as orchestrators, using infrastructure resources to achieve desired outcomes.

Current components:
- **Handlers** tied directly to endpoint resources.

## Example

To help illustrate how the components are structured in this project, let's take a look at the user's registration implementation:

### User Resource (Infrastructure)

This component handles the low-level request functionality, ensuring requests are properly received, validated, and parsed. It also handles errors raised by upper-level components.

:::note
The **most important aspect** of this component is that it doesn't need to know or care about the business logic behind the resource. It acts as a "tour guide" for incoming requests, directing them appropriately but not controlling the internal workings.
:::

```python
@bp.route("/register")
class Register(BaseResource):

    ...

    @bp.arguments(UserSchema)
    def post(self, user_data):
        try:
            self.handler.create_user(user_data=user_data)
            return {"message": "User created successfully"}
        except UserAlreadyExists as error:
            return self.handle_error(409, error)
    ...
```

### User Handler (Domain)

This component contains the business logic for the request, providing a high-level, decoupled view of the target logic.

:::note
The most important aspect of this component is its lack of deep coupling with low-level infrastructure resources. It acts as an orchestrator, knowing which services to call to achieve the desired outcome.
:::

```python
class UserHandler:

    ...

    def create_user(self, user_data):
        user = self.user_service.create_user(user_data)
        self.hangman_service.get_or_create_score(user_id=user.id)
    ...
```
In the case of **user registration**, the `UserHandler` calls the `UserService` to register the user and the `HangmanService` to create an empty score.

### User Service (Infrastructure)

This component performs the heavy lifting, aggregating low-level actions into high-level methods.

:::note
The most important aspect of this component is its specific focus on a single resource. It does not implement unrelated functions, ensuring changes to business requirements do not affect its scope.
:::

```python
class UserService:
    
    ...

    def create_user(self, user_data):
        if UserModel.query.filter(UserModel.email == user_data["email"]).first():
            raise UserAlreadyExists("User already exists")
        user = UserModel(
            name=user_data["name"],
            email=user_data["email"],
            password=pbkdf2_sha256.hash(user_data["password"]),
        )
        self.db.session.add(user)
        self.db.session.commit()
        return user
    ...
```

## Conclusion

This layered architecture ensures modularity and separation of concerns. It allows for significant changes without affecting core functionality, such as implementing OAuth, transitioning blueprints to a class-based approach, and adding dependency injection.

:::tip[Additional Info]

- The project uses an **object-oriented** approach.
- It heavily employs **dependency injection**.
- Most third-party libraries are wrapped inside a **service** or **client**.
    - Future plans include implementing interfaces to enforce the **Dependency Inversion Principle**.
      :::