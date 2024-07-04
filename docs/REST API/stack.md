---
sidebar_position: 2
---

# Stack

Languages, tools and architecture

## Language/Framework

The REST API is made with **[Python 3.12.4](https://www.python.org/)** and **[Flask](https://flask.palletsprojects.com/en/3.0.x/)**

Python was chosen because it is a language I have been using the most recently
and flask was chosen because I wanted to refresh my knowledge about it.

There weren't other requirements that made me choose Python
it could have been Node with JavaScript and I believe it would work the same way.

Flask on the other hand, besides being a framework that I wanted to get back to speed with
also seems to be more lightweight and less opinionated than Django.

Being less opinionated and more "bare bones" was an important thing to me since I wanted to
test out some architectural patterns as well as to try handling things like authentication all
by myself instead of relying on a framework.

## Tools

The tools I used in the development process were:
1. Python's `unittest` library for automated tests
2. Python's `coverage` library for test coverage reports
3. Python's `flake8` for linting
4. Docker for containerization
5. AWS for deployment
6. GitHub for VCS
7. GitHub Actions for CI/CD

## Architecture

The project was structured using a **[layered architecture](https://cs.uwaterloo.ca/~m2nagapp/courses/CS446/1195/Arch_Design_Activity/Layered.pdf)** approach.
Until now, I have chosen to use tree layers: **infrastructure, domain and setup**.

### Setup

The setup layer is responsible for components that help bootstrap the application.
Originally these components were also a parte of the **infrastructure** layer but as they grew
in size and complexity I decided to create a separate layer for them.
Most of these components interact directly with the flask `app` and add additional functionality into it
before the app is served.

Things such as **configs, cors, logger, dependency injector and blueprints registering** are all done in this layer.

### Infrastructure

The infrastructure layer is responsible for base components that are required in order to achieve the desired functionality
of the domain.

Thing such as **custom errors, services, schemas and blueprints** are all stored in this layer.

### Domain

The domain layer is responsible for the actual domain/business logic that we want to achieve for a specific resource.
The components in this layer can be seen as orchestrators that basically use the available resources
on the infrastructure layer to achieve the desired outcome.

For now, this layer only contain **handlers** that are directly tied to a specific endpoint resource.

### Conclusion

With this layered architecture, the application achieves a great degree of modularity and
separation of concerns.

With this approach I was able to change significant parts of the implementation multiple times in the past few days.
Such as implementing OAuth, changing blueprints from a functional approach to a class approach, adding dependency injection
and even with all of these modifications, the core functionality of the API endpoints were still the same.

:::tip[Additional Info]

- This project uses an **object-oriented** approach
- This project makes heavy use of **dependency injection**
- Most of the third party libraries used are wrapped inside a **service** or a **client**
  - I might implement interfaces for all of these in the future to enforce the **Dependency Inversion Principle**
:::