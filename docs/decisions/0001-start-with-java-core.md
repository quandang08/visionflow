# ADR 0001 — Start with a plain-Java workflow domain

- Status: Proposed
- Date: 2026-11-19

## Context

VisionFlow targets a reusable workflow engine, but its first use case is leave request approval. The initial goal is to verify business rules and developer understanding before adding infrastructure.

## Decision

Begin with Java 21, Maven and JUnit 5. Model statuses and transitions without Spring Boot or persistence. Introduce a modular-monolith Spring Boot architecture in V2.

## Consequences

- Faster feedback on domain logic and simpler tests.
- V1 cannot expose an API or persist requests.
- Persistence and security requirements will be introduced in later versions.
