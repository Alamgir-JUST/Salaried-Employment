# Salaried Employment as a Conditional Incubator of Entrepreneurial Intention

### The Serial Mediating Role of Financial Security and Risk Appetite in an Emerging Economy

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Python 3.11](https://img.shields.io/badge/python-3.11-blue.svg)](https://www.python.org/)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Alamgir-JUST/Salaried-Employment/blob/main/Salaried_Employment_as_a_Conditional_Incubator.ipynb)
[![Made with Jupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange.svg)](https://jupyter.org/)

This repository hosts the complete data, survey instrument, and analysis code
underpinning the study **"Salaried Employment as a Conditional Incubator of
Entrepreneurial Intention: The Serial Mediating Role of Financial Security and
Risk Appetite in an Emerging Economy."** All materials are shared openly to
support transparent peer review and full reproducibility of the reported
findings.

---

## Table of Contents

- [Overview](#overview)
- [Repository Contents](#repository-contents)
- [The Dataset](#the-dataset)
- [Constructs and Measures](#constructs-and-measures)
- [The Analysis Notebook](#the-analysis-notebook)
- [How to Reproduce the Results](#how-to-reproduce-the-results)
- [Requirements](#requirements)
- [Summary of Hypotheses and Findings](#summary-of-hypotheses-and-findings)
- [Ethics and Consent](#ethics-and-consent)
- [Citation](#citation)
- [Authors](#authors)
- [License](#license)

---

## Overview

The study investigates whether salaried employment constrains or cultivates
entrepreneurial ambition among working adults in Bangladesh. Drawing on the Job
Demands–Resources Theory, Prospect Theory, and the Theory of Planned Behavior,
it tests a conditional process model in which **financial security** and **risk
appetite** serially mediate the relationship between **job conditions** and
**entrepreneurial intention**, with **growth mindset** acting as a
boundary-condition moderator and **sector** and **employment type** as further
boundary conditions.

The model was tested on a cross-sectional survey of **1,001 salaried employees**
across ten occupational sectors, using hierarchical regression, bootstrapped
mediation and serial mediation, moderation and moderated mediation, and MANOVA.

---

## Repository Contents

| File | Description |
|------|-------------|
| `Jobs as Constraints or Stepping Stones.csv` | The raw survey dataset: 1,001 responses across 56 columns (demographics, 5-point Likert items, and open-ended responses). |
| `Questionnaire.pdf` | The full survey instrument as administered, including all demographic, Likert-scale, and open-ended questions. |
| `Salaried_Employment_as_a_Conditional_Incubator.ipynb` | The complete, annotated analysis notebook that reproduces every table and figure in the manuscript. |

---

## The Dataset

**File:** `Jobs as Constraints or Stepping Stones.csv`
**Rows:** 1,001 respondents (plus one header row)
**Columns:** 56

The dataset was collected through an anonymous online survey (Google Forms)
between September and October 2025. Each row is one respondent. No personally
identifiable information was collected.

### Column groups

| Group | Columns | Notes |
|-------|---------|-------|
| **Metadata** | `Timestamp` | Submission time. |
| **Demographics** | `Age`, `Gender`, `Marital Status`, `Higher Education Level`, `Current Sector`, `Job Title / Position`, `Years of Work Experience`, `Employment Type`, `Weekly Working Hours`, `Daily Communication (office to Home) Time` | Categorical / ordinal. |
| **Likert items (1–5)** | 30+ statement items (e.g. *"I have the freedom to decide how I complete my tasks."*) | Measured on a 5-point scale: 1 = Strongly Disagree … 5 = Strongly Agree. These form the six latent constructs below. |
| **Multi-select** | `Barriers`, `Enablers` | Semicolon-separated "check all that apply" responses. |
| **Open-ended** | Three free-text reflection questions | Qualitative, not used in the quantitative model. |

> **Note on scale direction.** Four items are negatively worded (e.g. workload
> burden, repetitive-task overload, preference for stability over independence)
> and are **reverse-coded** inside the notebook before any composite score is
> computed. The raw CSV preserves the original response values.

---

## Constructs and Measures

All multi-item constructs are 5-point Likert composites. The mapping from survey
items to constructs is applied in the notebook's preprocessing cell.

| Construct | Code | Items | Role in model |
|-----------|------|-------|---------------|
| Job Conditions | JC | 8 (job-resource items; 2 demand items removed per JD-R theory) | Antecedent |
| Financial Security | FS | 3 | Primary mediator |
| Skill Accumulation | SK | 3 | Parallel mediator |
| Risk Appetite | RA | 1 | Serial mediator |
| Growth Mindset | GM | 1 | Moderator |
| Entrepreneurial Intention | EI | 3 | Outcome |

Control variables: gender, education level, work experience, and employment
type (contract / part-time dummies, permanent as reference).

---

## The Analysis Notebook

**File:** `Salaried_Employment_as_a_Conditional_Incubator.ipynb`

The notebook is organized to mirror the manuscript, section by section. Running
it top to bottom reproduces every statistic, table, and figure.

1. **Preprocessing** — loads the CSV, renames and maps items to constructs,
   reverse-codes the four negatively-worded items, and builds the six composite
   scores.
2. **Reliability & Validity Analysis** — Cronbach's alpha, exploratory factor
   analysis, AVE and composite reliability, item-total correlations, the
   eight-item Job Conditions refinement, and Harman's single-factor test for
   common method bias.
3. **H1–H4** — hierarchical regression for the direct effects, with HC3 robust
   standard errors, Breusch–Pagan tests, VIF diagnostics, and diagnostic plots.
4. **H5 & H6** — bootstrapped simple mediation and serial mediation
   (5,000 iterations, bias-corrected and accelerated confidence intervals).
5. **H7, H8, H9** — moderation, simple-slopes / Johnson–Neyman probing, and the
   index of moderated mediation.
6. **H10 & H11** — MANOVA, univariate ANOVAs with Tukey post-hoc comparisons,
   sector-specific regression slopes, and parallel mediation with a contrast
   test.
7. **Tables & Results Narrative** — assembles the final tables as reported in
   the paper.

---

## How to Reproduce the Results

### Option A — Google Colab (no setup)

1. Click the **Open in Colab** badge at the top of this README.
2. Upload `Jobs as Constraints or Stepping Stones.csv` to your session (or to
   your Google Drive).
3. Update the data-loading path in the first code cell to point to the CSV, then
   run all cells.

> The notebook was originally authored in Colab and loads the data from a Google
> Drive path. If you are not using Drive, replace that line with a direct read,
> for example:
>
> ```python
> import pandas as pd
> df = pd.read_csv("Jobs as Constraints or Stepping Stones.csv")
> ```

### Option B — Local machine

```bash
# 1. Clone the repository
git clone https://github.com/Alamgir-JUST/Salaried-Employment.git
cd Salaried-Employment

# 2. (Recommended) create a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt   # or the one-line pip install below

# 4. Launch the notebook
jupyter notebook Salaried_Employment_as_a_Conditional_Incubator.ipynb
```

Before running, remove or comment out the two Colab-specific lines
(`from google.colab import drive` and `drive.mount(...)`) and set the CSV path as
shown above.

---

## Requirements

- Python 3.11+
- Jupyter Notebook or JupyterLab

Python packages:

```bash
pip install pandas numpy scipy statsmodels scikit-learn factor_analyzer matplotlib seaborn
```

| Package | Used for |
|---------|----------|
| `pandas`, `numpy` | Data handling and composite scoring |
| `scipy` | Statistical tests |
| `statsmodels` | Regression (HC3), MANOVA, Breusch–Pagan, VIF, Tukey HSD |
| `scikit-learn` | Standardization |
| `factor_analyzer` | Exploratory factor analysis / validity |
| `matplotlib`, `seaborn` | Figures |

---

## Summary of Hypotheses and Findings

All eleven hypotheses were supported.

| # | Hypothesis (abbreviated) | Key result |
|---|--------------------------|-----------|
| H1 | Job conditions → financial security | β = .839, *p* < .001 |
| H2 | Financial security → risk appetite | β = .528, *p* < .001 |
| H3 | Risk appetite → entrepreneurial intention | β = .573, *p* < .001 |
| H4 | Job conditions → entrepreneurial intention | β = .645, *p* < .001 |
| H5 | FS mediates JC → EI | indirect = .237 (35.7% of total) |
| H6 | Serial: JC → FS → RA → EI | serial chain accounts for 53.9% of total |
| H7 | Growth mindset weakens FS → RA (compensatory) | *B* = −.104, *p* < .001 |
| H8 | Employment type moderates JC → FS | *B* = .142, *p* = .002 |
| H9 | Moderated serial mediation (by growth mindset) | IMM = −.045, 95% CI [−.069, −.025] |
| H10 | Sector differences (MANOVA) | Wilks' λ = .772, *p* < .001 |
| H11 | FS and SK as equal parallel mediators | indirects .208 vs .212, contrast n.s. |

> Statistics are reported here for convenience. They are generated by, and should
> be verified against, the notebook output.

---

## Ethics and Consent

Ethical approval was obtained from the Skill Morph Ethics Committee, Dhaka,
Bangladesh (Approval Reference: SkillMorph/ES/2025/03(012)). Participation was
voluntary and anonymous, informed consent was obtained from all respondents, and
no personally identifiable information was collected. All procedures followed the
principles of the Declaration of Helsinki (1964) and its amendments.

---

## Citation

If you use the data, instrument, or code from this repository, please cite the
article:

> Yasmin, F., & Hossain, M. A. (2025). *Salaried Employment as a Conditional
> Incubator of Entrepreneurial Intention: The Serial Mediating Role of Financial
> Security and Risk Appetite in an Emerging Economy.*

```bibtex
@article{yasmin_hossain_salaried_employment,
  title   = {Salaried Employment as a Conditional Incubator of Entrepreneurial
             Intention: The Serial Mediating Role of Financial Security and Risk
             Appetite in an Emerging Economy},
  author  = {Yasmin, Farhana and Hossain, Md. Alamgir},
  year    = {2025},
  note    = {Data, instrument, and code: https://github.com/Alamgir-JUST/Salaried-Employment}
}
```

---

## Authors

- **Farhana Yasmin** — Skill Morph Research Lab.; Department of Sociology, Dhaka
  International University, Dhaka, Bangladesh.
  ORCID: [0000-0001-7605-306X](https://orcid.org/0000-0001-7605-306X)
- **Md. Alamgir Hossain** *(corresponding author)* — Skill Morph Research Lab.;
  Department of Computer Science and Engineering, State University of Bangladesh,
  Dhaka, Bangladesh.
  ORCID: [0000-0001-5120-2911](https://orcid.org/0000-0001-5120-2911)
  · Email: alamgir.cse14.just@gmail.com

---

## License

Unless stated otherwise, the materials in this repository are released under the
[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)
license. You are free to share and adapt the materials with appropriate credit.
