# Product Hub REST API Specification

**Product:** Product Hub

**Version:** 0.1.0

**API Version:** v1

**Status:** Draft

---

# Purpose

This document defines the REST API contract for Product Hub.

The API is the primary integration mechanism between Product Hub and external applications.

The API shall remain stable, versioned, secure, and backward compatible.

---

# API Principles

API-001

REST First

---

API-002

JSON Request and Response

---

API-003

HTTPS Only

---

API-004

Versioned Endpoints

---

API-005

Stateless

---

API-006

Idempotent Where Applicable

---

API-007

Secure by Default

---

API-008

Organization Isolation

---

API-009

Consistent Error Responses

---

API-010

Pagination for Collections

---

# Base URL

```
https://api.producthub.com/api/v1
```

---

# Authentication

Bearer Token

```
Authorization: Bearer {access_token}
```

---

# Standard Headers

```
Authorization

Content-Type

Accept

X-Correlation-Id
```

---

# Standard Response

```json
{
  "success": true,
  "data": {},
  "errors": [],
  "correlationId": "..."
}
```

---

# Standard Error Response

```json
{
  "success": false,
  "errors": [
    {
      "code": "PRODUCT_NOT_FOUND",
      "message": "Product not found."
    }
  ],
  "correlationId": "..."
}
```

---

# HTTP Status Codes

| Code | Description |
|------|-------------|
|200|Success|
|201|Created|
|204|No Content|
|400|Bad Request|
|401|Unauthorized|
|403|Forbidden|
|404|Not Found|
|409|Conflict|
|422|Validation Error|
|429|Too Many Requests|
|500|Internal Server Error|

---

# Authentication Endpoints

## Login

POST

```
/auth/login
```

---

## Logout

POST

```
/auth/logout
```

---

## Refresh Token

POST

```
/auth/refresh
```

---

## Register

POST

```
/auth/register
```

---

## Forgot Password

POST

```
/auth/forgot-password
```

---

## Reset Password

POST

```
/auth/reset-password
```

---

# Organization Endpoints

## List Organizations

GET

```
/organizations
```

---

## Get Organization

GET

```
/organizations/{id}
```

---

## Create Organization

POST

```
/organizations
```

---

## Update Organization

PUT

```
/organizations/{id}
```

---

## Delete Organization

DELETE

```
/organizations/{id}
```

---

# Product Endpoints

## List Products

GET

```
/products
```

Supports

- Pagination
- Sorting
- Filtering

---

## Get Product

GET

```
/products/{id}
```

---

## Create Product

POST

```
/products
```

---

## Update Product

PUT

```
/products/{id}
```

---

## Archive Product

POST

```
/products/{id}/archive
```

---

## Delete Product

DELETE

```
/products/{id}
```

---

# Product Model Endpoints

GET

```
/products/{id}/models
```

POST

```
/products/{id}/models
```

PUT

```
/models/{id}
```

DELETE

```
/models/{id}
```

---

# Variant Endpoints

GET

```
/models/{id}/variants
```

POST

```
/models/{id}/variants
```

PUT

```
/variants/{id}
```

DELETE

```
/variants/{id}
```

---

# Taxonomy Endpoints

GET

```
/taxonomy
```

POST

```
/taxonomy
```

PUT

```
/taxonomy/{id}
```

DELETE

```
/taxonomy/{id}
```

---

# Attribute Endpoints

GET

```
/attributes
```

POST

```
/attributes
```

PUT

```
/attributes/{id}
```

DELETE

```
/attributes/{id}
```

---

# Media Endpoints

GET

```
/products/{id}/media
```

POST

```
/products/{id}/media
```

DELETE

```
/media/{id}
```

---

# Document Endpoints

GET

```
/products/{id}/documents
```

POST

```
/products/{id}/documents
```

DELETE

```
/documents/{id}
```

---

# Import Endpoints

POST

```
/imports/products
```

---

GET

```
/imports/{id}
```

---

# Export Endpoints

POST

```
/exports/products
```

---

GET

```
/exports/{id}
```

---

# Search Endpoints

GET

```
/search
```

Supported Parameters

- keyword
- category
- status
- model
- variant
- page
- pageSize
- sort

---

# Audit Endpoints

GET

```
/audit
```

---

GET

```
/audit/{id}
```

---

# AI Endpoints

## Category Suggestion

POST

```
/ai/category-suggestions
```

---

## Attribute Suggestion

POST

```
/ai/attribute-suggestions
```

---

## Description Generation

POST

```
/ai/description-generation
```

---

## Data Quality Analysis

POST

```
/ai/data-quality
```

---

# Pagination

Request

```
?page=1&pageSize=25
```

Response

```json
{
  "page":1,
  "pageSize":25,
  "totalPages":10,
  "totalRecords":250
}
```

---

# Sorting

```
?sort=name

?sort=-createdDate
```

---

# Filtering

Examples

```
?status=Active

?category=Laptops

?brand=Dell
```

---

# Validation Rules

- Invalid requests return HTTP 400
- Business validation returns HTTP 422
- Unauthorized requests return HTTP 401
- Forbidden operations return HTTP 403

---

# Rate Limiting

Authenticated APIs

100 Requests / Minute

AI APIs

Configurable Per Organization

---

# Organization Isolation

Every request executes within one Organization.

Cross-organization access is prohibited.

---

# API Versioning

Current

```
v1
```

Future versions

```
v2

v3
```

Breaking changes require a new API version.

---

# Security Requirements

- HTTPS Required
- JWT Authentication
- RBAC Authorization
- Input Validation
- Output Encoding
- File Validation
- Audit Logging
- Correlation ID
- Rate Limiting

---

# Future Endpoints

Future releases may include

- GraphQL
- Webhooks
- MCP Server
- Bulk Operations
- Batch Import
- Batch Export
- Semantic Search
- AI Agent APIs

---

# Design Goals

The Product Hub REST API shall be

- Consistent
- Predictable
- Secure
- Versioned
- Extensible
- Enterprise Ready
- Cloud Native
- Provider Independent
- Low Operational Cost

This specification serves as the authoritative REST API contract for Product Hub.