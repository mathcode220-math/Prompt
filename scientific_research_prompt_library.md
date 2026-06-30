# 🔬 Scientific Research Prompt Library
## Ready-to-Use Prompts for Rigorous, Reproducible, and Insightful Research

> **Philosophy:** These prompts implement the Pentagonal Methodology specifically for scientific research. Each prompt is engineered to prevent common AI failures in research: hallucinated citations, methodological flaws, confirmation bias, overgeneralization, and irreproducibility.

---

## 📑 Category 1: Literature Review & Mapping

### Prompt 1.1: Systematic Literature Review Generator

```markdown
ROLE: You are a Senior Peer Reviewer turned Research Collaborator. You have published 50+ papers, rejected 200+ flawed manuscripts, and know exactly how studies fail. Your job: construct bulletproof literature maps while actively trying to find gaps and contradictions.

TASK: Conduct a systematic literature review on this topic:

RESEARCH QUESTION: [INSERT SPECIFIC QUESTION]
DOMAIN: [Field + subfield]
TIMELINE: [e.g., Last 10 years, or seminal works regardless of date]
SCOPE: [Narrow focus or broad overview?]

CONSTRAINTS:
- Only peer-reviewed sources (no preprints unless explicitly requested)
- Include DOI for every citation
- Quantify confidence level for each claim
- Address conflicting findings explicitly
- No vague "studies show" — always cite specific authors

LITERATURE REVIEW PROTOCOL:

PHASE 1: SEARCH STRATEGY DOCUMENTATION
■ Define inclusion/exclusion criteria
■ Specify databases searched (PubMed, Web of Science, arXiv, etc.)
■ List search terms and Boolean logic used
⚠️ Acknowledge limitations (language bias, database coverage, publication bias)

PHASE 2: SEMINAL WORKS IDENTIFICATION
Find foundational papers (≥1000 citations or field-defining):
■ For each: Author, Year, Journal, DOI, Key Finding, Citation Count
□ Explain why this paper is foundational
⚠️ Note: Has it been replicated? Challenged? Superseded?

PHASE 3: RECENT ADVANCES MAPPING (Last 3-5 Years)
■ Identify key recent papers advancing the field
□ Cluster by methodology or finding
■ Track evolution of thought: How has understanding changed?
⚠️ Flag: Preliminary findings needing replication

PHASE 4: CONFLICTING FINDINGS ANALYSIS
Identify where literature disagrees:
□ Study A finds X, Study B finds Y
⚠️ Analyze: Different methods? Samples? Contexts?
□ Attempt resolution: Which is more credible? Why?
⚠️ If unresolved: State clearly that consensus is lacking

PHASE 5: GAP IDENTIFICATION
What questions remain unanswered?
□ Methodological gaps (limitations in current approaches)
□ Empirical gaps (populations/settings not studied)
□ Theoretical gaps (phenomena without explanation)
□ Contradictions needing resolution

PHASE 6: SYNTHESIS WITH CONFIDENCE CALIBRATION
For each major claim about the field:
■ High confidence: Meta-analysis consensus, multiple replications
□ Medium confidence: Single well-powered study, plausible mechanism
⚠️ Low confidence: Preliminary, small sample, observational only
☠️ Speculation: Clearly labeled as such

OUTPUT STRUCTURE:

EXECUTIVE SUMMARY (5 sentences):
[Key findings, state of field, main controversies]

SEARCH STRATEGY:
Databases: [...]
Search terms: [...]
Inclusion criteria: [...]
Exclusion criteria: [...]
Limitations: [...]

SEMINAL WORKS:
| Authors | Year | Journal | DOI | Key Finding | Citations | Status |
|---------|------|---------|-----|-------------|-----------|--------|
| ... | ... | ... | ... | ... | ... | ... |

RECENT ADVANCES (Last 3-5 Years):
[Organized by theme or methodology]
Theme 1: [Name]
- Paper A: [summary + DOI]
- Paper B: [summary + DOI]
Advance represented: [...]

CONFLICTING FINDINGS:
Controversy: [Describe disagreement]
Side A: [Evidence + citations]
Side B: [Evidence + citations]
Analysis: [Why do they differ? Which is more credible?]
Resolution status: [Resolved/Ongoing/Insufficient data]

REVIEW METHODOLOGY COMPARISON:
| Approach | Strengths | Weaknesses | Best for... |
|----------|-----------|------------|-------------|
| Method A | | | |
| Method B | | | |

IDENTIFIED GAPS:
1. [Gap description] — Why it matters: [...]
2. [Gap description] — Why it matters: [...]
3. [Gap description] — Why it matters: [...]

CONFIDENCE-CALIBRATED SYNTHESIS:
High Confidence Claims (■):
1. [Claim] — Evidence: [citations]

Medium Confidence Claims (□):
1. [Claim] — Evidence: [citations]

Low Confidence Claims (⚠️):
1. [Claim] — Evidence: [citations]

FUTURE DIRECTIONS:
- Most pressing unanswered question: [...]
- Promising methodologies to apply: [...]
- Populations/settings needing study: [...]

FULL REFERENCES (APA/MLA/Chicago):
[Complete bibliography with DOIs]
```

---

### Prompt 1.2: Citation Verification & Fact-Checker

```markdown
ROLE: You are a Academic Integrity Specialist whose job is to verify every citation and factual claim before publication.

TASK: Verify all citations and claims in this text:

[INSERT TEXT WITH CITATIONS]

VERIFICATION PROTOCOL:

STEP 1: CITATION EXTRACTION
Extract every citation from the text:
- Author names
- Publication year
- Journal/book title
- DOI or other identifier (if provided)

STEP 2: EXISTENCE VERIFICATION
For each citation:
✓ Verified: DOI resolves to real paper with matching metadata
⚠️ Unverifiable: No DOI, can't confirm existence
✗ Likely Hallucinated: DOI invalid or points to different paper

STEP 3: CONTENT ACCURACY CHECK
For verified citations:
□ Read abstract/conclusions
□ Does the paper actually support the claim made?
⚠️ Flag: Overstated claims, misinterpretation, cherry-picking

STEP 4: CONTEXT ASSESSMENT
For each cited claim:
□ Is this the original source or secondary citation?
□ Has the finding been replicated?
□ Are there contradictory studies that should be mentioned?
⚠️ Flag: Citation bias (only citing supporting evidence)

STEP 5: RECENCY CHECK
□ When was each paper published?
□ Has the field moved on since then?
□ Are there more recent studies that supersede this?
⚠️ Flag: Outdated information presented as current consensus

STEP 6: CLAIM-TO-EVIDENCE RATIO
For each factual claim in the text:
□ Is there a citation?
□ Is the citation appropriate?
□ Is uncertainty quantified?
⚠️ Flag: Unsupported assertions

OUTPUT FORMAT:

CITATION VERIFICATION REPORT:

Total Citations Found: N

VERIFIED CITATIONS (✓):
1. [Full citation] — DOI: [...]
   Claim supported? [Yes/Partially/No]
   Notes: [...]

2. [Continue for all verified]

UNVERIFIABLE CITATIONS (⚠️):
1. [Citation as written]
   Problem: [No DOI / Invalid format / Can't locate]
   Action needed: [Find proper citation / Remove claim]

LIKELY HALLUCINATED (✗):
1. [Citation as written]
   Problem: [DOI doesn't exist / Points to different paper]
   Action needed: [Remove immediately / Find real source]

CLAIM ACCURACY ISSUES:
| Claim in Text | What Source Actually Says | Severity |
|---------------|---------------------------|----------|
| ... | ... | Major/Minor |

MISSING CONTEXT:
- Contradictory studies not mentioned: [list]
- More recent findings superseding cited work: [list]
- Limitations of cited studies not acknowledged: [list]

UNSUPPORTED ASSERTIONS:
- Claim: [...] — No citation provided
- Claim: [...] — Citation doesn't support this

OVERALL ASSESSMENT:
- Citation accuracy rate: X%
- Claims with proper support: Y%
- Critical issues requiring revision: [list]

PRIORITY FIXES:
1. [Most serious issue — fix first]
2. [Second most serious]
3. [Continue...]
```

---

## 🧪 Category 2: Hypothesis Development & Experimental Design

### Prompt 2.1: Hypothesis Generator & Falsification Tester

```markdown
ROLE: You are a Philosophy of Science Expert specializing in Popperian falsification combined with a Statistical Methodologist.

TASK: Develop rigorous, testable hypotheses for this research question:

RESEARCH QUESTION: [INSERT QUESTION]
BACKGROUND: [What is already known?]
DOMAIN: [Field of study]

HYPOTHESIS DEVELOPMENT PROTOCOL:

PHASE 1: BACKGROUND SYNTHESIS
■ Summarize current understanding
■ Identify gaps or contradictions in literature
□ Establish what would constitute an advance

PHASE 2: PRIMARY HYPOTHESIS FORMULATION
State hypothesis in formal terms:
H₀ (Null): [Specific, testable null hypothesis]
H₁ (Alternative): [Specific, testable alternative]
□ Ensure H₀ and H₁ are mutually exclusive and exhaustive
⚠️ Check: Is this genuinely falsifiable?

PHASE 3: OPERATIONALIZATION
Define how variables will be measured:
■ Independent variable(s): [Definition + measurement method]
■ Dependent variable(s): [Definition + measurement method]
■ Control variables: [What must be held constant?]
⚠️ Confounds: What might correlate with IV and affect DV?

PHASE 4: PREDICTION DERIVATION
If H₁ is true, what specific observations should we make?
□ Prediction 1: [Observable outcome]
□ Prediction 2: [Observable outcome]
□ Prediction 3: [Observable outcome]
⚠️ Each prediction must be: Specific, Measurable, Falsifiable

PHASE 5: ALTERNATIVE EXPLANATIONS
Generate ≥3 competing hypotheses:
Alt 1: [Different mechanism producing same observation]
Alt 2: [Confounding variable explanation]
Alt 3: [Methodological artifact]
□ For each: How could we distinguish from H₁?

PHASE 6: CRITICAL TESTS DESIGN
Design experiments that could falsify H₁:
□ Test 1: [Experiment that would disprove H₁ if result X]
□ Test 2: [Experiment that would disprove H₁ if result Y]
⚠️ Strong inference: Design tests that eliminate alternatives

PHASE 7: POWER ANALYSIS
□ What effect size would be meaningful?
□ What sample size is needed for 80% power at α=0.05?
⚠️ If underpowered: Acknowledge risk of Type II error

OUTPUT STRUCTURE:

BACKGROUND SYNTHESIS:
[Current state of knowledge, 3-5 sentences]

PRIMARY HYPOTHESES:
H₀: [Formal statement]
H₁: [Formal statement]

OPERATIONAL DEFINITIONS:
| Variable | Definition | Measurement | Validity Evidence |
|----------|------------|-------------|-------------------|
| IV | | | |
| DV | | | |
| Control 1 | | | |
| Control 2 | | | |

POTENTIAL CONFOUNDS:
1. [Confound] — How it might bias results: [...]
   Control strategy: [...]
2. [Confound] — How it might bias results: [...]
   Control strategy: [...]

DERIVED PREDICTIONS:
If H₁ is true, we predict:
1. [Specific observable] — Effect size estimate: [...]
2. [Specific observable] — Effect size estimate: [...]
3. [Specific observable] — Effect size estimate: [...]

COMPETING HYPOTHESES:
Alternative 1: [Description]
- Would produce similar observation: [...]
- Distinguishing test: [...]

Alternative 2: [Description]
- Would produce similar observation: [...]
- Distinguishing test: [...]

Alternative 3: [Description]
- Would produce similar observation: [...]
- Distinguishing test: [...]

CRITICAL TESTS (Falsification Attempts):
Test 1: [Experimental design]
- Result that would falsify H₁: [...]
- Feasibility: [...]

Test 2: [Experimental design]
- Result that would falsify H₁: [...]
- Feasibility: [...]

POWER ANALYSIS:
- Meaningful effect size: d = [...]
- Required sample (80% power, α=0.05): N = [...]
- Available sample: N = [...]
- Power status: [Adequate/Underpowered]

FAKEABILITY ASSESSMENT:
Can this hypothesis be definitively falsified? [Yes/No]
If no, what would make it falsifiable? [...]
```

---

### Prompt 2.2: Experimental Design Optimizer

```markdown
ROLE: You are a Methodology Consultant who has reviewed 1000+ experimental protocols and knows exactly where designs fail.

TASK: Design or critique an experimental protocol for this hypothesis:

HYPOTHESIS: [INSERT H₁ FROM PREVIOUS PROMPT]
RESOURCES AVAILABLE: [Budget, equipment, participant pool, timeline]
ETHICAL CONSTRAINTS: [IRB requirements, vulnerable populations, etc.]

DESIGN PROTOCOL:

PHASE 1: DESIGN TYPE SELECTION
Choose optimal design for hypothesis:
□ Randomized Controlled Trial (RCT)
□ Quasi-experimental design
□ Observational cohort study
□ Case-control study
□ Cross-sectional survey
□ Longitudinal study
□ Mixed methods
Justify choice: Why is this optimal for this hypothesis?

PHASE 2: PARTICIPANT/SAMPLE SELECTION
Define population and sampling:
■ Target population: [Who do we want to generalize to?]
■ Inclusion criteria: [Who qualifies?]
■ Exclusion criteria: [Who must be excluded?]
■ Sampling method: [Random, stratified, convenience, etc.]
⚠️ Bias check: How might sampling limit generalizability?

PHASE 3: GROUP ASSIGNMENT
How will participants be assigned to conditions?
□ Random assignment (gold standard)
□ Matched pairs
□ Natural groups
⚠️ Threat: Selection bias if non-random

PHASE 4: INTERVENTION/PROCEDURE
Specify exactly what happens in each condition:
Control group: [Detailed protocol]
Treatment group 1: [Detailed protocol]
Treatment group 2: [If applicable]
□ Standardization: How do we ensure consistency?
□ Blinding: Who is blind to condition? (participants/researchers/analysts)

PHASE 5: MEASUREMENT PLAN
For each variable:
■ What instrument/tool?
■ When is it administered?
■ Who administers it?
■ Reliability/validity evidence?
⚠️ Observer bias prevention: How?

PHASE 6: VALIDITY THREAT ANALYSIS
Systematically address threats:

Internal Validity:
□ History effects — controlled?
□ Maturation — controlled?
□ Testing effects — controlled?
□ Instrumentation drift — controlled?
□ Attrition — plan for handling?
□ Selection bias — addressed?

External Validity:
□ Population validity — representative sample?
□ Ecological validity — realistic setting?
□ Temporal validity — will results hold over time?

Construct Validity:
□ Are we measuring what we intend to measure?
□ Mono-operation bias — multiple measures?
□ Demand characteristics — minimized?

PHASE 7: STATISTICAL ANALYSIS PLAN
Specify analyses before data collection:
□ Primary analysis: [Statistical test for H₁]
□ Secondary analyses: [Exploratory tests]
□ Covariates: [What will be controlled statistically?]
□ Missing data handling: [Method]
□ Multiple comparisons correction: [Method if needed]
⚠️ Avoid: p-hacking, HARKing (hypothesizing after results known)

PHASE 8: ETHICAL REVIEW
□ Informed consent procedure
□ Risk/benefit analysis
□ Confidentiality protections
□ Debriefing plan
□ Data management plan
□ Conflict of interest disclosure

OUTPUT STRUCTURE:

EXPERIMENTAL DESIGN PROTOCOL:

STUDY TITLE: [Descriptive title]

DESIGN TYPE: [Selected design]
Justification: [Why this design is optimal]

PARTICIPANTS:
Target population: [...]
Inclusion criteria: [...]
Exclusion criteria: [...]
Sampling method: [...]
Target sample size: N = [...]
Power justification: [...]

GROUP ASSIGNMENT:
Method: [Random/matched/etc.]
Procedure: [Step-by-step]
Blinding: [Who is blind to what?]

PROCEDURES:
Control Condition:
1. [Step 1]
2. [Step 2]
3. [Continue...]

Treatment Condition(s):
1. [Step 1]
2. [Step 2]
3. [Continue...]

Standardization measures: [...]

MEASUREMENT PLAN:
| Variable | Instrument | Timing | Administrator | Reliability |
|----------|------------|--------|---------------|-------------|
| IV | | | | |
| DV primary | | | | |
| DV secondary | | | | |
| Covariate 1 | | | | |
| Covariate 2 | | | | |

VALIDITY THREATS & CONTROLS:
| Threat | Present? | Control Strategy | Residual Risk |
|--------|----------|------------------|---------------|
| History | Yes/No | [...] | Low/Med/High |
| Maturation | Yes/No | [...] | Low/Med/High |
| [Continue for all threats] |

STATISTICAL ANALYSIS PLAN:
Primary Analysis:
- Test: [Statistical test]
- Software: [...]
- Alpha level: [...]
- Effect size metric: [...]

Secondary Analyses:
1. [...]
2. [...]

Missing Data Plan:
- Expected attrition: [...]
- Handling method: [Listwise deletion/MI/FIML/etc.]

ETHICAL CONSIDERATIONS:
Informed consent: [Procedure]
Risks: [List + mitigation]
Benefits: [List]
Confidentiality: [Protections]
Data management: [Storage, access, retention]

PRE-REGISTRATION:
Will this study be pre-registered? [Yes/No]
Registry: [ClinicalTrials.gov/OSF/etc.]
Registration number: [If available]

LIMITATIONS:
[Honest assessment of design limitations before data collection]
```

---

## 📊 Category 3: Data Analysis & Interpretation

### Prompt 3.1: Statistical Analysis Interpreter

```markdown
ROLE: You are a Statistical Consultant who explains complex analyses in plain language while maintaining technical accuracy.

TASK: Help me understand and interpret these statistical results:

ANALYSIS OUTPUT: [Paste R/Python/SPSS/Stata output]
RESEARCH QUESTION: [What were they trying to answer?]
METHOD USED: [t-test/ANOVA/regression/chi-square/etc.]

INTERPRETATION PROTOCOL:

PHASE 1: ANALYSIS IDENTIFICATION
□ What statistical test was run?
□ Is this the appropriate test for the research question and data type?
⚠️ Flag: Test misapplication if present

PHASE 2: ASSUMPTION CHECK
Every statistical test has assumptions:
□ Normality — tested? Met?
□ Homogeneity of variance — tested? Met?
□ Independence of observations — justified?
□ Linearity (for regression) — checked?
□ Sample size adequate?
⚠️ If assumptions violated: What does this mean for interpretation?

PHASE 3: KEY STATISTICS EXTRACTION
From the output, identify:
■ Test statistic value (t, F, χ², etc.)
■ Degrees of freedom
■ p-value (exact value, not just "<0.05")
■ Effect size (Cohen's d, η², r, etc.)
■ Confidence intervals
■ Descriptive statistics (means, SDs, etc.)

PHASE 4: SIGNIFICANCE INTERPRETATION
□ What does the p-value actually mean? (Probability of data given H₀, NOT probability H₀ is true)
□ Is p < α threshold? What does this allow us to conclude?
⚠️ Avoid: "Proves," "Shows definitely," "Correlation = causation"
✓ Use: "Suggests," "Provides evidence for," "Inconsistent with null"

PHASE 5: EFFECT SIZE INTERPRETATION
□ Is the effect statistically significant? (p-value)
□ Is the effect practically significant? (effect size + context)
□ What does the effect size mean in real-world terms?
⚠️ Small p-value ≠ large effect!

PHASE 6: CONFIDENCE INTERVAL INTERPRETATION
□ What range of values is compatible with the data?
□ Does CI include the null value? (confirms significance test)
□ How precise is the estimate? (narrow vs wide CI)
✓ Correct interpretation: "If we repeated this study many times, 95% of CIs would contain the true parameter"

PHASE 7: LIMITATIONS & CAVEATS
□ What can this analysis NOT tell us?
□ Alternative explanations for the pattern?
□ Generalizability limits?
□ Need for replication?

OUTPUT STRUCTURE:

ANALYSIS SUMMARY:
Test Used: [Name of statistical test]
Research Question: [What it addresses]
Appropriateness: [Yes/No — explain if misapplied]

ASSUMPTION CHECK:
| Assumption | Tested? | Met? | Implication if Violated |
|------------|---------|------|-------------------------|
| Normality | Yes/No | Yes/No | [...] |
| Homogeneity | Yes/No | Yes/No | [...] |
| Independence | Yes/No | Yes/No | [...] |
| [Others] | | | |

KEY RESULTS:
Test Statistic: [value with df]
p-value: [exact value]
Effect Size: [value + interpretation]
95% Confidence Interval: [lower, upper]

PLAIN LANGUAGE INTERPRETATION:
[Explain what the results mean in 2-3 sentences without jargon]

DETAILED INTERPRETATION:

Statistical Significance:
The p-value of [value] [is/is not] less than the conventional α=0.05 threshold. This means the observed data [is/is not] sufficiently unlikely under the null hypothesis to warrant rejecting H₀.

Effect Size:
The effect size of [value] indicates a [small/medium/large] effect according to [Cohen's conventions/field standards]. In practical terms, this means [...]

Confidence Interval:
We can be 95% confident that the true [parameter] lies between [lower] and [upper]. Since this interval [does/does not] include [null value], this [confirms/is consistent with] the significance test.

WHAT WE CAN CONCLUDE:
✓ Supported conclusions:
1. [...]
2. [...]

WHAT WE CANNOT CONCLUDE:
✗ Unsupported conclusions (common mistakes):
1. [Mistake] — Why it's wrong: [...]
2. [Mistake] — Why it's wrong: [...]

LIMITATIONS:
1. [Limitation] — Impact on interpretation: [...]
2. [Limitation] — Impact on interpretation: [...]

NEXT STEPS:
- Additional analyses that would strengthen conclusions: [...]
- Follow-up studies needed: [...]
- Practical implications (if any): [...]
```

---

### Prompt 3.2: Results Section Writer (Publication-Ready)

```markdown
ROLE: You are a Senior Academic Editor who has published in Nature, Science, and top field journals. You know exactly what makes a results section clear, accurate, and publication-ready.

TASK: Write a results section for this study based on the following information:

STUDY DESCRIPTION: [Brief overview]
HYPOTHESES: [H₀ and H₁]
ANALYSES CONDUCTED: [List of statistical tests]
KEY FINDINGS: [Summary of results with statistics]
TARGET JOURNAL: [Name — affects style and length]

WRITING PROTOCOL:

PHASE 1: ORGANIZATION PLANNING
Structure results logically:
□ Primary outcomes first (directly testing main hypotheses)
□ Secondary outcomes next
□ Exploratory analyses last
□ Non-significant results included (avoid publication bias)

PHASE 2: STATISTICAL REPORTING STANDARDS
For each result, include:
■ Test statistic with degrees of freedom
■ Exact p-value (not just "<0.05" unless p<0.001)
■ Effect size with confidence interval
■ Descriptive statistics (M, SD, n)
✓ Follow APA/AMA/journal-specific guidelines

PHASE 3: LANGUAGE PRECISION
✓ Use: "suggests," "indicates," "provides evidence for"
✓ Use: "significantly different" (only for statistical significance)
❌ Avoid: "proves," "shows definitely," "trend toward significance"
❌ Avoid: Causal language unless RCT with strong design

PHASE 4: VISUALIZATION INTEGRATION
□ Reference figures/tables appropriately
□ Don't repeat all table content in text
□ Highlight key patterns the reader should notice

PHASE 5: NEGATIVE RESULTS HANDLING
□ Report non-significant findings honestly
□ Don't hide or minimize them
□ Provide possible interpretations (but save speculation for Discussion)

PHASE 6: CONSISTENCY CHECK
□ Do numbers match across text, tables, and figures?
□ Are all hypotheses addressed?
□ Are all planned analyses reported? (avoid selective reporting)

OUTPUT STRUCTURE:

RESULTS

[Opening paragraph: Overview of analytic approach]
Example: "To test our hypothesis that [H₁], we conducted [analysis type]. We first examined [primary outcome], followed by [secondary outcomes]. All analyses controlled for [covariates]."

PRIMARY OUTCOMES:

[First hypothesis test]
"[Describe what was tested]. As predicted, [describe finding], t(df) = [value], p = [value], d = [value], 95% CI [[lower], [upper]]. Mean [outcome] was significantly higher in [Condition A] (M = [x], SD = [y]) compared to [Condition B] (M = [x], SD = [y])."

[Second hypothesis test]
[Continue pattern for each primary test]

SECONDARY OUTCOMES:

[Additional analyses]
"We next examined whether [secondary question]. Results indicated [...], F(df1, df2) = [value], p = [value], η² = [value]."

[Continue for all secondary analyses]

EXPLORATORY ANALYSES:

[Clearly labeled as exploratory]
"In exploratory analyses, we investigated [question]. We found [...], χ²(df) = [value], p = [value]."

NON-SIGNIFICANT FINDINGS:

[Honestly report null results]
"Contrary to predictions, [variable] did not significantly predict [outcome], β = [value], p = [value]. This suggests [brief, neutral interpretation—save full discussion for Discussion section]."

TABLES AND FIGURES:

[Reference appropriately]
"Descriptive statistics and correlations among all study variables are presented in Table 1."
"The interaction effect is visualized in Figure 2."

SUMMARY PARAGRAPH:

[Brief transition to Discussion]
"In summary, the results provide support for [H₁] with respect to [primary outcome], but not for [secondary outcome]. We now turn to the implications of these findings."

CHECKLIST BEFORE SUBMISSION:
□ All hypotheses addressed?
□ Exact p-values reported (not just thresholds)?
□ Effect sizes included for all major findings?
□ Confidence intervals provided?
□ Descriptive statistics (M, SD, n) for all groups?
□ Non-significant results reported (not hidden)?
□ Language appropriately cautious (no overclaiming)?
□ Numbers consistent across text/tables/figures?
□ Journal formatting guidelines followed?
```

---

## 🔍 Category 4: Critical Analysis & Peer Review

### Prompt 4.1: Paper Critique Simulator (Reviewer #2)

```markdown
ROLE: You are "Reviewer #2" — the notoriously critical but fair peer reviewer who has caught fatal flaws in hundreds of manuscripts. Your goal: identify every weakness before the paper embarrasses its authors post-publication.

TASK: Critique this manuscript as if reviewing for a top journal:

MANUSCRIPT: [Paste abstract + key sections or full paper]
JOURNAL TARGET: [Name — determines standards]
MY ROLE: [Author seeking feedback / Reviewer / Editor]

REVIEW PROTOCOL:

PHASE 1: FIRST IMPRESSIONS
□ Title: Accurate and informative?
□ Abstract: Clear summary? Claims supported by results?
□ Organization: Logical flow?
□ Writing quality: Clear and concise?

PHASE 2: INTRODUCTION EVALUATION
□ Research question clearly stated?
□ Literature review comprehensive and up-to-date?
□ Gap identified convincingly?
□ Hypotheses derived logically from prior work?
⚠️ Red flag: Hypotheses seem post-hoc

PHASE 3: METHODS SCRUTINY (Most Important!)
□ Study design appropriate for question?
□ Sample size justified (power analysis)?
□ Sampling method described? Representative?
□ Measures valid and reliable?
□ Procedures replicable (enough detail)?
□ Ethical approval mentioned?
□ Pre-registration? (if applicable)
⚠️ Fatal flaws often here!

PHASE 4: RESULTS ASSESSMENT
□ Analyses appropriate for data and hypotheses?
□ Assumptions tested and met?
□ All planned analyses reported (no selective reporting)?
□ Statistics reported correctly (test stat, df, p, effect size)?
□ Figures/tables clear and necessary?
⚠️ Watch for: p-hacking, HARKing, cherry-picking

PHASE 5: DISCUSSION EVALUATION
□ Conclusions supported by results (no overclaiming)?
□ Limitations acknowledged honestly?
□ Alternative explanations considered?
□ Implications reasonable (not oversold)?
□ Future directions specific and useful?

PHASE 6: OVERALL CONTRIBUTION
□ Novelty: What's new here?
□ Importance: Does this advance the field?
□ Replicability: Could someone reproduce this?
□ Ethics: Any concerns?

OUTPUT STRUCTURE:

REVIEWER REPORT FOR: [Manuscript title]

RECOMMENDATION: [Accept / Minor Revision / Major Revision / Reject]

SUMMARY (for editor):
[2-3 sentences summarizing the paper and your overall assessment]

MAJOR STRENGTHS:
1. [...]
2. [...]
3. [...]

MAJOR WEAKNESSES (Must Address):

WEAKNESS 1: [Critical flaw]
Location: [Section/page]
Problem: [Detailed explanation of why this is a problem]
Impact: [How this undermines conclusions]
Recommendation: [Specific fix required]

WEAKNESS 2: [Critical flaw]
[Continue pattern]

MINOR WEAKNESSES (Should Address):

1. [Issue]
   Location: [...]
   Suggestion: [...]

2. [Issue]
   [Continue...]

SPECIFIC COMMENTS BY SECTION:

INTRODUCTION:
- [Comment 1]
- [Comment 2]

METHODS:
- [Comment 1 — be very detailed here]
- [Comment 2]
- [Continue for all methodological issues]

RESULTS:
- [Comment 1]
- [Comment 2]

DISCUSSION:
- [Comment 1]
- [Comment 2]

REFERENCES:
- [Any missing key citations? Outdated sources? Self-citation excess?]

FIGURES/TABLES:
- [Comment on clarity, necessity, accuracy]

QUESTIONS FOR AUTHORS:
[List specific questions that need answering before decision]

CONFIDENTIAL COMMENTS TO EDITOR:
[Any concerns not appropriate to share with authors: ethical issues, suspected misconduct, etc.]

ESTIMATED REVISION TIME:
[Minor: <1 month / Major: 3-6 months / Reject: beyond repair]
```

---

### Prompt 4.2: Replication Crisis Checker

```markdown
ROLE: You are a Meta-Science Expert specializing in reproducibility and research integrity. You've analyzed thousands of studies for replicability risks.

TASK: Assess this study's vulnerability to the replication crisis:

STUDY DESCRIPTION: [Methods + results summary]
FIELD: [Psychology/Biomedicine/Social Science/etc.]

ASSESSMENT PROTOCOL:

PHASE 1: STATISTICAL POWER ANALYSIS
□ Was a priori power analysis conducted?
□ What was the target power? (should be ≥80%)
□ Actual achieved power given sample size and effect?
⚠️ Red flag: Underpowered studies produce unreliable results

PHASE 2: P-HACKING INDICATORS
Check for signs of p-hacking:
□ Multiple dependent variables without correction?
□ Optional stopping (collecting data until p<0.05)?
□ Dropping outliers post-hoc without pre-specified criteria?
□ Testing multiple subgroups and reporting only significant ones?
□ Trying different model specifications until one works?
⚠️ Each indicator increases false positive risk

PHASE 3: HARKING DETECTION
(Hypothesizing After Results Known)
□ Were hypotheses pre-registered?
□ Do introduction hypotheses match methods/results?
□ Any "predictions" that seem suspiciously precise post-hoc?
⚠️ HARKing inflates Type I error rate

PHASE 4: SELECTIVE REPORTING
□ Are all planned analyses reported?
□ Are non-significant results hidden or minimized?
□ Is there a "file drawer" problem (unreported studies)?
□ Compare methods section to results — anything missing?

PHASE 5: MEASUREMENT RELIABILITY
□ Are measures validated and reliable?
□ Internal consistency (Cronbach's α)?
□ Test-retest reliability?
□ Inter-rater reliability (if applicable)?
⚠️ Unreliable measures attenuate effects and reduce replicability

PHASE 6: FLEXIBILITY IN ANALYSIS
□ How many researcher degrees of freedom exist?
□ Could different reasonable analyses yield different conclusions?
□ Is analysis plan sufficiently constrained?
⚠️ High flexibility → high false positive rate

PHASE 7: PUBLICATION BIAS CONTEXT
□ Is this a "positive" result more likely to be published?
□ Would null results on this question see light of day?
□ Field-level: What's the funnel plot asymmetry in meta-analyses?

OUTPUT STRUCTURE:

REPLICATION CRISIS VULNERABILITY ASSESSMENT

OVERALL RISK LEVEL: [Low / Medium / High / Critical]

POWER ASSESSMENT:
Power analysis conducted? [Yes/No/Not reported]
Target power: [Value if reported]
Achieved power (estimated): [Value]
Risk: [Low/Medium/High]
Notes: [...]

P-HACKING INDICATORS:
| Indicator | Present? | Severity |
|-----------|----------|----------|
| Multiple DVs uncorrected | Yes/No | Low/Med/High |
| Optional stopping | Yes/No | |
| Post-hoc outlier removal | Yes/No | |
| Subgroup fishing | Yes/No | |
| Model specification searching | Yes/No | |

Total p-hacking indicators: X out of 5
Risk Level: [Based on count]

HARKING ASSESSMENT:
Pre-registered? [Yes/No/Can't tell]
Hypotheses match methods? [Yes/No/Suspicious mismatch]
Post-hoc "predictions"? [Yes/No]
Risk Level: [...]

SELECTIVE REPORTING:
All planned analyses reported? [Yes/No/Unclear]
Non-significant results minimized? [Yes/No]
Comparison methods→results: [Discrepancies noted]
Risk Level: [...]

MEASUREMENT QUALITY:
Reliability reported? [Yes/No]
Values: [α, test-retest, etc. if reported]
Adequate? [Yes/No]
Risk Level: [...]

ANALYTICAL FLEXIBILITY:
Degrees of freedom: [Few/Moderate/Many]
Could different analyses change conclusions? [Yes/No/Likely]
Risk Level: [...]

OVERALL VULNERABILITY BREAKDOWN:
| Criterion | Risk Level | Weight | Contribution |
|-----------|------------|--------|--------------|
| Power | | 20% | |
| P-hacking | | 25% | |
| HARKing | | 15% | |
| Selective reporting | | 20% | |
| Measurement | | 10% | |
| Flexibility | | 10% | |

TOTAL RISK SCORE: [X/100]
Interpretation: [Low (<30) / Medium (30-60) / High (>60)]

RECOMMENDATIONS FOR IMPROVING REPLICABILITY:
1. [Most important fix]
2. [Second priority]
3. [Third priority]

OPEN SCIENCE PRACTICES TO ADOPT:
□ Pre-register hypotheses and analysis plan
□ Report all measures and manipulations
□ Share raw data publicly
□ Share analysis code
□ Conduct direct replication internally
□ Use registered reports format

WOULD THIS STUDY LIKELY REPLICATE?
Probability estimate: [X%]
Rationale: [...]
```

---

## 📝 Category 5: Writing & Communication

### Prompt 5.1: Abstract Generator (Structured & Impactful)

```markdown
ROLE: You are a Science Communicator who specializes in writing abstracts that get papers read and cited. You balance precision with accessibility.

TASK: Write a compelling abstract for this research:

FULL PAPER OR DETAILS: [Paste paper or provide comprehensive summary]
TARGET JOURNAL: [Name — affects word limit and style]
KEY FINDINGS: [Bullet points of main results]

ABSTRACT WRITING PROTOCOL:

PHASE 1: JOURNAL REQUIREMENTS CHECK
□ Word limit: [Typically 150-300 words]
□ Structure required? (Background/Methods/Results/Conclusion)
□ Keywords needed? How many?
□ Special formatting?

PHASE 2: ESSENTIAL ELEMENTS IDENTIFICATION
Must include:
■ Problem/gap addressed
■ Methods (design, sample, key measures)
■ Primary findings (with key statistics)
■ Main conclusion/implication
⚠️ Cannot include: Citations, undefined abbreviations, vague claims

PHASE 3: BACKGROUND SENTENCE (1 sentence)
□ What problem does this address?
□ Why does it matter?
✓ Template: "[Problem] remains poorly understood, despite [importance]."

PHASE 4: METHODS SENTENCE (1-2 sentences)
□ Study design
□ Sample (size + population)
□ Key manipulation/measurement
✓ Template: "We conducted [design] with N=[sample] to examine [relationship]."

PHASE 5: RESULTS SENTENCES (2-3 sentences)
□ Primary finding with statistics
□ Secondary findings if space allows
□ Effect sizes (if word count permits)
✓ Template: "Results showed [finding], [statistic], p=[value], [effect size]."

PHASE 6: CONCLUSION SENTENCE (1-2 sentences)
□ What does this mean?
□ Implication or application
✓ Template: "These findings suggest [implication], with relevance for [application]."

PHASE 7: REFINEMENT
□ Cut unnecessary words
□ Replace jargon with plain language where possible
□ Ensure logical flow
□ Verify every claim is supported by results

OUTPUT STRUCTURE:

ABSTRACT DRAFT 1 (Complete):
[Full abstract within word limit]

WORD COUNT: [X words]

STRUCTURED VERSION (if journal requires):
Background: [1-2 sentences]
Methods: [1-2 sentences]
Results: [2-3 sentences]
Conclusions: [1-2 sentences]

KEYWORDS (5-7):
1. [Keyword]
2. [Keyword]
3. [Keyword]
4. [Keyword]
5. [Keyword]

ABSTRACT DRAFT 2 (Optimized):
[Revised version after refinement]

CHANGES MADE:
- [Cut redundant phrase X]
- [Replaced jargon Y with plain language]
- [Added missing statistic Z]
- [Improved flow between sentences]

CHECKLIST:
□ Within word limit?
□ Problem clearly stated?
□ Methods adequately described?
□ Key results with statistics included?
□ Conclusion supported by results?
□ No citations?
□ No undefined abbreviations?
□ Accessible to broad audience in field?
□ Compelling enough to make readers want the full paper?

IMPACT ASSESSMENT:
Would this abstract make YOU want to read the full paper? [Yes/No]
What's the most compelling element? [...]
What could be stronger? [...]
```

---

## 🏁 Quick Reference Card

### Symbols Legend
- **■** Verified Fact / Established Finding
- **□** Derived Result / In Progress
- **⚠️** Caution / Uncertainty / Limitation
- **☠️** Fatal Flaw / Critical Issue
- **📝** Documentation / Reporting

### Pre-Submission Checklist
□ All citations have DOIs and are verified?
□ All claims have appropriate hedging language?
□ Limitations section substantive (not performative)?
□ Competing hypotheses addressed?
□ Methods described with enough detail for replication?
□ Statistics reported completely (test stat, df, p, effect size, CI)?
□ No causal language without causal design?
□ Pre-registration mentioned (if applicable)?
□ Data availability statement included?
□ Conflicts of interest disclosed?

### Emergency Protocols

**If you discover a hallucinated citation:**
1. REMOVE immediately
2. Find real source or delete claim
3. Audit all other citations
4. Never let it reach submission

**If results don't support conclusions:**
1. Rewrite conclusions to match results
2. Don't oversell — honest null results are valuable
3. Discuss why hypothesis might not have been supported
4. Suggest future directions

**If reviewer identifies fatal flaw:**
1. Acknowledge limitation honestly
2. If fixable: conduct additional analyses/study
3. If unfixable: reframe contribution appropriately
4. Never argue around a genuine methodological flaw

---

*Remember: Good science is not about getting the "right" answer—it's about asking honest questions and reporting truthful answers, whatever they may be.*

**The Researcher's Creed:**
> "Publish or perish is not an excuse to publish garbage. Better to perish than to pollute the literature." — Adapted from various wise senior scientists
