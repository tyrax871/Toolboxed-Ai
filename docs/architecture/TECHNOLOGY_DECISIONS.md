# Initial Technology Decisions

**Status:** Provisional architecture baseline  
**Plan item:** `PL-0003`  
**Date:** 2026-09-18

## Purpose

This document establishes an implementation-ready starting point for Toolboxed while preserving decisions that require later evidence or domain review.

## Decision summary

| Area | Initial decision | Confidence |
|---|---|---|
| Application shape | Modular monolith with explicit domain modules and background-job seams | Provisional |
| Frontend | TypeScript web application; framework remains open until team and deployment constraints are confirmed | Open |
| Backend | Typed HTTP API with command/query separation and module-owned business rules | Provisional |
| Database | PostgreSQL-compatible relational database; spatial extension remains under evaluation | Provisional |
| BIM and geometry | Stable model IDs, immutable revisions, explicit coordinate systems, and geometry behind an adapter boundary | Provisional |
| Files | S3-compatible object storage with metadata in the relational database | Provisional |
| Identity | Managed OIDC/OAuth2-capable identity provider with application-owned organisation and membership records | Provisional |
| Jobs | Durable queue and workers for generation, metrics, exports, and imports | Provisional |
| Realtime | Polling or server-sent events for the first vertical slice; WebSockets deferred | Provisional |
| Deployment | Separate local, test, staging, and production environments with repeatable migrations | Provisional |
| Observability | Structured logs, metrics, traces, error reporting, and user-visible job status | Provisional |
| Testing | Domain, API contract, integration, end-to-end, accessibility, and performance checks | Provisional |

## Architectural principles

- The central model is the source of truth; views, metrics, exports, and alternatives are derived or provisional.
- Approved revisions are immutable. New changes create new revisions or controlled transactions.
- Frontend code consumes screen projections and typed contracts, not database tables.
- Backend commands enforce permissions, validation, units, provenance, and audit events.
- Geometry and BIM exchange are isolated behind adapters so the domain model is not coupled to one vendor or file format.
- Long-running work is asynchronous, observable, retryable, cancellable where safe, and idempotent.
- Every tenant-scoped record carries organisation and, where applicable, project scope.

## Open decisions

- Frontend framework and rendering libraries.
- Backend language and framework.
- Exact spatial extension, geometry kernel, BIM exchange format, and model granularity.
- Identity provider, hosting provider, queue implementation, and object-storage provider.
- Initial building typology, regulatory jurisdiction, scale targets, and performance budgets.

## Consequences

This baseline supports Group 1 without prematurely committing the project to a geometry vendor or microservice architecture. It requires clear module boundaries, typed contracts, migration discipline, and early performance fixtures before BIM-heavy implementation begins.

## Acceptance state

This document is a provisional baseline for implementation planning. Critical open decisions require review before production implementation begins.
