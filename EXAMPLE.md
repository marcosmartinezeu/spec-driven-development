# Example — Starting a Derived Project

## Scenario

Assume you are a developer joining this repository for the first time.

You want to use it as the base for a real project called `Acme Customer Portal`.

For this example:

* the product will be a customer portal
* the active framework will be `Laravel`
* the interface will be `Blade`
* the persistence approach will be `Eloquent in Infrastructure adapters`
* the first feature will be `user registration`

The same flow works for Symfony.

Only the active stack choices change.

---

## Goal

By the end of this example, the derived project should have:

* a declared active stack
* a clear first product increment
* an architecture baseline
* enough delivery structure to start implementation safely

---

## Step 1 — Create the Derived Project

Copy this repository into the new project folder and rename it.

Example:

```bash
cp -R spec-driven-development acme-customer-portal
```

At this point, do not start writing application code yet.

---

## Step 2 — Read the Minimum Required Documents

Do not try to read everything first.

Start with these files only:

1. `README.md`
2. `AGENTS.md`
3. `docs/adr/0001-architecture-style.md`
4. `docs/adr/0002-project-structure-and-bounded-contexts.md`
5. `docs/project/active-stack.md`
6. `docs/standards/definition-of-ready.md`
7. `docs/standards/definition-of-done.md`
8. `docs/workflows/derived-project-setup.md`
9. `docs/workflows/feature-development.md`

This is enough context to begin safely.

---

## Step 3 — Define the First Product Increment

Create the first PRD from `docs/prd/TEMPLATE.md`.

Example file:

* `docs/prd/0001-user-registration.md`

For this example, the PRD should define:

* user: unauthenticated visitor
* problem: the visitor cannot create an account yet
* included scope: registration with name, email, and password
* excluded scope: social login, password recovery, admin approval
* acceptance criteria: successful registration, duplicate email prevention, validation feedback

At this stage, keep scope intentionally small.

Registration only is a good first slice.

---

## Step 4 — Declare the Active Stack

Edit `docs/project/active-stack.md` and replace placeholders with real choices.

Example:

```md
* language: `PHP`
* primary framework: `Laravel`
* interface delivery: `Blade`
* persistence adapter: `Eloquent`
* validation boundary: `Laravel Form Request`
* testing stack: `PHPUnit + Pest`
* async processing: `Laravel Jobs/Queues`
* UI styling system: `project choice`
* UI component approach: `shared components`
```

In `Active Skills`, list only the skills that apply.

Example:

```md
* `laravel-frameworks`
* `server-rendered-ui`
```

In `Explicit Non-Goals`, make the inactive options visible.

Example:

```md
* `Symfony`
* `Twig`
* `Doctrine`
```

This removes ambiguity for future implementation.

---

## Step 5 — Record the Stack as an ADR

Framework and delivery choices are architecture decisions.

Create an ADR from `docs/adr/TEMPLATE.md`.

Example file:

* `docs/adr/0003-active-project-stack.md`

For this example, the ADR should explain:

* why Laravel is the active framework
* why Blade is the interface choice
* why Eloquent remains in Infrastructure adapters
* why Pest and PHPUnit are both acceptable
* what is explicitly not part of the project

If the stack changes later, this ADR must be updated or replaced.

---

## Step 6 — Decide Whether Project Conventions Are Needed

Do not create project conventions by default.

Create them only when the project already has real repeated patterns.

If needed:

1. Copy `.codex/templates/skills/project-conventions/SKILL.md`
2. Rename it to `.codex/skills/laravel-project-conventions/SKILL.md`
3. Use `.codex/examples/skills/laravel-project-conventions/SKILL.md` as reference

Good reasons to create it now:

* the team already knows it will use Form Requests in a consistent way
* the team already wants a fixed testing split between Pest and PHPUnit
* the team already has clear Blade component conventions

Bad reason:

* "maybe we will need it later"

---

## Step 7 — Align the Project-Facing Guides

Before coding, adapt the generic repository language where needed.

At minimum, review:

* `README.md`
* `AGENTS.md`

Typical updates for the derived project:

* project name
* real product description
* actual active stack
* project-specific conventions skill if it exists

The goal is that a new developer can read the project guides and see reality, not placeholders.

---

## Step 8 — Validate Definition of Ready

Before the first implementation branch, confirm all of this is true:

* the user problem is clear
* the first PRD exists
* the active stack is declared
* the stack ADR exists
* the affected bounded context is known
* acceptance criteria are visible
* testing expectations are visible
* the first feature is small enough to review safely

For this example, the likely first bounded context is:

* `IdentityAccess`

If any of these items is unclear, stop and fix the documentation first.

---

## Step 9 — Start the First Feature Branch

Only now start implementation.

Example branch:

* `feature/user-registration`

Implementation goal:

* one vertical slice only
* one clear user-facing workflow
* one bounded context

For this example, that means:

* registration form
* registration use case
* duplicate email protection
* successful account creation
* tests for domain, application, and user-facing flow where appropriate

Avoid bundling login, password recovery, profile management, and admin features into the same first branch.

---

## Step 10 — Use the Delivery Templates

When collaborating on the work:

* use `.github/ISSUE_TEMPLATE/feature.yml` for the feature definition
* use `.github/PULL_REQUEST_TEMPLATE.md` for the pull request

The PR should point to:

* the PRD
* the ADR
* the active stack
* the tests executed

This keeps implementation traceable.

---

## Minimal File Set Before First Real Implementation

For this example, you should expect at least these files to exist before serious coding starts:

* `docs/prd/0001-user-registration.md`
* `docs/adr/0003-active-project-stack.md`
* `docs/project/active-stack.md`
* optional: `.codex/skills/laravel-project-conventions/SKILL.md`

The project may still be small, but it is no longer ambiguous.

---

## Common Mistakes

Do not:

* start coding before declaring the active stack
* mix Symfony and Laravel conventions in the same derived project
* write a huge first feature branch
* create project conventions without real repeated patterns
* let Eloquent or framework classes define domain truth
* treat templates as final documents without adapting them

The biggest early risk is not lack of code.

It is hidden ambiguity.

---

## Fast Checklist

If you want the shortest safe version, do this in order:

1. Read `README.md`, `AGENTS.md`, and the two ADRs.
2. Create `docs/prd/0001-user-registration.md`.
3. Fill `docs/project/active-stack.md`.
4. Create `docs/adr/0003-active-project-stack.md`.
5. Decide whether `laravel-project-conventions` is really needed.
6. Confirm Definition of Ready.
7. Create `feature/user-registration`.
8. Implement the feature in one small slice.
9. Open the PR using the provided template.
10. Validate Definition of Done before merge.

---

## Symfony Variant

If the project uses Symfony instead, the flow is the same.

Replace only the active choices:

* `Laravel` -> `Symfony`
* `Blade` -> `Twig`
* `Eloquent` -> `Doctrine`
* `Laravel Jobs/Queues` -> `Messenger`
* `laravel-frameworks` -> `symfony-frameworks`
* `laravel-project-conventions` -> `symfony-project-conventions`

Everything else remains the same.

---

## Final Rule

This repository is not trying to slow you down.

It is trying to make sure your first implementation decisions are explicit enough that the project can grow without hidden contradictions.
