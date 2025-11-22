# Interpretable_Multi_Omics_Integration_for_Breast_Cancer_Severity_Prediction_using_QLattice
Interpretable_Multi_Omics_Integration_for_Breast_Cancer_Severity_Prediction_using_QLattice_Symbolic_Regression
# Interpretable Multi-Omics Integration for Breast Cancer Prediction using QLattice

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-Feyn%20(QLattice)-purple)
![Type](https://img.shields.io/badge/Machine%20Learning-Symbolic%20Regression-green)
![Status](https://img.shields.io/badge/Status-Prototype-orange)

## 📌 Overview

This project implements an **Interpretable Machine Learning** pipeline for predicting Breast Cancer severity. Unlike "black-box" models (like Neural Networks) that provide predictions without explanation, this project uses **Symbolic Regression** via the **QLattice (Quantum Lattice)** engine to generate a transparent, mathematical equation that describes the relationship between biological features and disease severity.

The approach integrates heterogeneous Multi-Omics data sources to simulate a realistic bioinformatics workflow.

## 🧬 Key Features

* **Multi-Omics Data Integration**: Simulates and combines three distinct layers of biological data:
    * **Transcriptomics (mRNA)**: Gene expression levels.
    * **Genomics (CNV)**: Copy Number Variations.
    * **Clinical Data**: Patient age and tumor size.
* **Symbolic Regression**: Uses the `feyn` library to search for mathematical expressions that best fit the data.
* **White-Box Modeling**: The final output is not a matrix of weights, but a readable mathematical formula (e.g., `Severity = tanh(Gene_A * Age) + ...`).
* **Synthetic Data Generation**: Includes a robust generator to create realistic, non-linear biological relationships for testing without requiring external datasets.

## 🛠️ Technologies Used

* **Python 3.x**
* **[Feyn](https://docs.abzu.ai/)**: The Python client for the QLattice, used for Symbolic Regression.
* **Pandas & NumPy**: Data manipulation and synthetic data generation.
* **Scikit-Learn**: Data splitting and performance metrics (ROC AUC, Accuracy).
* **Matplotlib & Seaborn**: Visualization of feature distributions and model performance.

## 📊 Methodology

### 1. Data Simulation
The notebook generates a synthetic dataset to mimic the complexity of cancer biology:
- **Features**: Creates random distributions for Genes, CNVs, and Clinical factors.
- **Target Logic**: Defines a ground truth (Severity) based on non-linear interactions (e.g., `Gene_1 * Gene_2 + log(Tumor_Size)`), allowing us to verify if the model can "rediscover" the underlying biology.

### 2. The QLattice (Quantum Lattice)
Instead of training weights, the QLattice explores an infinite space of potential mathematical models.
1.  **Register**: The features are registered with semantic types (numerical, categorical).
2.  **Search**: The `ql.auto_run` function iterates through thousands of mathematical graphs, keeping the fittest models based on accuracy and simplicity (Occam's Razor).
3.  **Selection**: The best performing graph is selected as the final model.

### 3. Evaluation
The model is evaluated on a hold-out test set using:
- **ROC AUC Score**: To measure classification capability.
- **Confusion Matrix**: To visualize True Positives/Negatives.
- **Interpretability Check**: Visualizing the actual mathematical graph.

## 💻 Installation & Usage

### Prerequisites
You will need to install the `feyn` library along with standard data science tools.

```bash
pip install feyn pandas numpy scikit-learn matplotlib seaborn
