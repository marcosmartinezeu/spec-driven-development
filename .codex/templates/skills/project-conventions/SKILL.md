# Skill Template — <project-conventions-name>

## Purpose

Capture project-specific conventions that refine the generic skills used by this repository.

This template should be copied into a derived project and renamed to something explicit.

Examples:

* `laravel-project-conventions`
* `symfony-project-conventions`

This skill narrows defaults.

It must not replace architecture rules or contradict ADRs.

---

## Use This Skill When

Use this skill when:

* the active stack is already declared
* the project has repeated implementation conventions
* the team wants fewer default decisions left implicit
* framework-level rules are not specific enough for daily work

If the project has no real repeated conventions yet, do not create this skill.

---

## Required Inputs

Before using or writing this skill, review:

* `docs/project/active-stack.md`
* relevant ADRs
* current testing and deployment constraints
* existing code patterns in the derived project

Project conventions must follow real project decisions.

---

## Active Stack

Document the actual stack this skill assumes.

* framework: `<Laravel | Symfony>`
* templates: `<Blade | Twig | API only>`
* persistence: `<Eloquent | Doctrine | custom>`
* testing: `<Pest | PHPUnit | both>`
* UI approach: `<server-rendered UI | API only | other>`

If this section conflicts with `docs/project/active-stack.md`, fix the mismatch first.

---

## Convention Areas

### Naming Conventions

Document naming rules that are specific to the project.

Examples:

* use case naming
* handler naming
* repository naming
* DTO naming

### Framework Conventions

Document the preferred framework patterns.

Examples:

* Form Requests or custom request validation
* controllers vs single-action controllers
* service provider organization
* console command structure

### Persistence Conventions

Document how infrastructure persistence should be implemented.

Examples:

* Eloquent models only in adapters
* Doctrine mapping strategy
* transaction boundaries
* query organization

### Testing Conventions

Document the preferred testing style.

Examples:

* Pest for feature tests
* PHPUnit for unit tests
* test naming rules
* factories and fixtures

### UI Conventions

Document project-specific UI rules when relevant.

Examples:

* Blade component structure
* Twig partial conventions
* design system usage
* form composition patterns

### Operational Conventions

Document project-specific delivery constraints.

Examples:

* migration safety rules
* queue usage rules
* environment configuration rules
* local development assumptions

---

## Forbidden

List project-specific forbidden practices.

Examples:

* direct Eloquent usage in Domain
* controllers with orchestration logic
* duplicate validation layers
* introducing another primary framework

This section should be concrete.

---

## Expected Output

This skill should produce:

* consistent project-level decisions
* fewer repeated review comments
* faster onboarding
* less ambiguity in framework usage
* better alignment between architecture and implementation

The best project conventions reduce decision noise without creating process weight.
