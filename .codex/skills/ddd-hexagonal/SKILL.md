# Skill — ddd-hexagonal

## Purpose

Apply Domain-Driven Design (DDD) and Hexagonal Architecture consistently across the project.

This skill protects the Domain from framework pollution, preserves business clarity, and ensures architectural decisions remain explicit and sustainable.

The objective is not academic DDD.

The objective is operational clarity and long-term maintainability.

---

## Use This Skill When

Use this skill for:

* designing aggregates
* defining Entities and Value Objects
* creating repository contracts
* identifying bounded contexts
* defining ports and adapters
* protecting business invariants
* reviewing architectural boundaries
* validating dependency direction
* deciding Domain vs Application responsibilities

If the question is "where should this logic live?", this skill should be used.

---

## Core Rule

The Domain is the center.

Everything else serves it.

Frameworks, databases, queues, HTTP, and persistence are implementation details.

Never allow Infrastructure to define business truth.

---

## Decision Rules

### Domain

Use Domain for:

* business rules
* invariants
* Entities
* Value Objects
* Aggregates
* Domain Services
* repository contracts
* domain events

Domain must remain framework-independent.

---

### Application

Use Application for:

* use case orchestration
* commands and queries
* transactions
* workflow coordination
* interaction between Domain and Infrastructure

Application coordinates.

Domain decides.

---

### Infrastructure

Use Infrastructure for:

* ORM
* database access
* repository implementations
* external APIs
* messaging
* cache
* framework adapters

Infrastructure is replaceable.

---

### Interface

Use Interface for:

* controllers
* CLI commands
* workers
* request validation
* response formatting

Controllers must remain thin.

---

## Repository Rule

Repositories are defined in Domain.

Implementations live in Infrastructure.

Never design repositories from ORM limitations first.

Repositories must speak business language.

---

## Aggregate Rule

Ask:

* what invariant must be protected
* what consistency boundary exists
* what should change together

Do not create aggregates from tables.

Create them from business consistency.

---

## Value Object Rule

If a concept has:

* validation rules
* behavior
* meaning
* identity by value

it probably deserves a Value Object.

Avoid primitive obsession.

---

## Bounded Context Rule

Each context must have:

* clear ownership
* explicit language
* protected boundaries
* low ambiguity

Examples:

* Personnel Management
* Incident Management
* Vehicle Operations
* Equipment Control

Do not create fake shared ownership.

---

## Review Questions

Before implementation, ask:

* which bounded context owns this
* what invariant is protected
* is this Domain or Application logic
* is framework coupling leaking
* should this be a Value Object
* is this repository contract correct

If unclear, stop and redesign first.

---

## Forbidden

* fat controllers
* anemic domain models
* generic service classes full of business logic
* framework annotations inside Domain
* direct ORM usage inside Domain
* Infrastructure deciding business rules
* unclear bounded contexts

These are architecture failures, not style issues.

---

## Expected Output

This skill should produce:

* clear layer placement
* explicit aggregate boundaries
* protected Domain invariants
* repository contracts aligned with business language
* safe dependency direction
* architecture decisions aligned with ADRs

The result should make the system simpler to evolve, not more complex.
