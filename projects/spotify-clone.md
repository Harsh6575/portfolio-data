---
title: "Spotify Clone - Music Streaming Platform"
slug: spotify-clone
description: "A full-stack music streaming app inspired by Spotify, built with Next.js and Supabase. Handles song uploads, playback, liked songs, and Stripe-powered premium subscriptions."
category: Full-Stack
status: Completed
date: "Aug - Sep 2023"
technologies:
  - Next.js
  - TypeScript
  - Supabase
  - Stripe
  - Zustand
  - Tailwind CSS
features:
  - Song upload with audio and cover image storage
  - Custom audio player with playback controls
  - Liked songs and personal library
  - Search across the song catalog
  - Stripe-powered premium subscription checkout and billing
  - Email/password and OAuth authentication via Supabase
links:
  - type: github
    label: Code
    url: https://github.com/harsh6575/spotify-clone
order: 3
hidden: false
---

A full-stack music streaming app inspired by Spotify, tying song upload, playback, and premium subscriptions together in one app.

## How It Works

- Supabase covers authentication, a Postgres database, and file storage in one project, so uploaded songs and cover images are stored and served without standing up a separate backend service.
- Tracks go up with their metadata through an upload modal, and songs, liked-song relations, and user records all live as related Postgres tables.
- Playback runs through a custom audio player built on `use-sound`, with Zustand holding the player state so it survives navigation between pages instead of resetting on every route change.
- Stripe handles premium subscriptions end to end. Products, prices, and customer billing get synced into Supabase tables (`customers`, `products`, `prices`, `subscriptions`), and subscription status from those tables is what gates the premium features.
- Tailwind CSS and Radix UI primitives (dialogs, sliders) round out the player and modal interfaces.

## Key Highlights

- Song upload with audio and cover image storage
- Custom audio player with playback controls
- Liked songs and personal library
- Search across the song catalog
- Stripe-powered premium subscription checkout and billing
- Email/password and OAuth authentication via Supabase

## Tech Stack

- **Next.js & TypeScript** for the full-stack application
- **Supabase** for auth, database, and file storage
- **Stripe** for subscription billing
- **Zustand** for player and modal state
- **Tailwind CSS & Radix UI** for the interface
