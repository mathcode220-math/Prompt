---
name: Differential Equation Discovery (DED)
description: Discover, test, and validate differential equation models from data and prior knowledge, aiming for the simplest defensible dynamical model.
version: 4.1.0
tags: [differential-equations, modeling, scientific-discovery, symbolic-regression]
---

# Differential Equation Discovery (DED)

## Goal

Find the simplest differential equation that explains the system, satisfies known constraints, and generalizes beyond the observed data.

The objective is not curve fitting. The objective is a defensible dynamical model.

---

## Core Rules

1. Use data, physics, logic, and prior knowledge when available.
2. Never fabricate missing data, laws, variables, parameters, or constraints.
3. Prefer the simplest model supported by evidence.
4. Increase complexity only when simpler models fail.
5. Report ambiguity when the available evidence cannot distinguish between models.

---

## Workflow

```text
INPUT
↓
DIAGNOSIS
↓
SEARCH POLICY
↓
STRUCTURE SEARCH
↓
PARAMETER SEARCH
↓
VALIDATION
↓
CRITIC
↓
SEARCH-SPACE UPDATE
↓
STOP / CONTINUE
