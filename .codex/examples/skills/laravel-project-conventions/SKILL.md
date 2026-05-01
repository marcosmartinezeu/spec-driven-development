# Skill — laravel-project-conventions

## Purpose

Capture a realistic example of project-specific conventions for a Laravel-derived project built from this repository.

This example is intentionally opinionated enough to be useful, but still small enough to adapt.

It should be copied and refined only when the derived project actually uses these conventions.

---

## Active Stack

* framework: `Laravel`
* templates: `Blade`
* persistence: `Eloquent in Infrastructure adapters`
* testing: `Pest for feature tests, PHPUnit where needed`
* UI approach: `server-rendered UI`

This example assumes `docs/project/active-stack.md` already declares Laravel as the active primary framework.

---

## Naming Conventions

* use case classes use explicit verbs such as `RegisterUser` or `ResetPassword`
* handlers use the `...Handler` suffix only when a separate handler is justified
* Eloquent models use the `Eloquent...Model` suffix when they need to stay visibly infrastructure-specific
* Blade components use names that reflect UI purpose, not implementation detail

---

## Framework Conventions

* controllers stay thin and delegate to Application use cases
* Form Requests validate transport concerns only
* service providers wire dependencies but do not hold business logic
* queues, jobs, and listeners must not hide core business flow
* route files stay organized by interface concern, not by generic convenience

---

## Persistence Conventions

* repository contracts belong to Domain
* Eloquent models stay in Infrastructure adapters
* aggregates are not represented directly by Eloquent shape
* transactional behavior is coordinated in Application or Infrastructure, never inside Domain entities
* query-specific read models are acceptable when they protect domain clarity

---

## Testing Conventions

* Pest is preferred for feature and HTTP-facing flows
* PHPUnit is acceptable for lower-level unit tests when clearer
* test names describe behavior, not method names
* factories exist to reduce setup noise, not to hide domain intent
* bugfixes add regression protection before closure

---

## UI Conventions

* Blade components are preferred for repeated form, layout, and feedback patterns
* shared partials must not become hidden logic containers
* server-rendered forms always show validation feedback clearly
* UI naming follows product language used in PRDs

---

## Operational Conventions

* migrations must be reversible when practical
* queue usage must remain traceable
* environment variables are documented when added
* scheduled jobs must be explicit about operational impact

---

## Forbidden

* direct Eloquent usage in Domain
* business rules inside Form Requests
* fat controllers coordinating multiple workflows
* facades inside Domain logic
* adding a second primary framework to the project

---

## Expected Output

This skill should produce:

* consistent Laravel usage across the project
* lower review friction
* explicit Infrastructure boundaries
* predictable testing style
* maintainable Blade-based delivery
