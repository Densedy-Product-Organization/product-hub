# Contributing Guide

**Product:** Product Hub

**Version:** 0.1.0

---

# Purpose

This document defines the engineering standards for contributing to Product Hub.

Every contribution shall improve maintainability, consistency, quality, and long-term sustainability.

---

# Engineering Principles

- Business First
- Domain Driven Design
- Clean Architecture
- Modular Monolith
- API First
- Security by Default
- AI is Optional
- Low Cloud Cost
- Enterprise Quality
- Simplicity over Cleverness

---

# Branch Strategy

Main Branch

```
main
```

Protected.

Development Branch

```
develop
```

Feature Branch

```
feature/<feature-name>
```

Bug Fix

```
bugfix/<issue-name>
```

Hot Fix

```
hotfix/<issue-name>
```

Documentation

```
docs/<topic>
```

---

# Commit Convention

Format

```
type(scope): summary
```

Examples

```
feat(product): add product aggregate

feat(taxonomy): recursive taxonomy

fix(search): pagination bug

docs(api): update endpoints

refactor(ai): simplify provider routing

test(product): add aggregate tests
```

---

# Commit Types

- feat
- fix
- docs
- refactor
- test
- build
- ci
- perf
- style
- chore

---

# Pull Requests

Every Pull Request shall

- Build successfully
- Pass all tests
- Include documentation updates
- Maintain architecture principles
- Preserve backward compatibility unless approved

---

# Coding Standards

General

- Prefer readability.
- Avoid premature optimization.
- Keep methods small.
- Keep classes cohesive.
- Prefer composition over inheritance.
- Avoid duplicated logic.

---

# Architecture Rules

Business logic belongs only in the Domain Layer.

Infrastructure shall never contain business rules.

Presentation shall never access persistence directly.

External providers shall always be abstracted.

---

# Domain Rules

Every new domain concept shall

- Have a clearly defined Aggregate Root.
- Define invariants.
- Define ownership.
- Define lifecycle.
- Define domain events where applicable.

---

# API Rules

Every endpoint shall

- Validate input.
- Enforce authorization.
- Return consistent responses.
- Support correlation identifiers.
- Avoid exposing internal implementation details.

---

# Security Rules

Never

- Commit secrets.
- Disable authorization.
- Ignore validation.
- Trust client input.
- Log passwords.
- Log tokens.
- Log AI provider keys.

---

# AI Rules

AI features shall

- Be optional.
- Require user confirmation.
- Be provider independent.
- Be measurable.
- Be budget controlled.

Business rules always override AI recommendations.

---

# Testing Requirements

Every feature shall include

- Unit Tests
- Integration Tests where applicable
- Authorization Tests where applicable

Critical business rules shall always be tested.

---

# Documentation Requirements

Every architectural change shall update the appropriate documentation.

Possible documents include

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

# Definition of Done

A feature is complete only when

- Requirements implemented
- Tests passing
- Documentation updated
- Code reviewed
- Security considered
- Build successful

---

# Code Review Checklist

Reviewers shall verify

- Business correctness
- Architecture compliance
- Security
- Performance
- Readability
- Maintainability
- Test coverage
- Documentation updates

---

# Contributor Philosophy

Every contribution should leave Product Hub better than it was before.

Quality, simplicity, maintainability, and long-term sustainability take precedence over short-term speed.