# ADR-0002: Data and Storage Strategy

- **Status:** Accepted as provisional
- **Plan item:** `PL-0003`
- **Date:** 2026-09-18

## Decision

Use a PostgreSQL-compatible relational database for transactional entities, tenancy, permissions, revisions, audit, and workflow state. Evaluate a spatial extension for site and model queries. Store large models, drawings, documents, previews, and exports in S3-compatible object storage, with checksums, media metadata, ownership, retention, and access records in the database.

Model revisions must be immutable snapshots or references to immutable model artifacts. Geometry is accessed through a domain adapter rather than embedded throughout application modules.

## Alternatives considered

- Document database first: rejected for transactional governance, relationships, and audit-heavy workflows.
- Filesystem-only storage: rejected for multi-user deployment, access control, retention, and provenance.
- Geometry-specific database as the whole system of record: deferred until model scale and exchange requirements are measured.

## Consequences

The project gains strong transactional integrity and clear provenance. Spatial indexing and large-model performance need dedicated fixtures. Object-storage lifecycle and database/file consistency require explicit workflows and repair tools.

## Open questions

Exact spatial extension, BIM exchange format, geometry kernel, model granularity, snapshot format, and retention policy remain open.
