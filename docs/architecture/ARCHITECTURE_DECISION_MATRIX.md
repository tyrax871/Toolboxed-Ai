# PL-0003 Architecture Decision Matrix

- **Status:** Provisional recommendations pending stakeholder acceptance
- **Plan item:** `PL-0003`
- **Increment:** Frame and design the remaining architecture decisions
- **Date:** 2026-09-19

This matrix records a bounded recommendation set for the first implementation slice. Recommendations are not production-final until the required stakeholders review the assumptions and acceptance evidence.

## Decision matrix

| Area | Recommended baseline | Alternatives considered | Rationale | Acceptance evidence | State |
|---|---|---|---|---|---|
| Frontend | TypeScript web application using React, a standards-based accessible component system, and a Vite-style development/build workflow | Vue, Svelte, server-rendered HTML with progressive enhancement | Strong ecosystem for complex project workspaces, typed contracts, accessibility tooling, and future model-view integration | Working shell, keyboard/accessibility checks, route and contract tests, measured initial-load budget | Provisional |
| 2D/3D rendering | Rendering adapter boundary; start with a 2D document/model workspace and add a WebGL viewer through an isolated adapter, initially evaluating Three.js or an equivalent renderer | Direct renderer coupling, vendor-specific viewer SDK first | Keeps domain and UI independent of one geometry viewer and permits document-first Group 1 work | Prototype with representative model fixture, selection/linking test, memory and frame-time measurements | Open pending fixture |
| Backend | TypeScript modular monolith with a typed HTTP API, explicit domain modules, command/query separation, and durable worker interfaces | Python web stack, JVM/Kotlin stack, Go service, microservices first | Aligns one language across contracts and application surfaces while preserving module and worker seams | Module-boundary tests, API contract tests, permission tests, worker integration test | Provisional |
| Database | PostgreSQL with PostGIS evaluated as the initial spatial extension | PostgreSQL without spatial support, separate spatial database, document database | Supports transactional tenancy, revisions, permissions, audit, and spatial queries without splitting the system of record | Spatial fixture, migration/recovery test, query plans, representative model-scale benchmark | Provisional pending benchmark |
| Geometry kernel | Geometry behind an adapter; evaluate Open Cascade or a comparable licensed-compatible kernel only after representative operations are defined | Browser-only geometry, vendor SDK, custom kernel | Avoids coupling domain rules to one kernel and prevents premature heavy dependency | Wall/opening/room operations, validity checks, section/view fixture, licensing review | Open |
| BIM exchange | IFC4-compatible import/export adapter, with loss and provenance reporting | Proprietary native format first, IFC2x3-only baseline, direct database interchange | Provides an open exchange boundary while keeping the internal model authoritative | Round-trip fixture, unsupported-property report, stable IDs, revision/provenance checks | Provisional pending fixture |
| Model granularity | Semantic domain entities plus immutable revisions and derived geometry/artifacts; do not store the application as a mesh-only model | Mesh-only model, file-only model, one giant JSON document | Supports rooms, elements, relationships, views, permissions, audit, and controlled change propagation | Model invariant tests, revision diff, dependency graph, export/import provenance | Provisional |
| Identity | Managed OIDC/OAuth2 provider behind an adapter; Toolboxed owns organisations, memberships, roles, project access, invitations, and audit | Custom authentication, provider-owned authorisation, anonymous access | Reduces security-sensitive custom code while preserving domain-specific access control | Login/logout, invitation expiry, tenant isolation, role and project permission tests | Provisional pending provider review |
| Hosting | Containerised deployment with separate local, test, staging, and production environments; provider remains replaceable | Provider-specific serverless deployment, desktop-first deployment, microservices platform | Keeps deployment repeatable while requirements and scale are still being learned | Reproducible local startup, migration run, health checks, rollback/recovery exercise | Provisional |
| Jobs and queue | Durable provider-agnostic job interface; select a managed or self-hosted queue after worker payloads and retry requirements are measured | In-memory queue, synchronous HTTP, WebSockets-first coordination | Long-running generation/import/export/validation needs durable state, retries, and idempotency | Restart recovery, retry, cancellation, idempotency, progress and error-state tests | Provisional interface; provider open |
| Object storage | S3-compatible object storage with database metadata, checksums, ownership, retention, and repair workflow | Filesystem-only storage, database blobs, vendor-native file API | Supports large documents and generated artifacts with provenance and controlled access | Upload/download authorization, checksum, lifecycle, orphan repair, signed-access tests | Provisional |
| Initial product fixture | Low-rise residential project based on the existing reference context; jurisdiction, standards, and professional responsibilities must be confirmed by the product owner | Generic building, commercial project, multi-jurisdiction baseline | Provides a bounded fixture without pretending one jurisdiction covers all future projects | Confirmed fixture brief, representative drawings/model, units and code assumptions | Assumption pending confirmation |
| Initial scale target | Prototype target: one project, approximately 10,000 semantic elements, 100 concurrent read sessions, and one active generation/import job; revise after fixture measurement | Unlimited scale target, enterprise target first | Makes performance work measurable without claiming production capacity | Load fixture, p95 API/view timings, memory budget, worker throughput and recovery results | Proposed target |
| Initial performance budgets | p95 ordinary read API under 500 ms; autosave acknowledgement under 1 s in normal conditions; initial workspace usable under 3 s on the agreed test profile; long jobs expose progress and never block ordinary reads | No budget, rendering-only budget, production SLOs immediately | Establishes testable early constraints while allowing revision after evidence | Automated or repeatable timing fixtures with hardware/network profile recorded | Proposed target |

## Required review and acceptance

The following roles must review the matrix before the recommendations become production architecture:

- Product owner: fixture, jurisdiction, scope, and product priorities.
- Technical lead: frontend/backend/runtime, deployment, and operational fit.
- BIM/domain architect: model granularity, IFC boundary, geometry operations, and provenance.
- Security lead: identity, tenancy, secrets, storage access, and audit requirements.
- QA lead: acceptance fixtures, testability, accessibility, performance, and recovery criteria.

Acceptance requires the reviewers to approve or amend each provisional recommendation, assign owners and due dates to unresolved items, and record the evidence required for the next implementation increment. Until then, this matrix is a design aid and not a final vendor or framework commitment.

## Immediate next step

Create a small representative fixture and run the frontend, backend, spatial, geometry, exchange, storage, and job-recovery evaluations before authorising deep implementation. Update the relevant ADRs with evidence-backed decisions rather than treating this matrix as proof of runtime suitability.
