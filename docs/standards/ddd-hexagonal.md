# Standard — DDD and Hexagonal Architecture

## Objective

Define the mandatory architectural rules for applying Domain-Driven Design (DDD) and Hexagonal Architecture consistently across the project.

These rules exist to protect the Domain, preserve business clarity, and prevent framework-driven development.

Architecture is a constraint system, not a suggestion.

---

## Core Rule

The Domain is the center of the system.

Everything else exists to serve it.

Frameworks, databases, queues, APIs, and UI are delivery mechanisms, not business owners.

If the Domain depends on Infrastructure, the architecture is already broken.

---

## Layer Model

## Domain

Responsible for:

* Entities
* Value Objects
* Aggregates
* Domain Services
* Domain Events
* Business invariants
* Ubiquitous language
* Repository contracts

Rules:

* no framework dependencies
* no ORM annotations
* no HTTP concerns
* no persistence knowledge
* no infrastructure details

The Domain defines truth.

---

## Application

Responsible for:

* use cases
* command handling
* query handling
* transaction orchestration
* application services
* workflow coordination

Rules:

* orchestrates business flow
* does not contain business rules
* depends on Domain only

Application coordinates, Domain decides.

---

## Infrastructure

Responsible for:

* database access
* ORM
* external APIs
* messaging
* cache
* filesystem
* repository implementations
* framework adapters

Rules:

* may depend on Domain and Application
* never the opposite

Infrastructure is replaceable.

---

## Interface Layer

Responsible for:

* controllers
* CLI commands
* workers
* API endpoints
* request validation
* response formatting

Rules:

* must remain thin
* must not contain business logic

Controllers translate, they do not decide.

---

## Repository Rule

Repositories are defined in Domain.

Repository implementations live in Infrastructure.

Forbidden:

* designing repositories from ORM limitations first
* leaking query builders into Domain
* exposing framework collections as domain contracts

Repositories serve business language, not persistence convenience.

---

## Aggregate Rule

Aggregates protect invariants.

Rules:

* keep aggregate boundaries explicit
* avoid oversized aggregates
* avoid anemic models
* protect consistency inside aggregate boundaries
* external access must respect aggregate rules

Aggregates exist for consistency, not for folder structure.

---

## Value Object Rule

Use Value Objects when behavior and meaning matter.

Examples:

* EmailAddress
* DateRange
* Money
* OrderStatus

Avoid primitive obsession.

If a concept has rules, it probably deserves a Value Object.

---

## Domain Service Rule

Use Domain Services only when behavior does not belong naturally inside a single Entity or Aggregate.

Forbidden:

* procedural service classes replacing real domain models
* dumping business logic into generic service folders

If everything becomes a service, DDD is not being applied.

---

## Bounded Context Rule

Each bounded context must have:

* clear ownership
* explicit language
* defined boundaries
* protected responsibilities

Avoid shared ambiguity.

Examples for this project may include:

* Identity and Access
* Billing
* Reporting
* Notifications

Context boundaries reduce accidental complexity.

---

## Dependency Direction

Correct direction:

Interface → Application → Domain
Infrastructure → Domain + Application

Forbidden direction:

Domain → Infrastructure
Domain → Framework
Application → Controller

Dependency mistakes create long-term architectural debt.

---

## Forbidden

* fat controllers
* framework-driven entities
* direct ORM usage inside Domain
* generic service classes full of business logic
* infrastructure-first design
* hidden business rules in listeners or observers
* implicit domain behavior

These create architecture drift.

---

## Mandatory Questions Before Implementation

Before writing code, ask:

* which bounded context owns this behavior
* what invariant must be protected
* should this be an Entity or Value Object
* does this belong in Domain or Application
* is the framework leaking into the model

If the answer is unclear, implementation should pause.
