# Product Hub Architecture

**Product:** Product Hub

**Version:** 0.1.0

**Status:** Draft

---

# Purpose

This document defines the architectural blueprint for Product Hub.

The architecture is designed to support long-term maintainability, enterprise scalability, modular development, low operational cost, AI extensibility, and platform reuse.

Product Hub shall serve as the reference implementation for future products built upon the shared Platform Core.

---

# Scope

This architecture applies to all editions of Product Hub, including:

- Community Edition
- Professional Edition
- Enterprise Edition

unless explicitly stated otherwise.

---

# Architectural Principles

## AP-001

Architecture shall prioritize business domains over technical layers.

---

## AP-002

The system shall be implemented as a Modular Monolith.

---

## AP-003

Every module shall have a single responsibility.

---

## AP-004

Business logic shall remain independent of infrastructure.

---

## AP-005

AI capabilities shall remain optional.

---

## AP-006

Every module shall expose stable public contracts.

---

## AP-007

Every module shall be independently testable.

---

## AP-008

External providers shall always be abstracted.

---

## AP-009

Infrastructure shall never contain business rules.

---

## AP-010

Platform Core capabilities shall remain reusable across future products.

---

## AP-011

Modules shall communicate only through well-defined contracts.

---

## AP-012

Domain models shall remain independent of external frameworks.

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
                        ▲
                        │
              Infrastructure Layer
                        │
                        ▼
                 External Systems
```

The Domain Layer is independent of Infrastructure.

Infrastructure depends upon abstractions defined by the Domain and Application layers.

---

# Architecture Style

Product Hub adopts a **Modular Monolith** architecture.

Reasons include

- Lower Infrastructure Cost
- Faster Development
- Simplified Deployment
- Easier Testing
- Strong Domain Isolation
- Enterprise Maintainability
- Future Platform Extraction

Modules remain logically independent while being deployed as a single application.

Future extraction into distributed services shall not require domain redesign.

---

# Clean Architecture

Product Hub follows Clean Architecture principles.

Responsibilities are separated into four primary layers.

```
Presentation

↓

Application

↓

Domain

↑

Infrastructure
```

The Domain layer has no dependency on Infrastructure.

Infrastructure implements interfaces defined by the Application and Domain layers.

---

# Layered Architecture

## Presentation Layer

Responsibilities

- React User Interface
- REST API
- Authentication
- Request Validation
- Response Formatting

The Presentation Layer shall never contain business rules.

---

## Application Layer

Responsibilities

- Use Cases
- Commands
- Queries
- Transactions
- Authorization
- Workflow Coordination
- Module Orchestration

The Application Layer coordinates business operations but does not implement business rules.

---

## Domain Layer

Responsibilities

- Business Rules
- Entities
- Aggregates
- Value Objects
- Domain Events
- Domain Services
- Specifications

The Domain Layer is the heart of Product Hub.

Business rules shall exist only within this layer.

---

## Infrastructure Layer

Responsibilities

- Database
- Object Storage
- Search Providers
- AI Providers
- Email
- Logging
- Caching
- External APIs
- Background Messaging

Infrastructure implements technical concerns only.

Business rules are prohibited within this layer.

---

# Cross-Cutting Concerns

The following concerns apply consistently across every module.

- Authentication
- Authorization
- Validation
- Logging
- Audit Logging
- Configuration
- Exception Handling
- Localization
- Caching
- Observability

Cross-cutting concerns shall remain reusable and independent of business modules.

---

# Business Modules

The MVP consists of the following business modules.

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

AI Capabilities

Configuration
```

Each module owns its own business logic, data model, validation rules, and public interfaces.

---

# Module Responsibilities

## Identity

Authentication, user identities, and credential integration.

---

## Organization

Organizations, tenants, memberships, and ownership.

---

## Authorization

Roles, permissions, policies, and access control.

---

## Product

Product master data and lifecycle management.

---

## Taxonomy

Categories, hierarchies, and classification structures.

---

## Attributes

Attribute definitions, groups, validation, and values.

---

## Models

Reusable product templates and model definitions.

---

## Variants

Variant relationships and SKU generation.

---

## Media

Images, videos, documents, and digital assets.

---

## Documents

Document management and product attachments.

---

## Search

- Full Text Search
- Semantic Search
- Search Index Management
- Query Processing

---

## Import

Bulk product import and validation.

---

## Export

Product export and data transformation.

---

## Audit

Business audit events and history.

---

## AI Capabilities

Business-facing AI features including

- Description Generation
- Category Suggestion
- Attribute Suggestion
- Translation
- OCR
- Image Understanding
- Semantic Search

Business modules interact only with AI capabilities and never with AI providers directly.

---

## Configuration

Configuration management including

- Organization Settings
- Storage Configuration
- AI Configuration
- Feature Flags
- Provider Configuration

---

# Module Communication

Modules communicate only through stable public contracts.

Communication mechanisms include

- Application Services
- Domain Events
- Public Module Interfaces

A module shall never access another module's persistence directly.

Direct database access across module boundaries is prohibited.

Module dependencies shall remain explicit, minimal, and directional.

---

# Module Dependencies

```
Presentation

↓

Application

↓

Domain

↑

Infrastructure
```

Dependencies shall follow these rules

- Presentation depends on Application.
- Application depends on Domain.
- Infrastructure depends on Application and Domain abstractions.
- Domain shall never depend on Infrastructure.
- Circular dependencies are prohibited.

---

# Background Processing

Background processing shall execute independently of user requests.

Typical workloads include

- Import Processing
- Export Processing
- AI Processing
- Media Processing
- Scheduled Maintenance
- Cleanup Jobs

Background workers invoke Application Layer use cases and shall never bypass business rules.

---

# AI Architecture

Artificial Intelligence is implemented as an optional platform capability.

Business modules remain completely functional without AI.

```
React

↓

ASP.NET Core API

↓

AI Capability Layer

↓

AI Gateway

↓

Python AI Services
```

Business rules remain exclusively inside ASP.NET Core.

Python services perform computational AI workloads only.

---

```
User

↓

Product Hub

↓

AI Capability Layer

↓

AI Gateway

↓

Decision Router

↓

Provider Router

↓

AI Provider

↓

Response Validator

↓

User Review

↓

Accept / Reject
```

Business modules never communicate directly with AI providers.

---

# AI Capability Layer

The AI Capability Layer exposes reusable business-oriented AI capabilities.

Supported capabilities include

- Description Generation
- Product Categorization
- Attribute Suggestion
- Translation
- Semantic Search
- OCR
- Image Understanding
- Document Intelligence

The capability layer remains independent of specific AI providers.

---

# AI Gateway

The AI Gateway is the only component permitted to communicate with AI providers.

Responsibilities include

- Provider Selection
- Provider Authentication
- Prompt Execution
- Prompt Version Resolution
- Retry Logic
- Timeout Management
- Provider Failover
- Token Estimation
- Cost Tracking
- Usage Tracking
- Response Validation
- Response Normalization
- Structured Output Parsing
- Safety Validation

The AI Gateway shall never contain business rules.

---

# Decision Router

The Decision Router determines

- Whether AI should be used
- Which AI capability is required
- Whether organizational policies permit execution

Examples include

- Description Generation
- Product Categorization
- OCR
- Translation
- Semantic Search

---

# Provider Router

The Provider Router selects the most appropriate provider and model based upon

- Cost
- Availability
- Latency
- Model Capability
- Organization Preferences
- Edition Restrictions
- Regulatory Requirements

Provider selection remains internal to the AI platform.

---

# Python AI Services

Dedicated Python services perform computational AI workloads including

- Semantic Search
- Embedding Generation
- Vector Search
- OCR
- Image Understanding
- Document Intelligence
- Model Fine-Tuning
- Experimental AI Models

Python services communicate with ASP.NET Core through internal APIs.

Python services shall remain stateless whenever practical.

Python services shall never implement business rules.

---

# Integration Architecture

External systems communicate through integration components implemented within Infrastructure.

Examples include

- ERP Systems
- eCommerce Platforms
- Supplier Systems
- REST APIs
- File Imports
- Webhooks

Business modules remain independent of external integrations.

---

# Cost Optimization

The platform shall prioritize low recurring operational cost.

Development

- Local Docker

Production

- Linux VPS

Future

- Cloud Native Deployments

Infrastructure complexity shall increase only when justified by customer growth.

Vendor lock-in shall be avoided wherever practical.

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

Requirements

- Complete tenant isolation
- No cross-organization access
- Tenant-aware authorization
- Tenant-aware auditing

---

# Authentication

Initial authentication methods

- Email / Password

Future authentication providers

- Microsoft Entra ID
- Google
- GitHub
- SAML
- OpenID Connect

Authentication shall be delegated to an external identity provider whenever practical.

---

# Authorization

Authorization follows Role-Based Access Control (RBAC).

Initial roles

- Owner
- Administrator
- Editor
- Viewer

Future versions may support

- Custom Roles
- Permission Policies
- Attribute-Based Authorization

---

# API Architecture

Architecture Style

REST

Current Version

v1

Future capabilities

- GraphQL
- Webhooks
- Model Context Protocol (MCP) Server

Public APIs shall remain backward compatible whenever practical.

---

# Storage Architecture

Structured Data

- PostgreSQL

Object Storage

- Cloudflare R2

Temporary Storage

- Local Storage

Vector Data

- PostgreSQL with pgvector

Future Vector Storage

- Dedicated Vector Database

Backups

- PostgreSQL Backup
- Object Storage Backup

Large binary files shall never be stored inside PostgreSQL.

---

# Persistence

Database

- PostgreSQL

ORM

- Entity Framework Core

Migration Strategy

- Code First

Persistence implementations belong exclusively within Infrastructure.

---

# File Storage

Initial

- Local Storage

Future

- Cloudflare R2
- Azure Blob Storage
- Amazon S3
- Google Cloud Storage
- MinIO

Storage providers shall remain replaceable.

---

# Search

Initial implementation

- PostgreSQL Full Text Search

Capabilities

- Full Text Search
- Search Indexing

Future capabilities

- Semantic Search
- Elasticsearch
- OpenSearch

Search providers shall remain abstracted.

---

# Caching

Initial

- In-Memory Cache

Future

- Redis

Caching shall be considered an implementation detail and shall never alter business behavior.

---

# Logging

Application Logging

- Structured JSON Logs

Audit Logging

- Business Events

AI Logging

- Usage Metrics

Infrastructure Logging

- Operational Events

Sensitive information including credentials, secrets, and confidential prompts shall never be logged.

---

# Configuration

Configuration sources

- appsettings.json
- Environment Variables
- Secret Store

Configuration shall support

- Feature Flags
- AI Settings
- Storage Providers
- Organization Settings

Secrets shall never be committed to source control.

---

# Error Handling

Every exception shall produce

- Correlation ID
- Error Code
- User-safe Message

Internal implementation details shall never be exposed.

---

# Security Architecture

Security shall be enforced across multiple architectural layers.

Security controls include

- Authentication
- Authorization
- Input Validation
- Output Validation
- File Validation
- Secret Management
- Encryption
- Audit Logging
- Tenant Isolation

---

# Deployment Architecture

## Development

```
Developer

↓

Docker Compose

├── Product Hub API
├── React
├── PostgreSQL
├── Background Worker
└── Local Storage
```

---

## Production (Recommended)

```
Internet

↓

Cloudflare DNS

↓

Cloudflare CDN / SSL

↓

Linux VPS

↓

Docker Compose

├── Nginx
├── Product Hub API
├── PostgreSQL
├── Background Worker
└── Cloudflare R2
```

---

# Networking

Public DNS

- Cloudflare

SSL

- Cloudflare Universal SSL

Origin Certificates

- Let's Encrypt

TLS Mode

- Full (Strict)

Supported Protocols

- HTTP/2
- HTTP/3

All production deployments shall enforce encrypted communication.

---

# Enterprise Deployment

```
Internet

↓

Load Balancer

↓

Container Platform

↓

Multiple Product Hub Instances

↓

Managed PostgreSQL Cluster

↓

Cloudflare R2
```

Enterprise deployments may additionally include

- Redis
- Dedicated Vector Database
- Centralized Logging
- Monitoring Platform
- Secret Management Service

---

# Deployment Principles

Deployment shall follow the following principles

- Container First
- Provider Independent
- Self-Host Friendly
- Cloud Native Ready
- Immutable Deployments
- Infrastructure as Code Ready

Docker is the deployment artifact.

Kubernetes is optional and not required for the MVP.

Supported deployment targets

- Docker
- Docker Compose

Future deployment targets

- Kubernetes
- Azure Container Apps
- Google Cloud Run
- Amazon ECS

---

# CI/CD

Source Control

- GitHub

Continuous Integration

- GitHub Actions

Deployment

- Docker

Future improvements may include

- Automated Security Scanning
- Dependency Scanning
- Container Image Scanning
- Automated Deployment Validation

Deployment pipelines shall remain reproducible and automated whenever practical.

---

# AI Cost Strategy

Managed AI usage shall remain economically sustainable.

Requirements

- Usage Limits
- Organization Quotas
- Monthly Budgets
- Daily Budgets
- Request Limits
- Provider Abstraction
- Bring Your Own Provider (BYOP)
- Cost Tracking
- Usage Auditing

Artificial Intelligence shall never become an uncontrolled operational expense.

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

Extraction shall occur only after reuse has been validated across multiple products.

Stable public contracts shall be preserved during extraction.

---

# Technology Stack

## Frontend

- React
- TypeScript
- Vite

---

## Backend

- ASP.NET Core (.NET 10 LTS)
- Entity Framework Core

---

## Artificial Intelligence

- AI Capability Layer
- AI Gateway
- Python AI Services

---

## Database

- PostgreSQL

---

## Vector Storage

Initial

- PostgreSQL with pgvector

Future

- Dedicated Vector Database

---

## Object Storage

- Cloudflare R2

---

## Search

Initial

- PostgreSQL Full Text Search

Future

- Elasticsearch
- OpenSearch

---

## Caching

Initial

- In-Memory Cache

Future

- Redis

---

## Containerization

- Docker
- Docker Compose

---

## Reverse Proxy

- Nginx

---

## DNS

- Cloudflare

---

## SSL

- Cloudflare Universal SSL
- Let's Encrypt (Origin)

---

## Cloud Platforms

Future supported platforms include

- Google Cloud Run
- Azure Container Apps
- Amazon ECS

---

## CI/CD

- GitHub Actions

---

# Architecture Decision Records

## ADR-001

Decision

Architecture Style

Value

Modular Monolith

Status

Accepted

---

## ADR-002

Decision

Architecture Pattern

Value

Clean Architecture

Status

Accepted

---

## ADR-003

Decision

Domain Modeling

Value

Domain-Driven Design (DDD)

Status

Accepted

---

## ADR-004

Decision

API Style

Value

REST

Status

Accepted

---

## ADR-005

Decision

Database

Value

PostgreSQL

Status

Accepted

---

## ADR-006

Decision

AI Integration

Value

Provider Abstraction

Status

Accepted

---

## ADR-007

Decision

Deployment

Value

Docker

Status

Accepted

---

# Architecture Goals

The architecture shall provide

- Maintainability
- Extensibility
- Testability
- Scalability
- Low Operational Cost
- Enterprise Readiness
- AI Extensibility
- Strong Domain Isolation
- Platform Reusability
- Provider Independence
- Long-Term Sustainability

---

# Architecture Vision

Product Hub shall be built as a modular, enterprise-ready Product Information Management platform that prioritizes maintainability, business domain integrity, and long-term evolution over short-term technical convenience.

The architecture shall enable rapid product development for a solo founder while remaining capable of supporting enterprise customers without fundamental architectural redesign.

Business domains, rather than infrastructure technologies, shall remain the primary organizing principle of the system.

Future products shall reuse validated Platform Core capabilities while preserving strong domain boundaries and stable public contracts.

---