# Skill — delivery-process

## Purpose

Ensure every feature, bugfix, and architectural decision follows a predictable delivery process aligned with PRDs, ADRs, and project workflows.

This skill prevents accidental development, undocumented decisions, and architecture drift.

The objective is controlled delivery, not reactive implementation.

---

## Use This Skill When

Use this skill for:

* starting new features
* evaluating bugfix scope
* deciding if an ADR is required
* validating PRD alignment
* preparing pull requests
* checking Definition of Done
* release preparation
* preventing undocumented architecture decisions

If the question is "should we implement this yet?", this skill should be used.

---

## Core Rule

No work starts from code.

Work starts from understanding.

The mandatory order is:

PRD → ADR → Design → Implementation → Tests → Review → Merge

Never the opposite.

Skipping steps creates hidden future cost.

---

## PRD Rule

Before implementation, validate:

* who needs this feature
* what problem it solves
* expected business value
* acceptance criteria
* measurable success condition

If there is no clear user, implementation should not start.

PRD defines why the work exists.

---

## ADR Rule

Before architecture decisions, validate:

* affected bounded context
* dependency direction
* technical constraints
* operational impact
* long-term maintainability

If the decision changes architecture, it requires explicit ADR review.

Architecture must never change silently.

---

## Scope Rule

Keep scope intentionally small.

Required:

* small feature increments
* small PRs
* reversible deployments
* focused branch ownership

Forbidden:

* large uncertain deliveries
* speculative architecture work
* unrelated mixed implementations

Small safe delivery beats large risky delivery.

---

## Definition of Done Rule

Work is done only when:

* product intent is satisfied
* architecture is respected
* tests protect behavior
* PR is reviewable
* documentation is updated if needed
* deployment risk is acceptable

Code written is not completion.

Operational confidence is completion.

---

## Bugfix Rule

Bugfixes require:

* reproduction first
* root cause identification
* regression protection
* architecture validation

Never patch symptoms only.

Fast wrong fixes create repeated failures.

---

## Pull Request Rule

PRs must explain:

* problem being solved
* why this solution is correct
* architecture impact
* testing performed
* operational impact if relevant

Reviewers must understand decisions, not only code.

---

## Release Rule

Before release:

validate:

* `main` is stable
* critical workflows are safe
* rollback is possible
* operational risks are known
* important documentation is current

Shipping uncertainty is not delivery.

---

## Review Questions

Before implementation, ask:

* is the user problem clear
* is the PRD complete enough
* does architecture require ADR review
* is scope small enough
* are tests planned
* is rollback safe

If unclear, stop before coding.

---

## Forbidden

* coding before understanding
* architecture changes without ADR
* large speculative implementations
* undocumented hotfixes
* false Definition of Done
* hidden delivery risks
* shipping because of urgency alone

Delivery discipline protects long-term speed.

---

## Expected Output

This skill should produce:

* predictable delivery flow
* traceable decisions
* safe architecture evolution
* small reviewable changes
* reliable releases
* fewer regressions
* higher delivery confidence

The best process is the one that makes good decisions repeatable.
