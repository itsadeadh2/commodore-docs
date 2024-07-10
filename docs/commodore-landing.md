---
slug: /
sidebar_position: 1
---

# [Commodore Landing](https://itsadeadh2.com/)

Welcome to the **Commodore Landing** SPA (Single Page Application) landing page, crafted with React. This page emulates a classic Commodore 64 terminal for an interactive and nostalgic user experience.

🚀 **See the code on [GitHub](https://github.com/itsadeadh2/commodore-landing)**  
✨ **Access the [frontend](https://itsadeadh2.com/)**

## Stack

This project is built with the following technologies:
- **[Node.js](https://nodejs.org/pt)**
- **[React](https://react.dev/)**
- **[JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)**
- **[GitHub Pages](https://pages.github.com/)**

## Purpose

Commodore Landing provides an interactive interface for users to engage with the **[REST API](./REST%20API/overview.md)**. It mimics the vintage Commodore 64 terminal, adding a fun and unique twist to the user experience.

![Commodore Landing](./img/commodore_landing.gif)

## Responsibilities

The primary function of Commodore Landing is to handle user requests through an "emulated" terminal interface.

### Terminal Commands

Users can interact with the terminal using `rootcommand` followed by an `action`, when applicable. Here are some examples:

```sh
contact foo@bar.com
# rootcommand: contact
# action: foo@bar.com

help
# rootcommand: help
# action: None
```

## Infrastructure

### Initial Setup

Initially, Commodore Landing was hosted on AWS. The process involved:
1. Building the project into a **Docker** image.
2. Uploading the image to **ECR** (Elastic Container Registry).
3. Deploying it on an **ECS Service** behind an **Application Load Balancer**.

While this setup was a great learning experience and performed well, it was ultimately overkill for the project's needs. It resulted in higher costs and longer deployment times.

### Current Setup

To optimize costs and deployment efficiency, Commodore Landing was migrated to **GitHub Pages**, where it is **[currently deployed](https://itsadeadh2.github.io/commodore-landing/)**. This new setup is more streamlined and cost-effective.

Enjoy the nostalgic experience of Commodore Landing and feel free to explore the code and functionality on GitHub! ✨