---
title: "Tailor Track"
slug: tailor-track
description: "A tailoring business management system for small and medium tailoring shops, built as a Turborepo monorepo with a Next.js web app, an Expo mobile app, and an Express + PostgreSQL API sharing a single validation layer."
category: Full-Stack
status: In Progress
date: "Oct 2025 - Present"
technologies:
  - Next.js
  - React
  - TypeScript
  - Node.js
  - Express
  - PostgreSQL
  - Prisma
  - Redis
  - REST APIs
  - Tailwind CSS
  - shadcn/ui
  - TanStack Query
  - Zustand
  - Zod
  - Expo
  - React Native
  - Turborepo
  - Vitest
  - Docker
  - Jenkins
  - SonarQube
features:
  - Designed around the real day-to-day workflow of a family-run tailoring shop
  - Multi-shop workspaces with role-based membership (owner/staff)
  - Customer management with per-customer measurement records
  - Shared validation and type layer across web, mobile, and API
  - Cookie-based auth for web, token + SecureStore auth for mobile
  - Mobile app built with Expo, covering auth, shops, customers, and measurements
  - 260+ API tests across services, controllers, middleware, and routes
  - Jenkins pipeline for lint, typecheck, tests, build, and Docker images
  - Redis-backed rate limiting, structured request logging, and bcrypt password hashing
links: []
order: 1
hidden: false
---

A tailoring business management system built for a family member's tailoring shop, and a personal experiment in running a monorepo across a web app, a mobile app, and an API with a single shared codebase for validation and types.

It started in Oct 2025 as two separate repos, a Next.js frontend and an Express backend. In Jun 2026 I moved both into a Turborepo monorepo, carried most of their code over, and added the Expo mobile app.

## How It Works

- A Turborepo + pnpm workspace holds three apps - a Next.js web app, an Expo/React Native mobile app, and an Express API - alongside shared packages for Zod validation schemas and shadcn/Radix UI components.

```mermaid
flowchart LR
    subgraph shared["Shared packages"]
        V["Zod validation"]
        U["UI components"]
    end
    W["Next.js web app"] -- "httpOnly cookies" --> API["Express API"]
    M["Expo mobile app"] -- "Bearer token from SecureStore" --> API
    V -.-> W & M & API
    U -.-> W
    API --> PG[("PostgreSQL via Prisma")]
    API --> R[("Redis")]
```

- The web app authenticates over httpOnly cookies, while the mobile app authenticates with tokens stored in Expo SecureStore, both against the same Express API.
- Prisma models users, shops, and shop membership so a single account can belong to multiple shops with an OWNER or STAFF role, alongside per-shop customers and their measurements.
- Every request is logged through morgan into winston and passes a Redis-backed rate limiter. Protected routes then check the JWT and a Redis denylist, so logout, password change and account deletion revoke the current token immediately. Shop routes also check the caller is a member of that shop. Passwords are hashed with bcrypt, and the same Zod schemas validate input on both the API and the clients that consume it.

```mermaid
flowchart TD
    A["Request"] --> B["morgan → winston logging"] --> C["Rate limiter (Redis)"] --> D["JWT check + denylist (Redis)"] --> E["Shop membership check"] --> F["Controller → service"] --> G[("PostgreSQL")]
```

- The API has 260+ tests written with Vitest and Supertest, covering services, controllers, middleware, and routes.
- A Jenkins pipeline runs lint, typecheck, tests, the build, and Docker image builds for the API and web app, with SonarQube used for code-quality analysis.

```mermaid
flowchart LR
    A["Checkout"] --> B["Install with pnpm"] --> C["Lint + typecheck"] --> D["Tests"] --> E["Build"] --> F["Docker images"]
```

Turborepo filters each stage to the packages changed since the last commit or the target branch, so a change to one app doesn't rebuild the others.

## Key Highlights

- Designed around the real day-to-day workflow of a family-run tailoring shop
- Multi-shop workspaces with role-based membership (owner/staff)
- Customer management with per-customer measurement records
- Shared validation and type layer across web, mobile, and API
- Cookie-based auth for web, token + SecureStore auth for mobile
- Mobile app built with Expo, covering auth, shops, customers, and measurements
- 260+ API tests across services, controllers, middleware, and routes
- Jenkins pipeline for lint, typecheck, tests, build, and Docker images
- Redis-backed rate limiting, structured request logging, and bcrypt password hashing
- Orders, payments, and delivery tracking are still in progress

## Tech Stack

- **Next.js & React** for the web app
- **Expo & React Native** for the mobile app
- **Node.js, Express, Prisma & PostgreSQL** for the API and data layer
- **Redis** for rate limiting and revoking access tokens
- **Zod** for shared validation across every app
- **TanStack Query & Zustand** for data fetching and client state
- **Turborepo & pnpm** to manage the monorepo
- **Vitest & Supertest** for API tests
- **Docker, Jenkins & SonarQube** for builds, CI, and code quality
