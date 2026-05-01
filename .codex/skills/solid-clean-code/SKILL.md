# Skill — solid-clean-code

## Purpose

Apply SOLID principles and Clean Code practices to keep the codebase readable, maintainable, testable, and safe to evolve.

This skill exists to reduce accidental complexity and prevent technical debt from becoming the default architecture.

The objective is sustainable delivery, not clever code.

---

## Use This Skill When

Use this skill for:

* reviewing class responsibilities
* reducing complexity
* improving naming
* refactoring legacy code
* validating dependency design
* improving readability
* reducing coupling
* improving testability
* preventing god classes

If the question is "is this code becoming harder to maintain?", this skill should be used.

---

## Core Rule

Code must be easy to understand by someone who did not write it.

Future maintainers are part of the team.

The project prioritizes:

* clarity over cleverness
* explicitness over magic
* maintainability over speed
* composition over inheritance
* readability over premature abstraction

Simple code scales better than smart code.

---

## Single Responsibility Rule

Each class should have one clear reason to change.

Ask:

* what responsibility does this class own
* would unrelated changes modify the same class

If the answer is yes, the class is too large.

Large classes create hidden risk.

---

## Open/Closed Rule

Code should be extendable without unsafe modification.

Prefer:

* composition
* explicit collaboration
* stable boundaries

Avoid:

* fragile inheritance chains
* switch-based architecture everywhere

Extension should not require architectural damage.

---

## Liskov Substitution Rule

Abstractions must behave honestly.

Do not create interfaces that lie about behavior.

If replacing an implementation breaks expectations, the abstraction is wrong.

Bad abstractions create invisible bugs.

---

## Interface Segregation Rule

Prefer small focused contracts.

Avoid:

* giant interfaces
* dependencies on unused behavior

Consumers should depend only on what they need.

Fat interfaces create false coupling.

---

## Dependency Inversion Rule

High-level business decisions must not depend on low-level technical details.

Required:

* explicit contracts
* infrastructure behind boundaries

Forbidden:

* business logic coupled to concrete technical implementations

Dependency direction defines architecture quality.

---

## Naming Rule

Names must explain intent.

Good names reduce comments.

Forbidden:

* generic words like Helper, Manager, Processor, Util
* unclear abbreviations
* framework terms replacing business language

Naming is not cosmetic.

It is design.

---

## Refactoring Rule

Refactoring is continuous work.

Required:

* improve clarity when touching code
* remove duplication intentionally
* reduce unnecessary complexity

Forbidden:

* large speculative refactors without business justification
* mixing dangerous refactors into urgent fixes

Refactor to simplify, not to impress.

---

## Complexity Rule

Every abstraction must justify its cost.

Ask:

* does this make change easier
* does this improve understanding
* is this solving a real problem

If not, remove it.

Accidental abstraction is technical debt.

---

## Review Questions

Before implementation, ask:

* is the class too large
* is naming clear
* is complexity justified
* is coupling too high
* is testing unnecessarily difficult
* would another developer understand this quickly

If the answer is no, refactor first.

---

## Forbidden

* god classes
* generic service folders
* inheritance without strong reason
* hidden side effects
* procedural code disguised as architecture
* unclear naming
* unnecessary abstractions
* duplicated business logic

These slow every future feature.

---

## Expected Output

This skill should produce:

* small cohesive classes
* explicit responsibilities
* clear naming
* low coupling
* high readability
* safe refactoring paths
* maintainable long-term architecture

The best code is the code that remains easy to change.
