# Standard — PHP Development

## Objective

Define the mandatory development standards for writing PHP code that is maintainable, explicit, testable, and aligned with DDD and Hexagonal Architecture.

PHP is an implementation tool, not the architecture itself.

The language must serve the Domain, not dominate it.

---

## Core Rule

Write code for future maintainers.

Readable code is more valuable than clever code.

The project prioritizes:

* explicitness over magic
* clarity over shortcuts
* maintainability over brevity
* composition over inheritance
* predictable behavior over hidden automation

If code requires explanation, it probably requires improvement.

---

## Naming Rules

Names must explain intent.

Required:

* business language first
* explicit class names
* explicit method names
* explicit variable names
* consistency with ubiquitous language

Forbidden:

* generic names like `Manager`, `Helper`, `Processor`, `Util`
* abbreviations without strong justification
* framework terminology replacing domain terminology

Examples:

Good:

* `AssignGuardToFirefighter`
* `VehicleMaintenanceStatus`
* `IncidentRegistrationService`

Bad:

* `DataManager`
* `ProcessHandler`
* `GeneralService`

Naming is architecture.

---

## Class Rules

Rules:

* one responsibility per class
* small cohesive classes
* explicit dependencies
* constructor injection only
* avoid static business logic
* avoid hidden side effects

Classes should be easy to test and difficult to misuse.

---

## Method Rules

Rules:

* methods must express one intention
* avoid long methods
* avoid boolean flag arguments
* return meaningful values
* avoid hidden mutation
* prefer early clarity over nested complexity

Small methods improve review quality.

---

## Dependency Rules

Required:

* dependency injection
* interface-driven collaboration where appropriate
* explicit boundaries between layers

Forbidden:

* service locators
* hidden framework resolution inside Domain
* global state
* static containers

Dependencies must be visible.

---

## Framework Rule

Laravel and Symfony are delivery tools.

Rules:

* framework code stays outside Domain
* framework models do not define business truth
* avoid framework-first architecture decisions

The framework may change.

The Domain should survive that change.

---

## Error Handling

Rules:

* domain failures must be explicit
* exceptions must communicate intent
* avoid silent failures
* avoid generic catch blocks
* never hide important business failures

Bad error handling creates invisible bugs.

---

## Collections and Arrays

Rules:

* avoid associative-array-driven business logic
* prefer Value Objects and explicit models
* avoid passing raw arrays across layers

Arrays are not domain models.

---

## Null Handling

Rules:

* avoid nullable behavior without meaning
* prefer explicit optional concepts
* validate boundaries early

Null should be intentional, not accidental.

---

## Comments Rule

Comments explain why, not what.

Forbidden:

* obvious comments
* outdated comments
* comments replacing bad naming

Good code reduces comment dependency.

---

## Forbidden

* god classes
* generic service folders
* static business logic
* hidden framework coupling
* primitive obsession
* copy-paste development
* unclear naming
* side-effect-heavy methods

These create long-term maintenance cost.

---

## Mandatory Questions Before Commit

Before committing, ask:

* does the name explain intent
* is the class too large
* is the Domain protected
* is framework coupling leaking
* can this be tested easily
* would another developer understand this quickly

If the answer is no, refactor first.
