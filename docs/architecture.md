# VisionFlow Architecture Notes

## Initial direction

**V1** is a small plain-Java codebase focused on domain modeling, OOP, state transitions and unit tests. Do not introduce Spring or a database prematurely.

**V2–V3** will be one Spring Boot application organized by business capability (modular monolith), with layers within modules where useful. This is an intended architecture, not an implemented one.

**V4** may extract a configurable workflow core so multiple business systems can reuse the same workflow engine through APIs.

## Initial workflow

```text
DRAFT --submit--> PENDING --approve--> APPROVED
                         \\--reject--> REJECTED
```

`APPROVED` and `REJECTED` are terminal states in V1. Define invalid transitions explicitly and test them.

## Architectural decisions to validate

1. State transitions are enforced in the domain, not only in controllers.
2. Later: approval and audit persistence must be atomic.
3. Later: resource-level authorization is required, not only roles.
4. Later: concurrent requests must not produce conflicting approvals.
5. Keep deployment simple until concrete needs justify distributed services.
