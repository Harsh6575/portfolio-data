---
title: "Hotel Reservation Platform"
slug: hotel-reservation-platform
description: "A full-stack hospitality marketplace inspired by Airbnb, built with Next.js and Prisma. Covers multi-provider auth, host listings with map-based search, and a full booking flow from browsing to reservation."
category: Full-Stack
status: Completed
date: "2022"
technologies:
  - Next.js
  - TypeScript
  - Tailwind CSS
  - Prisma
  - MongoDB
  - NextAuth.js
  - React-Leaflet
  - Cloudinary
  - Zustand
features:
  - Multi-provider authentication - GitHub, Google, and email/password
  - Host workflow for creating listings with Cloudinary image uploads
  - Advanced search and filtering by category, location, dates, and guests
  - Interactive map-based location search and picker
  - Booking system with date-range reservations and price calculation
  - Favorites and a dedicated trips/reservations dashboard
  - Responsive design across all devices
links:
  - type: github
    label: Code
    url: https://github.com/harsh6575/airbnb-clone
  - type: live
    label: Demo
    url: https://hotel-reservation-harsh6575.vercel.app/
order: 2
hidden: false
---

A full-stack hospitality marketplace inspired by Airbnb, covering the full booking experience from browsing listings to confirming a reservation. It's also the project that helped land my previous full-stack role, and the one where a lot of my early full-stack habits took shape.

## How It Works

- Authentication runs through NextAuth.js with GitHub, Google, and a bcrypt-backed credentials flow, so signing up isn't locked to a single method.
- Hosts list properties through a multi-step form, and photos go straight to Cloudinary instead of sitting on the application server.
- Search goes beyond a text box: React-Leaflet renders an interactive map so guests can browse and narrow listings by location.
- Prisma sits over MongoDB as a type-safe ORM, modeling users, listings, reservations, and linked OAuth accounts as related entities, with reservation pricing derived from the selected date range.
- Zustand handles the lighter client state, modals and search filters, while Tailwind CSS keeps the UI usable from phone to desktop.
- Guests can favorite listings and track upcoming and past stays from a dedicated trips page.

## Key Highlights

- Multi-provider authentication - GitHub, Google, and email/password
- Host workflow for creating listings with Cloudinary image uploads
- Advanced search and filtering by category, location, dates, and guests
- Interactive map-based location search and picker
- Booking system with date-range reservations and price calculation
- Favorites and a dedicated trips/reservations dashboard
- Responsive design across all devices

## Tech Stack

- **Next.js & TypeScript** for the full-stack application
- **Prisma & MongoDB** for type-safe, flexible-schema data storage
- **NextAuth.js** for multi-provider authentication
- **React-Leaflet** for interactive map search
- **Cloudinary** for image hosting
- **Zustand** for client-side UI state
