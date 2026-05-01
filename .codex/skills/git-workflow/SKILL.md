# Skill — git-workflow

## Purpose

Apply trunk-based development safely and consistently to protect delivery speed, review quality, and production stability.

This skill ensures Git supports architecture and operational reliability instead of becoming a source of hidden risk.

The objective is safe continuous delivery, not commit quantity.

---

## Use This Skill When

Use this skill for:

* creating feature branches
* preparing pull requests
* reviewing branch scope
* deciding merge strategy
* rebasing safely
* handling hotfixes
* resolving conflicts
* validating rollback safety
* protecting `main`

If the question is "is this safe to merge?", this skill should be used.

---

## Core Rule

`main` must always remain stable.

Everything else exists to protect that rule.

The project uses:

* trunk-based development
* short-lived branches
* small pull requests
* frequent merges
* continuous review

Delayed integration creates delayed failure.

---

## Branch Rule

Always branch from `main`.

Allowed branches:

* `feature/*`
* `fix/*`
* `hotfix/*`

Examples:

* `feature/user-registration`
* `feature/report-export`
* `fix/email-delivery-status`
* `hotfix/session-timeout-failure`

Rules:

* keep branches short-lived
* keep scope intentionally small
* delete branches after merge

Long-lived branches are architectural risk.

---

## Commit Rule

Each commit must represent one clear intention.

Required:

* safe to revert
* understandable without external explanation
* small enough to review

Good examples:

* `Add user registration validation`
* `Prevent duplicate email registration`
* `Fix report history persistence`

Bad examples:

* `changes`
* `fix things`
* `last update`

Commit history is operational memory.

---

## Pull Request Rule

PRs must be:

* small
* focused
* reviewable
* linked to business intent
* linked to ADR when architecture changes

Required:

* problem explanation
* implementation reasoning
* testing summary
* operational impact if relevant

Forbidden:

* mixed unrelated work
* hidden refactors
* speculative large changes
* unclear scope

Large PRs create bad reviews.

---

## Merge Rule

Merge frequently.

Do not accumulate integration risk.

Before merge:

* tests pass
* review completed
* architecture validated
* documentation updated if needed
* rollback remains possible

Safe merge beats fast merge.

---

## Rebase Rule

Use rebase to preserve clean history when appropriate.

Rules:

* rebase before merge when necessary
* resolve conflicts carefully
* validate behavior after conflicts
* avoid unnecessary merge commits

Conflict resolution is a production decision.

---

## Hotfix Rule

Hotfixes are exceptions.

Rules:

* identify real root cause first
* keep scope minimal
* add regression protection immediately
* review fully after urgency passes

Urgency does not justify architectural damage.

---

## Rollback Rule

Every important change must be reversible.

Required:

* isolated change scope
* deployment validation
* operational verification

If rollback is unsafe, deployment is unsafe.

---

## Review Questions

Before pushing, ask:

* is branch scope small enough
* is the PR easy to review
* can this be reverted safely
* does this protect `main`
* is there hidden architecture impact
* should documentation be updated

If unclear, stop and reduce scope.

---

## Forbidden

* giant PRs
* direct uncontrolled production fixes
* undocumented hotfixes
* delayed integration
* mixing urgent fixes with large refactors
* force-pushing shared unstable work
* unclear commit history

Git discipline protects delivery confidence.

---

## Expected Output

This skill should produce:

* stable `main`
* safe frequent merges
* clear commit history
* reviewable pull requests
* low integration risk
* fast rollback paths
* predictable delivery flow

Good Git practices reduce operational chaos.
