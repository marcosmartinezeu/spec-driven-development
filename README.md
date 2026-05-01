# Spec-Driven Development Base

Opinionated foundation for building software through explicit product requirements, architecture decisions, development standards, and reusable agent skills.

This repository is intentionally lightweight.

It is not an application skeleton.

It is a structured base for spec-driven delivery.

## Purpose

The goal is to help teams start from understanding before implementation.

The repository is designed to make these questions explicit:

* why the work exists
* which user benefits
* what architecture constraints apply
* how the work should be delivered safely
* what standards define acceptable quality

## What This Repository Contains

* `docs/prd/` for product requirements and templates
* `docs/adr/` for architecture decisions and templates
* `docs/standards/` for development standards, including Definition of Ready and Definition of Done
* `docs/workflows/` for feature, bugfix, and review workflows
* `.codex/skills/` for reusable skills
* `.opencode/agent/` for agent roles and responsibilities
* `AGENTS.md` as the project orchestration guide

## Current Focus

The delivery system is generic, but the included implementation skills are currently optimized for PHP projects using:

* Symfony
* Laravel
* server-rendered UI with Twig or Blade

The process documents remain useful even if the stack evolves.

## Core Principles

* DDD and Hexagonal Architecture
* explicit bounded contexts
* product clarity before code
* architecture decisions documented through ADRs
* incremental and reviewable delivery
* high testability and maintainability

## Recommended Workflow

1. Start from `docs/prd/TEMPLATE.md` to define the feature intent.
2. Review existing ADRs and create a new one from `docs/adr/TEMPLATE.md` when architecture changes.
3. Validate `docs/standards/definition-of-ready.md` before implementation.
4. Implement incrementally following the standards and workflows.
5. Validate `docs/standards/definition-of-done.md` before considering the work complete.

## Suggested Starting Points

* `AGENTS.md`
* `docs/prd/0000-product-development-principles.md`
* `docs/adr/0001-architecture-style.md`
* `docs/adr/0002-project-structure-and-bounded-contexts.md`
* `docs/standards/definition-of-ready.md`
* `docs/standards/definition-of-done.md`
* `docs/workflows/feature-development.md`

## Customization Guidance

Use this repository as a base and adapt it intentionally.

Examples:

* replace PHP-specific skills if your stack changes
* add project-specific UI or framework skills only when they reflect real repeated conventions
* keep templates generic and project examples explicit

Avoid mixing generic process guidance with domain-specific examples unless the repository is intended for a single product.
