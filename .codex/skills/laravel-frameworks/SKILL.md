# Skill — laravel-frameworks

## Purpose

Apply Laravel as a delivery tool without allowing framework decisions to dominate architecture.

This skill ensures Laravel supports the Domain instead of becoming the center of the system.

The objective is Laravel productivity without Laravel dependency.

---

## Use This Skill When

Use this skill for:

* integrating Domain with Laravel
* designing controllers and HTTP entry points
* configuring the service container and bindings
* implementing Artisan commands and handlers
* using jobs, events, and listeners responsibly
* defining validation boundaries
* designing Eloquent-backed adapters
* making Laravel-specific implementation decisions

If the question is "how should Laravel support this?", this skill should be used.

---

## Core Rule

Laravel is a delivery mechanism.

It is not the architecture.

The Domain must remain valid even if Laravel is replaced.

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

Use explicit constructor injection and clear bindings.

Required:

* visible dependencies
* testable classes
* bindings that make architectural intent clear

Forbidden:

* hidden container resolution inside Domain
* static framework access for business logic
* facade-driven domain behavior

Dependencies must be obvious.

---

## Persistence Rule

Eloquent is Infrastructure.

Rules:

* repository contracts belong to Domain
* implementations belong to Infrastructure
* Eloquent models must not define business truth
* avoid Active Record-first domain modeling

Do not design aggregates from tables.

Design persistence around the Domain.

---

## Validation Rule

Validation has two layers.

### Interface Validation

Use Laravel validation for:

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

## Jobs, Events, and Listeners Rule

Use jobs, events, and listeners intentionally.

Good use cases:

* domain events
* integration boundaries
* async side effects
* decoupled technical reactions

Forbidden:

* hiding business flow inside listeners
* invisible domain behavior
* debugging through event or job sprawl

If behavior becomes hard to trace, usage is wrong.

---

## Service Container Rule

The container wires the system.

It must not become part of business logic.

Forbidden:

* resolving dependencies dynamically in Domain
* hidden runtime architecture decisions
* using facades as shortcuts inside business logic

Explicit architecture beats magical resolution.

---

## Review Questions

Before implementation, ask:

* is the Domain protected
* is Laravel logic leaking into business rules
* does the controller remain thin
* is Eloquent driving the model
* is validation in the correct layer
* is dependency injection explicit

If Laravel is shaping the Domain, redesign first.

---

## Forbidden

* fat controllers
* Eloquent-driven domain design
* framework models inside Domain
* hidden business rules in listeners
* facade access inside Domain
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
* Laravel productivity without architectural dependency
* safe future migration paths

Laravel should accelerate delivery, not own the system.
