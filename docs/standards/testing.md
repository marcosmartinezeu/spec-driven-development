# Standard — Testing Strategy

## Objective

Define the mandatory testing standards that ensure safe delivery, regression protection, and confidence in architectural evolution.

Tests are not a final step.

They are part of the implementation itself.

Reliable delivery requires reliable verification.

---

## Core Rule

Test behavior, not implementation details.

The objective is not coverage percentage.

The objective is confidence.

The project prioritizes:

* meaningful validation over cosmetic tests
* domain protection over framework testing
* regression prevention over false coverage
* maintainable tests over fragile assertions

A test suite that nobody trusts is technical debt.

---

## Testing Priorities

Priority order:

1. Domain behavior
2. Application use cases
3. Critical integrations
4. Interface validation
5. Framework-specific behavior only when necessary

Protect the business first.

---

## Domain Tests

Must validate:

* business rules
* invariants
* aggregate consistency
* Value Object behavior
* domain events
* failure scenarios

Rules:

* fast execution
* isolated from framework
* isolated from database
* explicit business language

Domain tests are the highest-value tests.

---

## Application Tests

Must validate:

* use case orchestration
* command and query handling
* transaction boundaries
* repository collaboration
* external dependency coordination

Rules:

* validate flow, not infrastructure internals
* focus on business outcomes

Application tests verify decisions between layers.

---

## Integration Tests

Must validate:

* persistence correctness
* repository implementations
* external API adapters
* messaging behavior
* infrastructure contracts

Rules:

* only where failure risk justifies cost
* avoid excessive slow test suites

Integration tests protect reality.

---

## Controller and Interface Tests

Must validate:

* request validation
* authorization behavior
* response contracts
* API expectations

Rules:

* controllers remain thin
* avoid placing business logic here

Do not replace Domain tests with HTTP tests.

---

## Regression Rule

Every important bug must leave a test behind.

Required:

* reproduce the failure
* add regression protection
* ensure future failure becomes visible

A bug fixed without regression protection is unfinished work.

---

## Test Naming

Rules:

* describe behavior clearly
* explain expected outcome
* use business language

Good:

* it_prevents_duplicate_user_registration
* it_marks_a_subscription_as_expired_after_its_end_date

Bad:

* test_registration
* should_work
* validation_test

Test names are documentation.

---

## Mocking Rule

Use mocks carefully.

Required:

* isolate external dependencies
* avoid mocking internal business truth

Forbidden:

* mocking the system so much that behavior becomes fictional
* testing mocks instead of behavior

Too much mocking creates false confidence.

---

## Forbidden

* tests created only for coverage metrics
* fragile implementation-coupled tests
* skipping tests for critical business flows
* testing framework internals instead of business behavior
* unmaintained broken test suites
* false green pipelines

Broken trust in tests breaks delivery speed.

---

## Mandatory Questions Before Merge

Before merging, ask:

* are business rules protected
* does this change create regression risk
* is the failure observable in tests
* are tests readable and maintainable
* are critical integrations verified
* would future refactors remain safe

If confidence is weak, tests are incomplete.

## Mutation Testing

Mutation testing may be introduced later using Infection when the Domain layer becomes more mature.

It must not be required during the initial project setup.

Use mutation testing to validate the strength of tests around:

- business invariants
- Value Objects
- Aggregates
- Domain Services
- critical application use cases

Mutation testing should not be used to chase scores blindly.

It exists to improve confidence in business-critical behavior.
