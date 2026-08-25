# Adaptive Modular Build Protocol — Pragmatic Construction Skill

> A project is not a collection of files.
> A project is a set of responsibilities, contracts, dependencies, and observable behavior.
>
> **Build the simplest architecture that safely supports the current goal and can evolve when the system requires it.**

---

## 1. Purpose

This protocol guides an AI agent or developer when creating, extending, or refactoring a software project.

Its purpose is not to maximize modularity.

Its purpose is to achieve:

```text
Correctness
   ↓
Clear responsibilities
   ↓
Testability
   ↓
Controlled dependencies
   ↓
Observability
   ↓
Replaceability where useful
   ↓
Minimal unnecessary complexity
```

The protocol therefore rejects both extremes:

```text
❌ Monolithic design
```

and

```text
❌ Over-engineered modularity
```

The target is:

```text
✅ Minimal sufficient architecture
```

---

# 2. Core Principle

## Do not create structure without a reason.

Before introducing a:

* file
* module
* interface
* abstraction
* dispatcher
* validator
* backend layer
* service
* adapter
* logging layer

the agent must be able to identify the concrete problem that structure solves.

Valid reasons include:

```text
• isolates a changing responsibility
• protects a public contract
• enables independent testing
• separates external dependencies
• allows implementation replacement
• prevents dependency leakage
• improves observability
• reduces cognitive complexity
• supports multiple implementations
• protects an important invariant
```

If none applies:

```text
Do not add the abstraction.
```

---

# 3. Architecture Is Adaptive

There is no mandatory number of layers or files.

The architecture must scale with the actual complexity of the task.

### Level 0 — Simple

For a small feature, a single module may be sufficient:

```text
feature.c
feature.h
test_feature.c
```

Do not introduce additional layers merely for symmetry.

---

### Level 1 — Separated Responsibilities

When responsibilities begin to diverge:

```text
api
implementation
tests
```

For example:

```text
api.h
feature.c
validator.c
test_feature.c
```

---

### Level 2 — Replaceable Implementations

When multiple implementations exist or are expected:

```text
api
validator
backend interface
backend implementations
tests
```

Example:

```text
include/
    api.h

src/
    validator.c
    dispatcher.c

backends/
    sim_backend.c
    hw_backend.c

tests/
    test_api.c
```

---

### Level 3 — Complex System

Only when justified:

```text
API
 ↓
Validation
 ↓
Routing
 ↓
Implementation
 ↓
Observability
```

Possible structure:

```text
include/
src/
    api/
    validation/
    routing/
    core/
    backends/
    observability/
tests/
tools/
```

The important rule is:

> **These are available architectural boundaries, not mandatory layers.**

---

# 4. Architecture Selection Procedure

Before modifying the project, evaluate the task.

```text
Task
 ↓
Understand the goal
 ↓
Identify responsibilities
 ↓
Identify dependencies
 ↓
Identify likely points of change
 ↓
Estimate complexity
 ↓
Choose minimal sufficient structure
 ↓
Implement
 ↓
Test
 ↓
Observe
 ↓
Refactor only when justified
```

The agent must not begin by creating files.

It must begin by understanding the change.

---

# 5. Responsibility Boundaries

A responsibility should normally have one clear owner.

Examples:

```text
Input validation
Backend selection
Core computation
Hardware interaction
Persistence
Logging
Testing
```

Avoid code such as:

```text
business logic
      +
hardware access
      +
test behavior
      +
logging policy
```

inside the same responsibility unless the combination is genuinely simple.

The objective is:

```text
High cohesion
Low unnecessary coupling
```

not maximum fragmentation.

---

# 6. Public API

Public interfaces define the contract between the system and its users.

Example:

```c
int project_init(void);
int project_dispatch(const input_t *in, output_t *out);
void project_reset(void);
```

Rules:

```text
• Keep public interfaces small.
• Do not expose implementation details unnecessarily.
• Do not expose tests through production APIs.
• Do not expose backend-specific state unless required by the contract.
• Prefer stable contracts over convenient leakage of internals.
```

The API should describe:

```text
WHAT the system provides
```

not:

```text
HOW the system implements it
```

---

# 7. Validation

Validation exists to establish that an operation can safely proceed.

A validator should normally:

```text
• reject invalid input
• reject impossible states
• enforce explicit limits
• verify required preconditions
• return a meaningful failure reason
```

Example:

```c
static int validate(const input_t *in)
{
    if (!in) return ERR_NULL;
    if (in->size > MAX_SIZE) return ERR_SIZE;
    return OK;
}
```

Prefer validation before side effects.

However:

> Do not create a separate validator module for trivial validation that is clearer directly at the API boundary.

Validation is a responsibility, not necessarily a file.

---

# 8. Routing and Dispatch

A dispatcher is justified when the system has multiple execution paths.

For example:

```text
request
   ↓
validation
   ↓
backend selection
   ↓
implementation
```

The dispatcher should decide:

```text
WHO executes
```

rather than implement:

```text
HOW the computation works
```

Do not create a dispatcher when there is only one implementation and no meaningful routing decision.

A simple direct call is preferable:

```c
return backend_run(in, out);
```

to introducing an unnecessary routing layer.

---

# 9. Backends and Adapters

Separate implementations when they are genuinely interchangeable.

Examples:

```text
simulation
hardware
CPU
GPU
remote service
mock
optimized implementation
```

Preferred dependency direction:

```text
Public contract
      ↓
Implementation interface
      ↓
Concrete backend
```

The public API should not need to know backend internals.

A backend should not modify unrelated application responsibilities merely because it can.

---

# 10. Observability

Observability should exist wherever it provides meaningful diagnostic value.

Useful signals include:

```text
errors
state transitions
important operations
performance measurements
backend selection
resource failures
unexpected conditions
```

Example:

```c
trace_log("backend", "run", result, cycles);
```

However:

> Do not log every function call merely because the protocol says so.

Logging must have a purpose.

Use appropriate levels:

```text
ERROR
WARN
INFO
DEBUG
TRACE
```

and allow production builds to reduce unnecessary overhead.

---

# 11. Dependency Direction

Dependencies should generally flow toward stable contracts.

A healthy structure resembles:

```text
Application
    ↓
Domain / Core
    ↓
Interfaces
    ↓
Infrastructure
```

Tests may depend on production interfaces:

```text
tests ─────→ production
```

but production code should not depend on test code:

```text
production ──X──→ tests
```

Avoid:

```c
#ifdef TEST
```

when a cleaner dependency boundary can solve the problem.

Testing mechanisms should preferably remain outside production logic.

---

# 12. Avoid Implementation Leakage

Avoid exposing infrastructure decisions to higher-level business logic.

Bad:

```c
if (simulation_mode) {
    ...
}
```

repeated throughout business logic.

Prefer:

```text
business logic
      ↓
contract
      ↓
selected implementation
```

The system should contain infrastructure-specific knowledge at the narrowest reasonable boundary.

---

# 13. File and Function Size

There are no absolute universal limits such as:

```text
6 lines
50 lines
200 lines
```

Length alone is not a reliable measure of complexity.

Instead ask:

```text
• Does the function perform one coherent responsibility?
• Can it be understood without excessive mental state?
• Does it have difficult branching?
• Is it difficult to test?
• Does it contain unrelated responsibilities?
• Is the file difficult to navigate?
• Would splitting it improve clarity?
```

Split code when the split provides a real improvement.

Do not split code merely to satisfy an arbitrary line count.

---

# 14. The Abstraction Test

Before introducing an abstraction, answer:

```text
What problem does this abstraction solve?
```

Then ask:

```text
What does it cost?
```

Cost includes:

```text
• additional files
• indirection
• cognitive overhead
• maintenance
• testing surface
• debugging complexity
• dependency management
```

Introduce the abstraction when:

```text
Expected benefit > added complexity
```

Otherwise keep the simpler implementation.

---

# 15. Change Isolation

A strong architecture isolates changes that are expected to happen independently.

For example:

```text
Hardware implementation changes
        ↓
should NOT
        ↓
require redesigning the public API
```

Similarly:

```text
Logging implementation changes
        ↓
should NOT
        ↓
modify business logic
```

Modularity should therefore be driven partly by:

> **How the system is expected to change.**

---

# 16. Testing

Tests are separate consumers of the system.

Prefer:

```text
production code
      ↑
      │
     API
      │
      ↑
tests
```

Tests should verify contracts and behavior, not implementation details unless implementation-level testing is explicitly required.

For each meaningful change, consider:

```text
Unit test
Integration test
Regression test
Edge-case test
Failure-path test
```

Do not create tests merely for line coverage.

Test the behaviors that matter.

---

# 17. Refactoring Trigger

Refactoring is justified when evidence indicates structural problems.

Typical signals:

```text
• repeated logic
• growing coupling
• difficult testing
• unstable interfaces
• duplicated backend decisions
• excessive branching
• difficult debugging
• frequent unrelated changes in the same file
• dependency cycles
• performance problems caused by architecture
```

Do not refactor simply because a different architecture looks cleaner.

---

# 18. Forbidden Patterns

These are strong warnings, not arbitrary style rules.

| Pattern                                                          | Problem                  |
| ---------------------------------------------------------------- | ------------------------ |
| One module owns unrelated responsibilities                       | High coupling            |
| Tests embedded into production behavior                          | Dependency contamination |
| Backend details spread through business logic                    | Infrastructure leakage   |
| Global mutable state without clear ownership                     | Hidden coupling          |
| Abstraction with only one trivial use and no foreseeable benefit | Over-engineering         |
| Many tiny modules with little semantic value                     | Fragmentation            |
| Circular dependencies                                            | Unstable architecture    |
| Logging with no diagnostic purpose                               | Noise and overhead       |
| Public API exposes implementation details                        | Contract instability     |
| Architecture chosen before understanding the task                | Premature structure      |

---

# 19. Decision Matrix

When deciding whether to create a new boundary:

| Question                                            | Yes →                         | No →                              |
| --------------------------------------------------- | ----------------------------- | --------------------------------- |
| Does the responsibility change independently?       | Consider separation           | Keep together                     |
| Are there multiple implementations?                 | Consider interface/dispatcher | Direct implementation may suffice |
| Does it need independent testing?                   | Consider module boundary      | Keep local                        |
| Does it isolate an external dependency?             | Consider adapter              | Avoid abstraction                 |
| Does separation reduce cognitive load?              | Split                         | Keep together                     |
| Will separation only add indirection?               | Avoid                         | —                                 |
| Is the boundary required for correctness or safety? | Create it                     | Not mandatory                     |

---

# 20. Commit Gate

Before committing a significant change, ask:

```text
[ ] Is the public contract clear?
[ ] Are responsibilities clearly owned?
[ ] Are dependencies flowing in a sensible direction?
[ ] Are invalid inputs rejected before unsafe side effects?
[ ] Can important implementations be tested independently?
[ ] Are backend details isolated where useful?
[ ] Is observability sufficient for diagnosing failures?
[ ] Did I avoid unnecessary abstractions?
[ ] Did I avoid unnecessary file splitting?
[ ] Can the likely next change be made without excessive collateral modification?
[ ] Did I choose this architecture because of the problem, rather than because of a template?
```

If a box fails:

```text
Investigate first.
Refactor only when the failure represents a real architectural problem.
```

---

# 21. Adding a New Feature

Use this sequence:

```text
Step 1 — Understand
What behavior is actually required?

Step 2 — Locate
Which existing responsibility owns this behavior?

Step 3 — Evaluate
Can the feature fit cleanly into the existing structure?

Step 4 — Separate if necessary
Create a new boundary only when there is a concrete reason.

Step 5 — Implement
Keep the change local and dependency-safe.

Step 6 — Test
Verify normal, edge, and failure behavior.

Step 7 — Observe
Add diagnostics where failures would otherwise be difficult to understand.

Step 8 — Review
Check whether the new feature increased coupling or unnecessary complexity.

Step 9 — Refactor
Only when evidence shows that the current structure is becoming a problem.
```

---

# 22. Architectural Principle for AI Agents

An AI coding agent must not interpret modularity as:

```text
more files = better architecture
more layers = better architecture
more abstractions = better design
```

Instead:

```text
good architecture
=
the smallest structure that safely expresses the system's responsibilities
and remains capable of evolving with justified future requirements.
```

The agent should therefore optimize for:

```text
Correctness
>
Safety
>
Determinism
>
Observability
>
Maintainability
>
Replaceability
>
Simplicity
```

When two designs are functionally equivalent:

```text
choose the simpler one
```

unless the more complex design provides a concrete, defensible advantage.

---

# 23. Final Rule

> **Do not build layers because the protocol says layers should exist.**
>
> **Build boundaries when the system gives you a reason to need them.**

The goal is not:

```text
Maximum modularity
```

The goal is:

```text
Minimum sufficient complexity
+
Clear contracts
+
Controlled dependencies
+
Testable behavior
+
Useful observability
+
Room for justified evolution
```

That is modularity without over-engineering.

---

## Quick Mental Model

```text
              ┌─────────────┐
              │    GOAL     │
              └──────┬──────┘
                     ↓
              ┌─────────────┐
              │ UNDERSTAND  │
              └──────┬──────┘
                     ↓
           ┌───────────────────┐
           │   NEED A BOUNDARY?│
           └─────────┬─────────┘
                     │
             ┌───────┴───────┐
             │               │
            NO              YES
             │               │
             ↓               ↓
         Keep simple     Create boundary
             │               │
             └───────┬───────┘
                     ↓
                  TEST
                     ↓
               OBSERVE
                     ↓
             REFACTOR ONLY
             WHEN JUSTIFIED
```

> **Simple by default. Modular by reason. Complex only by necessity.**
