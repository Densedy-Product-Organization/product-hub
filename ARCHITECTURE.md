# Product Hub Architecture

**Product:** Product Hub

**Version:** 0.1.0

**Status:** Draft

---

# Purpose

This document defines the architectural blueprint for Product Hub.

The architecture must support:

- Enterprise scalability
- Low operational cost
- Modular development
- AI extensibility
- SaaS deployment
- Self-hosted deployment

---

# Architectural Principles

AP-001

Architecture shall prioritize business domains over technical layers.

---

AP-002

The system shall be implemented as a Modular Monolith.

---

AP-003

Every module shall have a single responsibility.

---

AP-004

Business logic shall remain independent of infrastructure.

---

AP-005

AI capabilities shall be optional.

---

AP-006

Every module shall expose stable contracts.

---

AP-007

Every module shall be independently testable.

---

AP-008

External providers shall always be abstracted.

---

AP-009

Infrastructure shall never contain business rules.

---

AP-010

Platform Core capabilities shall remain reusable across future products.

---

# High-Level Architecture

```
                    Product Hub

                Presentation Layer
                        │
                        ▼
                Application Layer
                        │
                        ▼
                  Domain Layer
                        │
                        ▼
              Infrastructure Layer
                        │
                        ▼
                   External Systems
```

---

# Architecture Style

Product Hub adopts a

**Modular Monolith**

Reasons

- Solo Founder
- Lower Cloud Cost
- Faster Development
- Easier Testing
- Easier Deployment
- Enterprise Maintainability

---

# Layered Architecture

## Presentation Layer

Responsibilities

- Web UI
- REST API
- Authentication
- Request Validation

Must not contain business rules.

---

## Application Layer

Responsibilities

- Use Cases
- Commands
- Queries
- Transactions
- Authorization
- Orchestration

Must not contain infrastructure logic.

---

## Domain Layer

Responsibilities

- Business Rules
- Entities
- Aggregates
- Value Objects
- Domain Events
- Domain Services

This is the heart of Product Hub.

---

## Infrastructure Layer

Responsibilities

- Database
- File Storage
- AI Providers
- Email
- Logging
- Cache
- Search
- External APIs

No business logic is permitted.

---

# Modules

The MVP consists of the following modules.

```
Identity

Organization

Authorization

Product

Taxonomy

Attributes

Models

Variants

Media

Documents

Search

Import

Export

Audit

AI

Configuration
```

Each module owns its own business logic.

---

# Module Dependencies

```
Presentation

↓

Application

↓

Domain

↓

Infrastructure
```

Dependencies may only move downward.

No upward dependencies.

---

# AI Architecture

```
Product Module

↓

AI Gateway

↓

Provider Router

↓

OpenAI

Azure OpenAI

Gemini

Anthropic

Ollama

Future Providers
```

The Product Module never communicates directly with an AI provider.

---

# AI Gateway Responsibilities

- Provider Selection
- Prompt Execution
- Cost Tracking
- Retry Logic
- Timeout
- Usage Logging
- Safety Validation
- Response Validation

---

# Multi-Tenancy

Every request belongs to exactly one Organization.

```
Organization

↓

Products

↓

Taxonomy

↓

Attributes

↓

Media

↓

Audit
```

No cross-organization access is permitted.

---

# Authentication

Supported

- Email / Password

Future

- Microsoft Entra ID
- Google
- GitHub
- SAML
- OpenID Connect

---

# Authorization

Role-Based Access Control

Initial Roles

- Owner
- Administrator
- Editor
- Viewer

Future versions may support custom roles.

---

# API Architecture

Architecture Style

REST

Version

v1

Future

- GraphQL
- Webhooks
- MCP Server

---

# Persistence

Database

PostgreSQL

ORM

Entity Framework Core

Migration Strategy

Code First

---

# File Storage

Initial

Local Storage

Future

- Azure Blob Storage
- Amazon S3
- Google Cloud Storage
- MinIO

---

# Search

Initial

PostgreSQL Full Text Search

Future

- Elasticsearch
- OpenSearch

---

# Logging

Application Logging

Structured JSON Logs

Audit Logging

Business Events

AI Logging

Usage Only

Never log sensitive prompts or secrets.

---

# Configuration

Configuration Sources

- appsettings.json
- Environment Variables
- Secret Store

Secrets shall never be committed to source control.

---

# Error Handling

Every exception shall produce

- Correlation Id
- Error Code
- User-safe Message

Internal implementation details shall never be exposed.

---

# Security Architecture

Security is enforced at multiple layers.

- Authentication
- Authorization
- Input Validation
- Output Validation
- File Validation
- Secret Management
- Audit Logging

---

# Deployment

Supported

- Docker
- Docker Compose

Future

- Kubernetes

The MVP does not require Kubernetes.

---

# CI/CD

Source Control

GitHub

Build

GitHub Actions

Deployment

Docker

---

# AI Cost Strategy

Managed AI usage must remain economically sustainable.

Requirements

- Usage Limits
- Organization Quotas
- Monthly Budget
- Request Limits
- Provider Abstraction
- BYOK Support

AI shall never become an uncontrolled operational expense.

---

# Future Platform Core Extraction

The following modules are candidates for extraction into Platform Core.

- Identity
- Authorization
- Configuration
- Audit
- AI Gateway
- Notifications
- Licensing

Extraction shall occur only after reuse is validated across multiple products.

---

# Technology Stack

Backend

- .NET 9
- ASP.NET Core
- Entity Framework Core

Frontend

- React
- TypeScript

Database

- PostgreSQL

Authentication

- ASP.NET Identity

Container

- Docker

Repository

- GitHub

CI/CD

- GitHub Actions

---

# Architecture Decision Summary

ADR-001

Architecture Style

Modular Monolith

Status

Accepted

---

ADR-002

API Style

REST

Status

Accepted

---

ADR-003

Database

PostgreSQL

Status

Accepted

---

ADR-004

AI Integration

Provider Abstraction

Status

Accepted

---

ADR-005

Deployment

Docker

Status

Accepted

---

# Architecture Goals

The architecture shall provide

- Maintainability
- Extensibility
- Testability
- Low Cloud Cost
- Enterprise Readiness
- AI Extensibility
- Strong Domain Isolation
- Platform Reusability
- Long-Term Sustainability

This document serves as the authoritative architectural reference for Product Hub.