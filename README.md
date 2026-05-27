<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=180&section=header&text=Contabo%20Cloud%20Portal&fontSize=40&fontColor=fff&animation=twinkling&fontAlignY=38&desc=Graduation%20Project%20%E2%80%94%20Multi-Tenant%20VPS%20Reseller%20%26%20CD%20Platform&descAlignY=58&descSize=16&descColor=cbd5e1"/>

<div align="center">

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Traefik](https://img.shields.io/badge/Traefik-24A1C1?style=flat-square&logo=traefikproxy&logoColor=white)

</div>

---

## Overview

**Contabo Cloud Portal** is a production-grade multi-tenant SaaS platform built as a graduation project (Alexandria University — Computer & System Engineering, 2026). It allows resellers to provision and manage Contabo VPS instances for their clients through a unified dashboard, with a built-in Git-based continuous deployment pipeline (Heroku-style: `git push` → live deploy).

Built on top of [Dokploy](https://dokploy.com) and extended with a full multi-tenancy layer, advanced monitoring, and distributed architecture enhancements.

---

## Key Features

| Feature | Description |
|---------|-------------|
| **Multi-Tenant Architecture** | Three-tier RBAC: Admin → Resellers → Clients with full isolation |
| **Git-Based CD Pipeline** | Push to deploy — Heroku-style, no manual steps |
| **Isolated Billing** | Per-reseller and per-client billing dashboards and resource quotas |
| **Monitoring Stack** | Real-time metrics via integrated monitoring service |
| **Scheduler** | Background jobs for billing cycles and resource checks |

---

## Architecture

```
┌──────────────────────────────────────────────────────┐
│                  Contabo Cloud Portal                 │
│                                                       │
│  ┌──────────┐   ┌──────────┐   ┌──────────────────┐  │
│  │  Admin   │   │ Reseller │   │     Client       │  │
│  │Dashboard │   │Dashboard │   │    Dashboard     │  │
│  └────┬─────┘   └────┬─────┘   └────────┬─────────┘  │
│       └──────────────┴──────────────────┘             │
│                       │                               │
│               ┌───────▼────────┐                      │
│               │   REST API     │  (Node.js + tRPC)    │
│               └───────┬────────┘                      │
│                       │                               │
│        ┌──────────────┼──────────────┐                │
│        ▼              ▼              ▼                │
│  ┌──────────┐  ┌──────────┐  ┌──────────────┐        │
│  │PostgreSQL│  │  Docker  │  │   Traefik    │        │
│  │   (DB)   │  │(Deployer)│  │(Reverse Proxy│        │
│  └──────────┘  └──────────┘  └──────────────┘        │
│                                                       │
│  ┌──────────────┐    ┌────────────────┐               │
│  │  Monitoring  │    │   Scheduler    │               │
│  │   Service    │    │    Service     │               │
│  └──────────────┘    └────────────────┘               │
└──────────────────────────────────────────────────────┘
```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React, TypeScript, TailwindCSS |
| Backend | Node.js, tRPC, TypeScript |
| Database | PostgreSQL |
| Deployment Engine | Docker, Traefik |
| Package Manager | pnpm (monorepo workspace) |

---

## Project Structure

```
CloudDeploy/
├── apps/
│   ├── api/          # Backend API (Node.js + tRPC)
│   ├── dokploy/      # Frontend dashboard (React)
│   ├── monitoring/   # Metrics & monitoring service
│   └── schedules/    # Background job scheduler
├── packages/         # Shared packages (types, utils)
├── Dockerfile.*      # Per-service Dockerfiles
└── docker-compose.yml
```

---

## Getting Started

### Prerequisites
- Docker & Docker Compose
- Node.js 18+ and pnpm

### Run Locally

```bash
git clone https://github.com/Ibrahimtareq952001/CloudDeploy.git
cd CloudDeploy
pnpm install
docker-compose up -d
pnpm dev
```

---

<div align="center">

*Graduation Project — Computer & System Engineering, Alexandria University 2026*

[![Resume](https://img.shields.io/badge/View_Resume-PDF-008080?style=flat-square&logo=latex&logoColor=white)](https://github.com/Ibrahimtareq952001/Resume/blob/main/resume.pdf)
[![Portfolio](https://img.shields.io/badge/GitHub-Ibrahimtareq952001-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Ibrahimtareq952001)

</div>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer"/>
