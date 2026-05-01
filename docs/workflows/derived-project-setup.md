# Workflow — Derived Project Setup

## Objective

Define the mandatory process for turning this repository into a real derived project without losing architectural clarity or stack consistency.

Derived project setup is not copying files only.

It is the moment where project intent, active stack, and delivery rules become explicit.

---

## Default Rule

Do not start implementation in a derived project until the project baseline is declared.

The correct order is:

Product Intent → Architecture Baseline → Active Stack → Project Conventions → Delivery Setup

Never the opposite.

---

## Step 1 — Confirm Product Direction

Before customizing the project, confirm:

* what kind of product is being built
* who the primary users are
* which business capability is expected first
* which parts of the base repository are relevant

Source of truth:

* `docs/prd/0000-product-development-principles.md`
* `docs/prd/TEMPLATE.md`

---

## Step 2 — Review Architecture Baseline

Before selecting tools, review:

* architecture style
* bounded context rules
* Domain protection rules
* delivery constraints already defined by ADRs

Source of truth:

* `docs/adr/0001-architecture-style.md`
* `docs/adr/0002-project-structure-and-bounded-contexts.md`

---

## Step 3 — Declare Active Stack

Before implementation, fill:

* `docs/project/active-stack.md`

Required:

* one primary PHP framework
* one main interface delivery approach
* one persistence path
* one testing direction

If the project does not know its active stack yet, it is not ready for implementation.

---

## Step 4 — Select Base Skills

Choose the skills that match the declared stack.

Examples:

* Laravel project: `laravel-frameworks` + `server-rendered-ui`
* Symfony project: `symfony-frameworks` + `server-rendered-ui`

The selected skills must follow `docs/project/active-stack.md`.

---

## Step 5 — Add Project Conventions Only When Real Patterns Exist

If the project already has repeated implementation decisions, create a project conventions skill.

Start from:

* `.codex/templates/skills/project-conventions/SKILL.md`

Reference examples:

* `.codex/examples/skills/laravel-project-conventions/SKILL.md`
* `.codex/examples/skills/symfony-project-conventions/SKILL.md`

Do not create project conventions to speculate.

Create them to reduce repeated review friction.

---

## Step 6 — Align Project Guides

Before coding, adapt the project-facing guides so they describe reality.

Review and update when necessary:

* `README.md`
* `AGENTS.md`
* issue templates
* pull request template

Derived projects should not keep generic text when the real stack is already known.

---

## Step 7 — Confirm Delivery Readiness

Before first implementation, validate:

* `docs/standards/definition-of-ready.md`
* `docs/standards/definition-of-done.md`
* `docs/workflows/feature-development.md`
* `docs/workflows/bugfix.md`
* `docs/workflows/code-review.md`

The project must know how work starts, how it is reviewed, and when it is complete.

---

## Step 8 — Add Minimal Automation

Before team use begins, ensure the derived project has at least:

* pull request template
* issue templates
* minimal CI validation for documentation or structural rules

Good process guidance without automation erodes quickly.

---

## Mandatory Checklist

A derived project setup is complete only when:

* active stack is declared
* one primary framework is active
* architecture baseline is reviewed
* delivery workflow is understood
* project conventions are added only if justified
* collaboration templates exist
* minimal CI validation exists

---

## Forbidden

Do not start a derived project by:

* mixing Symfony and Laravel as active primary frameworks
* copying generic templates without adapting them
* creating project conventions without real repeated patterns
* writing implementation code before stack and workflow clarity exist

Derived project setup must reduce ambiguity, not move it into code.
