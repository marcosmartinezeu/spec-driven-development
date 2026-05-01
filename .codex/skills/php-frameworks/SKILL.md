# Skill — php-frameworks

## Purpose

Apply Laravel and Symfony as delivery tools without allowing framework decisions to dominate architecture.

This skill ensures the framework supports the Domain instead of becoming the center of the system.

The objective is framework productivity without framework dependency.

---

## Use This Skill When

Use this skill for:

* integrating Domain with Laravel or Symfony
* designing controllers and HTTP entry points
* configuring dependency injection
* implementing commands and handlers
* using events responsibly
* persistence strategy decisions
* validation boundaries
* infrastructure adapters
* framework migration decisions

If the question is "how should the framework support this?", this skill should be used.

---

## Core Rule

Laravel and Symfony are delivery mechanisms.

They are not the architecture.

The Domain must remain valid even if the framework changes.

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

ORM is Infrastructure.

Rules:

* repository contracts belong to Domain
* implementations belong to Infrastructure
* persistence models must not define business truth
* avoid ORM-first domain modeling

Do not design aggregates from tables.

Design persistence around the Domain.

---

## Validation Rule

Validation has two layers.

### Interface Validation

Use framework validation for:

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

## Events Rule

Use events intentionally.

Good use cases:

* domain events
* integration boundaries
* async side effects
* decoupled operational reactions

Forbidden:

* hiding business flow inside listeners
* invisible domain behavior
* debugging through event chaos

If behavior becomes hard to trace, event usage is wrong.

---

## Commands and Handlers

Use commands for:

* explicit use case execution
* clear application boundaries
* orchestration clarity

Handlers should:

* coordinate flow
* call Domain behavior
* remain focused and small

Do not turn handlers into god classes.

---

## Service Container Rule

The container wires the system.

It must not become part of business logic.

Forbidden:

* resolving dependencies dynamically in Domain
* hidden runtime architecture decisions

Explicit architecture beats magical resolution.

---

## Framework Upgrade Rule

Before adopting framework features, ask:

* does this improve delivery or only novelty
* does this increase coupling
* would the Domain survive replacement

Framework upgrades must improve maintainability, not dependency.

---

## Review Questions

Before implementation, ask:

* is the Domain protected
* is framework logic leaking into business rules
* does the controller remain thin
* is persistence driving the model
* is validation in the correct layer
* is dependency injection explicit

If the framework is shaping the Domain, redesign first.

---

## Forbidden

* fat controllers
* ORM-driven domain design
* framework annotations inside Domain
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
* framework productivity without architectural dependency
* safe future migration paths

The framework should accelerate delivery, not own the system.
