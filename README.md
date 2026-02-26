# Hyperparameter Tunability Analysis

Analysis of hyperparameter tunability of selected machine learning algorithms, built as part of a university project.

> **Authors:** [Ada Wojterska](https://github.com/adawojterska), [Katarzyna Skoczylas](https://github.com/kskoczylas), [Miłosz Zieliński](https://github.com/miloszz)  
> **Date:** November 18, 2025  
> 📄 [Full Project Report](./hyperparameter_tunability.pdf)  
> 📄 [Reference Article – Tunability: Importance of Hyperparameters of Machine Learning Algorithms](https://jmlr.org/papers/volume20/18-444/18-444.pdf)

---

## Overview

This project analyzes how sensitive three classification algorithms are to hyperparameter tuning:
**Decision Tree**, **K-Nearest Neighbors (KNN)**, and **XGBoost**. These were chosen to represent
different learning strategies.

We compared two tuning strategies across 4 medical datasets, each run for 100 iterations
per algorithm and evaluated using ROC-AUC:
- **RandomizedSearchCV** (scikit-learn) — random sampling with a fixed seed; includes a *Star*
  configuration computed as the mean of best hyperparameters across all datasets
- **BayesSearchCV** (scikit-optimize) — iterative Bayesian optimization; Star configuration
  not applicable here by design

Hyperparameter ranges were based on the reference article, with minor adjustments to improve
search space coverage and reduce computation time.

---

## Datasets

Four medical binary classification datasets from Kaggle: heart attack, diabetes, breast cancer, and Alzheimer's. Each contains between 800 and 6900 samples, split 75/25 into train and test sets.

Preprocessing included one-hot encoding for categorical features and Min-Max scaling for numerical ones. 

---

## Results

All models benefited from tuning — default configurations consistently achieved the lowest ROC-AUC scores. Bayesian optimization slightly outperformed random search in most cases. The most significant gains from Bayesian optimization occur within the **first 10 iterations**, with improvements becoming marginal after ~20 iterations.

In the [full report](./hyperparameter_tunability.pdf) you can find detailed results, plots, and hyperparameter tables.

---


