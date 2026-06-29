# 🗂️ Production Projects Portfolio

> Source code for these projects is private due to client confidentiality agreements.
> This repository documents the architecture, decisions, and outcomes of each production application I have built.

I'm — a Full Stack Developer with hands-on experience building production-grade applications across marketplaces, SaaS platforms, internal tools, and AI-powered products.

📌 **Portfolio:** [ahasnat.dev](https://ahasnat.dev) &nbsp;|&nbsp; 💼 **LinkedIn:** [in/a-hasnat](https://linkedin.com/in/a-hasnat) &nbsp;|&nbsp; 📧 **Email:** a.hasnat.dev1@gmail.com

---

## Projects at a Glance

| Project | Type | Stack | Status |
|---|---|---|---|
| [WabiSaviArt](#-wabisaviart--multi-vendor-marketplace) | Multi-Vendor Marketplace | React, NestJS, PostgreSQL, Stripe | ✅ Production |
| [MyStudyPal](#-mystudypal--ai-powered-study-platform) | AI SaaS Platform | React, NestJS, PostgreSQL, Redis, Docker | ✅ Production |
| [Sarkar Group SMD](#-sarkar-group-smd--internal-management-system) | Internal Management System | Next.js, Express, MongoDB, Prisma, MUI | ✅ Production |
| [DovePDF](#-dovepdf--browser-based-pdf-toolkit) | Web-Based PDF Editor | React, Express, tRPC, PDF-lib, Turborepo | ✅ Production |

---

## 🛒 WabiSaviArt — Multi-Vendor Marketplace

**[📁 View Project Folder](./The_WabiSaviArt) &nbsp;|&nbsp; [🌐 Portfolio Details](https://ahasnat.dev/projects/wabisaviart)**

An Etsy-inspired multi-vendor marketplace connecting buyers with independent makers and artists. Built to support the full commerce lifecycle — from seller onboarding to order fulfillment and dispute resolution.

Live at: **[wabisabiart.com](https://wabisabiart.com/)**

### My Role
Full-stack ownership of the backend architecture and API layer, plus the admin dashboard frontend.

### Tech Stack
![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat&logo=nestjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat&logo=postgresql&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-3982CE?style=flat&logo=Prisma&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DD0031?style=flat&logo=redis&logoColor=white)
![Stripe](https://img.shields.io/badge/Stripe-626CD9?style=flat&logo=Stripe&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-0db7ed?style=flat&logo=docker&logoColor=white)

### Key Features Delivered
- **Role-based access control** for Buyer, Seller, and Admin — each with isolated dashboard workflows
- **Stripe Connect integration** for seller onboarding, product checkout, and automated payouts
- **S3-compatible media uploads** with presigned URL generation for secure product image management
- **Order lifecycle management** — tracking, refunds, and dispute resolution flows
- **Maker verification system** with authenticity badges and admin approval workflow
- **Real-time buyer-seller messaging** via Socket.IO

### Architecture Highlights
- Designed a normalized PostgreSQL schema supporting multi-tenant seller storefronts with shared product catalog
- Implemented JWT cookie-based auth with role guards at both REST and WebSocket layers
- Built a Stripe webhook handler for async payment state reconciliation
- Containerized all services with Docker Compose for consistent dev/prod parity

---

## 📄 DovePDF — Browser-Based PDF Toolkit

**[📁 View Project Folder](./Dove-PDF) &nbsp;|&nbsp; [🌐 Portfolio Details](https://ahasnat.dev/projects/dove-pdf)**

A privacy-first, web-based PDF processing platform. All editing happens client-side in the browser — no file is sent to a server unless explicitly required — making it fast, private, and scalable without expensive cloud processing costs.

Live at: **[dovepdf.com](https://dovepdf.com/)**

### My Role
Full-stack development — client-side PDF processing pipeline, state management architecture, backend API, and monorepo setup.

### Tech Stack
![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat&logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-38B2AC?style=flat&logo=tailwind-css&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-404d59?style=flat&logo=express&logoColor=61DAFB)
![tRPC](https://img.shields.io/badge/tRPC-2596BE?style=flat&logo=trpc&logoColor=white)

### Key Features Delivered
- **Client-side PDF editing** — highlighting, annotations, signatures, image insertion, and page reordering using PDF-lib
- **Merge, compress, and optimize** — batch PDF operations with real-time progress feedback
- **Drag-and-drop interactions** with full undo/redo history
- **Web Workers** for off-thread PDF processing — keeps the UI responsive on large files
- **Local persistence** for resuming editing sessions without re-uploading
- **Google Ads integration** for monetization without server-side processing overhead

### Architecture Highlights
- Structured as a **Turborepo monorepo** — clean separation between the PDF tools app, shared UI components, and backend API
- Used **tRPC** for fully type-safe API communication between client and server
- Offloaded all heavy PDF processing to Web Workers to prevent main-thread blocking
- Designed an overlay coordinate normalization system to ensure pixel-accurate annotation export across different screen sizes and zoom levels

---

## 📚 MyStudyPal — AI-Powered Study Platform

**[📁 View Project Folder](./MyStudyPal) &nbsp;|&nbsp; [🌐 Portfolio Details](https://ahasnat.dev/projects/mystudypal-ie)**

A production AI study platform built specifically for the Irish school curriculum. Students get AI-generated explanations, exam-style answers, smart quizzes, and a progress dashboard — all tailored to their subject and marking scheme.

Live at: **[mystudypal.ie](https://mystudypal.ie)**

### My Role
Full-stack development — backend API, microservice orchestration, AI pipeline integration, infrastructure setup on VPS via Dokploy.

### Tech Stack
![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat&logo=nestjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DD0031?style=flat&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-0db7ed?style=flat&logo=docker&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-6DA55F?style=flat&logo=node.js&logoColor=white)

### Key Features Delivered
- **AI Study Buddy** — marking-scheme-aligned answers across Maths, Science, English, and Irish; supports direct image question uploads
- **Notes Generator** — instantly produces clean revision notes strictly based on the Irish curriculum
- **Smart Quiz Engine** — AI-generated quizzes targeting weak areas, with instant correction and topic tagging
- **Progress Dashboard** — XP level system, weekly improvement stats, and a strength/weakness heatmap
- **Automated past paper ingestion** via a Puppeteer scraping pipeline pulling from official Irish curriculum sources
- **Rust-based file server (Rustfs)** for fast, secure student file and image uploads

### Architecture Highlights
- Designed and deployed **7 containerized microservices**: Admin Dashboard, User Dashboard, Landing Page, NestJS API Server, Rustfs file server, PostgreSQL, and Redis
- Managed full infrastructure lifecycle via Dokploy on a self-hosted VPS
- Integrated LLM API with custom system prompts per subject and marking scheme alignment
- Built Redis-backed caching layer for AI response optimization and rate limiting

---

## 🏗️ Sarkar Group SMD — Internal Management System

**[📁 View Project Folder](./SMD_Internal_Management_System) &nbsp;|&nbsp; [🌐 Portfolio Details](https://ahasnat.dev/projects/sarkar-group-smd)**

A production-grade internal platform for a construction and marine engineering company. Five distinct user roles operate within fully isolated, permission-controlled dashboards — managing projects, equipment, HR workflows, finances, and real-time notifications.

### My Role
Full-stack development — database schema design, backend API, frontend dashboard implementation across all 5 role dashboards.

### Tech Stack
![Next.js](https://img.shields.io/badge/Next.js-black?style=flat&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat&logo=typescript&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-404d59?style=flat&logo=express&logoColor=61DAFB)
![MongoDB](https://img.shields.io/badge/MongoDB-4ea94b?style=flat&logo=mongodb&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-3982CE?style=flat&logo=Prisma&logoColor=white)
![MUI](https://img.shields.io/badge/MUI-007FFF?style=flat&logo=mui&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-0db7ed?style=flat&logo=docker&logoColor=white)

### Key Features Delivered
- **5 isolated role dashboards** — SUPER_ADMIN, ADMIN, PROJECT_MANAGER, ENGINEER, CLIENT — each with scoped permissions
- **Project lifecycle management** — engineer assignment, equipment linking, and multi-stage status tracking
- **Equipment registry** — real-time status tracking (WORKING / RUNNING / STAND_BY / BREAK_DOWN) with crew assignment and request workflow
- **Payment & requisition engine** — document upload, decline reason enforcement, multi-level approval chain
- **8 HR application types** — leave, resignation, transfer, salary advance, loan, complaint, grievance, expense reimbursement
- **Real-time SSE notifications** — pushed to all relevant users on every workflow event
- **Rich media/blog system** — TipTap editor, image upload, keyword tagging, and comment threads

### Architecture Highlights
- Designed a MongoDB schema supporting deeply nested role-permission relationships without sacrificing query performance
- Built an SSE (Server-Sent Events) notification system that fans out to multiple role-based channels simultaneously
- Used Prisma transactions for atomic approval state changes across payment and HR workflows
- Implemented KPI dashboard with month-over-month delta calculations using parallel Prisma aggregation queries

---

## 💬 Let's Talk

I'm currently open to **full-time**, **contract**, and **remote** roles in full-stack or frontend engineering.

- 📧 **Email:** a.hasnat.dev1@gmail.com
- 🌐 **Portfolio:** [ahasnat.dev](https://ahasnat.dev)
- 💼 **LinkedIn:** [linkedin.com/in/a-hasnat](https://linkedin.com/in/a-hasnat)
- 🐙 **GitHub:** [github.com/aHasnat1997](https://github.com/aHasnat1997)
