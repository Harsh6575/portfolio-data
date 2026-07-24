---
title: "Shortify - URL Shortener"
slug: shortify
description: "A high-throughput URL shortening platform engineered to demonstrate advanced system design principles and scalable backend architecture. Features a collision-resistant custom hashing generator, scalable MongoDB persistence, and an optimized Redis caching hierarchy to achieve sub-millisecond redirect lookups."
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
  - Hash-based short ID generation using SHA-256 + Base62 encoding
  - Three-tier caching architecture with Redis (7-day TTL)
  - Async database operations using Motor (MongoDB async driver)
  - RESTful API with automatic documentation (Swagger/OpenAPI)
  - Deterministic URL shortening with collision detection
  - Real-time cache invalidation and TTL management
  - Scalable MongoDB document storage for long-term URL mapping
  - Horizontal scalability with stateless API design
links:
  - type: github
    label: View Source
    url: https://github.com/harsh6575/shortify
order: 1
hidden: false
---

Shortify is a high-throughput URL shortening platform built to explore advanced
system design principles rather than just wrap a database in an API. The
redirect path is optimized end-to-end: a collision-resistant SHA-256 + Base62
hashing scheme generates short IDs, MongoDB provides durable long-term storage,
and a three-tier Redis caching layer keeps hot redirects at sub-millisecond
latency.

## Key Highlights

- Hash-based short ID generation using SHA-256 + Base62 encoding
- Three-tier caching architecture with Redis (7-day TTL)
- Async database operations using Motor (MongoDB async driver)
- RESTful API with automatic documentation (Swagger/OpenAPI)
- Deterministic URL shortening with collision detection
- Real-time cache invalidation and TTL management
- Scalable MongoDB document storage for long-term URL mapping
- Horizontal scalability with stateless API design
