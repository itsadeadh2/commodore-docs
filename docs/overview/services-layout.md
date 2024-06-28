---
sidebar_position: 3
---

# Services Layout

The following image represents the current services layout.

![Services Layout](./img/services_layout.png)

When we strip away the underlying infrastructure tools, we are left with the following services:
- **[API Gateway](/services/api-gateway)**
- **[Commodore Landing](/services/commodore-landing)**
- **[Email Sender](/services/email-sender)**
- **[Email Worker](/services/email-worker)**
- **[Users Manager](/services/users-manager)**
- **[Games Service](/services/games-service)**

The main idea behind this layout is to isolate most services from incoming internet traffic for security reasons while allowing inter-service communication.

Additionally, I want the flexibility to run asynchronous operations, jobs, databases, storage systems, or any other services, and only expose what I choose through the **API Gateway**.

You can find more details about each of these services by clicking on them in the list above.
