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

**All routes should be prefixed with `/api`**

## Authentication

- `POST /api/auth` - Client sends a JSON object `AuthRequest`

## Contents

### Prerequisites

Assumes that the ids are defined as:

```rust
/// Marker trait to simplify implementations of actions on any id-type
trait Id {}

#[derive(Clone, Copy, PartialEq, PartialOrd, Eq, Ord, Debug)]
struct CategoryId(u32);
impl Id for CategoryId {}

#[derive(Clone, Copy, PartialEq, PartialOrd, Eq, Ord, Debug)]
struct ThreadId(u32);
impl Id for ThreadId {}

#[derive(Clone, Copy, PartialEq, PartialOrd, Eq, Ord, Debug)]
struct CommentId(u32);
impl Id for CommentId {}

#[derive(Clone, Copy, PartialEq, PartialOrd, Eq, Ord, Debug)]
struct UserId(u32);
impl Id for UserId {}

/// Optional wrapper for any type which implements Id
struct OptId<I: Id>(Option<I>);

impl<I: Id> Deref for OptId<I> {
    type Target = Option<I>;

    fn deref(&self) -> &Self::Target {
        &self.0
    }
}
```

### Routes

- `GET /api/category/<opt_id>` - Client gets all categories or specific category if `opt_id` is `Some(id)`
- `GET /api/category/<id>/threads` - Client gets all threads for a specific category
- `GET /api/thread/<opt_id>` - Client gets all threads (*should be limited*) or specific thread if `opt_id` is `Some(id)`
- `GET /api/thread/<id>/comments` - Client gets all comments for specific thread
- `GET /api/comments/<opt_id>` - Client gets all comments (*should be limited*) or specific comment if `opt_id` is `Some(id)`

- `GET /api/user/<id>` - Get info on specific user
- `GET /api/search?<query>` - Search through categories, threads, comments and users

**NB! All POST request should have a [`RequestGuard`](https://rocket.rs/guide/requests/#request-guards)**

- `POST /api/category` - Make new or edit category based on content of JSON object `ContentRequest`
- `POST /api/thread` - Make new or edit thread based on content of JSON object `ContentRequest`
- `POST /api/comment` - Make new or edit comment based on content of JSON object `ContentRequest`
