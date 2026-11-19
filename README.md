# VisionFlow

> A reusable workflow automation engine built with Java.  
> Current phase: **V1 — Java Core & State Machine** (not yet a deployable workflow service).

## Problem Statement

Many business applications implement approval flows separately. Repeated workflow logic can become difficult to change, test and audit as the number of processes grows.

**VisionFlow aims to provide a reusable workflow orchestration core** that can eventually be integrated into HRM, ERP and CRM systems through APIs.

> TODO (developer): Rewrite this problem statement in your own words and describe one concrete example.

## MVP Scope

**First use case:** Leave request approval.

Planned MVP capabilities (V1–V3):
- Create and submit a leave request.
- Approve or reject a pending request, with authorized actors.
- Validate state transitions (`DRAFT → PENDING → APPROVED/REJECTED`).
- Store an audit history of approval actions.
- Enforce data consistency under concurrent approval requests.
- Expose REST APIs and test the workflow end-to-end.

**Out of scope for the MVP:** Visual workflow designer, multi-tenancy, Kafka, Redis, Kubernetes, microservices, SaaS billing and arbitrary workflow configuration.

## Architecture

- **V1:** Plain Java domain model + state machine + JUnit 5.
- **V2–V3 (planned):** Spring Boot modular monolith with REST API, persistence, authorization and audit.
- **V4 (future):** Configurable workflow definitions, instances, tasks and versioning.

See [Architecture Notes](docs/architecture.md).

## Tech Stack (Current)

- Java 21
- Maven
- JUnit 5

**Planned later:** Spring Boot, Spring Security, Spring Data JPA, PostgreSQL, Docker, k6.

## Local Setup

Prerequisites: JDK 21, Maven 3.9+, Git and IntelliJ IDEA (optional).

```bash
java -version
mvn -version
mvn clean test
```

Run the placeholder application:

```bash
mvn -q -DskipTests compile
java -cp target/classes com.visionflow.App
```

## Project Structure

```text
src/main/java/com/visionflow/
├── App.java
├── model/       # WorkflowStatus and LeaveRequest (to be implemented)
└── engine/      # Transition validation (to be implemented)
src/test/java/com/visionflow/  # JUnit tests (to be implemented)
```

## Current Checklist

- [ ] Explain the problem statement in your own words.
- [ ] Confirm valid and invalid workflow transitions.
- [ ] Implement `WorkflowStatus`.
- [ ] Implement `LeaveRequest` and its state-changing methods.
- [ ] Write meaningful JUnit tests for valid and invalid transitions.
- [ ] Commit the first working implementation.

## Status

**Scaffold only.** Workflow behavior has not yet been implemented or tested. Do not claim production readiness or performance benchmarks.
