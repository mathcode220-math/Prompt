# 🔬 Scientific Research Methodology for AI
## A Pentagonal Framework for Rigorous, Reproducible, and Insightful Research Assistance

---

## ⚠️ The Problem: Why Generic Research Prompts Fail

| Failure Mode | Cause | Consequence |
|---|---|---|
| **Hallucinated Citations** | Model invents papers that don't exist | Wasted hours searching for non-existent sources |
| **Methodological Flaws** | Skips critical experimental design steps | Invalid conclusions, irreproducible results |
| **Confirmation Bias** | cherry-picks evidence supporting hypothesis | Misses contradictory data, flawed analysis |
| **Overgeneralization** | Extrapolates beyond data scope | Misleading conclusions, poor peer review |
| **Citation Amnesia** | Forgets which sources said what | Inconsistent references, academic integrity issues |

**Root Cause:** Generic prompts like "analyze this topic" treat research as **text generation** rather than **knowledge construction**.

---

## 🎯 The Solution: The Researcher's Pentagonal Framework

### Step 1: Problem Space Diagnosis

| Question | Answer | Impact on Protocol |
|---|---|---|
| **Nature of Information** | Partial, evolving, peer-reviewed | Requires source verification at every step |
| **Presence of Adversary** | Yes: competing hypotheses, reviewer scrutiny | Must anticipate counter-arguments |
| **Certainty in Solution** | Probabilistic, confidence intervals | Never claim absolute truth, always quantify uncertainty |
| **Domain Specificity** | High: methods vary by field | Customize methodology per discipline |
| **Reproducibility Requirement** | Critical: others must replicate | Document every assumption and parameter |

**Classification:** **Adversarial Knowledge Construction** — Building defensible claims under scrutiny with incomplete information.

---

### Step 2: Mental Model Selection

> **"You are a Senior Peer Reviewer turned Research Collaborator. You have published 50+ papers, rejected 200+ flawed manuscripts, and know exactly how studies fail. Your job: construct bulletproof arguments while actively trying to demolish your own hypotheses before anyone else does."**

This model provides:
- **Rigor:** Tests every claim against strongest counter-arguments
- **Humility:** Quantifies uncertainty, avoids overclaiming
- **Systematicity:** Follows established methodological pipelines
- **Anticipation:** Pre-empts reviewer criticisms

---

### Step 3: Building Thinking Stages (The 5-Phase Research Protocol)

```
PHASE 1: LITERATURE MAPPING (■ Known Sources)
├─ Identify seminal papers (≥1000 citations)
├─ Find recent reviews (last 3 years)
├─ Map conflicting findings
├─ ■ Record: Author, Year, Journal, DOI, Key Finding
└─ ⚠️ Flag: Unverified claims, paywalled data

PHASE 2: HYPOTHESIS FORMULATION (□ Logical Derivation)
├─ State null hypothesis (H₀) clearly
├─ State alternative hypothesis (H₁)
├─ Define operational variables
├─ □ Derive: If H₁ true → predict X observable
└─ ⚠️ Constraint: Falsifiability requirement

PHASE 3: METHODOLOGY DESIGN (■ Established Methods)
├─ Select gold-standard methods for domain
├─ Calculate statistical power (minimum 80%)
├─ Define inclusion/exclusion criteria
├─ ■ Document: Sample size, controls, blinding
└─ ⚠️ Check: Confounding variables addressed?

PHASE 4: CRITICAL ANALYSIS (⚠️ Uncertainty Quantification)
├─ Run sensitivity analyses
├─ Test robustness to assumptions
├─ Calculate confidence intervals (95% CI)
├─ ⚠️ Report: Effect sizes, p-values, limitations
└─ □ Conclude: Only what data supports

PHASE 5: SYNTHESIS & DOCUMENTATION (■ Verified Claims)
├─ ■ Claim: Supported by ≥2 independent sources
├─ ⚠️ Speculation: Clearly labeled, not in abstract
├─ □ Citation: Every claim traced to source
└─ 📝 Output: Structured abstract, full references
```

---

### Step 4: Checkpoints and Catastrophe Prevention

| Checkpoint | Prevents | Enforcement Rule |
|---|---|---|
| **"No Citation Without DOI"** | Hallucinated references | Reject any citation lacking verifiable identifier |
| **"Correlation ≠ Causation"** | Overinterpretation | Flag causal language unless RCT or strong quasi-experimental design |
| **"Sample Size Justification"** | Underpowered studies | Require power analysis before accepting methodology |
| **"Limitations Section Mandatory"** | Overgeneralization | Cannot conclude without explicit limitations paragraph |
| **"Alternative Hypotheses Tested"** | Confirmation bias | Must address ≥2 competing explanations |
| **"Data Availability Statement"** | Irreproducibility | Specify where raw data/code would be deposited |

---

### Step 5: Linguistic Adaptation

**Precision Language Rules:**
- ✅ "suggests" (p < 0.05) / "strongly indicates" (p < 0.01) / "demonstrates" (p < 0.001 + replication)
- ❌ NEVER: "proves", "undoubtedly", "clearly shows" (unless mathematical proof)
- ⚠️ Always: "in our sample", "under these conditions", "pending replication"
- ■ Citation format: `(Author et al., Year, DOI)` — never vague "studies show"

**Uncertainty Calibration:**
- High confidence (■): Meta-analysis consensus, n > 10,000
- Medium confidence (□): Single well-powered RCT, consistent mechanisms
- Low confidence (⚠️): Preliminary findings, small samples, observational only

---

## 🧪 Applied Example: Climate Change Impact on Coral Reefs

### THINKING PROTOCOL FOR THIS QUERY:

```
1. LITERATURE MAP:
   ■ Hoegh-Guldberg (1999, Science, DOI:10.1126/science.284.5411.149) — thermal stress threshold
   ■ Hughes (2017, Nature, DOI:10.1038/nature21707) — 2016 bleaching event
   ⚠️ Conflicting: Some reefs show adaptation (Palumbi 2014) vs. universal decline (Hughes 2018)

2. HYPOTHESIS:
   □ If ocean warming >1.5°C → >90% coral mortality predicted
   H₀: No significant relationship between temperature anomaly and bleaching severity
   H₁: Positive correlation, threshold effect at +1°C above summer max

3. METHODOLOGY:
   ■ Satellite SST data (NOAA Coral Reef Watch)
   ■ In-situ bleaching surveys (AGRRA protocol)
   ■ Statistical: Generalized linear mixed models, reef as random effect
   ⚠️ Control: Local stressors (pollution, overfishing) included as covariates

4. CRITICAL ANALYSIS:
   ⚠️ Uncertainty: Regional variation ±15%, adaptation potential unknown
   ⚠️ Limitation: Observational data cannot prove causation alone
   □ Robustness: Result holds across 5 independent datasets

5. SYNTHESIS:
   ■ Conclusion: Strong evidence for temperature-driven bleaching (p<0.001)
   ⚠️ Caveat: Adaptive capacity may modify trajectory
   📝 Recommendation: Urgent emissions reduction + local management
```

---

## 📋 Quick Reference: Research Prompt Template

```markdown
RESEARCH QUERY: [Your specific question]

DOMAIN: [Field + subfield]
TIMELINE: [Recent 5 years? Historical?]
DEPTH: [Review article depth? Primary research depth?]

CONSTRAINTS:
- Only peer-reviewed sources (no preprints unless specified)
- Include DOIs for all citations
- Quantify uncertainty for each claim
- Address counter-arguments explicitly

OUTPUT STRUCTURE:
1. Executive Summary (3 sentences, key finding)
2. Literature Map (seminal + recent papers)
3. Methodology Assessment (strengths/weaknesses)
4. Confidence-Calibrated Conclusions
5. Limitations & Future Directions
6. Full References (APA/MLA/Chicago style)

CHECKPOINTS BEFORE OUTPUT:
□ All citations verified with DOI?
□ Correlation/causation language appropriate?
□ Sample sizes and power discussed?
□ Alternative hypotheses addressed?
□ Limitations section included?
```

---

## 🎯 Specialized Protocols by Discipline

### Biomedical Research
```
ADDITIONAL CHECKPOINTS:
- CONSORT/PRISMA guidelines followed?
- IRB approval mentioned for human subjects?
- Conflict of interest disclosed?
- Clinical trial registration number provided?
```

### Social Sciences
```
ADDITIONAL CHECKPOINTS:
- Sampling strategy justified (probability vs. convenience)?
- Measurement validity/reliability reported?
- Cultural bias addressed?
- Qualitative: Saturation achieved? Quantitative: Power analysis?
```

### Physical Sciences
```
ADDITIONAL CHECKPOINTS:
- Error propagation calculated?
- Instrument calibration described?
- Raw data availability statement?
- Computational methods: Code repository linked?
```

### Humanities
```
ADDITIONAL CHECKPOINTS:
- Primary sources distinguished from secondary?
- Translation issues acknowledged?
- Historiographical context provided?
- Interpretive framework made explicit?
```

---

## 🛡️ Anti-Failure Mechanisms

| Failure | Prevention Mechanism |
|---|---|
| Fake citations | DOI requirement + cross-reference check |
| P-hacking encouragement | Require pre-registration discussion, multiple testing correction |
| Publication bias | Search for unpublished/null results, mention file drawer problem |
| Outdated info | Filter by publication date, flag seminal older papers separately |
| Jargon misuse | Define technical terms, check against field glossaries |
| Ethical oversights | Mandatory ethics checklist per domain |

---

## 💡 Pro Tips for Research Prompts

1. **Specify the Review Type:**
   - "Systematic review protocol" vs. "Narrative overview"
   - Different standards for each

2. **Request Confidence Scores:**
   - "Rate each claim: High/Medium/Low confidence with justification"

3. **Ask for Contradictory Evidence:**
   - "What would falsify this hypothesis?"
   - "List top 3 competing theories"

4. **Demand Reproducibility Info:**
   - "What parameters would another researcher need to replicate this?"

5. **Use Iterative Refinement:**
   - First pass: Literature map
   - Second pass: Deep dive on 3 key papers
   - Third pass: Synthesis with critique

---

## 📊 Quality Metrics for Research Output

Before accepting AI-generated research assistance, verify:

| Metric | Threshold | How to Check |
|---|---|---|
| **Citation Accuracy** | 100% verifiable DOIs | Random sample 5 citations, search DOI |
| **Uncertainty Calibration** | All claims have confidence level | Scan for hedging language, CI mentions |
| **Methodological Rigor** | Power analysis or equivalent | Look for sample size justification |
| **Balance** | Counter-arguments represented | Check if opposing views get ≥20% space |
| **Recency** | ≥50% sources from last 5 years | Calculate publication date distribution |
| **Reproducibility** | Methods described in detail | Could you replicate based on description? |

---

## 🚀 Advanced: Meta-Research Prompt

For evaluating research quality itself:

```
"You are a Methodologist specializing in [FIELD]. Critique this study design:

STUDY: [Description]

EVALUATE:
1. Internal Validity: Threats and controls
2. External Validity: Generalizability limits
3. Construct Validity: Measurement appropriateness
4. Statistical Conclusion Validity: Power, assumptions, corrections
5. Ethical Compliance: IRB, consent, data protection

OUTPUT:
- Fatal flaws (must fix before proceeding)
- Major weaknesses (address in discussion)
- Minor issues (note for transparency)
- Strengths worth highlighting

FORMAT: Traffic light system (🔴 Stop, 🟡 Caution, 🟢 Go)"
```

---

## 🏁 Final Checklist Before Publishing AI-Assisted Research

□ **Every factual claim** has a traceable citation  
□ **All statistics** include confidence intervals or error margins  
□ **Limitations section** is substantive, not performative  
□ **Competing hypotheses** are fairly represented  
□ **Methods** are described with enough detail for replication  
□ **Language** matches certainty level (no overclaiming)  
□ **Ethics** considerations addressed where applicable  
□ **Data availability** statement included  
□ **Conflicts of interest** disclosed  
□ **Peer review simulation**: What would Reviewer #2 say?  

---

*Remember: AI is a research **assistant**, not a co-author. Ultimate responsibility for accuracy, ethics, and interpretation rests with the human researcher.*
