# ADR-0001: Initial Application Architecture

- **Status:** Accepted as provisional
- **Plan item:** `PL-0003`
- **Date:** 2026-09-18

## Context

Toolboxed has no application code yet but must support identity, project access, BIM model governance, background generation, documents, approvals, and future specialist overlays.

## Decision

Start with a modular monolith. Organise the backend around explicit modules such as identity/access, projects, design briefs, model/revisions, documents, coordination, and audit. Keep background computation behind durable job interfaces. Keep geometry, BIM exchange, notifications, and object storage behind adapters.

## Alternatives considered

- **Microservices first:** rejected because the domain and operational requirements are not yet measured; it would add deployment and consistency complexity too early.
- **Unstructured monolith:** rejected because it would allow duplicated rules and make later boundaries difficult to recover.
- **Frontend-only prototype:** rejected because permissions, revision history, provenance, and model integrity require authoritative backend behaviour.

## Consequences

Positive: simpler local development, transactional workflows, shared domain rules, and a clear path to later extraction. Negative: module boundaries must be actively enforced and compute-heavy workloads still require separate workers.

## Exit or revision criteria

Reconsider service separation only after measured workload, team ownership, scaling, deployment, or isolation requirements justify it.
