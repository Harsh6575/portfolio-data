---
title: "Tailor Track"
slug: tailor-management-system
description: "A tailoring business management system for small and medium tailoring shops, built as a Turborepo monorepo with a Next.js web app, an Expo mobile app, and an Express + PostgreSQL API sharing a single validation layer."
category: Full Stack
status: In Progress
date: "Jun 2026 - Present"
technologies:
  - Next.js
  - React
  - Expo
  - React Native
  - Express
  - PostgreSQL
  - Prisma
  - Redis
  - TypeScript
  - Zod
  - Tailwind CSS
  - shadcn/ui
  - TanStack Query
  - Zustand
  - Turborepo
features:
  - Designed around the real day-to-day workflow of a family-run tailoring shop
  - Multi-shop workspaces with role-based membership (owner/staff)
  - Customer management with per-customer measurement records
  - Shared validation and type layer across web, mobile, and API
  - Cookie-based auth for web, token + SecureStore auth for mobile
  - Mobile app built with Expo, covering auth, shops, customers, and measurements
links: []
order: 1
hidden: false
---

A tailoring business management system built for a family member's tailoring shop, and a personal experiment in running a monorepo across a web app, a mobile app, and an API with a single shared codebase for validation and types.

## How It Works

- A Turborepo + pnpm workspace holds three apps - a Next.js web app, an Expo/React Native mobile app, and an Express API - alongside shared packages for Zod validation schemas and shadcn/Radix UI components.
- The web app authenticates over httpOnly cookies, while the mobile app authenticates with tokens stored in Expo SecureStore, both against the same Express API.
- Prisma models users, shops, and shop membership so a single account can belong to multiple shops with an OWNER or STAFF role, alongside per-shop customers and their measurements.
- Redis backs rate limiting and background jobs via BullMQ, and the same Zod schemas validate input on both the API and the clients that consume it.

## Key Highlights

- Designed around the real day-to-day workflow of a family-run tailoring shop
- Multi-shop workspaces with role-based membership (owner/staff)
- Customer management with per-customer measurement records
- Shared validation and type layer across web, mobile, and API
- Cookie-based auth for web, token + SecureStore auth for mobile
- Mobile app built with Expo, covering auth, shops, customers, and measurements
- Orders, payments, and delivery tracking are still in progress

## Tech Stack

- **Next.js & React** for the web app
- **Expo & React Native** for the mobile app
- **Express, Prisma & PostgreSQL** for the API and data layer
- **Redis** for rate limiting and background jobs
- **Zod** for shared validation across every app
- **TanStack Query & Zustand** for data fetching and client state
- **Turborepo & pnpm** to manage the monorepo
