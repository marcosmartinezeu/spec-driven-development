# Project Stack Declaration

## Objective

Declare the active technical stack for the derived project.

This document exists to remove ambiguity.

Each derived project should have one primary active PHP framework.

If the stack is unclear, implementation decisions become inconsistent.

---

## How To Use This Document

Replace the placeholder values with the actual stack decisions for the derived project.

Keep this document updated when the active stack changes.

If the active stack changes materially, create or update the relevant ADR.

---

## Active Stack

* language: `PHP`
* primary framework: `<Symfony | Laravel>`
* interface delivery: `<Twig | Blade | API only | other>`
* persistence adapter: `<Doctrine | Eloquent | custom>`
* validation boundary: `<Symfony Validator | Laravel Form Request | custom>`
* testing stack: `<PHPUnit | Pest | PHPUnit + Pest>`
* async processing: `<Messenger | Laravel Jobs/Queues | none | other>`
* UI styling system: `<project choice>`
* UI component approach: `<shared components | design system | minimal custom components>`

---

## Active Skills

List the skills that should be preferred for this project.

Example:

* `laravel-frameworks`
* `server-rendered-ui`
* `<project-specific conventions skill when present>`

Only list skills that actually apply to the project.

---

## Explicit Non-Goals

List technologies that are not part of the active stack unless a new ADR approves them.

Examples:

* the inactive PHP framework
* a second templating approach
* a second ORM approach
* a second queue system

This protects the project from silent stack drift.

---

## Rules

* only one primary PHP framework should be active in a derived project
* implementation must follow the active stack before using generic defaults
* introducing another primary framework requires explicit ADR review
* project-specific conventions must refine this declaration, not contradict it

---

## References

* `AGENTS.md`
* `docs/adr/`
* `docs/standards/definition-of-ready.md`
* `.codex/templates/skills/project-conventions/SKILL.md`
