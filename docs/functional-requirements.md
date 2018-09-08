---
title: Functional Requirements
subject: imt3501
author:
- Ole Martin Ruud
institute: Norwegian University of Science and Technology
lang: en-US
---


# Task overview

- Simple GUI
- Controller
- Database

- Sign up/login
- Create topics
- Post replies and new messages

- Visitors and logged in users into user groups
- Privileges and rights are given based on these groups

# Forum posts

## Post handling

- Replies should refer to the post they answered
- Can create hierartical views of answers to organize a thread or show a linear thread based on arrival of answer

## Post hierarchy

- Category (made by moderator)
    - Thread (made by users)
        - Messages and replies (made by users)

# Usergroups

All groups (except admin) should have a limited actions per unit time, e.g can post 1 message per 5 seconds.

- Admin
    - access to everything
    - administrate usergroups
    - hide categories
- Moderator
    - hide messages from users (to remove explicit content)
        - should not directly delete the messages because an attacker that get elevated privilages could wipe the database
    - add/alter categories
- User
    - create topics/threads
    - change your own topics/threads
    - hide your own topics/threads
- Visitors
    - view content of threads


# Functional requirements of processes

## GUI client

- Web client
- Encrypted communication with the server

## Controller

- Strong input validation (reject all invalid requests)
- Several servers to provide redundancy against DoS
- Separate authentication server which gives back a token or similar

## Database

- Vertification of authentication before every write operation
- Separate user and post database (post database contains simple user info to a user to a post)

# DFD-diagram

See [assets/dfd-draft.xml](assets/dfd-draft.xml) which is a diagram created using [draw.io](draw.io)
