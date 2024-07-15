---
sidebar_position: 2
---

# Stack

Languages and tools

## Language/Framework

The REST API is built with **[Python 3.12.4](https://www.python.org/)** and **[Django Rest Framework 3.15.2](https://www.django-rest-framework.org/)**.

### Why Python and Django?

- **Python**: Chosen because it's the language I've been using the most recently. Its simplicity and readability make development faster and more efficient.
- **Flask**: [Flask](https://flask.palletsprojects.com/en/3.0.x/) was the previous choice, but lots of code were being written for basic CRUD functionality. Django made development faster and more streamlined, and thus became the main choice for this project.

## Tools

The tools used in the development process include:
1. `unittest` - For automated tests.
2. `coverage` - For test coverage reports.
3. `django-cors-headers` - For cors handling
4. `django-filter` - For automatic/east to configure filtering on endpoints
5. `djangorestframework_simplejwt` - For JWT authentication
6. `flake8` - For linting.
7. **Docker** - For containerization.
8. **AWS** - For deployment.
9. **GitHub** - For version control.
10. **GitHub Actions** - For CI/CD.