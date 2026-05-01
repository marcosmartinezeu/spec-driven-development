# ADR-0001 — Architecture Style

## Status

Accepted

---

## Context

The project requires long-term maintainability, clear business boundaries, and the ability to evolve independently from framework decisions.

The codebase must support:

* Complex business rules
* Incremental delivery
* Testability
* Team scalability
* Reduced framework coupling
* Explicit technical decisions

Using framework-first development creates long-term problems such as business logic leakage into controllers, poor testability, infrastructure coupling, and high refactoring cost.

A clear architectural baseline is required from the beginning.

---

## Decision

The project will use:

* Domain-Driven Design (DDD)
* Hexagonal Architecture (Ports and Adapters)
* Framework-independent Domain Layer
* Application Layer for use cases orchestration
* Infrastructure Layer for technical implementations
* Explicit bounded contexts

Frameworks such as Symfony or Laravel are considered delivery mechanisms, not the center of the architecture.

The Domain must remain independent from:

* ORM implementations
* HTTP controllers
* framework services
* queues
* persistence details
* external APIs

All framework-specific concerns must remain in Infrastructure or Interface layers.

---

## Layer Responsibilities

## Domain

Responsible for:

* Entities
* Value Objects
* Aggregates
* Domain Services
* Domain Events
* Business invariants
* Ubiquitous language

Must not depend on frameworks.

---

## Application

Responsible for:

* Use cases
* Command handling
* Query handling
* Transaction orchestration
* Application services
* Coordination between domain and infrastructure

Contains business flow, but not business rules.

---

## Infrastructure

Responsible for:

* Database access
* ORM
* Messaging
* External services
* Cache
* Framework adapters
* Repository implementations

This layer depends on Domain and Application, never the opposite.

---

## Interface Layer

Responsible for:

* HTTP controllers
* CLI commands
* Workers
* API endpoints
* Request validation
* Response formatting

Thin adapters only.

Controllers must never contain business logic.

---

## Consequences

### Positive

* Higher maintainability
* Safer refactoring
* Better testability
* Explicit architecture decisions
* Lower framework lock-in
* Better onboarding for new developers

### Negative

* Higher initial complexity
* More upfront design effort
* Slower early development speed
* Requires discipline across the team

These trade-offs are accepted in favor of long-term sustainability.

---

## Rules Derived From This Decision

### Forbidden

* Fat controllers
* Domain logic inside services tied to the framework
* Direct ORM usage inside Domain
* Framework annotations inside Domain models
* Repositories defined in Infrastructure first

### Required

* Repository contracts defined in Domain
* Use cases isolated in Application
* Explicit ports and adapters
* ADR update when architecture changes

---

## Review Policy

This ADR must be reviewed when:

* a new bounded context is introduced
* architecture complexity grows significantly
* a major framework migration is proposed
* a new delivery model is adopted

Architecture changes must produce a new ADR, never silent implementation drift.
