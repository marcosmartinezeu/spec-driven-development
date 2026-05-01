# Workflow — Feature Development

## Objective

Define the mandatory process for developing new features in a predictable, reviewable, and architecture-safe way.

Features must be delivered incrementally and aligned with product requirements, architecture decisions, and domain boundaries.

Implementation without workflow discipline creates architecture drift.

---

## Default Rule

No feature starts from code.

Every feature starts from product understanding.

The correct order is:

PRD → ADR → Active Stack → Definition of Ready → Design → Implementation → Tests → Review → Merge → Definition of Done

Never the opposite.

---

## Readiness Gate

Before implementation starts, the work must satisfy:

* `docs/project/active-stack.md`
* `docs/standards/definition-of-ready.md`

If readiness is weak, implementation should pause.

---

## Step 1 — Validate Product Need

Before implementation, confirm:

* which user needs the feature
* what problem it solves
* expected business value
* acceptance criteria
* measurable success condition

If no clear user exists, the feature should not start.

Source of truth:

* `docs/prd/`
* `docs/prd/TEMPLATE.md` when a new PRD is needed

---

## Step 2 — Review Architecture Constraints

Before coding, verify:

* affected bounded context
* domain ownership
* existing ADR constraints
* required new ADRs if architecture changes
* infrastructure impact

Never implement architecture decisions silently.

Source of truth:

* `docs/adr/`
* `docs/adr/TEMPLATE.md` when a new ADR is needed

---

## Step 3 — Confirm Active Stack

Before implementation, verify:

* one primary framework is active for the project
* the selected framework is declared in `docs/project/active-stack.md`
* interface, persistence, and testing choices match that declaration
* new stack changes are raised explicitly instead of introduced silently

Implementation should follow the active stack before using generic defaults.

---

## Step 4 — Define Implementation Approach

Prepare:

* use case definition
* affected aggregates
* value objects
* repositories involved
* ports and adapters required
* application services required
* integration points
* testing strategy

The objective is clarity, not premature detail.

---

## Step 5 — Create Short-Lived Branch

Using trunk-based development:

* branch from `main`
* keep branch short-lived
* keep scope intentionally small

Examples:

* `feature/user-registration`
* `feature/report-export`
* `fix/email-delivery-status`

Long-lived branches are forbidden.

---

## Step 6 — Implement Incrementally

Rules:

* protect Domain first
* keep controllers thin
* framework stays outside Domain
* write explicit code
* prefer small commits
* avoid hidden complexity

Large feature branches indicate bad scope definition.

---

## Step 7 — Add or Update Tests

Required validation includes:

* domain behavior validation
* application flow validation
* integration tests where needed
* regression protection

Tests are part of delivery, not optional polish.

---

## Step 8 — Self Review

Before opening PR:

validate:

* architecture consistency
* naming clarity
* bounded context correctness
* unnecessary complexity
* test coverage
* documentation impact

Review before asking for review.

---

## Step 9 — Pull Request

Rules:

* small and reviewable
* clear business intent
* explicit technical reasoning
* linked PRD/ADR reference when relevant
* no unrelated changes

Bad PRs create bad architecture.

---

## Step 10 — Merge to Main

Rules:

* merge frequently
* keep `main` stable
* avoid delayed integration
* delete branch after merge

Main must always be production-safe.

---

## Mandatory Checklist

Before merge:

* PRD validated
* ADR reviewed
* active stack validated
* architecture respected
* tests passing
* PR reviewed
* branch small enough
* documentation updated if needed

If any item fails, merge should not happen.

---

## Forbidden

* coding before understanding the problem
* large speculative implementations
* hidden architecture decisions
* framework-driven domain design
* large unreviewable PRs
* delayed integration

Speed without control creates future slowdown.
