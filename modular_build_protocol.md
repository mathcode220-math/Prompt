# Modular Build Protocol — Layered Construction Skill

> A project is not a file. A project is a graph of contracts.
> Build layers, not lumps.

---

## The Fatal Pattern (What to Avoid)

```
❌ ONE BIG FILE
    init + logic + backend + test + main
    → Change test → recompile everything
    → Add feature → break everything
    → Debug → no idea where the bug lives
```

---

## The Protocol: 5 Layers, 5 Files Minimum

Every addition to a project MUST pass through these 5 layers:

```
LAYER 1: API        (what the world sees)
    ↓ contract
LAYER 2: Validator  (is this request sane?)
    ↓ gate
LAYER 3: Dispatcher (which backend handles this?)
    ↓ route
LAYER 4: Backend    (how it actually works)
    ↓ execute
LAYER 5: Trace      (what happened, where, when)
    ↓ log
```

---

## Layer Rules (Max 6 Lines of Logic Per Function)

### LAYER 1 — API
```c
// api.h — ONLY declarations. NO implementation. NO globals.
int  project_init(void);
int  project_dispatch(const input_t *in, output_t *out);
void project_reset(void);
```
> Rule: If a user includes this header, they must NOT see registers, mocks, or tests.

### LAYER 2 — Validator
```c
// validator.c — Gatekeeper. Returns ERROR before any side effect.
static int preflight(const input_t *in) {
    if (!in)              return ERR_NULL;
    if (in->size > MAX)   return ERR_SIZE;
    if (!backend_ready()) return ERR_BUSY;
    return OK;
}
```
> Rule: Validator never modifies state. It only says YES or NO with a reason.

### LAYER 3 — Dispatcher
```c
// dispatcher.c — Router. Picks backend, never implements it.
int dispatch(const input_t *in, output_t *out) {
    if (preflight(in) != OK) return ERR_PREFLIGHT;
    if (use_simulation)      return sim_backend_run(in, out);
    else                     return hw_backend_run(in, out);
}
```
> Rule: Dispatcher knows WHAT exists, not HOW it works.

### LAYER 4 — Backend
```c
// sim_backend.c — ONE backend per file. NO #ifdef mixing.
// hw_backend.c  — Another file. Can be empty (placeholder) but MUST exist.
```
> Rule: Each backend is a standalone unit. Swapping backends = changing one line in dispatcher.

### LAYER 5 — Trace
```c
// trace.c — Records every cross-layer jump.
void trace_log(const char *layer, const char *op, int result, uint64_t cycles);
```
> Rule: Trace is the debugger you will need in 3 months. Write it now or suffer later.

---

## Forbidden Patterns (Hard No)

| Pattern | Why It Kills Projects |
|---|---|
| `static` globals in API files | Hidden state → untestable |
| `#ifdef TEST` inside production code | Test code infects release binary |
| `if (sim_mode)` inside business logic | Backend logic leaks into dispatcher |
| Functions > 50 lines | Cognitive load → bugs hide |
| Files > 200 lines | Monolith reborn |
| Including `<test headers>` in production | Dependency direction reversed |

---

## Checklist Before Committing

```
□ Can I swap the backend without touching the API?
□ Can I add a new test without recompiling the driver?
□ Can I read the dispatcher and know ALL backends available?
□ Does every public function have a validator gate?
□ If this crashes, can trace tell me which layer died?
□ Is there ANY production code that knows it is "simulation"?
```

If any answer is NO → refactor before commit.

---

## Quick Reference: Adding a New Feature

```
Step 1: Define the API in api.h (what does the world need?)
Step 2: Write validator rules (what can go wrong?)
Step 3: Add dispatcher route (which backend?)
Step 4: Implement in ONE backend file (sim first, hw later)
Step 5: Add trace points at every layer crossing
Step 6: Write test in test/ — NOT inside the source
```

---

*This is a construction protocol. It does not contain code. It contains the rules that prevent code from becoming a monolith.*
