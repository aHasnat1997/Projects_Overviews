# WabiSaviArt

## Overview

WabiSaviArt is an Etsy-inspired, multi-vendor marketplace that emphasizes transparency, authenticity, and community trust. The platform connects buyers and verified makers through role-based dashboards, secure checkout, messaging, and a rich product catalog that supports variants, media, and storytelling.

## Problem / Challenge

The client needed a production-ready marketplace where sellers could manage products, orders, and shop identity while buyers could browse, purchase, and communicate seamlessly. Beyond standard e-commerce, the platform had to support authenticity signals such as maker verification, imported reviews, transparent fees, and admin oversight of listings and disputes. The system also required reliable media handling and multi-seller payment flows without compromising performance or maintainability.

## Solution

I delivered a modular backend built with NestJS and Prisma, designed around clear domain boundaries for users, sellers, catalog, orders, payments, and messaging. I integrated Stripe for checkout, refunds, and seller onboarding, implemented S3-compatible media uploads with presigned URLs, and added Redis-backed caching and sessions for stability. The API supports role-based workflows for buyers, sellers, and admins, enabling marketplace operations, verification features, and transparency reporting.

## My Role

Backend Developer

- Architected and implemented core API modules for auth, catalog, orders, payments, and media
- Built role-based access control for admin, seller, and customer workflows
- Modeled and migrated the database schema with Prisma, including catalog variants and order lifecycle
- Integrated Stripe checkout, refunds, and seller onboarding and payout flows
- Implemented object storage uploads with presigned URLs and secure validation
- Supported deployment with Docker and runtime configuration for production

## Tech Stack

### Frontend

- React
- Vite
- Refine
- Material UI
- TypeScript

### Backend

- Node.js (Bun runtime)
- NestJS
- Prisma ORM

### Database

- PostgreSQL

### Infrastructure & Tools

- Docker / Docker Compose
- Redis
- Stripe
- S3-compatible object storage (AWS SDK)
- Twilio (SMS)
- Nodemailer (SMTP)
- Git

## Key Features

- Role-based authentication and authorization for buyer, seller, and admin roles
- Admin dashboard for marketplace oversight, listing review, and dispute management
- Product listings with variants, inventory, and media galleries
- Order management with refunds, disputes, and lifecycle tracking
- Messaging between buyers and sellers
- Review import and verified review workflows
- Maker verification and badge-based authenticity signals
- Seller shop journal for updates and storytelling
- Stripe checkout with seller onboarding and payouts
- Analytics and transparency reporting

## My Contributions

- Built the core NestJS modules and API contracts for marketplace operations
- Designed Prisma models for users, sellers, products, orders, refunds, and disputes
- Implemented Stripe payment intent flow, refunds, and seller onboarding
- Added media uploads using S3-compatible storage with presigned URLs
- Introduced Redis-backed caching and session support for performance
- Hardened validation and error handling across public-facing endpoints
- Packaged the app for containerized deployment with Docker

## Challenges & Solutions

### Challenge 1: Multi-variant catalog and data integrity

#### Problem

The product catalog needed to support variants, inventory, and rich media while preserving consistency and fast queries.

#### Solution

I designed a normalized catalog schema with variant relationships and indexes, then enforced validation in the API to keep inventory, pricing, and media in sync.

### Challenge 2: Reliable media handling

#### Problem

Seller uploads had to be secure, scalable, and resilient to failed or partial uploads.

#### Solution

I implemented presigned URL uploads to S3-compatible storage with size and type validation, plus consistent cleanup patterns for failed uploads.

### Challenge 3: Payments, refunds, and seller payouts

#### Problem

The platform needed to handle multi-seller checkout, refunds, and payouts while keeping order and payment states consistent.

#### Solution

I integrated Stripe for checkout and seller onboarding, enforced order state transitions, and added webhook-driven updates for payment status and refunds.

## Results / Impact

- Delivered a production-ready backend aligned with the transparency and authenticity goals of the platform
- Simplified deployment and environment management using Docker
- Enabled secure payment and payout flows for a multi-vendor marketplace
- Improved maintainability with modular services and a well-structured schema

## Screenshots / Demo

- Admin dashboard overview (insert screenshot)
- Seller catalog and order management views (insert screenshot)
- Buyer browsing and checkout flow (insert screenshot)
- Mobile responsiveness preview (insert screenshot)
- Architecture diagram (optional)
- Live demo: Not publicly available
- GitHub: Not publicly available

## What I Learned

This project deepened my understanding of scalable marketplace architecture, Stripe Connect workflows, and the operational trade-offs of building trust features such as verification and transparent reporting.

## Confidentiality Note (Optional)

Due to client confidentiality, source code and live production links are not publicly available.
