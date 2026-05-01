# Skill — symfony-frameworks

## Purpose

Apply Symfony as a delivery tool without allowing framework decisions to dominate architecture.

This skill ensures Symfony supports the Domain instead of becoming the center of the system.

The objective is Symfony productivity without Symfony dependency.

---

## Use This Skill When

Use this skill for:

* integrating Domain with Symfony
* designing controllers and HTTP entry points
* configuring dependency injection and service wiring
* implementing console commands and handlers
* using Messenger or events responsibly
* defining validation boundaries
* designing Doctrine-backed adapters
* making Symfony-specific implementation decisions

If the question is "how should Symfony support this?", this skill should be used.

---

## Core Rule

Symfony is a delivery mechanism.

It is not the architecture.

The Domain must remain valid even if Symfony is replaced.

Framework convenience must never justify domain pollution.

---

## Controller Rule

Controllers must remain thin.

Controllers are responsible for:

* receiving requests
* validation at interface boundaries
* calling application use cases
* formatting responses

Controllers must not:

* contain business rules
* orchestrate complex workflows
* directly implement domain decisions

Controllers translate.

They do not decide.

---

## Dependency Injection Rule

Use explicit constructor injection.

Required:

* clear dependencies
* visible collaboration
* testable classes

Forbidden:

* service locators
* hidden container resolution inside Domain
* static framework access for business logic

Dependencies must be obvious.

---

## Persistence Rule

Doctrine is Infrastructure.

Rules:

* repository contracts belong to Domain
* implementations belong to Infrastructure
* Doctrine models must not define business truth
* avoid Doctrine-first domain modeling

Do not design aggregates from tables.

Design persistence around the Domain.

---

## Validation Rule

Validation has two layers.

### Interface Validation

Use Symfony validation for:

* request shape
* required fields
* input format
* transport concerns

### Domain Validation

Use Domain for:

* business rules
* invariants
* operational constraints

Framework validation is not business validation.

---

## Events and Messenger Rule

Use events and Messenger intentionally.

Good use cases:

* domain events
* integration boundaries
* async side effects
* decoupled technical reactions

Forbidden:

* hiding business flow inside listeners
* invisible domain behavior
* debugging through handler sprawl

If behavior becomes hard to trace, usage is wrong.

---

## Service Container Rule

The container wires the system.

It must not become part of business logic.

Forbidden:

* resolving dependencies dynamically in Domain
* hidden runtime architecture decisions

Explicit architecture beats magical resolution.

---

## Review Questions

Before implementation, ask:

* is the Domain protected
* is Symfony logic leaking into business rules
* does the controller remain thin
* is Doctrine driving the model
* is validation in the correct layer
* is dependency injection explicit

If Symfony is shaping the Domain, redesign first.

---

## Forbidden

* fat controllers
* Doctrine-driven domain design
* framework annotations or attributes inside Domain when they define business truth
* hidden business rules in listeners
* container access inside Domain
* generic service classes replacing real use cases
* persistence-first architecture

These create framework lock-in.

---

## Expected Output

This skill should produce:

* thin controllers
* explicit use cases
* protected Domain boundaries
* Infrastructure isolated from business truth
* Symfony productivity without architectural dependency
* safe future migration paths

Symfony should accelerate delivery, not own the system.
