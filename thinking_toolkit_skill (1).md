# Thinking Toolkit — Skill Reference

> **Date:** 2026-08-24  
> **Description:** A systematic atlas for diagnosing problems and selecting the right tool. Not a mandatory sequence — the model is chosen based on the nature of the problem.

---

## 1. Core Philosophy

### Bayesian → Frequentist
> "Bayesian for thinking, Frequentist for testing."

- Assume probabilities (priors), update them, then test predictions by experiment.
- The central reasoning framework for research and decision-making.

### Manifold / Atlas
> "Draw the problem as a closed Manifold"

- Transform a complex system state into a point on a bounded 2D chart.
- Geometric boundaries = laws/constraints, operations = geometric transformations.
- Goal: Make the solution space visible to both humans and computers (2D images are easier than raw data).
- Applicable to any domain.

### Atlas of Sheets
> "An Atlas of low-dimensional Sheets"

- Transform a high-dimensional problem into a set of low-dimensional sheets.
- Each sheet shows one facet, transitions between them = transition maps.
- Principle: Whitney/Nash embedding theorem.

---

## 2. Problem Diagnosis & Tool Selection

### Slice & Tool
> Decompose the problem into pieces of different nature; each piece gets a simple fitting tool.

**Available tools:** Sort, Greedy, Filter, Local Search, Cluster, Similarity, Backhaul, Round Robin, Normalize, Balance.

**Decomposition rule:**
- **Clear seam** → hierarchical (sequential ordering: start with what unlocks the rest; if stuck → backtrack)
- **Else** → flat (independent pieces)

**Operational results:**
- Logistics: +115% profit
- Finance: improved Sharpe Ratio

### Black-Box Probe
> Preprocessor to reveal the structure of a black box in a wide space.

**Mechanism:**
- Fast random exploration (n computed from μ and σ² via concentration bounds)
- Sample analysis

**Mappings to other tools:**
| What it reveals | Next tool |
|-----------------|-----------|
| Sensitivity | Slice & Tool (seams) |
| Correlation | SSA (k vars) |
| PCA structure | Manifold/Atlas (sheets) |
| Distribution | Bayesian (prior) |
| Mean progress | FIP-AI (initial estimate) |

**Scope:** Continuous optimization, hyperparameter search.  
**Fails in:** Hard constraints (SAT) and discrete problems.

---

## 3. Specialized Tools

### Selective Shallow Abstraction (SSA)
> "Pay depth only where it pays off."

**Mechanism:**
1. O(n) scan → identify k=4-7 high-degree seam variables
2. Brute force on seams (2^k)
3. Greedy on interior
4. Reassemble

**Results:**
- 6x–1237x speedup on resource allocation (12-25 tasks) and SAT (25 vars, 130 clauses)
- Exploring <0.1% of search space
- Scales to 30+ variables

**Relation:** Linked to Slice & Tool.

### FIP-AI (Fermian Inference Protocol)
> For quantitative estimation — never give a single number without three paths.

**Steps:**
1. Deconstruct into variables with 90% confidence ranges + geometric mean
2. Three independent paths: demographic, supply chain, alternative data
3. Convergence filter:
   - ratio > 10 → stop (unreliable)
   - ratio > 3 → low confidence
   - ratio ≤ 3 → geometric mean
4. **Output:** Central estimate, confidence range, all paths, sensitivity, knowns/unknowns

### Adversarial Assembly
> When assembling contradictory pieces to build a complete picture.

**Mechanism:**
- Path 1 & Path 2: explore two different angles
- Path 3: verify upon conflict
- Record historical accuracy of each path and weight votes by earned confidence
- If one path solves a piece that unlocks another → propagate knowledge immediately

**Used after:** Slice & Tool when pieces are interdependent or data is contradictory.

### SAT Encoding
> Encode the problem as SAT and use a solver.

---

## 4. Research Context

### Local Topology-Constrained Folding Dynamics
> Scientific hypothesis: local topological constraints measurably alter protein / lattice polymer folding dynamics.

- Current phase: prototype/engine building (Month 1-2 of a 6-month plan)
- Values: precise mathematical definitions, incremental engineering, falsifiable hypotheses

---

## 5. Workflow Integration

```
Problem arrives
    ↓
Diagnose nature
    ↓
┌─────────────────┬─────────────────┬─────────────────┐
│  Black-Box?     │  Structure      │  Estimation     │
│  → Black-Box    │  known?         │  needed?        │
│    Probe        │  → Slice & Tool │  → FIP-AI       │
│                 │  → SSA          │                 │
│                 │  → SAT Encoding │                 │
└─────────────────┴─────────────────┴─────────────────┘
    ↓
Conflicting pieces? → Adversarial Assembly
    ↓
Need visualization? → Manifold / Atlas of Sheets
    ↓
Test predictions? → Frequentist validation
```

---

## 6. Quick Reference Card

| Problem | Tool |
|---------|------|
| I don't know the system structure | Black-Box Probe |
| I know the structure and want to decompose | Slice & Tool |
| Wide search + many variables | SSA |
| Quantitative estimate with limited data | FIP-AI (3 paths) |
| Contradictory data | Adversarial Assembly |
| I want to see the solution space | Manifold / Atlas |
| Logic/synthesis problem | SAT Encoding |
| Hypothesis testing | Bayesian → Frequentist |

---

*Last updated: 2026-08-24*
