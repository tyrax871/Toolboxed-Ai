# ADR-0003: Authentication and Access

- **Status:** Accepted as provisional
- **Plan item:** `PL-0003`
- **Date:** 2026-09-18

## Decision

Use a managed OIDC/OAuth2-capable identity provider for authentication, while keeping organisation, membership, role, project access, invitation, suspension, and audit records in Toolboxed. The backend remains the authority for tenant isolation and action permissions.

Use short-lived access credentials with secure session handling, explicit sign-out, invitation expiry, account recovery through the provider, and auditable security-sensitive actions.

## Alternatives considered

- Build authentication from scratch: rejected because identity security and recovery are not the product differentiator.
- Provider-owned authorisation: rejected because project, professional-role, approval, and model permissions are domain-specific.
- Anonymous application access: rejected because Toolboxed handles controlled project information and auditability.

## Consequences

Authentication can be replaced behind an adapter, while domain access rules remain stable. Provider selection, regional requirements, session implementation, MFA policy, and enterprise SSO needs require review.
