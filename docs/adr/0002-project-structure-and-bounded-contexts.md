# ADR-0002 — Project Structure and Bounded Contexts

## Status

Accepted

---

## Context

The project requires long-term maintainability, explicit domain ownership, and safe evolution across multiple business capabilities.

Using the default framework-first structure such as:

* Controller
* Entity
* Repository
* Service

creates long-term architectural problems:

* business logic spread across technical folders
* weak domain ownership
* poor bounded context separation
* framework-driven design
* high coupling between unrelated modules
* difficult onboarding and refactoring

The system must be organized around business capabilities, not framework concerns.

A bounded-context-first structure is required.

---

## Decision

The project will use a business-oriented structure based on bounded contexts and DDD principles.

Symfony remains the application framework, but the internal code organization will be domain-first.

The concrete bounded contexts depend on the product domain and must be defined intentionally.

The project structure will be:

```txt
src/
├── Shared/
├── <BoundedContextA>/
├── <BoundedContextB>/
└── Infrastructure/
```

Each bounded context owns its business language, use cases, and domain rules.

Framework folders are not the primary architecture.

---

## Bounded Contexts

### Shared

Responsible for:

* shared kernel concepts
* common abstractions
* base domain contracts
* cross-context technical primitives when justified

Rules:

* keep extremely small
* avoid dumping unrelated code
* avoid fake reuse

Shared exists to reduce duplication, not to hide design problems.

---

### Business Contexts

Each bounded context is responsible for one cohesive business capability.

Rules:

* own its own ubiquitous language
* protect its own invariants
* expose explicit integration boundaries
* avoid hidden cross-context dependencies
* evolve independently when possible

Concrete context names must come from the product domain, not from technical convenience.

---

## Internal Layer Structure

Each bounded context should internally follow:

```txt
Context/
├── Domain/
├── Application/
├── Infrastructure/
└── Interface/
```

Example:

```txt
<BoundedContextName>/
├── Domain/
├── Application/
├── Infrastructure/
└── Interface/
```

This preserves Hexagonal Architecture inside each context.

---

## Framework Rule

Symfony lives at project level:

* config/
* public/
* bin/
* vendor/
* console

But business code must remain inside bounded contexts.

Forbidden:

* architecture centered around framework folders
* global service folders for business logic
* framework entities defining domain truth

Symfony supports delivery.

It does not define architecture.

---

## Dependency Rule

Correct dependency direction:

Interface → Application → Domain
Infrastructure → Domain + Application

Forbidden:

Domain → Framework
Domain → Doctrine
Domain → Controllers

Dependency direction must remain visible and enforceable.

---

## Consequences

### Positive

* explicit domain ownership
* safer refactoring
* better onboarding
* lower accidental coupling
* better architectural reviews
* clearer product alignment

### Negative

* more upfront design discipline
* slower early development
* requires stronger architectural consistency

These trade-offs are accepted in favor of long-term sustainability.

---

## Forbidden

* src/Service as a generic business folder
* src/Entity as the system center
* global repositories without context ownership
* controllers containing domain logic
* cross-context hidden dependencies

These create architecture drift.

---

## Review Policy

This ADR must be reviewed when:

* a new bounded context is introduced
* context ownership becomes unclear
* product scope changes significantly
* a major architecture simplification or split is proposed

Context boundaries must evolve intentionally, never accidentally.
