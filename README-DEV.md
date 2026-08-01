# Product Hub Development Guide

**Product:** Product Hub

**Version:** 0.1.0

---

# Purpose

This document describes the local development environment, prerequisites, build process, testing process, and development workflow.

---

# Prerequisites

Install the following software before contributing.

## Required

- Git
- .NET 9 SDK
- Node.js LTS
- PostgreSQL
- Docker Desktop

---

## Recommended

- Visual Studio 2022
- Visual Studio Code
- pgAdmin
- Postman

---

# Repository

Clone

```bash
git clone https://github.com/DensedyOrg/product-hub.git
```

---

# Backend

Restore packages

```bash
dotnet restore
```

Build

```bash
dotnet build
```

Run

```bash
dotnet run
```

---

# Frontend

Install packages

```bash
npm install
```

Run

```bash
npm run dev
```

Production Build

```bash
npm run build
```

---

# Database

Create Database

```sql
CREATE DATABASE producthub;
```

Apply Migrations

```bash
dotnet ef database update
```

---

# Docker

Build

```bash
docker compose build
```

Run

```bash
docker compose up -d
```

Stop

```bash
docker compose down
```

---

# Configuration

Copy

```
.env.example
```

to

```
.env
```

Update values according to the local environment.

---

# Running Tests

Run all tests

```bash
dotnet test
```

Run a specific project

```bash
dotnet test tests/ProductHub.Domain.Tests
```

---

# Coding Standards

- Follow `.editorconfig`.
- Follow `CONTRIBUTING.md`.
- Follow `ARCHITECTURE.md`.
- Follow `DOMAIN-MODEL.md`.

---

# Git Workflow

Create feature branch

```bash
git checkout -b feature/my-feature
```

Commit

```bash
git commit -m "feat(product): add product aggregate"
```

Push

```bash
git push origin feature/my-feature
```

---

# Pull Request Checklist

- Build succeeds.
- Tests pass.
- Documentation updated.
- No secrets committed.
- Architecture preserved.

---

# Debugging

Backend

```
https://localhost:5001
```

Frontend

```
http://localhost:5173
```

API

```
https://localhost:5001/api/v1
```

---

# Troubleshooting

## Restore Packages

```bash
dotnet restore
```

## Clean Solution

```bash
dotnet clean
```

## Rebuild

```bash
dotnet build
```

## Reset Database

```bash
dotnet ef database drop

dotnet ef database update
```

---

# End of Document