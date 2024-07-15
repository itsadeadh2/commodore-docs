---
sidebar_position: 4
---

# Features

Discover what the API can do!

## Send Contact Info

:::warning[email required]
:::

The `/contact` endpoint allows users to submit an email address and receive my contact information via email. It also stores the provided email in the database to keep track of who requested my contact info.


## Register/Login/Logout

The api allows users to register, log in and log out.
By doing so you'll get access to some additional functionalities such as the games

It is possible to log in using sessions with CSRF or JWT tokens.

## Hangman 
:::warning[registered users only]
:::
By using the resources on the `/hangman` endpoint you can play a quick game of [hangman](https://en.wikipedia.org/wiki/Hangman_(game)) on the api.
And it also stores your scores on a leaderboard.

## Projects 
The `/projects` endpoint returns all of my pet projects that I have registered within the application.  

## Scores

The `/scores` endpoint returns a list of scores for the games available in the api. At the moment, only **Hangman** is available, 
but, it is implemented in a way that would make it easily extensible if any other games are added in the future.