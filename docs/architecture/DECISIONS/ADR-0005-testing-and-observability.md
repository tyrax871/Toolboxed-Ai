# ADR-0005: Testing and Observability

- **Status:** Accepted as provisional
- **Plan item:** `PL-0003`
- **Date:** 2026-09-18

## Decision

Build validation in layers: domain invariants and permission tests; API contract and integration tests; end-to-end Group 1 workflows; accessibility and visual-state checks; performance fixtures for model and generation workloads; and recovery tests for jobs and storage failures.

Use structured logs with correlation IDs, metrics for requests, jobs, and model validation, traces across API and workers, error reporting with redaction, and user-visible status for recoverable failures.

## Alternatives considered

- End-to-end tests only: rejected because domain and permission failures would be slow to diagnose.
- Logs only: rejected because job health, performance, and cross-service timing require metrics and traces.
- Observability after launch: rejected because the platform has asynchronous and model-integrity risks from the beginning.

## Consequences

Every module and job needs test seams and correlation metadata. Exact tools and thresholds remain open until runtime and hosting choices are selected.
