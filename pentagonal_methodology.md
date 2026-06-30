# The Pentagonal Methodology: A Five-Step Framework for Building Failure-Proof AI Prompts

## Introduction

Random prompts fail because they are "wishes" not "engineering." This methodology is the cure: instead of writing one prompt for everything, we build a **specialized assistant mind** for each problem.

---

## 🧪 Practical Application: The "Black Box" Puzzle (from Simon Tatham)

### Step 1: Problem Space Diagnosis

| Question | Answer | Impact |
|----------|--------|--------|
| **Nature of Information** | Incomplete — hidden balls inside a box | Cannot be solved by pure deduction alone |
| **Presence of Opponent** | No opponent — nature is static | No need to predict "reaction" |
| **Certainty in Solution** | Single solution (ball positions are fixed) | Goal is clear, path is unclear |

**Classification:** **Exploratory Closed Problem** — We need an "experimental world" that designs experiments (firing rays) to explore a fixed truth.

---

### Step 2: Mental Model Selection

> **"You are an experimental physicist facing a black box. Inside are stationary metal balls. You cannot see them. You fire laser beams from edge ports and observe which port they exit. Your task: deduce the ball positions."**

This model provides:
- **Boldness:** It experiments (fires rays).
- **Caution:** It does not claim to see what it cannot see.
- **Logic:** Every deduction is based on "What if the ball were here?"

---

### Step 3: Building Thinking Stages

```
1. Representation:
   - Draw the grid: 8×8 box, ports on edges.
   - ■ Given certainty: "I fired a ray from top-north, it exited from middle-east."
   - ⚠️ Possibility: "The ball may be at (3,3) or (3,4)."

2. Exploit Certainty:
   - If the ray exits from the same port it entered → immediate reflection → ball in adjacent square.
   - □ Deduction: "Square (1,2) contains a ball."
   - Repeat: Does this eliminate other possibilities?

3. Handle Uncertainty:
   - Next ray: From which port do we fire?
   - Hypotheses: "If the ball is at A, it will exit from X. If at B, it will exit from Y."
   - Experiment: Fire a ray that distinguishes between A and B.
   - Criterion: Maximum information, minimum risk.

4. Act & Update:
   - Ray exited from Z → Hypothesis A is falsified.
   - ⚠️ Delete A. □ Keep B.
   - Return to Step 2.

5. Documentation:
   - ■ "Ball at (3,3)" — proven by two independent experiments.
   - ⚠️ "Ball at (5,5)" — single hypothesis only, needs confirmation.
```

---

### Step 4: Checkpoints and Catastrophe Prevention

| Checkpoint | How It Prevents Failure |
|------------|------------------------|
| **"Do not proceed before completing the previous"** | Prevents: "I assumed a ball at (3,3) and built 5 deductions on it" — then it turns out to be at (4,3). |
| **"Contradiction Detection"** | If the ray says (3,3) is empty, but previous deduction says it's full → stop, review. |
| **"Do not treat hypothesis as certain"** | ⚠️ remains ⚠️ until two independent experiments confirm it. |
| **"Minimax at Impasse"** | If all ports are exhausted and no new experiment, choose the ray that gives information even if it doesn't lead to full discovery. |

---

### Step 5: Linguistic Adaptation

> **"Fire a ray from [location]. Predict its exit based on every known ■. If the prediction is violated, ⚠️ the responsible hypothesis. Do not fire a second ray before updating the model."**

---

## ⚠️ How Would This Methodology Have Prevented Previous "Failures"?

| Failure Type | Cause | How the Methodology Prevents It |
|--------------|-------|--------------------------------|
| **Hallucination** | Model guesses ball positions | Step 1: Information is incomplete → claiming without experiment is not allowed |
| **Jumping** | "Therefore the ball is here" without justification | Step 3: Every □ must be built on ■ |
| **Building on Sand** | Hypothesis → 10 deductions → hypothesis is wrong | Step 4: ⚠️ Do not build □ on it |
| **Forgetting** | Forgetting that a deduction was exhausted | Step 5: Documentation forces review |
| **Impasse** | Doesn't know what to do next | Step 3: "Design an experiment" — there is always a next step |

---

## 🎯 Conclusion: Why This Methodology Is the Solution

> **Ordinary Prompt = "Analyze"**  
> **Methodology = "Build a world that analyzes"**

The difference is significant:
- A general prompt gives **instructions**.
- The methodology gives **an algorithm for building instructions**.

This means that even if you encounter a **problem we have never seen before**, you can apply the five steps and get a prompt that **does not fail** — because it is built on problem diagnosis, not on memorizing templates.

---

## 🔁 Apply This Methodology to Other Problems

You can use this framework for any problem type:

- **Chess** (smart opponent, complete information, multiple solutions) → "Strategic Accountant" model
- **Engineering System Design** (no absolute correct solution, trade-offs) → "Solutions Engineer" model
- **Complex Logic Puzzle** (complete information, single solution) → "Logical Mathematician" model
- **Negotiation Scenario** (dynamic opponent, incomplete information) → "Tactical Negotiator" model
- **Creative Writing** (open-ended, subjective quality) → "Narrative Architect" model

---

## 📋 Quick Reference Checklist

### Before Writing Any Prompt:

1. ✅ **Diagnose the Problem Space**
   - What is the nature of information? (Complete/Incomplete)
   - Is there an opponent? (Yes/No)
   - What is the certainty level? (Single/Multiple solutions)

2. ✅ **Select the Mental Model**
   - What persona fits this problem?
   - What attitudes does it need? (Boldness, Caution, Logic)

3. ✅ **Build Thinking Stages**
   - Define representation symbols (■, □, ⚠️)
   - Create sequential reasoning steps
   - Establish update mechanisms

4. ✅ **Set Checkpoints**
   - What prevents jumping ahead?
   - How are contradictions detected?
   - When is a hypothesis considered certain?

5. ✅ **Adapt the Language**
   - Create specific action commands
   - Enforce sequential execution
   - Mandate documentation

---

*This methodology transforms prompt engineering from guesswork into a systematic discipline.*
