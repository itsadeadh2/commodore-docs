---
sidebar_position: 2
---

# Stack

Languages, tools, and architecture

## Language/Framework

The REST API is built with **[Python 3.12.4](https://www.python.org/)** and **[Flask](https://flask.palletsprojects.com/en/3.0.x/)**.

### Why Python and Flask?

- **Python**: Chosen because it's the language I've been using the most recently. Its simplicity and readability make development faster and more efficient.
- **Flask**: Selected to refresh my knowledge. Flask is lightweight and less opinionated compared to Django, providing more flexibility for experimenting with architectural patterns and handling features like authentication independently.

## Tools

The tools used in the development process include:
1. `unittest` - For automated tests.
2. `coverage` - For test coverage reports.
3. `flake8` - For linting.
4. **Docker** - For containerization.
5. **AWS** - For deployment.
6. **GitHub** - For version control.
7. **GitHub Actions** - For CI/CD.

## Architecture

The project follows a **[layered architecture](https://cs.uwaterloo.ca/~m2nagapp/courses/CS446/1195/Arch_Design_Activity/Layered.pdf)** approach, divided into three layers: **Setup, Infrastructure, and Domain**.

### Setup

This layer is responsible for bootstrapping the application. Initially part of the **Infrastructure** layer, it was separated due to growing size and complexity. Components in this layer interact directly with the Flask `app`, adding functionality before the app is served.

Key components include:
- **Configurations**
- **CORS**
- **Logger**
- **Dependency Injector**
- **Blueprints Registration**

### Infrastructure

The Infrastructure layer contains base components required for domain functionality.

Key components include:
- **Custom Errors**
- **Services**
- **Schemas**
- **Blueprints**

### Domain

The Domain layer handles the actual business logic for specific resources. Components in this layer act as orchestrators, using infrastructure resources to achieve desired outcomes.

Current components:
- **Handlers** tied directly to endpoint resources.

### Conclusion

This layered architecture ensures modularity and separation of concerns. It allows for significant changes without affecting core functionality, such as implementing OAuth, transitioning blueprints to a class-based approach, and adding dependency injection.

:::tip[Additional Info]

- The project uses an **object-oriented** approach.
- It heavily employs **dependency injection**.
- Most third-party libraries are wrapped inside a **service** or **client**.
  - Future plans include implementing interfaces to enforce the **Dependency Inversion Principle**.
:::