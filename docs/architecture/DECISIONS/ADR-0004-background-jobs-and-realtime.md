# ADR-0004: Background Jobs and Realtime Updates

- **Status:** Accepted as provisional
- **Plan item:** `PL-0003`
- **Date:** 2026-09-18

## Decision

Run generation, metrics, imports, exports, and heavy validation as durable background jobs. Persist job state, progress, attempts, errors, cancellation requests, inputs, outputs, and correlation identifiers. Workers must be idempotent where practical and must not mutate an approved revision in place.

Use polling or server-sent events for the first vertical slice. Defer WebSockets until measured collaboration or interaction requirements justify them.

## Alternatives considered

- Synchronous HTTP work: rejected for long-running and failure-prone operations.
- WebSockets first: deferred because it increases operational and client-state complexity before collaboration needs are measured.
- In-memory queue: rejected because it cannot provide durable recovery.

## Consequences

The UI must represent queued, running, partial, completed, failed, cancelled, expired, and recoverable states. Queue and worker choice, progress semantics, and hosting integration remain open.
