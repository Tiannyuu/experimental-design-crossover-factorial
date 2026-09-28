# Experimental Design: Crossover & Factorial RCT Analysis

Two randomized field experiments analyzed end to end — a **crossover trial** and a
**2×2 factorial design** testing whether supplementary drinking water improves hydration
and cognitive performance in schoolchildren, plus a matched-pair **cluster RCT** on
maternal-health incentives.

**Key results:** water significantly improved afternoon hydration · significant positive
effect on reverse number recall, significant *negative* effect on line tracing · a large
**practice effect** (better scores on day 2 regardless of condition) confounds the
cognitive conclusions — a textbook lesson in experimental validity.

Capstone project for INF2178 (University of Toronto).

## Research questions

**Project 2 (code in this repo):** In water-scarce settings, does providing supplementary
drinking water to schoolchildren improve their hydration status and cognitive performance?
107 students (grades 5–6) from two rural primary schools in Mali each experienced two
conditions: a control day (normal school conditions) and a water day (1.5L refillable
bottle). Outcomes: afternoon hydration (urine specific gravity) and six cognitive tests
(visual attention, visual memory, short-term memory, visuomotor skills).

**Project 1 (report only):** Does paying financial incentives to community-based
volunteers improve maternal-health behaviors in rural Zambia? A matched-pair cluster
randomized trial across 98 rural health facilities.

## Methods

- **Hypothesis 1 — crossover design:** water intervention → short-term memory
  (Number Recall Reverse scores), controlling for visit-order effects. Two-way ANOVA
  with **blocking** (school) vs **covariate** (SGAM) specifications, Tukey HSD post-hoc.
- **Hypothesis 2 — 2×2 factorial design:** water × breakfast status → visual attention
  (Letter Cancellation scores). Two-way ANOVA with blocking (morning dehydration) vs
  covariate (age), plus **power analysis** (FTestAnovaPower, Cohen's f = 0.5).
- Data: 214 observations (107 students × 2 visits) — committed in `data/` with codebook.

## Key findings

| Analysis | Result |
|---|---|
| Hydration | Water day → significantly better afternoon hydration (lower urine specific gravity) |
| Cognition (H1) | Significant positive effect on reverse number recall |
| Cognition (H2) | Mixed — incl. a significant *negative* effect on line tracing |
| Validity check | Large **practice effect**: students scored better on day 2 regardless of water provision, clouding causal claims about cognition |
| Zambia cluster RCT | No significant effect on 1st-trimester ANC initiation; ~29% increase in accompanied visits; improved institutional delivery rate |

Full write-up: [`docs/capstone_report.pdf`](docs/capstone_report.pdf)

## Repo structure

```
├── notebooks/
│   └── experimental_design_analysis.ipynb   # full analysis (rendered with outputs on GitHub)
├── data/
│   ├── project2_data.csv                    # trial data (214 observations)
│   └── codebook.csv                         # variable codebook
├── docs/
│   └── capstone_report.pdf                  # capstone report (both projects)
```

## How to run

```
# 1. install dependencies
pip install pandas numpy statsmodels seaborn matplotlib jupyter

# 2. open the notebook
jupyter notebook notebooks/experimental_design_analysis.ipynb
```

Run cells top to bottom. The notebook loads data from `../data/project2_data.csv`
relative to the notebook location (the original Colab drive-mount cell was removed —
no logic changed).

## Tech stack

Python · pandas · statsmodels (OLS ANOVA, Tukey HSD, power analysis) · seaborn ·
matplotlib · Jupyter
