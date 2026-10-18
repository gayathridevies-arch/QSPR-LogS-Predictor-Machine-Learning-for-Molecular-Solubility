# QSPR-LogS-Predictor-Machine-Learning-for-Molecular-Solubility
Here is the complete README.md file text formatted so you can easily copy and paste it straight into GitHub:

Markdown
# QSPR LogS Predictor: Machine Learning for Molecular Solubility

## Project Overview

This repository contains an end-to-end Quantitative Structure-Property Relationship (QSPR) pipeline built to predict the aqueous solubility ($\log S$) of small molecules directly from their 2D chemical structures (SMILES).

By featurizing SMILES strings into **2048-bit Morgan Fingerprints (ECFP4)** via **RDKit**, the pipeline trains a **Random Forest Regressor** to learn non-linear structure-activity relationships on the benchmark **Delaney dataset**.

## Key Performance Metrics

The model was evaluated on a held-out test set ($20\%$ random split, `random_state=42`).

* **Coefficient of Determination ($R^2$):** `0.698`
* **Mean Absolute Error (MAE):** `0.860` log units

These results confirm a strong baseline for quantitative solubility prediction without requiring expensive manual laboratory assays.

## Methodology & Pipeline

1. **Data Ingestion:** Load the benchmark Delaney Dataset containing experimental $\log S$ values.
2. **Molecular Conversion:** Convert raw SMILES representations into RDKit `Mol` objects.
3. **Featurization (ECFP4):** Extract **2048-bit Morgan Fingerprints** ($radius = 2$) to capture circular atomic environments.
4. **Data Splitting:** Perform an $80/20$ Train/Test split for robust validation.
5. **Model Training:** Fit a Random Forest Regressor ($n\_estimators = 100$) on the training set.
6. **Evaluation & Visualization:** Evaluate using $R^2$ and MAE metrics, and plot experimental vs. predicted solubility values against an ideal reference target line ($y = x$).

## Tech Stack & Dependencies

* **Language:** Python
* **Cheminformatics:** `rdkit`
* **Machine Learning:** `scikit-learn`
* **Data Processing & Numerical Operations:** `pandas`, `numpy`
* **Visualization:** `matplotlib`
