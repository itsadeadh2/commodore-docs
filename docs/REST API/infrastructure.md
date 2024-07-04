---
sidebar_position: 4
---

# Infrastructure

Resources, pipelines, integrations


## Cloud Provider

This project is hosted on AWS, and it makes use of the following resources:

- **Cloudformation**: IaC tool
- **Elastic Container Registry**: Private docker registry
- **Elastic Container Service**: Container management
- **CloudWatch**: Logs
- **DynamoDB**: Persistence 
- **Elastic Load Balancer**: Routing, Load Balancing, SSL
- **VPC, Public Subnet**: Networking
- **Route 53**: Domain management

All of these resources are automatically created and configured using a set of **cloudformation** templates.

![infrastructure](./img/rest_api_infra.png)
## CI/CD

The CI/CD tool used for this project is GitHub Actions.
GitHub Actions is responsible for testing, linting, building and deploying the infrastructure
and the application to AWS.