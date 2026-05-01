# Standard — Git Workflow

## Objective

Define the mandatory Git standards for safe delivery using trunk-based development.

Git is not only version control.

It is part of architecture protection, delivery safety, and team collaboration.

Bad Git practices create hidden operational risk.

---

## Core Rule

`main` must always remain stable.

Every branch, commit, and pull request must protect that rule.

The project uses:

* trunk-based development
* short-lived branches
* small pull requests
* frequent integration
* continuous review

Long-lived branches create delayed failure.

---

## Branch Strategy

Allowed branches:

* `feature/*`
* `fix/*`
* `hotfix/*`

Examples:

* `feature/guard-assignment`
* `feature/incident-registration`
* `fix/vehicle-maintenance-status`
* `hotfix/shift-availability-bug`

Rules:

* always branch from `main`
* keep branches short-lived
* keep scope intentionally small
* delete branch after merge

Forbidden:

* long-lived branches
* parallel architecture branches
* personal permanent branches
* hidden work outside review

Branch scope defines review quality.

---

## Commit Rules

Commits must:

* represent one clear intention
* be small enough to review
* be safe to revert
* explain why the change exists

Good examples:

* `Add shift overlap validation`
* `Prevent invalid guard assignment`
* `Fix vehicle maintenance status sync`

Bad examples:

* `changes`
* `fix stuff`
* `updates`
* `final version`

Commit history is operational documentation.

---

## Pull Request Rules

PRs must be:

* small
* reviewable
* focused on one business objective
* linked to product intent
* linked to ADR when architecture is affected

Required:

* clear problem statement
* explanation of implementation approach
* testing summary
* operational impact if relevant

Forbidden:

* mixed unrelated changes
* large speculative refactors
* hidden architecture decisions
* emergency merges without visibility

Bad PRs damage long-term velocity.

---

## Merge Rule

Rules:

* merge frequently
* avoid delayed integration
* preserve stable `main`
* prefer safe merge over speed

Before merge:

* tests must pass
* review must be complete
* architecture must be validated
* documentation must be updated if needed

Merging incomplete work is forbidden.

---

## Rebase Rule

Use rebase to keep history clean when appropriate.

Rules:

* rebase before merge when needed
* avoid unnecessary merge commits
* resolve conflicts carefully
* validate behavior after conflict resolution

Conflict resolution is code review under pressure.

---

## Hotfix Rule

Hotfixes are exceptions, not normal workflow.

Rules:

* identify real root cause first
* keep scope minimal
* add regression protection immediately
* review after urgency passes

Urgency does not justify architecture damage.

---

## Rollback Rule

Every important change must be reversible.

Required:

* safe deployment strategy
* small isolated changes
* operational validation after release

If rollback is impossible, delivery is unsafe.

---

## Forbidden

* direct commits to unstable production state
* force pushing shared branches without control
* giant PRs
* delayed integration
* undocumented hotfixes
* mixing refactor and urgent fixes
* unclear commit history

Git discipline protects production.

---

## Mandatory Questions Before Push

Before pushing, ask:

* is the branch scope small enough
* does the commit explain intent clearly
* can this be reviewed safely
* can this be reverted safely
* does this protect `main`
* is documentation affected

If the answer is unclear, stop and fix it first.
