---
title: "Patient Management System"
slug: patient-management-system
description: "A distributed healthcare operations system built on Spring Boot microservices, with an API Gateway, gRPC for inter-service calls, and Kafka for async event streaming."
category: Backend
status: Completed
date: "Aug - Sep 2025"
technologies:
  - Java
  - Spring Boot
  - Microservices
  - gRPC
  - Kafka
  - PostgreSQL
  - Docker
  - JWT
features:
  - 5-service microservices architecture
  - API Gateway with request routing & auth
  - gRPC inter-service communication
  - Kafka event streaming for analytics
  - JWT authentication & authorization
  - Docker containerized deployment
links:
  - type: github
    label: Code
    url: https://github.com/harsh6575/patient-management-spring-boot
order: 7
hidden: true
---

A distributed healthcare operations system built to learn and apply enterprise-grade microservices patterns in a realistic domain, rather than a single monolithic service.

## How It Works

- Five independent services handle distinct responsibilities and communicate over gRPC, which keeps inter-service calls fast and strongly typed compared to plain REST.
- An API Gateway sits in front of the services, handling request routing, authentication, and rate limiting, so individual services don't each need to reimplement that logic.
- Kafka streams events between services asynchronously, so downstream analytics can process data without blocking the request path that generated it.
- JWT authentication secures the gateway and inter-service calls, and the whole system runs as containerized services via Docker.

## Key Highlights

- 5-service microservices architecture
- API Gateway with request routing & auth
- gRPC inter-service communication
- Kafka event streaming for analytics
- JWT authentication & authorization
- Docker containerized deployment

## Tech Stack

- **Spring Boot & Java** for the individual microservices
- **gRPC** for typed, low-latency inter-service communication
- **Kafka** for asynchronous event streaming
- **PostgreSQL** for persistent storage
- **Docker** for containerized deployment
