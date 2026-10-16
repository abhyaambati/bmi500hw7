# BMI 500: Week 7 Homework (HW3)

**Student:** Abhya Ambati  
**Email:** aambat3@emory.edu  
**Course:** BMI 500  
**Assignment:** Week 7 Homework (HW3)  
**Repository:** [abhyaambati/bmi500hw7](https://github.com/abhyaambati/bmi500hw7)

## Overview

This repository documents Week 7 Homework (HW3) for BMI 500. The assignment explores age-related trends in systolic and diastolic blood pressure (Part A), followed by synthetic population simulation, classification, and an analysis of accuracy–equity trade-offs (Part B).

## Repository Structure

The repository's existing README describes the following organization:

```text
bmi500hw7/
├── partA/
│   └── partA.ipynb
├── partB/
│   └── partB.ipynb
├── Hypothesis.pdf
└── README.md
```

> **File verification note:** This structure is based on the repository's published README. The notebook files could not be retrieved at the time this documentation was prepared; confirm their paths and commit them if needed.

## Part A: Blood Pressure Modeling vs. Age

### Objective

Compare alternative parametric models for how blood pressure varies with age, focusing on systolic blood pressure (SBP) and diastolic blood pressure (DBP).

### Approach and Discussion

- **SBP:** Compare a quadratic polynomial model with a nonlinear sigmoid model. A sigmoid can represent increasing blood pressure followed by a plateau at older ages.
- **DBP:** Compare a quadratic polynomial model with a Gaussian (bell-shaped) model. A bell-shaped relationship can represent an increase followed by a decrease at older ages.
- **Model evaluation:** Examine mean squared error (MSE), coefficient of determination (\(R^2\)), and, where computed, Akaike and Bayesian information criteria (AIC/BIC). Lower MSE and information criteria generally indicate better performance for comparable models, while higher \(R^2\) indicates more explained variation.

### Hypothesis Revisited

**Hypothesis:** SBP rises nonlinearly and may level off with age, while DBP follows a hump-shaped trajectory.

**Interpretation:** These shapes are consistent with age-associated vascular changes, including arterial stiffening and widening pulse pressure. The originally reported analysis favored nonlinear specifications. Numerical metrics and plots should be read directly from `partA/partA.ipynb` and should be checked before treating these conclusions as confirmed.

## Part B: Bivariate Population Simulation and Fairness Analysis

### Objective

Simulate correlated SBP/DBP measurements for two demographic groups and explore how a classifier's decision threshold affects aggregate performance and between-group metrics.

### Approach and Discussion

1. Generate synthetic bivariate-normal blood pressure measurements with group-specific means, standard deviations, and correlation parameters.
2. Train a logistic regression classifier to predict the simulated demographic label from blood pressure measurements.
3. Evaluate accuracy, F1 score, and area under the ROC curve (AUC) on a balanced evaluation dataset.
4. Sweep the classification threshold from 0 to 1 and study how accuracy and group-level recall vary.

**Results described in the assignment draft:** approximately 0.50 accuracy, 0.67 F1 score, and 0.63 AUC. These figures are reproduced from the supplied draft and **have not been independently verified** against notebook output.

### Accuracy–Equity Trade-off

The original draft defines disparity as:

\[
\phi = \left|\operatorname{recall}_{\mathrm{male}}-\operatorname{recall}_{\mathrm{female}}\right|.
\]

Inspect the threshold sweep to determine whether reducing the reported disparity lowers overall classification accuracy. Because the class being predicted is itself a demographic label, recall must be precisely defined for each group; consider class-specific true-positive rates and false-negative rates rather than assuming a generic fairness interpretation of the recall gap.

### Hypothesis Revisited

**Hypothesis:** Optimizing only for aggregate predictive performance can produce uneven classification results across demographic groups.

**Interpretation:** The proposed threshold analysis illustrates that a decision rule can change group-specific outcomes even when the underlying model remains fixed. Whether the trade-off is empirically demonstrated, and how large it is, depends on the notebook's actual results.

## AI Use Statement

**Statement: ChatGPT was used to complete this homework. The full chat is available at:**  
(https://chatgpt.com/share/6ad28c84-db6c-83ea-a362-5f6b0d0ccfcd)

ChatGPT was used **only to generate and format this README.md documentation**. It was not used to write the homework code, perform the analysis, or produce the results.



## Running the Notebooks

### Prerequisites

- Python 3.9 or newer
- Jupyter Notebook or JupyterLab
- Dependencies used by the notebooks, likely including NumPy, pandas, Matplotlib, SciPy, and scikit-learn (verify imports in the notebooks)

### Setup

```bash
git clone https://github.com/abhyaambati/bmi500hw7.git
cd bmi500hw7

python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate

python -m pip install jupyter numpy pandas matplotlib scipy scikit-learn
```

Open the notebooks, provided they are committed at the documented paths:

```bash
jupyter notebook partA/partA.ipynb
```

In a separate command or Jupyter session:

```bash
jupyter notebook partB/partB.ipynb
```

Run all cells in order and compare the output metrics and figures with the results discussed above.

## Submission Notes

- Ensure `partA/partA.ipynb`, `partB/partB.ipynb`, and `Hypothesis.pdf` exist in the repository at the paths shown.
- Check that required datasets are included or described, if the notebooks load external files.
- Verify all reported model-comparison statistics and classification scores using the notebook output.
- Confirm the AI use statement accurately reflects the work performed and complies with course policy.
