# Telecom Customer Churn — Data Mining with Orange

A data mining project analyzing customer churn in the telecommunications industry. The project applies supervised learning, unsupervised learning, association rule analysis, and dimensionality reduction — all built using the **Orange** visual data mining tool.

---

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Techniques & Methods](#techniques--methods)
- [Project Structure](#project-structure)
- [Tools & Technologies](#tools--technologies)
- [How to Run](#how-to-run)

---

## Overview

Customer churn — when subscribers leave a service provider — is one of the most costly challenges in the telecom industry. This project uses data mining techniques to uncover patterns and build models that can identify customers at risk of churning.

Unlike traditional Python-based ML pipelines, this project is built entirely in **Orange**, a powerful open-source data science platform with a visual, node-based workflow interface that makes data mining accessible and interpretable.

---

## Dataset

**File:** `churn telekom.csv`

The dataset contains information about telecom customers including demographics, services subscribed, account details, and churn status.

Typical features include:

| Feature | Description |
|---|---|
| `gender` | Customer gender |
| `SeniorCitizen` | Whether the customer is a senior citizen |
| `Partner` / `Dependents` | Relationship and family status |
| `tenure` | Number of months as a customer |
| `PhoneService`, `InternetService` | Subscribed services |
| `Contract` | Contract type (month-to-month, one year, two year) |
| `MonthlyCharges` / `TotalCharges` | Billing information |
| `Churn` | **Target variable** — whether the customer churned (Yes/No) |

---

## Techniques & Methods

This project explores multiple data mining approaches:

**Supervised Learning (Classification)**
- Predicting churn using classification algorithms (e.g., Logistic Regression, Decision Tree, Random Forest, Naive Bayes)
- Model comparison and evaluation using accuracy, precision, recall, F1-score, and AUC

**Unsupervised Learning (Clustering)**
- Customer segmentation using clustering methods (e.g., k-Means)
- Discovering natural groupings within the customer base

**Association Rule Analysis**
- Mining frequent patterns and associations between customer attributes and churn behavior

**Dimensionality Reduction**
- Applying techniques such as PCA to reduce feature space and improve visualization and model performance

---

## Project Structure

```
Churn-Telekom/
│
├── churn telekom.csv            # Dataset
└── churn_model_comparison.ows   # Orange workflow (all models & analyses)
```

---

## Tools & Technologies

- **[Orange](https://orangedatamining.com/)** — open-source visual data mining and machine learning tool
  - Version: Orange 3.x
  - Workflow format: `.ows`

No additional Python installation is required — everything runs through the Orange GUI.

---

## How to Run

1. **Install Orange** from the official website: [https://orangedatamining.com/download/](https://orangedatamining.com/download/)

2. **Clone or download this repository**
   ```bash
   git clone https://github.com/andjeladimic/Churn-Telekom.git
   ```

3. **Open Orange** and load the workflow:
   - Go to `File → Open`
   - Select `churn_model_comparison.ows`

4. The workflow will automatically load the dataset and run all analyses. You can interact with individual nodes to explore results, visualizations, and model comparisons.

---

## Author

**Anđela Dimić**
