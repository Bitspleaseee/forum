---
title: API-routes
subject: imt3501
author: Ole Martin Ruud
institute: Norwegian University of Science and Technology
lang: en-US
---

# Hosted web-client

- `GET /` - Return a static file `index.html` from `/static`
- `GET /static/<path...>` - Should return any file within the `/static` folder

# API endpoints

- **All routes should be prefixed with `/api`**
- **All POST request should have a [`RequestGuard`](https://rocket.rs/guide/requests/#request-guards)**

## Authentication

- `POST /api/auth` - Client sends a JSON object `AuthRequest`

## Contents

### Routes

- `GET /api/category/<opt_id>` - Client gets all categories or specific category if `opt_id` is `Some(id)`
- `GET /api/category/<id>/threads` - Client gets all threads for a specific category
- `GET /api/thread/<opt_id>` - Client gets all threads (*should be limited*) or specific thread if `opt_id` is `Some(id)`
- `GET /api/thread/<id>/comments` - Client gets all comments for specific thread
- `GET /api/comments/<opt_id>` - Client gets all comments (*should be limited*) or specific comment if `opt_id` is `Some(id)`

- `GET /api/user/<id>` - Get info on specific user
- `GET /api/search?<query>` - Search through categories, threads, comments and users

- `POST /api/content` - All interactions where the client is allowed to alter or add new content (`ContentRequest`)
