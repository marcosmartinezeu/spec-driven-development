# AGENTS.md

## Project Development System

This repository follows an agent-driven development approach using structured documentation, reusable skills, and architecture rules.

The objective is to maintain consistency across implementation, architecture, and delivery using DDD, Hexagonal Architecture, Clean Code, and SOLID principles.

---

## Core Principles

### Architecture

* Domain-Driven Design (DDD)
* Hexagonal Architecture (Ports and Adapters)
* Framework-independent Domain Layer
* Explicit bounded contexts
* Ubiquitous language across code and documentation

### Code Quality

* SOLID principles
* Clean Code
* Small and cohesive classes
* Explicit naming
* Composition over inheritance
* High testability
* Low coupling and high cohesion

### Delivery

* Small and reviewable pull requests
* Architecture decisions documented through ADRs
* Product decisions documented through PRDs
* Incremental delivery
* Refactoring as a continuous practice

### Git

* Descriptive branch names
* Small commits with clear intent
* Safe rebases and conflict resolution
* PR-first development workflow

---

## Documentation Sources of Truth

Before implementing any feature, agents must consult:

1. `docs/prd/` → Product requirements and business intent
2. `docs/adr/` → Architecture decisions and technical constraints
3. `docs/standards/` → Development standards and coding conventions
4. `docs/workflows/` → Delivery process definitions

Implementation must align with these documents.

---

## Main Agent

### php-ddd-lead-developer

Responsible for:

* Preserving architectural consistency
* Applying DDD and Hexagonal Architecture correctly
* Keeping domain isolated from framework concerns
* Selecting the right skill for each task
* Reviewing technical decisions
* Prioritizing simplicity and maintainability

This agent orchestrates specialized skills instead of concentrating all knowledge in a single prompt.

---

## Specialized Skills

### ddd-hexagonal

Used for:

* Aggregates
* Entities
* Value Objects
* Repositories
* Domain Services
* Application Services
* Ports and Adapters
* Invariants
* Bounded Contexts

### php-frameworks

Used for:

* Symfony
* Laravel
* Dependency Injection
* Commands and Handlers
* Events
* Validation
* Persistence strategies
* Framework integration without domain pollution

### solid-clean-code

Used for:

* SOLID
* Refactoring
* Naming
* Readability
* Complexity reduction
* Maintainability improvements

### git-workflow

Used for:

* Branch strategy
* Pull request preparation
* Rebases
* Safe merges
* Conflict resolution
* Rollback strategy

### delivery-process

Used for:

* ADR creation
* PRD creation
* Feature workflow
* Bugfix workflow
* Release workflow
* Definition of Done

---

## Mandatory Rules

### Never

* Put business rules inside controllers
* Couple domain logic to Laravel or Symfony directly
* Skip ADRs for important architectural decisions
* Introduce infrastructure concerns inside Domain
* Create large unreviewable pull requests
* Add complexity without explicit justification

### Always

* Protect the Domain first
* Prefer explicitness over magic
* Write code for future maintainers
* Validate architecture before implementation
* Keep documentation updated when decisions change

---

## Default Development Flow

1. Read PRD
2. Review existing ADRs
3. Identify affected bounded context
4. Propose implementation approach
5. Validate architecture constraints
6. Implement incrementally
7. Add or update tests
8. Prepare small PR
9. Update ADR/PRD if required

This order must be preserved unless there is strong justification to change it.

## Agent Orchestration

The system uses multiple specialized agents.

The main decision agent is:

- php-ddd-lead-developer

This agent is responsible for:

- interpreting product requirements
- validating architecture decisions
- coordinating implementation
- deciding when to delegate work

### Delegation Rule

The main agent must delegate UI and UX-related tasks to:

- frontend-ux-developer

Delegation must happen when:

- a user interface is required
- Twig templates are needed
- forms and layouts must be created
- usability and interaction design are involved
- Flowbite or Tailwind components are used

The frontend agent:

- must not implement domain logic
- must not make architecture decisions
- must focus only on UI and UX

The main agent remains responsible for:

- overall solution consistency
- architecture correctness
- integration between backend and frontend
