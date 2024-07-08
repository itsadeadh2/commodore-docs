---
sidebar_position: 5
---

# Infrastructure

Explore the resources, pipelines, and integrations of the project.

## Cloud Provider

This project is hosted on **AWS**, utilizing the following resources:

- **CloudFormation**: Infrastructure as Code (IaC) tool.
- **Elastic Container Registry (ECR)**: Private Docker registry.
- **Elastic Container Service (ECS)**: Container management.
- **CloudWatch**: Logging service.
- **AWS RDS**: Database for persistence (PostgreSQL).
- **Elastic Load Balancer (ELB)**: Routing, load balancing, and SSL termination.
- **VPC and Public Subnet**: Networking components.
- **Route 53**: Domain management service.

All these resources are automatically created and configured using a set of **CloudFormation** templates.

![Infrastructure](./img/rest_api_infra.png)

:::note
I **chose** not to deploy the database into a private subnet to save costs on **AWS Nat Gateways**.  
It is not ideal, but it wasn't an uninformed decision.
  :::
## CI/CD

The CI/CD pipeline for this project is managed by **GitHub Actions**. It handles:

- Testing
- Lint checking
- Building
- Deploying the infrastructure and application to AWS