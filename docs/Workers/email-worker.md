---
sidebar_position: 1
---

# Email Worker

Worker that runs email operations

See on **[GitHub](https://github.com/itsadeadh2/email-sender-worker)**

## Stack

**[Python](https://www.python.org/) | [SQS](https://aws.amazon.com/sqs/) | [AWS Lambda](https://aws.amazon.com/ecs/)**

## Purpose

This worker does all the heavy lifting necessary in order to send emails.
As of now it only sends emails related to contact information requests, but additional
scenarios might be included in the future.

## Reasoning

The reason behind creating this worker was to make the email sending process asynchronous.

Sending emails can be both a resource and time-consuming task. If I were to keep this functionality
within the **[REST API](../REST API)** it would very likely have made the response time of the endpoint
way too slow, so I decided to use a worker instead.

## Infrastructure

The infrastructure behind this worker is actually very simple.

The worker itself is a lambda function, and it is configured to be triggered by an SQS Queue.

So, upon a message being added to the queue, the worker is going to be triggered and process the given message.
After successfully processing it, the message is deleted.

All of this is deployed using **Github Actions** and **AWS Cloudformation**


