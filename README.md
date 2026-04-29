# asthma-data-challenge-ml
Machine learning project on asthma exacerbation prediction, regression and synthetic health data generation.

# Data

The original dataset is not shared publicly for confidentiality reasons.

The project was developed on anonymized health data related to asthma patients.
The dataset included clinical, treatment and healthcare cost variables.

To reproduce the project, use a file with the same structure as the original dataset.

presentations/.gitkeep

## Presentations

### Part 1 — kNN Asthma Classification

[![Part 1 Presentation](presentations/part1_preview.png)](presentations/DC2_Partie1_kNN_Asthme.pdf)

Short presentation of the classification pipeline: preprocessing, kNN, imbalance handling and threshold optimization.

### Part 3 — Synthetic Data Generation

[![Part 3 Presentation](presentations/part3_preview.png)](presentations/DC2_Partie3_Donnees_Synthetiques.pdf)

Overview of the synthetic data generation method based on Avatar: use of k-nearest neighbors, Dirichlet distribution and barycentric interpolation to create realistic and privacy-preserving health data.

# Asthma Data Challenge – Machine Learning & Synthetic Health Data

## Overview

This project was developed as part of a health data science challenge focused on asthma patients.

The project combines three complementary tasks:

1. Predicting the occurrence of asthma exacerbations within one year
2. Predicting the number of asthma exacerbations within one year
3. Generating realistic synthetic health data while preserving patient confidentiality

The goal is to apply machine learning methods to real-world anonymized health data and explore both predictive modeling and privacy-preserving data generation.

---

## Project Objectives

### Part 1 – Classification

The first objective is to predict whether a patient will experience at least one asthma exacerbation during the following year.

The target variable is derived from:

`post_index_exacerbations365`

It is recoded as:

- `0`: no exacerbation
- `1`: at least one exacerbation

The final output is a CSV file containing:

- `patid`
- `prediction`

---

### Part 2 – Regression

The second objective is to predict the number of asthma exacerbations occurring within one year.

This is a count prediction problem, evaluated with a Poisson log-likelihood metric.

The final output is a CSV file containing:

- `patid`
- `prediction`

where `prediction` is an integer representing the predicted number of exacerbations.

---

### Part 3 – Synthetic Data Generation

The third objective is to generate realistic synthetic health data that preserves the statistical properties of the original dataset while protecting patient confidentiality.

The approach is inspired by the Avatar method, using:

- k-nearest neighbors
- standardized patient profiles
- weighted barycenters
- Dirichlet distribution
- post-processing to ensure clinically realistic values

---

## Methods

### Data Preprocessing

The preprocessing pipeline includes:

- Missing value imputation
- Standardization of numerical variables
- Encoding of categorical variables
- Feature selection
- Removal of identifiers and potential data leakage variables

---

## Machine Learning Models

### Classification

A k-Nearest Neighbors model was used to predict the occurrence of exacerbations.

The classification pipeline includes:

- SimpleImputer
- StandardScaler
- OneHotEncoder
- SelectKBest
- kNN classifier
- Oversampling to handle class imbalance
- Decision threshold optimization based on F1-score

---

### Regression

Regression models were used to predict the number of exacerbations.

This part focuses on count prediction and model evaluation using Poisson log-likelihood.

---

### Synthetic Data

Synthetic patients were generated using a local neighbor-based approach.

Main steps:

1. Standardize the original data
2. Identify k nearest neighbors for each patient
3. Generate synthetic profiles using weighted combinations
4. Apply post-processing to ensure realistic values
5. Evaluate utility and confidentiality

Evaluation metrics include:

- Wasserstein distance
- Correlation difference
- Distance to Closest Record (DCR)

---

## Results

### Classification

The kNN model obtained realistic results for a difficult medical prediction task with imbalanced classes.

The goal is not to predict asthma perfectly, but to identify a population at higher risk that could benefit from closer monitoring.

### Synthetic Data

The synthetic data generation approach showed a good balance between utility and confidentiality.

Reported evaluation metrics:

- Wasserstein distance: 0.0975
- Correlation difference: 0.0105
- Distance to Closest Record: 0.8780

These results suggest that the generated data preserve statistical properties while reducing the risk of patient re-identification.

---
## Technologies

- Python
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- scipy
- Jupyter Notebook

---

## Important Note

The original dataset is not shared publicly due to confidentiality and health data protection concerns.

Only code, documentation, presentations and non-sensitive outputs are included.

---

## Author

PART 1
ASAS Nedah 
DURIMEL Yohaldère 
MHAIMID Mohammed
SAAD Fatima Zahra

PART 2
ATHMANE Mohamed Anis
DURIMEL Yohaldère
Mously Rym

PART 3
ASAS Nedah
DURIMEL Yohaldère
MUGISHA Abelard
 
Master 1 Intelligence en données de santé  
Université de Strasbourg  

GitHub: https://github.com/DurimelY  
LinkedIn: https://www.linkedin.com/in/yohaldère-durimel-a78003386

## Repository Structure

```text
asthma-data-challenge-ml/
│
├── README.md
├── requirements.txt
├── data/
├── notebooks/
├── presentations/
└── results/
