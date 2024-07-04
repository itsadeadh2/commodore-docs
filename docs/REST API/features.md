---
sidebar_position: 3
---

# Features

Things that the API can do

:::tip[Swagger]
This is a high-level overview of the API functionalities.
For a more in-depth version, check out the **[swagger documentation.](https://itsadeadh2.com/swagger-ui)** 
:::

## Route traffic to landing page

By accessing the root route of the API (https://itsadeadh2.com) it is going to redirect you to my landing page 
that is hosted on GitHub Pages (https://itsadeadh2.github.io/commodore-landing/).

**[why gh pages?](/#infrastructure)**


## Send contact info

The `/api/contact` resource of the API allows users to send in an email address and then emails them my contact information
it also stores the given email into a DynamoDB database so that I can see who requested my contact info.

:::info
I might simplify this flow in the future.

While I do think it's fair for the user to give me his contact info in order to access mine, I do not want
some basic contact info to be hidden behind this.

I might provide some basic contact info that doesn't require email, and additional ones upon the user's sending his own.

Also, the email will not be required if the user is **logged in**.
:::

## Login/Register with google

The API also provides the ability for the user to register/login with Google.
This functionality was designed to be used primarily with the **[frontend](../commodore-landing.md)**.

As of now, there isn't really a reason for users to do that, but I do plan to include some additional features
into the API that will require the user to be registered in order to use.

