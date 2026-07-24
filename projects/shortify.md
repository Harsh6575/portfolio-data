---
title: "Shortify - URL Shortener"
slug: shortify
description: "A URL shortener built to practice backend system design past basic CRUD. Combines deterministic hashing, MongoDB storage, and a tiered Redis cache to keep redirects fast as the mapping table grows."
category: Backend
status: Completed
date: "Nov 2025"
technologies:
  - Python
  - FastAPI
  - MongoDB
  - Redis
  - Docker
features:
  - Hash-based short ID generation using SHA-256 + Base62 encoding, scoped per user
  - Three-tier caching architecture with Redis (7-day TTL, refreshed on every hit)
  - Full CRUD API - create, redirect, delete, and list recent short URLs
  - Async database operations using Motor (MongoDB async driver)
  - Deterministic hashing with salted re-hash collision handling
  - Automatic cache invalidation and TTL-based expiry
  - Scalable MongoDB document storage for long-term URL mapping
  - Horizontal scalability with a stateless, Docker-ready API design
links:
  - type: github
    label: View Source
    url: https://github.com/harsh6575/shortify
order: 6
hidden: false
---

Shortify started as a way to practice system design beyond basic CRUD, so most of the interesting work happens on the redirect path. Hashing, storage, and caching are all tuned to keep lookups fast as the URL table grows.

## How It Works

- Incoming URLs get a short ID from a SHA-256 hash of the long URL plus user ID, encoded in Base62 for a compact, URL-safe string. If that ID already exists, a UUID salt gets appended and the URL is re-hashed, which keeps the scheme deterministic without needing a central counter.
- MongoDB holds the long-term URL mappings. It was picked for its flexible document model and the ability to scale horizontally as the dataset grows.
- A three-tier Redis cache sits in front of MongoDB with a 7-day TTL that resets on every access, so hot redirects resolve in well under a millisecond without ever touching the database.

```
Request → Redis (Cache) → MongoDB (Source of Truth)
          ↓ miss              ↓ found
          Query DB --------→ Cache result
```

- Database calls run through Motor, MongoDB's async driver, so the FastAPI service can handle many concurrent redirects without blocking.
- Beyond create-and-redirect, the API supports deleting short URLs and listing recently created ones, with cache entries invalidated automatically on delete.
- The API is documented automatically through FastAPI's built-in Swagger/OpenAPI support, and ships with a Docker Compose setup for local services.

## Key Highlights

- Hash-based short ID generation using SHA-256 + Base62 encoding, scoped per user
- Three-tier caching architecture with Redis (7-day TTL, refreshed on every hit)
- Full CRUD API - create, redirect, delete, and list recent short URLs
- Async database operations using Motor (MongoDB async driver)
- Deterministic hashing with salted re-hash collision handling
- Automatic cache invalidation and TTL-based expiry
- Scalable MongoDB document storage for long-term URL mapping
- Horizontal scalability with a stateless, Docker-ready API design

## Tech Stack

- **FastAPI** for async request handling and automatic API docs
- **MongoDB** for durable, horizontally scalable URL storage
- **Redis** for sub-millisecond cache reads on hot redirects
- **Docker** for a consistent, reproducible deployment environment
