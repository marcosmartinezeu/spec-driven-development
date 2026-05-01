# Standard — Definition of Ready

## Objective

Define the minimum conditions required before implementation starts.

Work is not ready because it sounds useful.

Work is ready when the team can implement it without guessing product intent, architecture boundaries, or delivery scope.

---

## Core Rule

Ready means clear enough to start safely.

If important questions remain hidden, the work is not ready.

If the likely implementation path is still speculative, the work is not ready.

---

## Product Clarity

Before implementation starts, verify:

* the user or stakeholder is identified
* the problem being solved is explicit
* expected business value is understood
* scope is intentionally limited
* acceptance criteria are visible

Implementation without product clarity creates accidental scope.

---

## Architecture Clarity

Before implementation starts, verify:

* the affected bounded context is known
* relevant ADRs have been reviewed
* layer responsibilities are understood
* architecture risks are visible
* a new ADR is planned if the change affects architecture

Architecture ambiguity before coding becomes architecture drift after coding.

---

## Stack Clarity

Before implementation starts, verify:

* the active stack is declared in `docs/project/active-stack.md`
* one primary framework is active for the project
* implementation choices follow the declared framework, template, and persistence path
* possible stack changes are explicit, not accidental

Stack ambiguity creates inconsistent implementation.

---

## Scope Readiness

Before implementation starts, verify:

* the work is small enough to review safely
* the branch scope can remain focused
* the change can be delivered incrementally
* obvious out-of-scope items are documented

Large uncertain work is not ready work.

---

## Dependency Readiness

Before implementation starts, verify:

* external dependencies are known
* upstream decisions are available
* required environments, credentials, or contracts are identified
* blocking open questions are visible

Hidden dependencies turn implementation into discovery by accident.

---

## Testing Readiness

Before implementation starts, verify:

* the behavior that needs protection is known
* likely domain and application tests are identified
* critical functional or integration checks are understood
* regression risk is visible when changing existing behavior

If testing strategy is unclear, implementation risk is unclear.

---

## Documentation Readiness

Before implementation starts, verify:

* the relevant PRD exists or will be created
* the relevant ADR exists or will be created
* templates are used when new documents are needed
* important assumptions are written down

Undocumented intent creates rework.

---

## Mandatory Checklist

A work item is ready only when:

* product intent is clear
* acceptance criteria exist
* active stack is declared
* bounded context ownership is known
* ADR impact is reviewed
* scope is small enough
* dependencies are visible
* testing strategy is identified
* unresolved blockers are documented

---

## Forbidden

Do not start implementation when:

* the user problem is unclear
* acceptance criteria are missing
* architecture ownership is unclear
* scope is too large to review safely
* key dependencies are unknown
* important open questions remain hidden

Starting unclear work is not speed.

It is delayed failure.

---

## Success Condition

The Definition of Ready succeeds when implementation begins with clear intent, manageable scope, visible constraints, and a realistic validation path.

The goal is not process theater.

The goal is predictable execution.
