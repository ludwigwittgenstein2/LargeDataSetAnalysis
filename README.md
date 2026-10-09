# Large-Scale GMETS Narrative Evaluation Analysis

AI-assisted mixed-methods analysis of Graduate Medical Education (GME) narrative evaluations using a grounded-theory-informed fixed-taxonomy framework.

This repository contains figures, statistical summaries, analysis outputs, and presentation materials from two large-scale GMETS narrative-analysis experiments:

- `50kRows/` — analysis of 50,000 narrative responses
- `100kRows/` — expanded analysis of 100,000 narrative responses

The project asks a broader question:

> **What can large-scale narrative evaluations tell us about the learning environment, mechanisms of learning, trainee development, feedback quality, and the contextual factors surrounding performance in Graduate Medical Education?**

---

## Project Overview

Graduate Medical Education generates large volumes of narrative evaluation data that are difficult to analyze manually at scale.

This project uses large language models together with statistical analysis to transform free-text evaluation narratives into structured qualitative and quantitative signals.

The analysis examines:

- the learning environment
- mechanisms through which learning occurs
- trainee developmental outcomes
- feedback quality
- psychological safety
- supervision and graduated autonomy
- workload and wellbeing
- workflow and systems barriers
- equity and discrimination climate
- relationships between narrative themes and structured scores
- differences across evaluation types
- temporal patterns
- longitudinal trainee score change
- taxonomy adequacy
- negative and contradictory cases
- non-obvious patterns visible only after integrating multiple analyses

The goal is not simply to classify comments.

The larger goal is to use narrative evaluation data to better understand the **educational ecosystem surrounding trainee development**.

---

# Analysis Design

The project follows a mixed inductive-confirmatory design.

An earlier pilot phase used inductive/open coding to identify recurring concepts in the narrative data.

Those concepts informed a fixed taxonomy that was subsequently applied at larger scale.

The large-scale workflow therefore combines:

1. prior inductive qualitative discovery
2. fixed-taxonomy LLM classification
3. constant comparison
4. taxonomy-gap analysis
5. negative-case analysis
6. event-level quantitative analysis
7. subgroup comparisons
8. structured-score associations
9. temporal and longitudinal analysis
10. final theoretical integration

This is best understood as an **AI-scaled qualitative and mixed-methods analysis**, rather than a purely unsupervised topic-modeling exercise.

---

# Study Scale

## 50K Analysis

The initial scaled analysis included:

- **50,000 narrative rows**
- **1,727 evaluation events**

This analysis established the initial large-scale patterns and provided an intermediate validation of the coding framework.

Results are available in:

```text
50kRows/
```

---

## 100K Analysis

The expanded analysis processed:

- **100,000 narrative rows**
- **1,888 unique evaluation events**
- **253 programs**
- **18 evaluation types**
- **189,689 eligible deduplicated narrative responses before sampling**
- **0 unresolved classification failures**
- **mean narrative response length: approximately 176 characters**

Results are available in:

```text
100kRows/
```

---

# Data Source and Sampling

The 100K analysis was generated from the GMETS research dataset.

Narrative responses were eligible when they contained:

- a valid evaluation-event identifier
- an evaluation question
- a non-trivial narrative response
- at least 20 characters of usable text

Trivial and placeholder responses were removed.

Rows were deduplicated using evaluation event, item order, question, and response content.

The most recent record was retained when duplicates existed.

A deterministic hash-based sampling procedure was then used to select 100,000 rows from the larger eligible corpus.

This makes the sampled dataset reproducible.

---

# Unit of Analysis

A critical methodological distinction is the difference between a **narrative row** and an **evaluation event**.

## Narrative row

One deduplicated:

```text
QUESTION + TEXT_RESPONSE
```

pair associated with an evaluation event.

This is the qualitative unit classified by the LLM.

---

## Evaluation event

Narrative rows belonging to the same evaluation were grouped using a de-identified:

```text
EVALUATION_ID_HASH
```

This is the principal unit used for event-level prevalence, co-occurrence, structured-score associations, and longitudinal analyses.

A single evaluation event may contain many narrative rows.

Therefore:

> **100,000 narratives provide qualitative depth, but they do not represent 100,000 statistically independent observations.**

The 100K narrative corpus was aggregated into **1,888 evaluation events** for most inferential analyses.

---

# Input Variables

The analysis uses several types of information.

## QUESTION

The evaluation prompt or item that the evaluator or respondent was answering.

This provides context for interpreting the free-text response.

---

## TEXT_RESPONSE

The narrative evaluation comment.

This is the primary qualitative evidence analyzed by the LLM.

---

## EVALUATION_ID_HASH

A de-identified identifier representing one evaluation event.

Multiple narrative rows can belong to the same event.

---

## ITEM_ORDER

The position of the question within the evaluation instrument.

This was used in deduplication and row identity.

---

## Structured Performance Score

The event-level structured score was calculated from available scaled option values.

It was used for:

- high-versus-low score comparisons
- continuous score associations
- longitudinal analyses

---

## EVALUATED_DATE / YEAR

The date of the evaluation.

This was used to study descriptive patterns over calendar time.

---

## EVALUATION_TYPE

Represents who is evaluating whom, or the type of evaluation instrument.

Examples include:

- faculty evaluating residents
- residents evaluating faculty
- peer evaluations
- self evaluations
- patient/staff evaluations
- program or hospital evaluations

---

## Program and Organizational Context

Program, department, institute, and related metadata were used for subgroup analysis.

---

## Trainee and Evaluator Identifiers

De-identified identifiers allow repeated observations to be studied without exposing individual names.

---

# AI Models

## Large-Scale Narrative Coding

```text
openai-gpt-5-nano
```

GPT-5 nano was used for large-scale structured classification of narrative responses.

The model applied the previously developed fixed taxonomy to each narrative row.

---

## Final Interpretation

```text
claude-sonnet-5
```

Claude Sonnet 5 was used after the quantitative analysis to interpret aggregate tables and identify:

- cross-chart patterns
- theoretical relationships
- non-obvious findings
- recommendations
- action steps
- possible future research directions

The final interpretation model received aggregate analytical outputs rather than raw narrative text.

GPT-5 nano served as a fallback interpretation model.

---

# Coding Framework

Each narrative could receive multiple codes.

The taxonomy contains three primary conceptual domains:

1. Learning Environment
2. Learning Mechanisms
3. Developmental Outcomes

Additional outputs captured feedback quality, performance signal, model confidence, sensitizing constructs, taxonomy gaps, and negative cases.

---

# Learning Environment

The learning-environment taxonomy includes:

### E01 — Faculty Teaching, Feedback, and Mentorship

Teaching, coaching, mentoring, role modeling, and faculty feedback.

### E02 — Supervision and Graduated Autonomy

Availability of supervision, oversight, independence, and increasing responsibility.

### E03 — Clinical Workload, Volume, and Complexity

Patient volume, workload, acuity, complexity, and clinical intensity.

### E04 — Rotation, Subspecialty, and Procedural Exposure

Breadth and quality of clinical or procedural exposure.

### E05 — Team and Interprofessional Collaboration

Interactions with multidisciplinary and interprofessional teams.

### E06 — Leadership and Role-Transition Opportunities

Leadership opportunities and transition into increasing professional responsibility.

### E07 — Teaching Infrastructure, Didactics, and Conferences

Formal teaching sessions, conferences, curriculum, simulation, and educational infrastructure.

### E08 — Scholarship and Research Opportunities

Research, scholarly activity, academic mentorship, and barriers to scholarship.

### E09 — Psychological Safety and Relational Climate

Interpersonal trust, respect, safe communication, and ability to seek help or disclose uncertainty.

### E10 — Workflow, Systems, Resources, and Operational Barriers

Operational friction, inefficient systems, resource limitations, and workflow problems.

### E11 — Wellbeing, Fatigue, and Work-Life Strain

Fatigue, stress, burnout, wellbeing, and work-life strain.

### E12 — Patient-Care Responsibility, Acuity, and Continuity

Responsibility for patients, continuity, complexity, and ownership of care.

### E13 — Assessment, Evaluation Processes, and Expectations

Clarity and quality of assessment systems, expectations, and evaluation processes.

### E14 — Equity, Inclusion, and Discrimination Climate

Bias, discrimination, fairness, equity, and inclusion.

### E15 — No Explicit Learning-Environment Feature

Used when the narrative row does not clearly describe a learning-environment feature.

---

# Learning Mechanisms

The analysis also identifies **how learning is described as occurring**.

These mechanisms include:

### M01 — Iterative Feedback, Coaching, and Modeling

Repeated feedback, coaching, demonstration, and faculty modeling.

### M02 — Repeated or Graduated Clinical Exposure

Learning through repeated clinical encounters or increasingly complex exposure.

### M03 — Direct Supervision, Scaffolding, and Availability

Learning through supervision, guidance, support, and progressive scaffolding.

### M04 — Autonomy, Ownership, and Responsibility

Development through increasing independence and ownership.

### M05 — Team Interaction and Interprofessional Learning

Learning from peers, teams, staff, and collaborative practice.

### M06 — Reflection, Self-Assessment, and Goal Setting

Learning through reflection, self-monitoring, feedback incorporation, and goal formation.

### M07 — Structured Teaching, Didactics, and Simulation

Formal educational activities and structured instruction.

### M08 — Research, Scholarship, and Deliberate Practice

Learning through research activity, scholarly development, or focused practice.

### M09 — No Explicit Mechanism

Used when the narrative contains no clearly identifiable learning mechanism.

---

# Developmental Outcomes

The analysis identifies what kinds of trainee development are described.

### D01 — Clinical Reasoning and Diagnostic Competence

Clinical reasoning, diagnostic thinking, judgment, and decision-making.

### D02 — Procedural and Technical Competence

Procedural skills and technical ability.

### D03 — Autonomy, Confidence, and Independent Judgment

Growth in independence, ownership, confidence, and professional judgment.

### D04 — Communication and Teamwork Development

Communication skills, teamwork, collaboration, and interpersonal effectiveness.

### D05 — Professional Identity and Leadership Formation

Professional identity, leadership, maturity, and role development.

### D06 — Feedback Receptivity and Self-Directed Learning

Ability to receive feedback, reflect, set goals, and direct one's own learning.

### D07 — Efficiency, Organization, and Workflow Management

Time management, organization, prioritization, and clinical efficiency.

### D08 — Scholarship, Research, and Teaching Development

Research development, academic growth, scholarship, and teaching ability.

### D09 — Wellbeing, Resilience, and Coping

Resilience, wellbeing, adaptive coping, and management of stress.

### D10 — No Explicit Developmental Effect

Used when no clear developmental outcome is described.

---

# Additional LLM Outputs

## Performance Signal

Each narrative was classified as:

- positive
- mixed
- concern
- neutral / non-evaluative

---

## Specificity

Model-rated feedback specificity on a **1–5 scale**.

Higher scores indicate more concrete and behavior-specific feedback.

---

## Actionability

Model-rated feedback actionability on a **1–5 scale**.

Higher scores indicate clearer guidance about what the learner should do next.

---

## Model Confidence

The model generated a confidence score from:

```text
0–100
```

This should be treated as a model-generated heuristic and **not as a calibrated probability**.

---

# Sensitizing Constructs

The pipeline explicitly searched for higher-level constructs including:

- psychological safety
- supervision availability
- workload and fatigue
- wellbeing and burnout
- discrimination and bias
- handoff or systems failure
- error disclosure
- serious patient outcomes

These constructs were included because they may represent educationally or clinically important contextual signals.

---

# Taxonomy-Gap Detection

The model identified cases in which an important concept appeared poorly represented by the existing taxonomy.

These were marked using a:

```text
TAXONOMY_GAP_FLAG
```

A short proposed gap concept was also generated.

Only approximately:

```text
0.43%
```

of the 100,000 narratives were flagged as potential taxonomy gaps.

This suggests that the broad codebook is approaching conceptual saturation.

However, several gap labels were:

- missing values
- duplicated wording
- variants of existing categories
- extremely narrow specialty-specific concepts

Further human review is therefore required before extending the taxonomy.

---

# Negative Cases

The analysis also identifies narratives that contradict or challenge dominant patterns.

These negative cases are important because large-scale qualitative analysis should not focus only on majority patterns.

Rare adverse or contradictory cases may provide important insights into:

- educational problems
- safety issues
- supervision failures
- workload stress
- bias
- system-level problems

---

# 100K Results

## Learning-Environment Prevalence

The most prevalent environment categories were:

| Learning-environment category | Percentage of evaluation events |
|---|---:|
| Faculty teaching, feedback, and mentorship | **97.5%** |
| Teaching infrastructure, didactics, and conferences | **86.3%** |
| Psychological safety and relational climate | **80.8%** |
| Clinical workload, volume, and complexity | **74.0%** |
| Wellbeing, fatigue, and work-life strain | **73.4%** |
| Supervision and graduated autonomy | **68.5%** |
| Assessment processes and expectations | **65.3%** |
| Patient-care responsibility and continuity | **64.6%** |
| Team and interprofessional collaboration | **51.8%** |
| Rotation and procedural exposure | **48.3%** |
| Workflow and system barriers | **33.6%** |
| Equity and discrimination climate | **24.1%** |
| Scholarship and research opportunities | **21.7%** |
| Leadership opportunities | **12.8%** |

These are event-level prevalence estimates.

A category only needs to appear in one narrative row within an evaluation event for that event to count as containing the theme.

---

# Developmental Outcomes

The most frequently identified developmental outcomes were:

| Developmental outcome | Percentage of evaluation events |
|---|---:|
| Communication and teamwork development | **93.1%** |
| Feedback receptivity and self-directed learning | **84.5%** |
| Clinical reasoning and diagnostic competence | **75.6%** |
| Autonomy, confidence, and independent judgment | **73.1%** |
| Professional identity and leadership formation | **63.9%** |
| Wellbeing, resilience, and coping | **59.2%** |
| Efficiency and organization | **51.4%** |
| Scholarship, research, and teaching development | **34.4%** |
| Procedural and technical competence | **33.5%** |

One notable finding is that developmental language is dominated by:

- communication
- reasoning
- feedback receptivity
- self-directed learning
- autonomy
- professional growth

rather than only procedural or technical competence.

---

# Learning Mechanisms

The most prevalent mechanisms were:

| Learning mechanism | Percentage of evaluation events |
|---|---:|
| Iterative feedback, coaching, and modeling | **94.1%** |
| Direct supervision, scaffolding, and availability | **90.0%** |
| Reflection, self-assessment, and goal setting | **84.3%** |
| Structured teaching, didactics, and simulation | **73.0%** |
| Autonomy, ownership, and responsibility | **71.9%** |
| Repeated or graduated clinical exposure | **57.2%** |
| Team interaction and interprofessional learning | **50.4%** |
| Research, scholarship, and deliberate practice | **22.6%** |

The mechanism profile suggests a recurring educational process:

```text
Clinical experience
        ↓
Observation and supervision
        ↓
Feedback and coaching
        ↓
Reflection and self-assessment
        ↓
Scaffolding
        ↓
Increasing autonomy
```

---

# Major Finding 1: Feedback and Supervision Form the Educational Engine

Faculty teaching, feedback, and mentorship occurred in almost every evaluation event.

Similarly, feedback/coaching and supervision/scaffolding were the dominant mechanisms through which learning was described.

Taken together, these findings suggest that the GMETS learning environment is highly **feedback-centered and supervision-dependent**.

Education appears to emerge not from isolated teaching events, but from repeated interaction between:

- clinical experience
- faculty guidance
- supervision
- coaching
- reflection
- increasing responsibility

---

# Major Finding 2: Psychological Safety Functions as Educational Infrastructure

Psychological safety appeared in approximately:

```text
80.8%
```

of evaluation events as a learning-environment category.

When explicitly analyzed as a sensitizing construct, psychological-safety signals appeared in approximately:

```text
83.7%
```

of events.

Supervision availability appeared in approximately:

```text
76.6%
```

of events.

This suggests that learning depends not only on educational content, but also on whether trainees can:

- ask questions
- disclose uncertainty
- seek help
- make mistakes safely
- communicate openly
- access supervision

Psychological safety and supervision may therefore represent **relational infrastructure for learning**.

---

# Major Finding 3: Workload and Wellbeing Are Part of the Learning Environment

Clinical workload and complexity appeared in approximately:

```text
74.0%
```

of evaluation events.

Wellbeing, fatigue, and work-life strain appeared in approximately:

```text
73.4%
```

of events.

Explicit workload/fatigue signals appeared in approximately:

```text
46.9%
```

of events.

Explicit wellbeing/burnout signals appeared in approximately:

```text
27.1%
```

of events.

This suggests that clinical education cannot be separated completely from the conditions under which the clinical work occurs.

Learning, supervision, workload, fatigue, and wellbeing repeatedly appear within the same evaluation ecosystem.

---

# Major Finding 4: Lower-Scoring Evaluations Contain More Environmental Friction

Several environmental categories appeared significantly more often in lower-scoring evaluation events.

Examples include:

| Category | High-score events | Low-score events | Odds Ratio |
|---|---:|---:|---:|
| Workflow/system barriers | 21.1% | 39.3% | **0.41** |
| Rotation/procedural exposure | 35.8% | 51.3% | **0.53** |
| Equity/discrimination climate | 17.8% | 30.0% | **0.50** |
| Clinical workload/complexity | 62.7% | 75.1% | **0.56** |
| Patient-care responsibility | 55.6% | 66.7% | **0.63** |
| Assessment expectations | 56.4% | 66.9% | **0.64** |
| Wellbeing/fatigue | 66.7% | 74.0% | **0.70** |

An odds ratio below 1 indicates that the theme appeared more often in the lower-score group.

These results should **not** be interpreted as showing that workload, equity issues, or workflow barriers caused lower performance.

A more defensible interpretation is:

> **Lower-scoring evaluations tend to contain richer descriptions of friction, constraints, burden, and environmental context.**

Narrative comments may therefore help explain structured scores rather than merely repeat them.

---

# Major Finding 5: Narrative Evaluations Are Overwhelmingly Positive

The narrative performance signal was:

| Narrative performance signal | Percentage |
|---|---:|
| Positive | **93.1%** |
| Neutral / non-evaluative | **5.7%** |
| Mixed | **0.8%** |
| Concern | **0.4%** |

The overwhelming positive skew creates an important class-imbalance problem.

Rare mixed and concern cases may be disproportionately important for:

- educational quality improvement
- trainee support
- patient safety
- identifying system failures
- detecting bias or discrimination
- identifying supervision problems

---

# Major Finding 6: Narrative and Structured Scores Capture Different Information

One of the most striking findings was the very low agreement between narrative-derived performance bands and structured numerical-score bands.

The quadratic weighted kappa was approximately:

```text
κ = 0.013
```

This represents essentially negligible agreement.

Many low structured-score evaluations still contained overwhelmingly positive narrative language.

This suggests that narrative comments and structured scores may be capturing different dimensions of the evaluation process.

Structured scores may primarily represent:

```text
performance judgment
```

while narrative comments may be richer sources of:

```text
context
learning processes
relationships
strengths
barriers
supervision
workload
developmental information
```

This raises an important hypothesis:

> **Narrative evaluations may be more useful for explaining the context and mechanisms surrounding performance than for reproducing the numerical performance score itself.**

---

# Major Finding 7: Feedback Is Common but Only Moderately Specific

Feedback and coaching appear throughout the evaluation corpus.

However, feedback-quality ratings generally cluster around approximately:

```text
3 / 5
```

for both specificity and actionability.

For example:

| Evaluation type | Mean specificity | Mean actionability |
|---|---:|---:|
| Faculty of resident | 3.15 | 3.23 |
| Faculty of program/hospital | 2.78 | 2.94 |
| Patient/staff of resident | 2.91 | 3.02 |
| Resident self evaluation | 2.94 | 3.06 |
| Resident of service/clinic | 2.97 | 3.13 |
| Resident of resident / peer | 3.18 | 3.28 |
| Resident of faculty | 3.27 | 3.34 |

This reveals a **feedback quantity–quality gap**.

The system already produces substantial amounts of feedback.

The more important intervention may therefore be:

> **Improve the specificity and actionability of existing feedback rather than simply increasing feedback volume.**

A useful feedback structure may be:

```text
Observed behavior
        ↓
Impact / context
        ↓
Specific next step
```

---

# Major Finding 8: No Simple System-Wide Longitudinal Improvement Was Observed

Among trainees with repeated structured-score observations:

```text
N = 213
```

approximately:

```text
51.6%
```

showed a positive first-to-last score change.

However:

```text
Mean change   ≈ -0.05
Median change ≈ +0.08
```

and neither the Wilcoxon test nor sign test indicated a significant overall shift.

This does not mean trainees fail to develop.

Rather, a simple first-versus-last score comparison is likely too crude because evaluations differ across:

- rotations
- evaluators
- specialties
- clinical difficulty
- evaluation instruments
- time intervals

A mixed-effects longitudinal model is therefore a more appropriate next step.

---

# Major Finding 9: The Taxonomy Appears Close to Saturation

Only:

```text
430 / 100,000 rows
```

were flagged as possible taxonomy gaps.

This corresponds to approximately:

```text
0.43%
```

of the corpus.

Many gap outputs were:

- missing values
- duplicate labels
- variants of existing concepts
- narrow specialty-specific concepts

Examples of genuine but uncommon concepts included:

- specialty-specific procedural training gaps
- rotation duration limiting learning progression
- narrow knowledge gaps
- highly specific technical-skill issues

This suggests that the broad codebook is already relatively comprehensive.

---

# Integrated Conceptual Model

The combined findings suggest the following working model:

```text
LEARNING ENVIRONMENT

Faculty teaching / mentorship
Teaching infrastructure
Psychological safety
Supervision / graduated autonomy
Workload and wellbeing context
Assessment and workflow context

                ↓

LEARNING MECHANISMS

Iterative feedback / coaching
Direct supervision / scaffolding
Reflection / self-assessment
Structured teaching
Repeated clinical exposure
Increasing ownership

                ↓

DEVELOPMENTAL OUTCOMES

Communication / teamwork
Feedback receptivity
Clinical reasoning
Autonomy / confidence
Professional identity
Efficiency / organization
```

The pathway may be influenced by contextual moderators including:

```text
Workflow barriers
Clinical workload
Wellbeing / fatigue
Assessment expectations
Rotation exposure
Patient-care responsibility
Equity / discrimination climate
```

This represents a **working conceptual model**, not a proven causal pathway.

---

# What Was Not Obvious From Any Single Analysis

Several findings became visible only when multiple results were interpreted together.

## 1. Lower scores may produce more informative narratives

Lower-scoring evaluations contain substantially more environmental and system context.

The narrative field may therefore function as an explanatory layer around the structured score.

---

## 2. Feedback has a quantity–quality gap

Feedback is nearly universal.

High-quality feedback is not.

The intervention target should therefore be **feedback quality**, not simply feedback volume.

---

## 3. Psychological safety and supervision form relational infrastructure

Psychological safety and supervision appear repeatedly across:

- prevalence analysis
- co-occurrence analysis
- sensitizing constructs
- learning-mechanism analysis

Together, they appear to form part of the relational infrastructure necessary for learning.

---

## 4. The 100K dataset increases depth more than statistical sample size

The corpus contains:

```text
100,000 narrative rows
```

but only:

```text
1,888 evaluation events
```

The large corpus therefore provides extremely rich within-event qualitative information rather than 100,000 independent observations.

---

## 5. Positive evaluation culture may hide important minority signals

Because approximately 93% of event-level narrative performance signals were positive, rare mixed and concern cases can easily disappear within overall averages.

Those cases may actually be among the most important observations for educational improvement.

---

# Practical Implications

The analysis suggests several potential interventions.

## Improve Feedback Specificity

Encourage feedback writers to use:

```text
Observed behavior
→ impact/context
→ specific next step
```

Possible metrics include:

- mean specificity
- mean actionability
- percentage of comments rated ≥4/5
- changes by evaluation type

---

## Monitor Psychological Safety

Programs could monitor:

- psychological safety
- help-seeking
- supervisor availability
- communication climate
- fatigue and workload

These indicators may be useful as educational-environment monitoring measures.

---

## Treat Low-Score Narratives as System Diagnostics

When structured performance scores are low, narrative review should consider whether the evaluation also describes:

- workflow barriers
- excessive workload
- inadequate supervision
- wellbeing strain
- rotation limitations
- unclear assessment expectations
- equity or discrimination concerns

This may help avoid interpreting every low score as solely a trainee-level problem.

---

## Human-Review Rare High-Value Cases

Priority cases for human review may include:

- concern narratives
- mixed narratives
- negative cases
- very low-confidence classifications
- serious patient outcomes
- discrimination/bias signals
- handoff failures
- error-disclosure cases

---

# Model Validation Priorities

The 100K pipeline completed successfully:

```text
100,000 rows classified
0 unresolved processing failures
```

However, successful processing is not equivalent to human validation.

The analysis identified:

```text
850 zero-confidence rows
21,736 rows below the predefined confidence threshold
1,429 events containing material requiring adjudication
```

Future validation should therefore include:

- stratified human review
- oversampling rare concern cases
- review of zero-confidence outputs
- review of taxonomy-gap cases
- precision
- recall
- F1
- human–LLM agreement
- inter-rater reliability

Accuracy alone should not be used because of the severe class imbalance in narrative performance signals.

---

# Future Research

## Phase 1 — Clean and Validate

Priorities:

- normalize taxonomy-gap labels
- remove missing and placeholder outputs
- review zero-confidence classifications
- conduct stratified human validation
- report precision, recall, F1, and agreement

---

## Phase 2 — Add Row-Level Analysis

Current prevalence estimates are primarily event-level.

Future work should report both:

```text
Event-level prevalence
```

and:

```text
Row-level prevalence
```

as well as:

```text
proportion of narratives within each event containing each code
```

This will distinguish:

> “The theme appeared somewhere in the evaluation”

from:

> “The theme dominated the evaluation.”

---

## Phase 3 — Multivariable Mixed-Effects Modeling

Structured-score analyses should adjust for clustering and confounding.

Possible covariates include:

- program
- specialty
- evaluation type
- evaluator
- trainee
- year
- repeated observations
- rotation context

This would help determine which learning-environment factors remain associated with scores after accounting for contextual differences.

---

## Phase 4 — Longitudinal Modeling

A longitudinal mixed-effects model could investigate:

> **Which learning-environment conditions are associated with better trainee development over time?**

Potential analyses include:

- environment × time interactions
- trainee-specific growth trajectories
- program-level effects
- evaluator effects
- evaluation-type effects

---

## Phase 5 — Prospective Educational Intervention

A future intervention could introduce a structured feedback-writing framework.

For example:

```text
Observed behavior
→ impact/context
→ specific next step
```

Pre/post outcomes could include:

- feedback specificity
- feedback actionability
- learner development
- structured scores
- narrative developmental signals
- psychological safety
- rare concern signals

---

# Central Future Research Question

The current analysis leads to the following question:

> **Which learning-environment conditions are associated with improved trainee development after accounting for program, evaluator, evaluation type, time, and repeated observations?**

---

# Repository Structure

```text
LargeDataSetAnalysis/
│
├── README.md
├── LICENSE
│
├── GMETS Analysis - Rick Rejeleene.pptx
├── GMETS_100K_Analysis_Rick_Rejeleene.pptx
│
├── 50kRows/
│   ├── 01_environment_prevalence.png
│   ├── 02_development_prevalence.png
│   ├── 03_mechanism_prevalence.png
│   ├── 04_confidence_distribution.png
│   ├── 05_performance_signal.png
│   ├── 06_high_vs_low_score_odds_ratios.png
│   ├── 07_environment_cooccurrence.png
│   ├── 08_sensitizing_constructs.png
│   ├── 09_feedback_by_evaluation_type.png
│   ├── 10_environment_over_time.png
│   ├── 11_repeated_evaluatee_change.png
│   ├── 12_taxonomy_gap_concepts.png
│   ├── analysis_payload.txt
│   ├── environment_by_evaluation_type.csv
│   ├── environment_cooccurrence.csv
│   ├── grounded_theory_interpretation.md
│   ├── high_vs_low_score_environment.csv
│   └── program_summary_min10.csv
│
└── 100kRows/
    ├── 01_environment_prevalence.png
    ├── 01_environment_prevalence.pdf
    ├── 02_development_prevalence.png
    ├── 02_development_prevalence.pdf
    ├── 03_mechanism_prevalence.png
    ├── 03_mechanism_prevalence.pdf
    ├── 04_confidence_distribution.png
    ├── 04_confidence_distribution.pdf
    ├── 05_performance_signal.png
    ├── 05_performance_signal.pdf
    ├── 06_high_vs_low_score_odds_ratios.png
    ├── 06_high_vs_low_score_odds_ratios.pdf
    ├── 07_environment_cooccurrence.png
    ├── 07_environment_cooccurrence.pdf
    ├── 08_sensitizing_constructs.png
    ├── 08_sensitizing_constructs.pdf
    ├── 09_feedback_by_evaluation_type.png
    ├── 09_feedback_by_evaluation_type.pdf
    ├── 10_environment_over_time.png
    ├── 10_environment_over_time.pdf
    ├── 11_repeated_evaluatee_change.png
    ├── 11_repeated_evaluatee_change.pdf
    ├── 12_taxonomy_gap_concepts.png
    ├── 12_taxonomy_gap_concepts.pdf
    ├── analysis_payload.txt
    ├── high_vs_low_score_environment.csv
    ├── sensitizing_constructs.csv
    └── taxonomy_gap_concepts.csv
```

---

# Included Visualizations

The repository includes figures examining:

1. learning-environment prevalence
2. developmental-outcome prevalence
3. learning mechanisms
4. model-confidence distribution
5. narrative performance signals
6. high-versus-low structured-score odds ratios
7. learning-environment co-occurrence
8. sensitizing constructs
9. feedback specificity and actionability
10. learning-environment trends over time
11. repeated-evaluatee structured-score change
12. taxonomy-gap concepts

PDF versions are included for many 100K figures to support publication-quality export.

---

# Presentation Files

Two slide decks are included.

```text
GMETS Analysis - Rick Rejeleene.pptx
```

summarizes the earlier analysis.

```text
GMETS_100K_Analysis_Rick_Rejeleene.pptx
```

presents the expanded 100K analysis, including:

- methodology
- input definitions
- LLM outputs
- figures
- interpretation
- non-obvious findings
- practical recommendations
- future research directions

---

# Important Methodological Limitations

These analyses should be interpreted with several limitations in mind.

### Association is not causation

The score-association analyses identify themes that occur more frequently in particular score groups.

They do not prove that those themes caused the observed scores.

### Event-level saturation

Evaluation events can contain many individual narrative responses.

A theme only has to appear once within an event for the event to count as containing the theme.

This can produce high event-level prevalence values.

### LLM confidence is not probability

Model confidence is self-reported by the model and is not statistically calibrated.

### Positive class imbalance

Narrative performance signals are overwhelmingly positive.

This makes standard accuracy an inappropriate validation metric.

### Structured and narrative evaluations differ

Very low agreement between narrative and structured performance bands suggests the two sources may capture different aspects of performance and context.

### Human validation remains necessary

The coding pipeline should not be used for high-stakes educational decisions without independent human validation.

---

# Interpretation

The central interpretation emerging from the 100K analysis is:

> **Trainee development appears to emerge from a relational learning system in which teaching, supervision, psychological safety, feedback, reflection, workload conditions, and progressively increasing responsibility interact.**

A second important finding is:

> **Narrative evaluation comments may be particularly valuable for explaining the context surrounding trainee performance rather than simply reproducing structured numerical scores.**

These findings should be treated as hypothesis-generating and require further validation through adjusted statistical models, longitudinal analysis, and prospective research.

---

# Status

This repository contains research-stage analyses.

The current results are intended for:

- methodological development
- exploratory research
- hypothesis generation
- educational quality-improvement planning
- future manuscript development

They should not yet be interpreted as final causal or policy conclusions.

---

# Data Governance

The repository is intended to contain analytical outputs rather than raw identifiable narrative data.

Researchers using similar pipelines should ensure compliance with:

- institutional data-governance policies
- privacy requirements
- applicable IRB requirements
- data-sharing agreements
- institutional policies governing external publication

Program-level or institutional outputs should be reviewed before public dissemination.

---

# Author

**Rick Rejeleene, PhD**

Artificial Intelligence / Machine Learning  
Graduate Medical Education Analytics

October 2026

---

# License

See:

```text
LICENSE
```

for repository licensing information.

---

# Suggested Citation

If referencing this repository in research or methodological work, a provisional citation format is:

```text
Rejeleene R. Large-Scale GMETS Narrative Evaluation Analysis:
AI-Assisted Mixed-Methods Analysis of Graduate Medical Education Narratives.
GitHub repository, 2026.
```

Formal citation details should be updated if the work is subsequently published in a peer-reviewed journal.

---

# Summary

In short, the 100K GMETS analysis suggests that:

- feedback and supervision are central mechanisms of learning
- psychological safety is a major component of the learning environment
- trainee development extends beyond technical competence
- workload and wellbeing are closely linked to educational context
- lower-scoring evaluations contain more system-level and environmental information
- narrative and structured performance measures capture different signals
- feedback is abundant but only moderately specific and actionable
- the coding taxonomy appears close to saturation
- rare negative and concern narratives may be disproportionately valuable
- future work should move from large-scale discovery toward validation, adjusted modeling, longitudinal analysis, and prospective intervention

The next analytical progression is:

```text
DISCOVER
   ↓
VALIDATE
   ↓
MODEL
   ↓
INTERVENE
   ↓
MEASURE AGAIN
```