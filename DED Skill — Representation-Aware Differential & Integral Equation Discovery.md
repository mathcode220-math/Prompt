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

The objective is not curve fitting.

The objective is to discover the simplest defensible governing law.

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

- time-series data,
- spatial-temporal data,
- multiple trajectories,
- control/input variables,
- initial conditions,
- boundary conditions,
- derivatives if experimentally available,
- physical laws,
- conservation relations,
- known symmetries,
- dimensional information,
- prior candidate equations,
- qualitative observations,
- measurement uncertainty.

Identify:

- dependent variables,
- independent variables,
- inputs,
- states,
- observed quantities,
- hidden quantities,
- units,
- sampling structure,
- experimental conditions,
- uncertainty.

Never assume unobserved quantities exist unless they are introduced explicitly as latent variables or justified by prior knowledge.

---

# 2. DIAGNOSIS

Before symbolic discovery, diagnose the data.

Estimate:

- noise level,
- sampling density,
- missingness,
- smoothness,
- stationarity,
- scale separation,
- repeated trajectories,
- transient versus steady-state regions,
- possible delays,
- possible memory effects,
- derivative reliability,
- integral stability,
- boundary or initial-condition information.

Determine whether the data appear primarily:

- local,
- cumulative,
- history-dependent,
- delayed,
- conservative,
- dissipative,
- periodic,
- multiscale,
- stochastic,
- spatially coupled,
- or nonstationary.

## Derivative Reliability Test

Do not automatically differentiate noisy data.

Estimate whether:

\[
y'(t),\; y''(t),\ldots
\]

can be recovered with sufficient stability.

If differentiation is unstable or amplifies noise substantially, prioritize integral formulations.

## Memory Test

Test whether:

\[
y(t)
\]

depends materially on earlier states or inputs.

Evidence for memory should increase the priority of:

\[
y(t)=f(t)+\int K(t,s)y(s)\,ds
\]

or more general history-dependent models.

---

# 3. REPRESENTATION DISCOVERY

This is the central stage.

Do not begin by assuming:

\[
\dot y = F(t,y).
\]

Instead construct and compare mathematically justified representations.

Generate candidates from:

## 3.1 Differential Form

\[
D[y]=F(t,y,u,\theta)
\]

including:

- ODE,
- PDE,
- higher-order equations,
- coupled systems.

## 3.2 Integral Form

Use exact or formally equivalent transformations when justified.

For example:

\[
\dot y(t)=F(t,y(t))
\]

may yield:

\[
y(t)=y(t_0)+\int_{t_0}^{t}F(s,y(s))\,ds.
\]

## 3.3 Linear Integral Form

Search for:

\[
y(t)=f(t)+\int_a^b K(t,s)y(s)\,ds.
\]

## 3.4 Volterra Form

Search for:

\[
y(t)=f(t)+\int_{t_0}^{t}K(t,s)y(s)\,ds.
\]

This form is especially important when causality or memory is present.

## 3.5 Integro-Differential Form

Permit:

\[
D[y](t)=F\left(t,y(t),\int K(t,s)y(s)\,ds\right).
\]

Use this only when evidence supports both local and historical effects.

## 3.6 Discrete Form

For discrete or poorly sampled systems consider:

\[
y_{k+1}=F(k,y_k,u_k).
\]

Do not force continuous-time structure when the observations do not justify it.

---

# 4. REPRESENTATION SCORING

Each representation must be evaluated before committing to symbolic search.

Use a conceptual score such as:

\[
S(R)=
E(R)+C(R)+I(R)+U(R)+G(R)
\]

where:

- \(E\): empirical error,
- \(C\): structural complexity,
- \(I\): identifiability difficulty,
- \(U\): numerical instability,
- \(G\): generalization risk.

Lower is better.

The exact scoring formula may vary by problem.

Prefer a representation that:

- requires fewer assumptions,
- has fewer active terms,
- uses fewer parameters,
- is numerically stable,
- is easier to validate,
- and exposes meaningful structure.

Do not select a representation using fit error alone.

---

# 5. INTEGRAL ADVANTAGE TEST

An integral representation receives higher priority when one or more of the following holds:

### A. Derivative instability

Differentiation amplifies measurement noise or produces unreliable derivatives.

### B. Cumulative dynamics

The physical or mathematical process is naturally cumulative.

### C. Memory

The current state depends on historical values.

### D. Green-function structure

A differential operator can be transformed into a useful kernel representation.

### E. Low-rank kernel structure

The kernel is exactly or approximately separable:

\[
K(t,s)\approx
\sum_{i=1}^{r}u_i(t)v_i(s),
\qquad r\ll n.
\]

### F. Convolution structure

The kernel depends primarily on the lag:

\[
K(t,s)=k(t-s).
\]

### G. Volterra structure

The causal domain:

\[
s\le t
\]

induces useful triangular structure.

### H. Integral representation substantially reduces search complexity

Use the integral form when symbolic discovery becomes simpler even when both forms are mathematically equivalent.

---

# 6. KERNEL DISCOVERY

For integral models, do not search over arbitrary functions first.

Use a structured kernel grammar.

Priority candidates include:

\[
K(t,s)=1
\]

\[
K(t,s)=t,\quad s,\quad t-s
\]

\[
K(t,s)=u(t)v(s)
\]

\[
K(t,s)=\sum_i u_i(t)v_i(s)
\]

\[
K(t,s)=k(t-s)
\]

and simple families such as:

\[
e^{-\lambda(t-s)},
\qquad
(t-s)^p,
\qquad
\sin(\omega(t-s)),
\qquad
\cos(\omega(t-s)).
\]

Expand the kernel grammar only when evidence requires it.

---

# 7. STRUCTURE SEARCH

After representation selection, search for the simplest structural form.

Priority order:

1. zero/constant structure,
2. linear structure,
3. separable structure,
4. sparse structure,
5. low-rank structure,
6. polynomial structure,
7. convolution structure,
8. symmetry/invariance structure,
9. known physical forms,
10. nonlinear composite structure,
11. unrestricted symbolic forms only as a last resort.

For integral equations explicitly test:

- separability,
- low rank,
- convolution,
- Volterra causality,
- symmetry,
- antisymmetry,
- triangular structure,
- known Green kernels,
- smoothness,
- locality,
- compact support.

---

# 8. PARAMETER SEARCH

Once structure is chosen, estimate parameters.

Prefer:

- linear regression when applicable,
- constrained regression,
- sparse regression,
- nonlinear least squares,
- robust regression under noise,
- Bayesian estimation when uncertainty matters.

Do not perform unrestricted symbolic search and parameter fitting simultaneously unless necessary.

Separate:

\[
\text{structure discovery}
\]

from:

\[
\text{parameter estimation}.
\]

---

# 9. INTEGRAL-TO-ALGEBRA REDUCTION

Whenever an integral kernel is separable or low rank, reduce the problem.

Given:

\[
y(t)=f(t)+
\int K(t,s)y(s)\,ds
\]

and

\[
K(t,s)=
\sum_{i=1}^{r}u_i(t)v_i(s),
\]

define:

\[
c_i=
\int v_i(s)y(s)\,ds.
\]

Then:

\[
y(t)=f(t)+
\sum_{i=1}^{r}u_i(t)c_i.
\]

Substitution should reduce the original functional problem to a finite-dimensional system whenever possible.

This reduction is strongly preferred over generic iterative solution when it is exact or demonstrably accurate.

---

# 10. EQUIVALENCE TEST

When two models have different mathematical forms, test whether they are equivalent.

Examples:

\[
\dot y=F(t,y)
\]

versus

\[
y(t)=y_0+\int_{t_0}^{t}F(s,y(s))\,ds.
\]

Do not treat equivalent representations as independent scientific discoveries.

Instead ask:

- Which form is easier to discover?
- Which form is more stable under noise?
- Which form is easier to validate?
- Which form is more interpretable?
- Which form reveals additional structure?
- Which form generalizes better?

---

# 11. VALIDATION

Validation must test more than training fit.

Evaluate:

- held-out trajectories,
- future prediction,
- parameter stability,
- perturbation robustness,
- residual structure,
- physical consistency,
- dimensional consistency,
- conservation laws,
- symmetry,
- stability,
- extrapolation,
- sensitivity to noise.

For integral models additionally evaluate:

- kernel identifiability,
- discretization sensitivity,
- quadrature sensitivity,
- kernel approximation error,
- dependence on the integration domain.

For differential models additionally evaluate:

- derivative-estimation sensitivity,
- discretization sensitivity,
- sensitivity to numerical differentiation.

---

# 12. MODEL COMPARISON

When multiple representations survive validation, compare them explicitly.

Prefer the model minimizing:

\[
\text{Total Complexity}
=
\text{Structural Complexity}
+
\text{Parameter Complexity}
+
\text{Assumption Complexity}
+
\text{Numerical Complexity}.
\]

Do not choose a more complicated integral model merely because it has slightly lower residual error.

Do not choose an ODE merely because the task was initially called "differential equation discovery."

---

# 13. CRITIC

The critic must actively try to invalidate the current model.

Ask:

- Is the model only fitting noise?
- Are parameters identifiable?
- Are hidden assumptions unsupported?
- Is the selected representation unnecessarily restrictive?
- Is there an equally good simpler representation?
- Did differentiation create artificial structure?
- Did integration hide important local dynamics?
- Is an apparent memory kernel actually an artifact of sampling?
- Is low-rank structure genuine or merely overfitted?
- Does the model fail under perturbation?
- Does the model violate known constraints?

The critic may trigger a return to:

- diagnosis,
- representation discovery,
- structure search,
- parameter search.

---

# 14. SEARCH-SPACE UPDATE

Search should be adaptive.

If a candidate fails, identify the failure type.

Examples:

- derivative instability → increase integral-form priority,
- missing memory → expand kernel search,
- poor locality → test integral or delay structure,
- excessive nonlinearity → test transformation or integral form,
- residual convolution pattern → test convolution kernels,
- repeated low-dimensional behavior → test low-rank structure,
- boundary-driven behavior → test Green-function formulation.

Do not simply enlarge the symbolic grammar after every failure.

Expand only the part of the search space implicated by evidence.

---

# 15. COMPLEXITY LADDER

Use progressive complexity.

### Level 0

Constants and trivial dynamics.

### Level 1

Simple linear ODEs and simple integral relations.

### Level 2

Sparse linear combinations.

### Level 3

Separable and low-rank integral kernels.

### Level 4

Convolution and Volterra structures.

### Level 5

Simple nonlinear dynamics.

### Level 6

Integro-differential and memory models.

### Level 7

General symbolic nonlinear models.

### Level 8

Unrestricted or highly complex discovery.

Stop as soon as a model is defensible.

Do not continue searching merely because a more complex model can reduce residual error.

---

# 16. REPRESENTATION SWITCHING

At any stage, DED may switch representation.

Examples:

\[
ODE
\rightarrow
Integral
\]

if derivatives are unstable.

\[
Integral
\rightarrow
ODE
\]

if the kernel has a simple finite-dimensional realization.

\[
Integral
\rightarrow
Convolution
\]

if:

\[
K(t,s)\approx k(t-s).
\]

\[
Convolution
\rightarrow
Finite\text{-}dimensional\ state
\]

if the kernel has a simple realization.

The system should prefer representations that expose simpler governing structure.

---

# 17. STOP CONDITIONS

Stop when:

1. The model passes independent validation.
2. The structure is sufficiently identifiable.
3. Complexity is justified.
4. Residuals contain no strong unexplained structure.
5. Known constraints are satisfied.
6. Further search produces only marginal improvement or unjustified complexity.

If several models remain equally defensible, report the ambiguity rather than forcing a unique answer.

---

# 18. OUTPUT

Return:

## A. Discovered representation

State clearly whether the final model is:

- differential,
- integral,
- integro-differential,
- discrete,
- or another justified representation.

## B. Governing equation

Give the final equation in exact symbolic form.

## C. Equivalent forms

When useful, provide equivalent differential/integral forms.

## D. Structure

Explain the discovered structure:

- sparse,
- separable,
- low rank,
- convolution,
- Volterra,
- nonlinear,
- etc.

## E. Parameters

List estimated parameters and uncertainty when available.

## F. Evidence

State what observations support the model.

## G. Validation

Report predictive and structural validation results.

## H. Limitations

State what the data cannot establish.

## I. Alternatives

List only serious competing representations.

---

# 19. META-RULE

The fundamental rule of DED is:

\[
\boxed{
\text{Do not search for the equation first.}
}
\]

Instead:

\[
\boxed{
\text{Search for the representation in which the governing law is simplest to discover.}
}
\]

Therefore:

\[
\boxed{
\text{Representation}
\rightarrow
\text{Structure}
\rightarrow
\text{Parameters}
\rightarrow
\text{Validation}
}
\]

rather than forcing:

\[
\boxed{
\text{Data}
\rightarrow
\text{Differentiation}
\rightarrow
\text{ODE}
}
\]

---

# 20. FINAL DECISION RULE

Given candidate representations \(R_1,\ldots,R_m\), select:

\[
R^*=
\arg\min_R
\left[
E_{\mathrm{validated}}
+
\lambda C_{\mathrm{structure}}
+
\mu C_{\mathrm{parameters}}
+
\nu C_{\mathrm{assumptions}}
+
\rho C_{\mathrm{numerical}}
\right]
\]

subject to:

\[
\text{Validity}(R)\geq \tau
\]

and all known scientific and mathematical constraints.

The chosen model must be:

\[
\boxed{
\text{simple}
+
\text{defensible}
+
\text{identifiable}
+
\text{generalizable}
}
\]

not merely accurate on the observed data.

---

# Compact Workflow

```text
INPUT
  ↓
DIAGNOSIS
  ↓
REPRESENTATION DISCOVERY
  ├── Differential
  ├── Integral
  ├── Integro-Differential
  └── Discrete
  ↓
REPRESENTATION SCORING
  ↓
STRUCTURE SEARCH
  ├── Sparse
  ├── Separable
  ├── Low-Rank
  ├── Convolution
  ├── Volterra
  └── Nonlinear
  ↓
PARAMETER SEARCH
  ↓
REDUCTION / SIMPLIFICATION
  ↓
VALIDATION
  ↓
CRITIC
  ↓
SEARCH-SPACE UPDATE
  ↓
REPRESENTATION SWITCH
  ↓
STOP / CONTINUE
  ↓
FINAL DEFENSIBLE MODEL
```