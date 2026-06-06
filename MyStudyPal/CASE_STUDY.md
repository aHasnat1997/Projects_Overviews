# MyStudyPal — AI Study Buddy for Irish Students

> **Case Study** | Role: Deployment & Automation Engineer | Scope: AI Educational Platform

---

## Overview

**MyStudyPal (mystudypal.ie)** is a fully-featured, AI-powered study helper designed specifically for the Irish curriculum. It acts as a personal AI study buddy, delivering instant explanations, exam-style answers, structured notes, smart quizzes, and detailed progress insights.

The platform provides a highly contextual learning environment where students can upload complex problems and receive step-by-step logic and grading-scheme-aligned feedback in seconds.

---

## Vision

Replace generic, unstructured study methods with a targeted, curriculum-specific AI tool that helps students actively identify weak points, generate concise revision notes, and test their knowledge against real exam standards.

## Technical Innovation

* **Automated Curriculum Ingestion:** Custom Puppeteer scraping scripts that continuously fetch and parse official past paper data to feed the backend, ensuring AI responses match real exam expectations.
* **Microservices Architecture:** 7 distinct containerized services (Admin Dashboard, User Dashboard, Landing Page, NestJS Server, Rustfs, Postgres-DB, Redis-db).
* **High-Performance Media Handling:** Rust-based file server (Rustfs) implemented explicitly to handle fast, secure processing of student question and image uploads.
* **Container Orchestration:** End-to-end deployment pipeline managed using Docker and Dokploy, enabling isolated, health-checked deployments for every service.

## Outcome

* Production-deployed platform serving students and admins efficiently.
* Highly available backend system driven by NestJS, Postgres, and Redis.
* Complete automation of past-paper data updates via Puppeteer.
* Clean, centralized infrastructure monitoring using Dokploy.

---

## Problem / Challenge

Students preparing for the Irish curriculum lacked a dedicated platform that provided instant, accurate feedback. Generic AI tools frequently hallucinate or fail to understand the highly specific marking schemes required for subjects like Irish, Science, and Maths.

**Core challenges:**

1. **Curriculum Alignment** — Creating an AI that understands specific Irish exam grading criteria rather than just generic knowledge.
2. **Media Processing** — Students need to submit screenshots of complex questions without lag, requiring an optimized file system.
3. **Complex Deployments** — Managing 7 isolated components (two React dashboards, a NestJS backend, static pages, databases, and a file server) required a cohesive, easy-to-maintain infrastructure strategy.
4. **Data Acquisition Pipeline** — Continually feeding the platform with the latest past papers manually was unscalable.

---

## Solution

### Backend & AI (NestJS)
* **NestJS Server** serving as the core API gateway and backend controller for user authentication, AI request routing, and data serving.

### Frontend (React + HTML)
* **User Dashboard** (React) providing the core learning portal with progress insights, quizzes, and the AI chat interface.
* **Admin Dashboard** (React) providing management tools for platform administrators.
* **Landing Page** (HTML) optimized for high-speed delivery and user conversion.

### Storage & Database (PostgreSQL + Redis + Rustfs)
* **PostgreSQL** serving as the primary relational database for user progress, quiz results, and generated notes.
* **Redis-db** implemented for high-speed caching and robust session management.
* **Rustfs** deployed as a dedicated, high-speed file server to handle all media and question uploads.

### Infrastructure & Automation (Docker + Dokploy + Puppeteer)
* Built a custom **Puppeteer** automation script that autonomously scrapes past paper data directly from Irish curriculum sources and feeds it to the backend server.
* **Dockerized** every application tier with custom `Dockerfile`s optimized for production.
* Centralized infrastructure management using **Dokploy**, giving clear visual insight and lifecycle control over all running containers.

---

## My Role

**Deployment & Automation Engineer**

* Designed and managed the entire microservices deployment strategy.
* Containerized all 7 microservices using Docker, ensuring lightweight, secure, and production-ready images.
* Orchestrated the platform using Dokploy, configuring environment variables, internal networking, and volume persistence for databases (Postgres, Redis) and file storage (Rustfs).
* Engineered a web-scraping pipeline using Puppeteer to extract past paper data autonomously and pipe it directly into the backend AI server.
* Ensured high availability, continuous uptime, and streamlined deployment workflows across all frontend and backend applications.

---

## Tech Stack

| Layer | Technologies |
|---|---|
| **Frontend** | React, HTML |
| **Backend API** | NestJS |
| **Media Server** | Rustfs (Rust) |
| **Databases** | PostgreSQL, Redis |
| **Automation** | Puppeteer, Node.js |
| **Infrastructure** | Docker, Dokploy |

---

## Key Features

* **AI Study Buddy** — Ask questions about Maths, Science, English, or Irish and get clear, step-by-step, marking-scheme-aligned answers in seconds. Supports direct image uploads.
* **Notes Generator** — Pick a subject or topic and instantly generate clean, structured revision notes strictly based on the Irish curriculum.
* **Smart Quizzes** — AI dynamically generates multiple-choice or written quizzes targeting the student’s weak areas, complete with instant correction and topic tagging.
* **Progress & Insights** — Comprehensive user dashboard featuring an XP level system, weekly improvement statistics, and a strength/weakness heatmap.

---

## Challenges & Solutions

### Complex Multi-Service Deployments
**Problem:** The platform required 7 distinct services (including varied tech like React, NestJS, and Rust) to communicate securely in production without massive manual configuration overhead.
**Solution:** I utilized Docker to containerize each service independently, then orchestrated the ecosystem using Dokploy. This allowed for centralized logging, automated network routing, and seamless environment variable management.

### Scaling AI Context Data
**Problem:** The AI Study Buddy required continuous feeding of highly specific Irish past paper data to provide accurate, localized answers.
**Solution:** I built a robust automation script using Puppeteer that scrapes official curriculum data, structures it, and automatically injects it into our NestJS backend, entirely eliminating manual data entry.

---

## Results / Impact

| Metric | Result |
|---|---|
| Platform Architecture | 7 robust, isolated, and containerized microservices |
| Data Automation | 100% automated past paper data ingestion |
| Service Management | Unified deployment control via Dokploy dashboard |
| AI Quality | High accuracy guaranteed by strict marking-scheme alignment |

---

## What I Learned

This project gave me extensive hands-on experience in managing complex deployment architectures and container orchestration. Using Dokploy alongside Docker simplified what would have been a tangled web of microservices into a clean, highly maintainable infrastructure. 

Additionally, building the Puppeteer pipeline highlighted the critical intersection between DevOps, automation, and AI accuracy. Ensuring the backend always had the most accurate, curriculum-specific data without manual intervention proved to be just as vital as the AI models themselves.

---

## Project Information

MyStudyPal is a live production educational platform demonstrating a sophisticated integration of modern frontend frameworks, scalable backend API routing, specialized Rust media servers, and comprehensive DevOps automation.
