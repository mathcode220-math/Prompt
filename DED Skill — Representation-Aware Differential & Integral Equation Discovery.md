---
name: Differential and Integral Equation Discovery (DED)
description: Discover, compare, test, and validate the simplest defensible dynamical representation of a system from data and prior knowledge, using differential, integral, discrete, and equivalent mathematical forms.
version: 5.0.0
tags: [differential-equations, integral-equations, dynamical-systems, scientific-discovery, symbolic-regression, representation-discovery, system-identification]
---

# Differential and Integral Equation Discovery (DED)

## Goal

Find the simplest defensible mathematical representation of a dynamical system that:

- explains the observed data,
- satisfies known physical, logical, and mathematical constraints,
- generalizes beyond the observed data,
- remains identifiable and interpretable,
- and uses no unnecessary complexity.

The preferred representation may be:

- an ordinary or partial differential equation,
- an integral equation,
- an integro-differential equation,
- a discrete-time recurrence,
- or another equivalent dynamical form when strongly justified.

> **The objective is not curve fitting.**  
> **The objective is to discover the simplest defensible governing law.**

---

## Core Principles

1. Use data, physics, mathematics, logic, and prior knowledge when available.
2. Never fabricate missing variables, data, parameters, laws, boundary conditions, or constraints.
3. Prefer the simplest representation supported by evidence.
4. Do not assume that the differential form is the easiest form to discover.
5. Treat representation choice as part of model discovery.
6. Increase complexity only when simpler representations fail.
7. Prefer exact structural simplicity over marginal numerical improvement.
8. Distinguish interpolation from genuine dynamical explanation.
9. Report ambiguity when available evidence cannot distinguish between competing models.
10. Reject models whose apparent simplicity depends on unjustified assumptions.
11. Preserve dimensional consistency, invariances, symmetries, and known conservation laws.
12. Separate discovery, fitting, validation, and criticism.
13. Never use a more complicated model merely because it fits the training data better.
14. When two representations are mathematically equivalent, prefer the one that is easier to discover, validate, interpret, or solve.

---

# 1. INPUT

Accept any combination of:

- time-series data
- spatial-temporal data
- multiple trajectories
- control/input variables
- initial conditions and boundary conditions
- derivatives if experimentally available
- physical laws and conservation relations
- known symmetries and dimensional information
- prior candidate equations
- qualitative observations and measurement uncertainty

### What to Identify

- dependent variables (what changes?)
- independent variables (along what do they change?)
- inputs and control variables
- states and observed quantities
- hidden quantities and latent variables
- units and dimensional structure
- sampling structure and experimental conditions
- uncertainty sources

**Key Principle:** Never assume unobserved quantities exist unless they are introduced explicitly as latent variables or justified by prior knowledge.

---

# 2. DIAGNOSIS

Before symbolic discovery, diagnose the data.

### Data Assessment

Estimate:

| Property | What to check |
|----------|--------------|
| **Noise** | noise level, signal-to-noise ratio |
| **Sampling** | sampling density, frequency, uniformity |
| **Completeness** | missingness, gaps, coverage |
| **Smoothness** | continuity, differentiability, roughness |
| **Stationarity** | time-dependence, drift, trends |
| **Scales** | scale separation, multiscale structure |
| **Trajectories** | repeated runs, uniqueness, diversity |
| **Transients** | transient vs. steady-state regions |
| **Causality** | delays, lead-lag relationships, memory |
| **Derivatives** | reliability of estimated derivatives |
| **Integrals** | stability of integral approximations |
| **Boundary conditions** | type and quality of boundary information |

### System Character

Determine whether the data appear primarily:

| Character | Implication |
|-----------|------------|
| **Local** | gradual, nearby-state dependent |
| **Cumulative** | history-dependent, path-dependent |
| **Memory** | past states strongly influence future |
| **Delayed** | lag or delay structures present |
| **Conservative** | energy/mass conserving |
| **Dissipative** | energy-decaying |
| **Periodic** | oscillatory, cyclic behavior |
| **Multiscale** | multiple timescales or length scales |
| **Stochastic** | randomness, noise, uncertainty |
| **Spatially coupled** | spatial gradients or interactions |
| **Nonstationary** | time-varying properties |

### Derivative Reliability Test

Do not automatically differentiate noisy data.

**Question:** Can we recover derivatives reliably?

$$y'(t), \quad y''(t), \quad y'''(t), \ldots$$

with sufficient stability and confidence?

**Decision Rule:**
- ✓ If derivatives are stable → Differential forms have priority
- ✗ If differentiation amplifies noise substantially → Prioritize integral formulations

### Memory Test

**Question:** Does $y(t)$ depend materially on earlier states or inputs?

**Evidence for memory indicates:**

$$y(t) = f(t) + \int_a^t K(t,s) \, y(s) \, ds$$

or more general history-dependent models should have high priority.

---

# 3. REPRESENTATION DISCOVERY

This is the central stage.

**Critical Principle:** Do not begin by assuming $\dot{y} = F(t,y)$.

Instead, construct and compare mathematically justified representations.

### 3.1 Differential Form

$$\frac{d}{dt}[y] = F(t, y, u, \theta)$$

**Includes:**
- Ordinary Differential Equations (ODE)
- Partial Differential Equations (PDE)
- Higher-order equations
- Coupled systems

### 3.2 Integral Form

Use exact or formally equivalent transformations when justified.

**Example:** Starting from

$$\dot{y}(t) = F(t, y(t))$$

we obtain

$$y(t) = y(t_0) + \int_{t_0}^{t} F(s, y(s)) \, ds$$

### 3.3 Linear Integral Form

$$y(t) = f(t) + \int_a^b K(t,s) \, y(s) \, ds$$

**Fredholm equation** — integration domain is fixed.

### 3.4 Volterra Form

$$y(t) = f(t) + \int_{t_0}^{t} K(t,s) \, y(s) \, ds$$

**Volterra equation** — causal domain with upper limit = current time.

*Especially important when causality or memory is present.*

### 3.5 Integro-Differential Form

$$\frac{d}{dt}[y](t) = F\left( t, y(t), \int_a^b K(t,s) \, y(s) \, ds \right)$$

**Use only when evidence supports both local and historical effects.**

### 3.6 Discrete Form

For discrete or poorly sampled systems:

$$y_{k+1} = F(k, y_k, u_k)$$

*Do not force continuous-time structure when observations do not justify it.*

---

# 4. REPRESENTATION SCORING

Each representation must be evaluated before committing to symbolic search.

### Scoring Conceptual Formula

$$S(R) = E(R) + C(R) + I(R) + U(R) + G(R)$$

where:

| Component | Meaning |
|-----------|---------|
| $E(R)$ | **Empirical error** on validation set |
| $C(R)$ | **Structural complexity** (terms, operators, kernels) |
| $I(R)$ | **Identifiability difficulty** (parameter uniqueness) |
| $U(R)$ | **Numerical instability** (conditioning, truncation) |
| $G(R)$ | **Generalization risk** (overfitting penalty) |

**Lower score is better.**

### Selection Criteria

Prefer a representation that:

- ✓ requires fewer assumptions
- ✓ has fewer active terms
- ✓ uses fewer parameters
- ✓ is numerically stable
- ✓ is easier to validate
- ✓ exposes meaningful structure

**Warning:** Do not select a representation using fit error alone.

---

# 5. INTEGRAL ADVANTAGE TEST

An integral representation receives higher priority when **one or more** of the following hold:

### A. Derivative Instability

Differentiation amplifies measurement noise or produces unreliable derivatives.

### B. Cumulative Dynamics

The physical or mathematical process is naturally cumulative or history-dependent.

### C. Memory

The current state depends on historical values.

### D. Green-Function Structure

A differential operator can be transformed into a useful kernel representation:

$$L[y] = f \quad \Rightarrow \quad y = \int G(\cdot, \cdot) \, f$$

### E. Low-Rank Kernel Structure

The kernel is exactly or approximately separable:

$$K(t,s) \approx \sum_{i=1}^{r} u_i(t) \, v_i(s), \qquad r \ll n$$

### F. Convolution Structure

The kernel depends primarily on the lag:

$$K(t,s) = k(t - s)$$

*Translation-invariant, often simpler than full $(t,s)$ dependence.*

### G. Volterra Structure

The causal domain $s \leq t$ induces useful triangular structure.

$$y(t) = f(t) + \int_{t_0}^{t} K(t,s) \, y(s) \, ds$$

### H. Reduced Search Complexity

Use the integral form when symbolic discovery becomes simpler even when both forms are mathematically equivalent.

---

# 6. KERNEL DISCOVERY

For integral models, do not search over arbitrary functions first.

**Use a structured kernel grammar.**

### Priority Candidates (in order)

| Kernel Form | Formula | Type |
|-------------|---------|------|
| **Constant** | $K(t,s) = 1$ | Simplest |
| **Linear** | $K(t,s) = t, \quad s, \quad t-s$ | Separable polynomials |
| **Separable** | $K(t,s) = u(t) v(s)$ | Rank-1 |
| **Low-rank** | $K(t,s) = \sum_i u_i(t) v_i(s)$ | Rank-$r$ |
| **Convolution** | $K(t,s) = k(t-s)$ | Translation-invariant |

### Standard Exponential and Oscillatory Kernels

$$e^{-\lambda(t-s)}, \quad (t-s)^p, \quad \sin(\omega(t-s)), \quad \cos(\omega(t-s))$$

**Expand the kernel grammar only when evidence requires it.**

---

# 7. STRUCTURE SEARCH

After representation selection, search for the simplest structural form.

### Priority Order (Progressive Complexity)

| Level | Structure | Example |
|-------|-----------|---------|
| 1 | Zero/constant | $y(t) = c$ |
| 2 | Linear combination | $y(t) = c_1 f_1(t) + c_2 f_2(t)$ |
| 3 | Separable | $K(t,s) = u(t)v(s)$ |
| 4 | Sparse (few nonzero terms) | Mostly zero except key terms |
| 5 | Low-rank (few hidden factors) | Rank-$r$ kernel with $r \ll n$ |
| 6 | Polynomial | $\sum a_i y^i$ |
| 7 | Convolution | $K(t,s) = k(t-s)$ |
| 8 | Symmetry/invariance | Preserved under transformation |
| 9 | Known physical forms | Newton's law, Ohm's law, etc. |
| 10 | Nonlinear composite | $F(G_1, G_2, \ldots)$ |
| 11 | Unrestricted symbolic | General search (last resort) |

### Integral Equation Tests

For integral equations, explicitly test:

- ✓ Separability: $K(t,s) = u(t)v(s)$?
- ✓ Low rank: $K(t,s) \approx \sum_i u_i(t)v_i(s)$ with small $r$?
- ✓ Convolution: $K(t,s) = k(t-s)$?
- ✓ Volterra causality: $K(t,s) = 0$ for $s > t$?
- ✓ Symmetry: $K(t,s) = K(s,t)$?
- ✓ Antisymmetry: $K(t,s) = -K(s,t)$?
- ✓ Triangular structure: useful sparsity pattern?
- ✓ Known Green kernels: match a standard form?
- ✓ Smoothness: continuity, differentiability?
- ✓ Locality: $K(t,s) \approx 0$ for $|t-s| > \Delta$?
- ✓ Compact support: $K(t,s) = 0$ outside a bounded region?

---

# 8. PARAMETER SEARCH

Once structure is chosen, estimate parameters.

### Preferred Methods (in order)

| Method | When to use |
|--------|------------|
| **Linear regression** | Structure is linear in parameters |
| **Constrained regression** | Known bounds or constraints on parameters |
| **Sparse regression** | Encourage fewer nonzero parameters |
| **Nonlinear least squares** | Parameters enter nonlinearly |
| **Robust regression** | High noise or outliers |
| **Bayesian estimation** | Uncertainty quantification needed |

### Key Principle

Separate:

$$\text{Structure Discovery} \quad \Leftrightarrow \quad \text{Parameter Estimation}$$

**Do not perform unrestricted symbolic search and parameter fitting simultaneously unless necessary.**

---

# 9. INTEGRAL-TO-ALGEBRA REDUCTION

Whenever an integral kernel is separable or low rank, reduce the problem.

### Setup

Given

$$y(t) = f(t) + \int_a^b K(t,s) \, y(s) \, ds$$

and separable kernel

$$K(t,s) = \sum_{i=1}^{r} u_i(t) \, v_i(s)$$

### Reduction

Define auxiliary variables:

$$c_i = \int_a^b v_i(s) \, y(s) \, ds$$

Then the integral equation becomes:

$$y(t) = f(t) + \sum_{i=1}^{r} u_i(t) \, c_i$$

### Benefit

**This reduces the original infinite-dimensional functional problem to a finite-dimensional algebraic system.**

**Strongly prefer this reduction over generic iterative solution when it is exact or demonstrably accurate.**

---

# 10. EQUIVALENCE TEST

When two models have different mathematical forms, test whether they are equivalent.

### Example

$$\dot{y} = F(t, y) \quad \text{versus} \quad y(t) = y_0 + \int_{t_0}^{t} F(s, y(s)) \, ds$$

These are mathematically equivalent.

### Critical Questions

Do not treat equivalent representations as independent scientific discoveries. Instead ask:

1. **Discoverability:** Which form is easier to discover from data?
2. **Stability:** Which form is more stable under measurement noise?
3. **Validation:** Which form is easier to validate?
4. **Interpretability:** Which form is more interpretable?
5. **Structure:** Which form reveals additional structure?
6. **Generalization:** Which form generalizes better?

**Choose the representation that wins on most criteria.**

---

# 11. VALIDATION

Validation must test more than training fit.

### General Evaluation Criteria

| Criterion | What to check |
|-----------|--------------|
| **Held-out data** | performance on unseen trajectories |
| **Future prediction** | accuracy over extended time horizons |
| **Parameter stability** | do parameters change with subsample? |
| **Perturbation robustness** | response to small input changes |
| **Residual structure** | are residuals random or patterned? |
| **Physical consistency** | does model obey conservation laws? |
| **Dimensional consistency** | do dimensions balance? |
| **Conservation laws** | energy, mass, charge preserved? |
| **Symmetry** | are known symmetries respected? |
| **Stability** | Lyapunov properties, equilibria stable? |
| **Extrapolation** | behavior at parameter extremes reasonable? |
| **Noise sensitivity** | performance under measurement noise? |

### For Integral Models — Additional Tests

| Criterion | What to check |
|-----------|--------------|
| **Kernel identifiability** | is kernel uniquely determined from data? |
| **Discretization sensitivity** | does result depend strongly on grid refinement? |
| **Quadrature sensitivity** | do numerical integration methods matter? |
| **Kernel approximation error** | how does truncating/approximating kernel affect results? |
| **Integration domain dependence** | results robust to domain choice? |

### For Differential Models — Additional Tests

| Criterion | What to check |
|-----------|--------------|
| **Derivative estimation sensitivity** | does numerical differentiation method matter? |
| **Discretization sensitivity** | does result depend on time step? |
| **Numerical differentiation robustness** | finite differences vs. smoothing-then-differentiating? |

---

# 12. MODEL COMPARISON

When multiple representations survive validation, compare them explicitly.

### Total Complexity

Prefer the model minimizing:

$$\text{Total Complexity} = C_{\text{structure}} + C_{\text{parameters}} + C_{\text{assumptions}} + C_{\text{numerical}}$$

### Breakdown

| Component | What counts |
|-----------|------------|
| $C_{\text{structure}}$ | number of terms, operators, kernels |
| $C_{\text{parameters}}$ | number of unknown parameters |
| $C_{\text{assumptions}}$ | unjustified hypotheses, missing data |
| $C_{\text{numerical}}$ | conditioning, truncation error, solver cost |

### Selection Rule

**Do NOT:**
- ✗ Choose a more complicated integral model merely because it has slightly lower residual error.
- ✗ Choose an ODE merely because the task was initially called "differential equation discovery."
- ✗ Accept unnecessary complexity for marginal accuracy gains.

**DO:**
- ✓ Explicitly document trade-offs between competing models.
- ✓ Report the Pareto frontier of simpler models with slightly higher error.

---

# 13. CRITIC

The critic must actively try to invalidate the current model.

### Critical Questions

Ask the model these hard questions:

- ❌ Is the model only fitting noise?
- ❌ Are parameters identifiable?
- ❌ Are hidden assumptions unsupported?
- ❌ Is the selected representation unnecessarily restrictive?
- ❌ Is there an equally good simpler representation?
- ❌ Did differentiation create artificial structure?
- ❌ Did integration hide important local dynamics?
- ❌ Is an apparent memory kernel actually an artifact of sampling?
- ❌ Is low-rank structure genuine or merely overfitted?
- ❌ Does the model fail under perturbation?
- ❌ Does the model violate known constraints?

### Feedback Loop

The critic may trigger a return to:

- 🔄 diagnosis (re-examine data)
- 🔄 representation discovery (try different form)
- 🔄 structure search (expand or contract grammar)
- 🔄 parameter search (refine estimates)

---

# 14. SEARCH-SPACE UPDATE

Search should be adaptive.

### Failure Analysis

If a candidate fails, identify the failure type and adapt the search.

| Failure Mode | Response |
|--------------|----------|
| Derivative instability | Increase integral-form priority |
| Missing memory effects | Expand kernel search or add history terms |
| Poor local dynamics | Test integral, delay, or feedback structures |
| Excessive nonlinearity | Test coordinate transformation or integral form |
| Residual convolution pattern | Test explicit convolution kernels |
| Repeated low-dim behavior | Test low-rank or separable structures |
| Boundary-driven behavior | Test Green-function formulation |
| Overfitting | Add regularization or reduce complexity |

### Principle

**Do not simply enlarge the symbolic grammar after every failure.**

**Expand only the part of the search space implicated by evidence.**

---

# 15. COMPLEXITY LADDER

Use progressive complexity. Stop as soon as a model is defensible.

### Complexity Levels

| Level | Description | Example |
|-------|-------------|---------|
| **0** | Constants, trivial dynamics | $y(t) = c$ |
| **1** | Simple linear ODEs/integrals | $\dot{y} = ay + b$, $y = f + \int K \cdot y$ |
| **2** | Sparse linear combinations | $\dot{y} = a_1 y + a_2 \sin(t) + a_3 x$ |
| **3** | Separable, low-rank kernels | $K(t,s) = u(t)v(s)$ |
| **4** | Convolution, Volterra structures | $y = f + \int_0^t k(t-s) y(s) ds$ |
| **5** | Simple nonlinear dynamics | $\dot{y} = a y + b y^2$ |
| **6** | Integro-differential, memory | $\dot{y} = F(y, \int K y)$ |
| **7** | General nonlinear symbolic | Unrestricted form search |
| **8** | Highly complex, multiple domains | PDEs, stochastic terms, etc. |

### Stopping Rule

**Stop as soon as a model is defensible.**

**Do not continue searching merely because a more complex model can reduce residual error.**

---

# 16. REPRESENTATION SWITCHING

At any stage, DED may switch representation.

### Switching Rules

| Condition | Action | Reason |
|-----------|--------|--------|
| Derivatives unstable | $\text{ODE} \rightarrow \text{Integral}$ | Avoid noise amplification |
| Kernel finite-dimensional | $\text{Integral} \rightarrow \text{ODE}$ | Simpler structure |
| Kernel translation-invariant | $\text{Integral} \rightarrow \text{Convolution}$ | Reduced parameters |
| Kernel admits state realization | $\text{Convolution} \rightarrow \text{Finite\text{-}dim}$ | ODE form more interpretable |
| Hidden multiscale behavior | $\text{ODE} \rightarrow \text{Multiscale}$ | Capture multiple timescales |

**The system should prefer representations that expose simpler governing structure.**

---

# 17. STOP CONDITIONS

Stop when **all** of the following hold:

1. ✓ The model passes independent validation (held-out data)
2. ✓ The structure is sufficiently identifiable (parameters unique)
3. ✓ Complexity is justified (vs. simpler alternatives)
4. ✓ Residuals contain no strong unexplained structure (white noise)
5. ✓ Known constraints are satisfied (conservation laws, etc.)
6. ✓ Further search produces only marginal improvement or unjustified complexity

### Handling Ambiguity

If several models remain equally defensible, **report the ambiguity rather than forcing a unique answer.**

---

# 18. OUTPUT

Return:

### A. Discovered Representation

State clearly whether the final model is:

- Differential (ODE or PDE)
- Integral (Fredholm or Volterra)
- Integro-differential (both local and history)
- Discrete (recurrence relation)
- or another justified representation

### B. Governing Equation

Give the final equation in exact symbolic form with all parameters labeled.

### C. Equivalent Forms

When useful, provide equivalent differential/integral forms and explain trade-offs.

### D. Structure

Explain the discovered structure:

- Sparse (few active terms)
- Separable (factorizable kernel)
- Low rank (rank-$r$ approximation)
- Convolution (lag-dependent kernel)
- Volterra (causal, memory)
- Nonlinear (specific type)
- etc.

### E. Parameters

List estimated parameters with uncertainty (standard error, confidence interval, or Bayesian posterior).

### F. Evidence

State what observations support the model:

- Which data were most constraining?
- What physical principles were used?
- What assumptions were critical?

### G. Validation

Report predictive and structural validation results:

- Held-out error, prediction accuracy
- Residual analysis
- Parameter identifiability
- Extrapolation performance

### H. Limitations

State what the data cannot establish:

- Unobservable variables
- Ambiguous parameter combinations
- Regime boundaries
- Long-term behavior

### I. Alternatives

List only serious competing representations:

- Why each was rejected (quantitatively)
- Model comparison table
- Pareto frontier if trade-offs exist

---

# 19. META-RULE

The fundamental rule of DED is:

$$\boxed{\text{Do not search for the equation first.}}$$

Instead:

$$\boxed{\text{Search for the representation in which the governing law is simplest to discover.}}$$

Therefore, follow:

$$\boxed{
\begin{align}
\text{Representation} &\rightarrow \text{Structure}\\
&\rightarrow \text{Parameters}\\
&\rightarrow \text{Validation}
\end{align}
}$$

rather than forcing:

$$\boxed{
\begin{align}
\text{Data} &\rightarrow \text{Differentiation}\\
&\rightarrow \text{ODE}
\end{align}
}$$

---

# 20. FINAL DECISION RULE

Given candidate representations $R_1, \ldots, R_m$, select:

$$R^* = \arg\min_R \left[ E_{\mathrm{validated}} + \lambda \, C_{\mathrm{structure}} + \mu \, C_{\mathrm{parameters}} + \nu \, C_{\mathrm{assumptions}} + \rho \, C_{\mathrm{numerical}} \right]$$

subject to:

$$\text{Validity}(R) \geq \tau$$

and all known scientific and mathematical constraints.

### Final Criterion

The chosen model must be:

$$\boxed{
\begin{align}
&\text{SIMPLE} \quad + \\
&\text{DEFENSIBLE} \quad + \\
&\text{IDENTIFIABLE} \quad + \\
&\text{GENERALIZABLE}
\end{align}
}$$

**not merely accurate on the observed data.**

---

# Compact Workflow

```
┌──────────────────────────────────────────────────┐
│                     INPUT                        │
│  Data, physics, constraints, prior knowledge     │
└────────────────────┬─────────────────────────────┘
                     ↓
┌──────────────────────────────────────────────────┐
│                   DIAGNOSIS                      │
│  Noise, smoothness, memory, derivative stability │
└────────────────────┬─────────────────────────────┘
                     ↓
┌──────────────────────────────────────────────────┐
│          REPRESENTATION DISCOVERY                │
│  ├─ Differential (ODE, PDE)                      │
│  ├─ Integral (Fredholm, Volterra)                │
│  ├─ Integro-Differential                         │
│  └─ Discrete (Recurrence)                        │
└────────────────────┬─────────────────────────────┘
                     ↓
┌──────────────────────────────────────────────────┐
│          REPRESENTATION SCORING                  │
│  S(R) = E + C + I + U + G  (lower is better)    │
└────────────────────┬─────────────────────────────┘
                     ↓
┌──────────────────────────────────────────────────┐
│           STRUCTURE SEARCH                       │
│  ├─ Constant / Linear / Separable                │
│  ├─ Sparse / Low-Rank / Polynomial               │
│  ├─ Convolution / Volterra / Symmetry            │
│  └─ Known Physical Forms                         │
└────────────────────┬─────────────────────────────┘
                     ↓
┌──────────────────────────────────────────────────┐
│           PARAMETER SEARCH                       │
│  Linear regression → Nonlinear LS → Bayesian    │
└────────────────────┬─────────────────────────────┘
                     ↓
┌──────────────────────────────────────────────────┐
│      REDUCTION / SIMPLIFICATION                  │
│  Integral-to-algebra, kernel factorization       │
└────────────────────┬─────────────────────────────┘
                     ↓
┌──────────────────────────────────────────────────┐
│           VALIDATION                             │
│  Held-out, extrapolation, conservation laws      │
└────────────────────┬─────────────────────────────┘
                     ↓
┌──────────────────────────────────────────────────┐
│            CRITIC                                │
│  Try to invalidate model, identify weak points   │
└─┬──────────────────────────────────────────────┬─┘
  │ Model passes all checks?                     │
  │ NO ↓                                          │ YES ↓
  └────────────────────────────────────────────────┘
                     ↓                            ↓
           ┌─────────────────┐      ┌──────────────────────┐
           │ SEARCH-SPACE    │      │ STOP / OUTPUT        │
           │ UPDATE          │      │ FINAL MODEL          │
           │ Try different   │      └──────────────────────┘
           │ representation/ │
           │ structure       │
           └────────┬────────┘
                    ↓
          REPRESENTATION SWITCH
                    ↓
            [loop back or continue]
```

---

# Quick Reference Cards

## Integral Advantage Checklist

- [ ] Derivatives are noisy/unreliable?
- [ ] Process is naturally cumulative?
- [ ] Memory effects present?
- [ ] Green-function structure available?
- [ ] Kernel is separable or low-rank?
- [ ] Convolution structure evident?
- [ ] Volterra (causal) structure present?
- [ ] Integral form reduces search complexity?

**If 2+ boxes checked → Prioritize integral representation**

## Stop Checklist

- [ ] Model passes held-out validation?
- [ ] Parameters are identifiable?
- [ ] Complexity is justified?
- [ ] Residuals are unstructured (white noise)?
- [ ] Conservation laws satisfied?
- [ ] Further search shows diminishing returns?

**If all boxes checked → STOP and report result**

## Output Checklist

- [ ] Representation type clearly stated
- [ ] Final equation in symbolic form
- [ ] All parameters listed with uncertainty
- [ ] Structure explained (sparse/separable/etc.)
- [ ] Evidence and assumptions documented
- [ ] Validation results reported
- [ ] Limitations and alternatives listed
- [ ] Code/data provided if applicable

**All items complete → Ready for publication/use**

---

*Version 5.0.0 — Last Updated: 2026*
