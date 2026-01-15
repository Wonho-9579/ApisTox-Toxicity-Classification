# ApisTox-Toxicity-Classification
Binary classification project predicting honey bee toxicity using machine learning and chemical features


# ApisTox – Honey Bee Toxicity Classification

## Overview
This project aims to predict whether a chemical compound is toxic to honey bees
using tabular data and molecular descriptors.
The primary objective is to achieve high recall for the toxic class in order to
minimize false negatives in ecological risk assessment.

---

## Dataset
- Binary classification dataset (~1,000 samples)
- Target variable: `label` (0 = non-toxic, 1 = toxic)
- Class imbalance present (toxic class ≈ 30%)
- Dataset compiled by integrating information from:
  - ECOTOX (U.S. EPA)
  - PPDB (Pesticide Properties Database)
  - BPDB (Bio-Pesticides Database)

> Raw data files are not included in this repository due to data source and licensing considerations.

---

## Methodology
1. **Preprocessing**
   - Removed identifier and leakage-prone variables
   - One-hot encoded categorical features
   - Added physicochemical descriptors from SMILES strings using RDKit

2. **Feature Engineering**
   - Generated 15 RDKit molecular descriptors (e.g., MolWt, MolLogP, TPSA)
   - Verified successful SMILES parsing with no missing descriptor values

3. **Modeling**
   - Train/test split with stratification
   - Applied SMOTE **only to the training set** to address class imbalance
   - Trained a tuned Random Forest classifier

4. **Evaluation**
   - Focused on toxic-class recall and Precision–Recall AUC
   - Evaluated performance using a confusion matrix and PR curve

5. **Interpretation**
   - Analyzed feature importance to identify key drivers of toxicity
   - Emphasized interpretability and domain consistency

---

## Results
- Strong recall for the toxic class
- High Precision–Recall AUC, indicating robust performance on imbalanced data
- Feature importance highlights the relevance of agrochemical indicators
  and physicochemical properties such as MolLogP and MolWt

---

## Repository Structure

ApisTox-Toxicity-Classification/
├── notebooks/
│   └── apistox.ipynb
├── images/
│   ├── class_distribution.png
│   ├── confusion_matrix.png
│   ├── pr_curve.png
│   └── feature_importance.png
├── requirements.txt
└── README.md


## How to Run

1. Clone this repository.
2. Create a `data/` directory in the project root.
3. Place the dataset file inside the directory and name it:

   `data/dataset_final.csv`

4. Open and run `notebooks/apistox.ipynb`.

> **Note:**  
> The dataset is not included in this repository due to licensing considerations.  
> If running on Google Colab, upload the dataset to `/content/data/dataset_final.csv` before execution.


## Tools & Libraries
- Python
- pandas, numpy
- scikit-learn
- imbalanced-learn
- RDKit
- matplotlib
