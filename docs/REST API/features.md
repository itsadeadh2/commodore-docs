---
sidebar_position: 3
---

# Features

Discover what the API can do!

:::tip[Swagger]
This is a high-level overview of the API functionalities.
For detailed information, check out the **[Swagger documentation](https://itsadeadh2.com/swagger-ui)**.
:::

## Route Traffic to Landing Page

By accessing the root route of the API (https://itsadeadh2.com), you will be redirected to my landing page hosted on GitHub Pages (https://itsadeadh2.github.io/commodore-landing/).

**[Why GitHub Pages?](/#infrastructure)**

## Send Contact Info

:::warning[email required]
:::

The `/api/contact` endpoint allows users to submit an email address and receive my contact information via email. It also stores the provided email in a DynamoDB database to keep track of who requested my contact info.

:::info
Future Plans:
- Simplify this flow.
- Provide basic contact info without requiring an email.
- Offer additional contact info upon receiving the user's email.
- No email required if the user is **logged in**.
  :::

## Register/Login/Logout

The api allows users to register, log in and log out.
By doing so you'll get access to some additional functionalities such as the games

## Hangman 
:::warning[registered users only]
:::
By using the resources on the `/api/games/hangman` endpoint you can play a quick game of [hangman](https://en.wikipedia.org/wiki/Hangman_(game)) on the api.
And it also stores your scores on a leaderboard.