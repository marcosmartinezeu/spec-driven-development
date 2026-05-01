# Workflow — Code Review

## Objective

Define the mandatory process for reviewing code in a way that protects architecture, improves maintainability, and keeps delivery safe.

Code review is not only about detecting bugs.

It exists to preserve product intent, architecture consistency, domain integrity, and long-term code quality.

---

## Default Rule

Every review must evaluate both:

* correctness of the implementation
* quality of the decision

A technically working change may still be rejected if it damages architecture, maintainability, or product clarity.

---

## Review Inputs

Before reviewing, check the relevant sources of truth:

* `docs/prd/` for product intent
* `docs/adr/` for architecture decisions
* `docs/project/` for active stack constraints
* `docs/standards/` for development standards
* `docs/workflows/` for delivery process

Do not review code in isolation when product or architecture context is required.

---

## Step 1 — Understand the Change

Confirm:

* what problem is being solved
* which user benefits
* which workflow is affected
* whether the scope matches the PR description
* whether unrelated changes are included

If the purpose is unclear, request clarification before reviewing implementation details.

---

## Step 2 — Validate Architecture

Check:

* the active stack is respected
* Domain remains framework-independent
* controllers are thin
* Application layer orchestrates use cases
* Infrastructure implements technical details
* dependencies point in the correct direction
* bounded context ownership is respected

Architecture violations must be treated as blocking issues.

---

## Step 3 — Validate Domain Model

Check:

* business rules are explicit
* invariants are protected
* naming follows ubiquitous language
* aggregates are not overloaded
* Value Objects are used where appropriate
* domain behavior is not replaced by procedural scripts

Domain clarity has priority over implementation convenience.

---

## Step 4 — Validate Code Quality

Check:

* classes and methods are cohesive
* names are clear and specific
* complexity is justified
* duplication is intentional or removed
* SOLID principles are respected
* code is readable by future maintainers

Clean code is required for sustainable delivery.

---

## Step 5 — Validate Tests

Check:

* important behavior is covered
* domain rules have tests
* regressions are protected
* tests are meaningful, not cosmetic
* test names explain behavior
* fragile tests are avoided

A feature without adequate tests is not complete.

---

## Step 6 — Validate Git Hygiene

Check:

* PR is small and reviewable
* branch scope is focused
* commits are clear enough
* no unrelated refactors are mixed in
* no temporary debugging artifacts remain

Large PRs should be split when possible.

---

## Step 7 — Provide Review Feedback

Feedback must be:

* specific
* actionable
* respectful
* tied to product, architecture, or maintainability
* clear about severity

Prefer explanations over commands.

Example:

Instead of:

`Move this.`

Use:

`This belongs in the Application layer because it orchestrates a use case and currently couples the controller to business flow.`

---

## Review Severity Levels

### Blocking

Must be fixed before merge.

Examples:

* architecture violation
* broken business rule
* missing critical test
* unsafe data handling
* unclear product behavior

---

### Important

Should be fixed before merge unless explicitly deferred.

Examples:

* unclear naming
* avoidable complexity
* weak test coverage
* minor domain modeling concern

---

### Suggestion

Optional improvement.

Examples:

* readability refinement
* minor refactor
* alternative implementation idea

---

## Approval Criteria

A PR can be approved only when:

* product intent is clear
* active stack is respected
* architecture is respected
* domain remains protected
* tests are adequate
* scope is focused
* code is maintainable
* no blocking issues remain

Approval means the reviewer accepts responsibility for the change entering `main`.

---

## Forbidden

* approving without understanding the change
* focusing only on syntax or formatting
* ignoring architecture drift
* accepting large unclear PRs
* requesting subjective changes without justification
* mixing unrelated discussions into review

Code review protects the future of the project.
