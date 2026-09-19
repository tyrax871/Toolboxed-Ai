# PL-0003 Architecture Evaluation Fixture

- **Status:** Proposed evaluation fixture
- **Plan item:** `PL-0003`
- **Increment:** Discover and define the representative architecture evaluation fixture
- **Date:** 2026-09-19

## Purpose

Define a bounded, representative fixture for evaluating the remaining Toolboxed architecture decisions before application implementation, migrations, public APIs, or provider-specific infrastructure are authorised. This document defines the workload and evidence target; it does not claim that the proposed technology choices are final.

## Fixture brief

Use a small, low-rise residential project with one primary building and a simple external site. The fixture should be sufficiently rich to exercise architectural model relationships, revisions, generated views, spatial queries, geometry operations, storage, and background-job seams without pretending to represent enterprise-scale performance.

### Assumptions

| Category | Fixture assumption | State |
|---|---|---|
| Building type | Low-rise residential building with a small number of levels and rooms | Proposed |
| Jurisdiction | To be confirmed by the product owner; use an explicitly labelled neutral assumption during evaluation | Open |
| Units | Metric units; store units and conversions explicitly | Proposed |
| Coordinates | Local project coordinates with documented origin, orientation, and reference system | Proposed |
| Standards | Project standards and naming conventions are fixture data, not hidden defaults | Proposed |
| Professional responsibility | Fixture is for architecture and platform evaluation, not regulatory approval | Confirmed constraint |
| Source provenance | Generated or adapted fixture must record its source, generator, version, and license | Required |

## Minimum model contents

- Site boundary, orientation, survey/reference points, setbacks, and constraints.
- Two or more levels, grids, reference geometry, and project units.
- Rooms/spaces with names, areas, zones, occupancy, and level relationships.
- Walls, floors/slabs, roof, ceilings, openings, doors, and windows.
- At least one material or assembly relationship and derived property.
- Existing, new, proposed, relocated, and superseded state examples where meaningful.
- Stable identifiers for project, levels, spaces, elements, relationships, revisions, snapshots, and audit events.
- Representative site plan, floor plan, section, elevation, and simple 3D/model view references.

The fixture must be small enough to inspect manually and rich enough to test containment, adjacency, connectivity, dependencies, change propagation, and provenance.

## Workloads and evaluation evidence

| Workload | Required evidence | Decisions informed |
|---|---|---|
| Model load and query | Entity/relationship counts, load time, representative query plans, coordinate and containment queries | Model granularity, database, spatial extension |
| Model edit | Wall, opening, room-boundary, level, and element-property changes with dependency effects | Geometry boundary, domain modules, revision semantics |
| Revision and recovery | Immutable revision, snapshot, diff, autosave acknowledgement, undo/redo seam, restore, and audit trail | Storage, transaction model, audit, recovery |
| IFC exchange | Import/export or adapter fixture, stable-ID mapping, unsupported-property report, loss/provenance record | BIM exchange and model granularity |
| Geometry | Wall/opening/room validity, section/elevation derivation, coordinate transforms, and adapter response | Geometry kernel and rendering boundary |
| Workspace | 2D workspace readiness, selection/linking, loading/error/recovery states, optional isolated WebGL view | Frontend, rendering, performance |
| Storage | Metadata, checksum, ownership, authorization, retention, signed access, and orphan-repair scenario | Object storage and operational design |
| Background job | Import, export, or validation payload with retry, restart recovery, idempotency, cancellation, progress, and failure states | Queue and worker architecture |
| Access and security | Positive/negative project permissions, tenant isolation, audit, redaction, and secure artifact access | Identity, authorization, storage, audit |
| Quality | Domain invariants, API contract shape, accessibility checks, recovery paths, and review checklist | Testing and observability strategy |

## Measurement protocol

Every measured result must record:

- Fixture version and source provenance.
- Tool, framework, runtime, database, renderer, and provider versions.
- Hardware, operating system, browser, network profile, and test configuration.
- Dataset entity count, relationship count, file size, and generated-artifact size.
- Warm/cold state, repetition count, percentile method, and known exclusions.
- Result, threshold or observation, limitation, and decision affected.

No benchmark is acceptance evidence if its environment, workload, or fixture version is missing.

## Initial target observations

These are evaluation targets, not production SLOs:

- Ordinary read paths should be assessed against the provisional p95 target of 500 ms.
- Autosave acknowledgement should be assessed against the provisional target of 1 second under normal conditions.
- Initial workspace usability should be assessed against the provisional target of 3 seconds on the agreed test profile.
- Long-running work must remain observable and must not block ordinary reads.
- Results may revise these targets when the fixture and environment show that they are inappropriate.

## Traceability matrix

| Evidence group | Fixture input | Expected record | Acceptance owner |
|---|---|---|---|
| Semantic model | Entity and relationship inventory | Model contract and provenance notes | BIM/domain and technical reviewers |
| Spatial | Coordinates, levels, containment, site boundary | Spatial decision and query evidence | Technical and BIM/domain reviewers |
| Geometry | Representative edit and view operations | Adapter/kernel evaluation | BIM/domain and technical reviewers |
| Exchange | IFC-compatible mapping or documented limitation | Import/export loss and provenance report | BIM/domain reviewer |
| Application | Account, project, model, save, revision, recovery flows | Vertical-slice acceptance evidence | Product and technical reviewers |
| Operations | Storage and background-job failure scenarios | Recovery and observability evidence | Technical, security, and QA reviewers |
| Quality | Permission, accessibility, error, and validation cases | Test and review record | Security and QA reviewers |

## Review checklist

- Product owner confirms building type, project scope, jurisdiction treatment, and first-slice relevance.
- Technical lead confirms the workload is sufficient to compare application, database, frontend, rendering, storage, and job alternatives.
- BIM/domain architect confirms semantic entities, relationships, geometry operations, exchange boundary, and provenance requirements.
- Security lead confirms tenant isolation, permission negatives, artifact access, secrets, redaction, and audit cases.
- QA lead confirms reproducibility, acceptance observations, accessibility, recovery, and failure-state coverage.

Reviewers must record amendments, unresolved questions, owners, unblock conditions, and evidence required for the next increment. Approval of the fixture does not approve a vendor or framework; it authorises measured evaluation only.

## Exit criteria for this increment

This fixture definition is ready for review when its scope, assumptions, workloads, measurement protocol, traceability, and review checklist are documented. The next increment may begin only after the fixture is accepted or its amendments are explicitly recorded. PL-0003 remains **Active / Partial execution** until measured evidence and architecture acceptance are complete.

## Known limitations

- No source BIM file, regulatory jurisdiction, stakeholder approval, runtime, benchmark, or provider has been confirmed in this document.
- The fixture does not establish enterprise-scale capacity.
- Geometry-kernel licensing and exact exchange behaviour require separate review.
- Application code and infrastructure are intentionally out of scope for this increment.
