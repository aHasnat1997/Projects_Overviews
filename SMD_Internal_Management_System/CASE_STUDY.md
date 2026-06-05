# Sarkar Group — SMD Internal Management System

> **Case Study** | Role: Fullstack Developer (Solo) | Scope: Full-Stack Internal Tool

---

## Overview

The **Sarkar Group SMD** is a production-grade internal management system built for a construction and marine engineering company. It consolidates project management, equipment tracking, employee management, financial workflows, media/blog publishing, and real-time notifications into a single, role-driven dashboard platform.

Multiple user roles — Super Admin, Admin, Project Manager, Engineer, and Client — each experience a tailored dashboard and permission scope, ensuring every team member only sees and acts on what they're authorized to.

---

## Vision

Replace fragmented spreadsheet-based workflows with a unified internal tool that handles the full lifecycle: from registering construction equipment and assigning it to projects, to approving financial requisitions, managing employee applications, and publishing company media — all in one place.

## Technical Innovation

- Role-based access control (RBAC) enforced at both route and service layers using JWT + custom `authGuard` middleware
- Reusable generic `PrismaQueryBuilder` class supporting dynamic search, filter, sort, paginate, and relation-include across every module
- Real-time notifications via Server-Sent Events (SSE) with per-user client registry, keepalive pings, and automatic cleanup
- Cloudinary-backed file storage for profile images, equipment photos, documents, and media posts
- Monolithic REST API with clean module separation: each domain has its own controllers, services, validation, and routes

## Outcome

- Production-deployed platform serving live company operations
- All 5 user roles operational with isolated dashboards and workflows
- 15+ REST API modules covering every business domain
- Real-time notification delivery to all relevant roles on workflow events
- Docker + Docker Compose deployment with health checks

---

## Problem / Challenge

The company managed construction equipment, marine vessels, engineering projects, and a workforce across multiple departments — all through manual processes and disconnected tools.

**Core challenges:**

1. **Multi-role access** — Different roles need isolated views and strict permission enforcement without duplicating code
2. **Equipment lifecycle** — Tracking equipment across STAND_BY → assigned → project completion states with request/approval flows
3. **Financial workflows** — Payments and requisitions needed a full request → admin review → approve/reject cycle with notification feedback
4. **Employee HR workflows** — Leave, resignation, salary advance, and other application types needed structured submission and approval
5. **Real-time feedback** — Employees needed instant notifications when admins acted on their submissions
6. **Media/Blog system** — Admins and employees needed a rich content system with image uploads and comments

---

## Solution

### Backend (Express + TypeScript + Prisma + MongoDB)

- **Rocket server class** wraps Express with structured `load()`, `initiate()`, and `launch()` lifecycle methods
- **JWT authentication** with separate access, refresh, and forgot-password tokens; role guard middleware on every protected route
- **PrismaQueryBuilder** — generic class accepting any Prisma delegate, chainable `.search()`, `.filter()`, `.sort()`, `.paginate()`, `.includeRelations()` — reused across all 15+ modules
- **SSE Notification Service** — singleton `NotificationService` class maintains a `Map<userId, Set<Response>>` for live push; broadcasts to roles on payment/requisition/application creation; sends targeted notifications on admin approval/rejection
- **Zod validation** on every mutating endpoint with detailed schemas per module
- **Cloudinary integration** for file uploads via Multer; Uint8Array assets stored as JSON in MongoDB

### Frontend (Next.js 16 + Redux Toolkit + MUI + TailwindCSS)

- **Next.js App Router** with separate route groups for auth `(auth)` and dashboard `(dashboard)`
- **Role-based dashboard routing** — `/dashboard/admin`, `/dashboard/project_manager`, `/dashboard/engineer` each with their own pages and sub-modules
- **Redux Toolkit + redux-persist** for global state; `next-auth` for session management
- **MUI + TailwindCSS** for UI components; `SMDDataTable` and `ProjectCard` as reusable data display components
- **TipTap rich text editor** for media/blog post creation with formatting, tables, images, highlights
- **PDF viewer** (`react-pdf` + `pdfjs-dist`) for in-app document viewing
- **Sonner** for toast notifications; SSE client for real-time notification badge updates

### Database (MongoDB via Prisma ORM)

- 20+ models covering Users, Admins, Engineers, ProjectManagers, Clients, Projects, Products, Crews, Payments, Requisitions, Applications, Medias, Comments, ProjectGallery, Notifications, DailyReports, and join tables
- Enum-driven status fields (PENDING / APPROVED / REJECTED) for all approval workflows
- Atomic `$transaction` blocks for multi-table updates (user + profile, media + comments)

### Infrastructure

- Docker multi-stage build (deps → builder → runner) with non-root user, dumb-init, and health check
- Docker Compose for local and production orchestration
- Deployed to Vercel (client) with MongoDB Atlas as the database

---

## My Role

**Fullstack Developer — Solo Project**

- Designed the entire MongoDB schema (20+ models, enums, relations, join tables)
- Built the generic `PrismaQueryBuilder` supporting search/filter/sort/paginate/include across all modules
- Implemented JWT auth system: sign/verify/decode/blacklist utilities, `authGuard` middleware with role array support, SSE-specific `sseAuthGuard` for query-param token
- Architected all 15+ API modules: users, admins, engineers, project managers, clients, projects, products, crews, payments, requisitions, applications, medias, project galleries, request products, notifications, dashboard
- Built the SSE notification system: singleton service with client registry, broadcast-to-roles, targeted send, keepalive, and connection cleanup
- Designed role-specific dashboard data aggregation (Prisma `$transaction` with parallel queries for KPI counts, month-over-month deltas, recent records)
- Set up Next.js frontend with role-based routing, Redux state management, MUI + Tailwind UI, TipTap editor, PDF viewer
- Configured Docker multi-stage builds, Docker Compose, and deployment pipeline

---

## Tech Stack

| Layer              | Technologies                                                                         |
| ------------------ | ------------------------------------------------------------------------------------ |
| **Backend**        | TypeScript, Express.js, Prisma ORM, MongoDB, JWT, Zod, Nodemailer, EJS, Multer       |
| **Frontend**       | Next.js 16, React 18, Redux Toolkit, redux-persist, next-auth, MUI, TailwindCSS      |
| **Rich Content**   | TipTap (heading, table, image, color, highlight, text-align, underline, font-family) |
| **File Storage**   | Cloudinary (images, documents, equipment photos)                                     |
| **Real-time**      | Server-Sent Events (SSE) with singleton NotificationService                          |
| **Infrastructure** | Docker (multi-stage), Docker Compose, Vercel, MongoDB Atlas, dumb-init               |
| **Utilities**      | Bcrypt, UUID, Axios, cookie-parser, CORS, Vitest                                     |

---

## Key Features

- **5 user roles** — SUPER_ADMIN, ADMIN, PROJECT_MANAGER, ENGINEER, CLIENT — each with isolated dashboards and permission-gated APIs
- **Project lifecycle** — Create → assign project manager → add engineers → attach equipment → track status (In_Process / Completed / ON_GOING)
- **Equipment management** — Register construction/marine/engineering equipment, track status (WORKING / RUNNING / STAND_BY / BREAK_DOWN), assign crews, attach to projects
- **Equipment request workflow** — Engineers/PMs request equipment for a project; admin approves/rejects; auto-assigns to project on approval
- **Payment requests** — Submit payment requests per project; admin approve/reject with decline reason; notifications sent on action
- **Requisition system** — Material/resource requisitions with document upload, approval workflow, notifications
- **HR applications** — 8 application types (leave, resignation, transfer, salary advance, loan, complaint, grievance, expense reimbursement) with date ranges and document upload
- **Media/Blog** — Rich-text posts with image, keyword, and comment system; accessible publicly for company content
- **Project gallery** — Upload project site photos per project; commenting system for team collaboration
- **Real-time notifications** — SSE stream delivers instant notifications; unread batch sent on connection; mark-as-read endpoint
- **Admin scheduler** — Personal schedule management for admins (title, note, date range)
- **Role dashboards** — KPI cards with month-over-month change indicators, recent records, active project lists

---

## Challenges & Solutions

### Generic Query Builder Across 15+ Modules

**Problem:** Every module needed search, filter, sort, paginate, and relation-include — duplicating this logic in each service would be unmaintainable.

**Solution:** Built `PrismaQueryBuilder<TModel, TWhereInput, TOrderByInput, TSelect, TInclude>` — a generic, chainable class that accepts any Prisma delegate and constructs queries dynamically. Every service instantiates it with `findMany` + `count` delegates and chains the needed operations. One class serves all modules.

---

### Real-time Notifications Without WebSocket Infrastructure

**Problem:** Engineers and PMs needed instant feedback when admins approved or rejected their submissions, but adding WebSocket infrastructure was complex.

**Solution:** Implemented SSE using Express `res.write()`. A singleton `NotificationService` maintains a `Map<userId, Set<Response>>` for all connected clients. On workflow events, it creates a DB record and pushes the event to all matching SSE connections. Keepalive pings every 20s prevent proxy timeouts. Connection cleanup is handled via `close`/`finish`/`error` events.

---

### Role-Based Dashboard Data Aggregation

**Problem:** Each role's dashboard needed different KPI data — admins need company-wide stats, project managers need their own project/requisition data, engineers need their assigned project data. Running multiple queries sequentially would be slow.

**Solution:** Used Prisma `$transaction` to run all aggregation queries in parallel for each dashboard endpoint. Admin dashboard runs 15 parallel queries (employee counts, application deltas, requisition deltas, product deltas, active clients, active projects, schedule). Each role gets purpose-built aggregation with month-over-month delta calculations.

---

### Equipment Assignment Validation Chain

**Problem:** Equipment can only be added to a project if the project is not Completed and the equipment is in STAND_BY status. The request-product approval flow needed to auto-assign equipment on approval without bypassing these rules.

**Solution:** Each assignment operation validates project status and equipment status before writing. The `RequestProductsService.declineOrAccept` calls `ProjectService.addProduct` internally after setting APPROVED status, reusing the same validation logic rather than duplicating it.

---

## Results / Impact

| Metric                | Result                                                      |
| --------------------- | ----------------------------------------------------------- |
| API Modules           | 15+ fully functional modules                                |
| User Roles            | 5 roles with complete permission isolation                  |
| Database Models       | 20+ Prisma models with full relations                       |
| Notification Delivery | Real-time SSE push to all relevant users                    |
| Approval Workflows    | 3 parallel workflows (payments, requisitions, applications) |
| Application Types     | 8 HR application types supported                            |
| Deployment            | Dockerized, health-checked, production live                 |

---

## Screenshots / Demo

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin: 20px 0;">
  <div>
    <img src="./assets/Admin dashboard.png" alt="Admin Dashboard Overview" style="width: 100%; border-radius: 8px;" />
    <p align="center"><em>Admin Dashboard Overview</em></p>
  </div>
  <div>
    <img src="./assets/Engineer dashboard.png" alt="Engineer dashboard Overview" style="width: 100%; border-radius: 8px;" />
    <p align="center"><em>Engineer Dashboard Overview</em></p>
  </div>
  <div>
    <img src="./assets/Project Manager dashboard.png" alt="Project Manager Dashboard Overview" style="width: 100%; border-radius: 8px;" />
    <p align="center"><em>Project Manager Dashboard Overview</em></p>
  </div>
  <div>
    <img src="./assets/Admin _ All projects.jpg" alt="All Projects" style="width: 100%; border-radius: 8px;" />
    <p align="center"><em>All Projects</em></p>
  </div>
  <div>
    <img src="./assets/All Employees.png" alt="All Employees" style="width: 100%; border-radius: 8px;" />
    <p align="center"><em>All Employees</em></p>
  </div>
  <div>
    <img src="./assets/Admin _ Media.png" alt="All Media View" style="width: 100%; border-radius: 8px;" />
    <p align="center"><em>All Media View</em></p>
  </div>
  <div>
    <img src="./assets/View Employee Details - Profile - Personal Information.png" alt="View Employee Details" style="width: 100%; border-radius: 8px;" />
    <p align="center"><em>View Employee Details</em></p>
  </div>
</div>

## What I Learned

This project deepened my understanding of designing multi-role enterprise systems where access control must be consistent across both the API and UI layers. Building the generic `PrismaQueryBuilder` taught me the value of abstraction — one well-designed utility eliminated hundreds of lines of repetitive query code.

Implementing SSE from scratch gave me practical experience with HTTP streaming, connection lifecycle management, and the trade-offs vs WebSockets for one-directional push scenarios. Designing the parallel dashboard aggregation queries with `$transaction` highlighted the importance of minimizing round trips for data-heavy endpoints.

The project also reinforced clean module architecture — keeping controllers thin, services as the business logic layer, and validation at the route level with Zod schemas — as the pattern that scales best when a codebase grows to 15+ interconnected modules.

---

## Project Information

Sarkar Group SMD is a live internal management system used by the company for day-to-day operations. It demonstrates production-grade patterns for multi-role enterprise applications with real-time capabilities.
