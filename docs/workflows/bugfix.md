# Workflow — Bugfix

## Objective

Define the mandatory process for fixing bugs without introducing hidden regressions, architectural damage, or unsafe hotfixes.

Bug fixing must prioritize understanding over speed.

Fast incorrect fixes create recurring incidents.

---

## Default Rule

Never fix symptoms first.

Always identify the real cause first.

The correct order is:

Reproduce → Understand → Isolate → Fix → Validate → Review → Merge

Never patch blindly.

---

## Step 1 — Reproduce the Problem

Before changing code, confirm:

* exact failing behavior
* affected users
* business impact
* reproducibility conditions
* environments affected
* severity level

A bug that cannot be reproduced is not yet understood.

---

## Step 2 — Identify Root Cause

Validate:

* where the failure originates
* if the issue is domain, application, infrastructure, or interface related
* if the problem is caused by data inconsistency
* if the issue reveals an architecture flaw
* if an ADR should be reviewed

Never assume the first visible failure is the real cause.

---

## Step 3 — Evaluate Scope of Impact

Confirm:

* affected bounded contexts
* related workflows
* possible hidden regressions
* required data corrections
* operational risk of deployment

Small visible bugs may indicate large architectural problems.

---

## Step 4 — Create Short-Lived Branch

Using trunk-based development:

Examples:

* `fix/shift-overlap-validation`
* `fix/incident-history-loss`
* `hotfix/vehicle-status-sync`

Scope must remain narrow and explicit.

---

## Step 5 — Implement the Real Fix

Rules:

* fix root cause, not only output
* preserve architecture boundaries
* avoid emergency complexity
* avoid workaround accumulation
* keep domain protected

Temporary patches require explicit justification.

---

## Step 6 — Add Regression Protection

Required:

* regression tests
* domain validation if business rules are involved
* integration tests if infrastructure caused the issue
* deployment validation when operational risk exists

Every important bug must leave the system safer than before.

---

## Step 7 — Self Review

Validate:

* real cause resolved
* no hidden side effects
* architecture preserved
* complexity not increased unnecessarily
* future recurrence reduced

Bugfixes must improve trust, not only silence errors.

---

## Step 8 — Pull Request

Rules:

* explain root cause clearly
* explain why the fix is correct
* describe regression protection added
* include operational impact if relevant
* avoid unrelated cleanup inside the same PR

The reviewer must understand the problem, not only the code.

---

## Step 9 — Merge and Validation

Rules:

* merge quickly after validation
* keep `main` stable
* verify production behavior when necessary
* delete branch after merge

Bugfix completion includes operational confidence.

---

## Mandatory Checklist

Before merge:

* issue reproduced
* root cause identified
* architecture impact reviewed
* regression tests added
* PR reviewed
* production risk evaluated
* documentation updated if needed

If root cause is unknown, merge should not happen.

---

## Forbidden

* blind patches
* fixing logs instead of fixing behavior
* silent architecture changes
* workaround accumulation
* mixing refactors with urgent bugfixes
* deploying without validation

Stability requires discipline, not urgency.
