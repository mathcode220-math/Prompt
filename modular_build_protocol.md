---

name: Adaptive Modular Build
description: Build and evolve software using the simplest architecture that safely satisfies the current goal.
version: 2.0.0
tags:

* architecture
* modularity
* software-engineering
* maintainability
* ai-agent

---

# Adaptive Modular Build

## Purpose

Build software with **minimal sufficient complexity**.

Avoid both:

* monolithic designs that mix unrelated responsibilities
* over-engineered designs with unnecessary layers, files, or abstractions

Target:

```text
Correctness
+ Clear responsibilities
+ Testability
+ Controlled dependencies
+ Useful observability
+ Justified extensibility
- Unnecessary complexity
```

## 1. Core Rule

> Do not create a file, layer, interface, abstraction, dispatcher, adapter, or service unless it solves a real problem.

Valid reasons include:

* isolating an independently changing responsibility
* enabling independent testing
* separating an external dependency
* supporting multiple implementations
* protecting a stable API or invariant
* reducing coupling or cognitive complexity
* improving observability

If none applies, keep the simpler design.

## 2. Choose Architecture Adaptively

Never assume a fixed number of layers or files.

Choose the smallest structure appropriate to the task:

```text
Simple feature
-> few files, direct implementation

Growing feature
-> separate responsibilities where useful

Multiple implementations
-> interface + routing/backend boundary

Complex system
-> explicit API / validation / routing / core / backend / observability
```

Architecture must grow because **system complexity requires it**, not because the protocol requires it.

## 3. Responsibility Boundaries

Each responsibility should have a clear owner.

Typical responsibilities:

```text
API
Validation
Core logic
Routing
Backend / infrastructure
Persistence
Observability
```

Prefer:

```text
High cohesion
Low coupling
```

Do not combine unrelated responsibilities merely to reduce file count.

Do not split closely related code merely to increase modularity.

## 4. Public API

Keep public interfaces:

* small
* stable
* explicit
* independent of implementation details

The API should describe **what** the system provides, not **how** it is implemented.

Do not expose backend-specific details unless required by the contract.

## 5. Dependencies and Backends

Dependencies should flow toward stable contracts.

Prefer:

```text
Application
    |
Core / Domain
    |
Interfaces
    |
Infrastructure / Backends
```

When multiple implementations exist, isolate them behind a common contract.

Examples:

```text
CPU
GPU
Simulation
Hardware
Remote
Mock
```

Do not spread backend-specific decisions throughout business logic.

Create a dispatcher only when there is a meaningful routing decision.

## 6. Validation and Safety

Validate inputs and important preconditions before unsafe side effects.

Validation should protect:

* invalid inputs
* impossible states
* explicit limits
* required invariants

Validation does not require a separate module. For simple cases, local validation is preferable.

## 7. Observability

Add observability where it helps diagnose:

* failures
* important state transitions
* backend selection
* performance problems
* unexpected conditions

Do not log every operation by default.

Observability should provide useful information with reasonable overhead.

## 8. Testing

Tests are independent consumers of production behavior.

For significant changes, verify as appropriate:

```text
Normal behavior
Edge cases
Failure paths
Integration behavior
Regression behavior
```

Test important contracts and behavior rather than implementation details alone.

Production code must not depend on test code.

## 9. Avoid Over-Engineering

Do not use arbitrary limits such as:

* maximum lines per function
* maximum lines per file
* mandatory number of modules
* mandatory architecture layers

Size is a signal, not a rule.

Refactor when evidence shows:

* excessive coupling
* repeated logic
* difficult testing
* unstable interfaces
* dependency cycles
* excessive branching
* difficult debugging
* frequent unrelated changes in the same place

## 10. Change Procedure

For every feature or modification:

```text
1. Understand the goal.
2. Locate the existing responsibility.
3. Try the simplest clean change.
4. Introduce a boundary only if justified.
5. Implement with minimal collateral change.
6. Test normal and failure behavior.
7. Add useful observability.
8. Review coupling and complexity.
9. Refactor only when evidence justifies it.
```

## 11. Architecture Decision Test

Before adding an abstraction, answer:

```text
What problem does this solve?
Why is the current structure insufficient?
What complexity does this add?
Will the benefit outweigh that complexity?
```

If the answer is unclear:

> Do not add the abstraction yet.

## 12. Final Principle

```text
Simple by default.
Modular by reason.
Complex only by necessity.
```

The best architecture is not the most modular architecture.

It is the **simplest architecture that clearly expresses responsibilities, protects important boundaries, remains testable, and can evolve when future requirements genuinely justify additional structure.**
