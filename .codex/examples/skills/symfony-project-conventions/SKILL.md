# Skill — symfony-project-conventions

## Purpose

Capture a realistic example of project-specific conventions for a Symfony-derived project built from this repository.

This example is intentionally opinionated enough to be useful, but still small enough to adapt.

It should be copied and refined only when the derived project actually uses these conventions.

---

## Active Stack

* framework: `Symfony`
* templates: `Twig`
* persistence: `Doctrine in Infrastructure adapters`
* testing: `PHPUnit`
* UI approach: `server-rendered UI`

This example assumes `docs/project/active-stack.md` already declares Symfony as the active primary framework.

---

## Naming Conventions

* use case classes use explicit verbs such as `RegisterUser` or `ResetPassword`
* command and query handlers are named after the use case they coordinate
* Doctrine models remain visibly infrastructure-specific when separated from domain objects
* Twig component and partial names describe UI purpose clearly

---

## Framework Conventions

* controllers stay thin and delegate to Application use cases
* request validation stays at the interface boundary
* Messenger usage must not hide core domain behavior
* service configuration stays explicit enough to preserve architecture readability
* console commands trigger use cases instead of embedding workflows directly

---

## Persistence Conventions

* repository contracts belong to Domain
* Doctrine mappings stay outside Domain truth
* aggregates are not designed from Doctrine entity shape
* transactional boundaries are coordinated explicitly
* query-side read models are acceptable when they simplify delivery without polluting Domain

---

## Testing Conventions

* PHPUnit is the default testing layer
* test names describe behavior clearly
* infrastructure integration tests are added when Doctrine or Messenger behavior is relevant
* bugfixes add regression protection before closure
* UI-facing flows receive functional tests when they represent important user journeys

---

## UI Conventions

* Twig partials and components are preferred for repeated layout and form patterns
* templates do not contain business logic
* user feedback states remain explicit and visible
* interface naming follows the language used in PRDs

---

## Operational Conventions

* Doctrine migrations must be reviewed for reversibility and deployment safety
* Messenger usage must be explicit about async side effects
* environment additions are documented
* cache and queue behavior must not create hidden coupling

---

## Forbidden

* direct Doctrine usage in Domain
* business rules inside controllers or validators
* hidden workflow orchestration in Messenger handlers
* framework attributes driving domain truth
* adding a second primary framework to the project

---

## Expected Output

This skill should produce:

* consistent Symfony usage across the project
* lower review friction
* explicit Doctrine boundaries
* predictable testing style
* maintainable Twig-based delivery
