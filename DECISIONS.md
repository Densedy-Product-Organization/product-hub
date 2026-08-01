# Product Hub Architecture & Product Decisions

**Product:** Product Hub

**Version:** 0.1.0

**Status:** Active

---

# Purpose

This document records significant product, architecture, technology, and engineering decisions.

Each decision includes the context, rationale, consequences, and current status.

Once accepted, decisions become part of the project's baseline unless superseded.

---

# Decision Status

- Proposed
- Accepted
- Deprecated
- Superseded

---

# DEC-001

## Title

Modular Monolith Architecture

### Status

Accepted

### Decision

Product Hub shall be implemented as a Modular Monolith.

### Rationale

- Solo founder
- Faster development
- Easier debugging
- Lower cloud cost
- Simpler deployment
- Easier testing

### Consequences

Positive

- Rapid delivery
- Low operational complexity

Negative

- Future extraction may be required

---

# DEC-002

## Title

REST API First

### Status

Accepted

### Decision

REST shall be the primary integration interface.

### Rationale

- Industry standard
- Broad ecosystem support
- Simple implementation

### Future

GraphQL

Webhooks

MCP

---

# DEC-003

## Title

PostgreSQL Database

### Status

Accepted

### Decision

PostgreSQL shall be the primary database.

### Rationale

- Mature
- Open Source
- Enterprise Ready
- Excellent JSON support
- Full Text Search

---

# DEC-004

## Title

Entity Framework Core

### Status

Accepted

### Decision

Entity Framework Core shall be the primary ORM.

### Rationale

- Native .NET support
- Productivity
- Migrations
- Strong tooling

---

# DEC-005

## Title

React Frontend

### Status

Accepted

### Decision

The web client shall use React and TypeScript.

### Rationale

- Mature ecosystem
- Component architecture
- Excellent tooling

---

# DEC-006

## Title

Provider Independent AI

### Status

Accepted

### Decision

AI providers shall never be directly referenced by business modules.

### Rationale

- Vendor independence
- Lower risk
- Easier migration

---

# DEC-007

## Title

AI Is Optional

### Status

Accepted

### Decision

Product Hub shall remain fully functional without AI.

### Rationale

- Lower operating cost
- Customer flexibility
- Enterprise adoption

---

# DEC-008

## Title

Human Approval Required

### Status

Accepted

### Decision

AI-generated content shall always require explicit user approval.

### Rationale

- Prevent accidental changes
- Improve trust
- Preserve data quality

---

# DEC-009

## Title

Organization Isolation

### Status

Accepted

### Decision

Every business entity belongs to exactly one Organization.

### Rationale

- Multi-tenancy
- Security
- Data isolation

---

# DEC-010

## Title

Business Rules Override AI

### Status

Accepted

### Decision

Business validation always has precedence over AI recommendations.

### Rationale

AI may assist.

AI never governs.

---

# DEC-011

## Title

Platform Core First

### Status

Accepted

### Decision

Reusable capabilities shall eventually be extracted into Platform Core.

### Candidate Modules

- Identity
- Authorization
- Audit
- AI Gateway
- Notifications
- Licensing

---

# DEC-012

## Title

Low Cloud Cost Strategy

### Status

Accepted

### Decision

Every feature shall be evaluated against operational cost.

### Rationale

The platform must remain profitable at small scale.

---

# DEC-013

## Title

Enterprise Documentation Standard

### Status

Accepted

### Decision

Every product repository shall maintain standardized documentation.

Required Documents

- README.md
- MVP-SCOPE.md
- PRODUCT-REQUIREMENTS.md
- DOMAIN-MODEL.md
- ARCHITECTURE.md
- API-SPECIFICATION.md
- SECURITY.md
- AI-STRATEGY.md
- ROADMAP.md
- CHANGELOG.md
- DECISIONS.md

---

# DEC-014

## Title

Documentation Before Code

### Status

Accepted

### Decision

Product requirements, domain model, and architecture shall be completed before implementation begins.

### Rationale

Reduce rework.

Improve quality.

---

# DEC-015

## Title

Build One Complete Workflow

### Status

Accepted

### Decision

The MVP shall prioritize one complete business workflow instead of numerous disconnected features.

### Workflow

Organization

↓

Taxonomy

↓

Attributes

↓

Import

↓

Validation

↓

AI Assistance

↓

Review

↓

Export

---

# DEC-016

## Title

AI Cost Governance

### Status

Accepted

### Decision

Managed AI usage shall always be budget controlled.

### Requirements

- Monthly Budget
- Request Limits
- Provider Routing
- Usage Tracking
- Cost Tracking

---

# DEC-017

## Title

Enterprise First

### Status

Accepted

### Decision

Every architectural decision shall support future enterprise growth without introducing unnecessary complexity into the MVP.

---

# DEC-018

## Title

Source of Truth

### Status

Accepted

### Decision

Product Hub shall become the authoritative source of product master data.

External systems synchronize from Product Hub.

---

# DEC-019

## Title

Technology Stack

### Status

Accepted

Backend

- .NET 9
- ASP.NET Core
- Entity Framework Core

Frontend

- React
- TypeScript

Database

- PostgreSQL

Container

- Docker

CI/CD

- GitHub Actions

---

# DEC-020

## Title

Founder Engineering Principles

### Status

Accepted

### Decision

The project shall follow these engineering principles:

- Solve business bottlenecks.
- AI is a capability.
- AI must pay for itself.
- Enterprise architecture over shortcuts.
- Low cloud cost.
- Platform before duplication.
- Architecture before implementation.
- Revenue before complexity.
- Founder time is valuable.
- Build for decades, ship today.

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 0.1.0 | Initial | Initial decision register established |