# Standard — Definition of Done

## Objective

Define the minimum conditions required for any work item to be considered complete.

A task is not done when code is written.

A task is done when it is understandable, tested, reviewable, integrated safely, and aligned with product and architecture expectations.

---

## Core Rule

Done means safe to review and safe to merge.

If a change cannot be reviewed confidently, it is not done.

If a change cannot be merged safely, it is not done.

---

## Product Alignment

Before considering work complete, verify:

* the user need is clear
* the implemented behavior matches the related PRD or task description
* scope has not expanded silently
* acceptance criteria are satisfied
* unresolved product questions are documented

Implementation without product alignment is incomplete.

---

## Architecture Alignment

Before considering work complete, verify:

* existing ADRs are respected
* architecture boundaries are preserved
* Domain remains protected from framework and infrastructure concerns
* no architecture decision was introduced silently
* new architecture decisions are documented with an ADR when needed

Architecture drift means the work is not done.

---

## Code Quality

Before considering work complete, verify:

* code is readable
* names explain intent
* classes and methods are cohesive
* complexity is justified
* duplication is intentional or removed
* no temporary debug code remains
* no unrelated refactors are included

Code must be maintainable by future developers.

---

## Testing

Before considering work complete, verify:

* relevant tests are added or updated
* domain rules are protected by unit tests when applicable
* application flows are tested when applicable
* functional tests are added for user-facing flows when needed
* regression tests are added for bugfixes
* tests are meaningful, not cosmetic
* the test suite passes

Default command:

```bash
php bin/phpunit
```

A change without adequate verification is not done.

---

## UI and UX

For user-facing work, verify:

* the interface is usable
* the layout is consistent with the product UI patterns
* the existing component library or design system is used when suitable
* forms have clear labels and error states
* navigation is predictable
* responsive behavior is acceptable
* accessibility basics are respected

A working screen that is confusing is not done.

---

## Git and Pull Request Readiness

Before considering work complete, verify:

* branch is short-lived and focused
* commits are small and clear
* PR scope is reviewable
* PR description explains the change
* PR includes tests executed
* PR documents known limitations
* PR suggests next steps when relevant

The PR is part of the delivery, not an afterthought.

---

## Documentation

Before considering work complete, verify:

* PRDs are updated if product behavior changed
* ADRs are updated or created if architecture changed
* standards are updated if development rules changed
* README is updated if setup or usage changed

Documentation must remain consistent with reality.

---

## Operational Safety

Before considering work complete, verify:

* configuration changes are documented
* environment variables are clear
* migrations are safe and reversible when possible
* rollback risk is understood
* no secrets are committed
* local setup remains functional

Operational uncertainty means the work is not done.

---

## Mandatory Checklist

A work item is done only when:

* product intent is satisfied
* architecture is respected
* code quality is acceptable
* tests pass
* UI/UX is acceptable when applicable
* documentation is updated when needed
* commits are clear
* PR is reviewable
* no known blocking issues remain

---

## Forbidden

Do not mark work as done when:

* tests are failing
* architecture is unclear
* product behavior is ambiguous
* PR is too large to review confidently
* debug code remains
* documentation is stale
* secrets are committed
* known blockers are hidden

Done must mean trustworthy.

---

## Success Condition

The Definition of Done succeeds when every completed task can be reviewed, merged, deployed, and understood with confidence.

The goal is not bureaucracy.

The goal is repeatable delivery quality.
