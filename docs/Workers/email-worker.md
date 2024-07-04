---
sidebar_position: 1
---

# Email Worker

Welcome to the **Email Worker** project, designed to efficiently handle email operations.

🚀 **See the code on [GitHub](https://github.com/itsadeadh2/email-sender-worker)**

## Stack

This project is built with the following technologies:
- **[Python](https://www.python.org/)**
- **[SQS](https://aws.amazon.com/sqs/)**
- **[AWS Lambda](https://aws.amazon.com/ecs/)**

## Purpose

The Email Worker handles all the heavy lifting required for sending emails. Currently, it focuses on sending emails related to contact information requests, but additional scenarios may be supported in the future.

## Reasoning

The primary reason for creating this worker was to make the email sending process asynchronous. Sending emails can be resource-intensive and time-consuming. Keeping this functionality within the **[REST API](../REST API)** could significantly slow down endpoint response times. Therefore, I opted for a worker to handle this task separately.

## Infrastructure

The infrastructure for this worker is straightforward:

1. The worker is an AWS Lambda function.
2. It is triggered by messages added to an SQS Queue.
3. When a message is added to the queue, the worker is triggered to process the message.
4. After successfully processing the message, it is deleted from the queue.

Deployment is managed using **GitHub Actions** and **AWS CloudFormation**.

This setup ensures efficient, asynchronous email processing, improving overall system performance and responsiveness.