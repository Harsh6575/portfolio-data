---
title: "Messenger Clone - Real-Time Chat App"
slug: messenger-clone
description: "Real-time one-on-one and group chat with image messages and live read receipts."
category: Full-Stack
status: Completed
date: "May - Jul 2023"
technologies:
  - Next.js
  - React
  - TypeScript
  - Node.js
  - Tailwind CSS
  - MongoDB
  - Prisma
  - NextAuth.js
  - Pusher
  - Cloudinary
features:
  - One-on-one and group conversations
  - Real-time message delivery via Pusher, no polling
  - Read receipts showing who has seen a message
  - Image messages with Cloudinary upload
  - Online/offline presence indicators
  - Multi-provider authentication - GitHub, Google, and email/password
links:
  - type: github
    label: Code
    url: https://github.com/harsh6575/messanger-clone-next
order: 7
hidden: false
---

A real-time chat app covering one-on-one and group conversations, image messages, and read receipts, built on a Next.js and Prisma stack mainly to get real-time architecture under my fingers.

## How It Works

- Sign-in goes through NextAuth.js, with GitHub, Google, and a bcrypt-backed credentials option side by side.
- Prisma models users, conversations, and messages over MongoDB, and an `isGroup` flag on each conversation is what separates a 1:1 thread from a named group chat.
- Pusher pushes new messages and seen-status updates to every connected client, so conversations stay live without polling the server.
- A message can carry an image uploaded through Cloudinary, either alongside its text or on its own.
- Each message keeps a list of who has seen it, which is what drives the read receipts in the UI.

## Key Highlights

- One-on-one and group conversations
- Real-time message delivery via Pusher, no polling
- Read receipts showing who has seen a message
- Image messages with Cloudinary upload
- Online/offline presence indicators
- Multi-provider authentication - GitHub, Google, and email/password

## Tech Stack

- **Next.js, React, TypeScript & Node.js** for the full-stack application
- **Tailwind CSS** for responsive chat UI styling
- **Prisma & MongoDB** for the data layer
- **NextAuth.js** for multi-provider authentication
- **Pusher** for real-time message delivery
- **Cloudinary** for image message hosting
