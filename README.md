# Telecom Customer Churn — Data Mining with Orange

A comprehensive data mining project for predicting customer churn in the telecommunications industry. Built entirely in **Orange**, an open-source visual data mining platform, the project covers the full pipeline from data preprocessing and EDA to supervised learning, unsupervised learning, association rule mining, and dimensionality reduction.

---

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Workflow Overview](#workflow-overview)
- [Techniques & Methods](#techniques--methods)
- [Tools & Technologies](#tools--technologies)
- [How to Run](#how-to-run)

---

## Overview

Customer churn — when subscribers cancel their telecom service — is a major business challenge. This project uses data mining techniques to discover patterns in customer behavior and build models capable of predicting churn. The analysis is organized into three parallel tracks: **supervised learning** on the original data, supervised learning **on k-Means clusters**, and supervised learning **on Hierarchical Clustering outputs**, allowing for a comparison of how clustering as a preprocessing step affects classification performance.

---

## Dataset

**File:** `churn telekom.csv`

The dataset contains records for telecom customers from various US states, with features covering usage patterns, account details, and subscription plans.

| Feature | Description |
|---|---|
| `State` | US state of the customer |
| `Account Length` | Number of days as a customer |
| `Area Code` | Customer area code |
| `Int'l Plan` | Whether the customer has an international plan |
| `VMail Plan` | Whether the customer has a voicemail plan |
| `VMail Message` | Number of voicemail messages |
| `Day Mins` / `Day Calls` / `Day Charge` | Daytime usage |
| `Eve Mins` / `Eve Calls` / `Eve Charge` | Evening usage |
| `Night Mins` / `Night Calls` / `Night Charge` | Nighttime usage |
| `Intl Mins` / `Intl Calls` / `Intl Charge` | International usage |
| `CustServ Calls` | Number of customer service calls |
| `Churn?` | **Target variable** — whether the customer churned |

---

## Project Structure

```
Churn-Telekom/
│
├── churn telekom.csv            # Dataset
└── churn_model_comparison.ows   # Orange workflow with all analyses
```

---

## Workflow Overview

The Orange workflow (`churn_model_comparison.ows`) is organized into several interconnected sections:

**1. Data Loading & EDA**
- Load dataset → Data Table, Scatter Plot
- Select relevant features with Select Columns

**2. Supervised Learning — Original Data**
- Preprocessing: Discretize, then Select Columns for association rules
- Classification models: Decision Tree, Logistic Regression, Random Forest, AdaBoost, Stacking (ensemble)
- Evaluation: Test and Score (cross-validation), Confusion Matrix, ROC Analysis, Performance Curve (Lift), Predictions
- Visualization: Tree Viewer, Nomogram (Logistic Regression feature weights)

**3. Unsupervised Learning**
- **Outlier detection** → Preprocessor (normalization) applied before all clustering
- **k-Means clustering** (k=2–8, optimized): Silhouette Plot for cluster quality, Data Table for cluster assignments
- **Hierarchical Clustering** (Ward linkage): Dendrogram + Data Table of selected clusters
- **DBSCAN** clustering with Distribution and Decision Tree visualization per cluster
- **Self-Organizing Map (SOM)**
- **PCA** (9 components): projected data and component loadings
- **Association Rule Mining**: Discretize → Frequent Itemsets → Association Rules + Sieve Diagram

**4. Supervised Learning on Cluster Subsets**
- After k-Means: Select cluster subset → Decision Tree, Logistic Regression, Random Forest, AdaBoost, Stacking → Test and Score, Confusion Matrix, ROC, Performance Curve, Predictions, Nomogram
- After Hierarchical Clustering: same classification pipeline applied to the selected cluster
- After DBSCAN: same classification pipeline applied to the DBSCAN output

---

## Techniques & Methods

**Supervised Learning (Classification)**
- Decision Tree
- Logistic Regression
- Random Forest (22 estimators, max depth 3, max features 13)
- AdaBoost (100 estimators, learning rate 0.5)
- Stacking (ensemble of the above four models)
- Evaluation: 2-fold cross-validation, metrics include CA, AUC, Precision, Recall, F1, MCC

**Unsupervised Learning (Clustering)**
- k-Means (k optimized from 2 to 8, evaluated with Silhouette score)
- Hierarchical Clustering (Ward linkage, distance-based)
- DBSCAN (density-based, with normalization)
- Self-Organizing Map (SOM)

**Dimensionality Reduction**
- PCA (9 components, normalized)

**Association Rule Mining**
- Discretization of continuous features
- Frequent Itemsets (min support 25%)
- Association Rules (min confidence 75%, min support 25%)
- Sieve Diagram for rule visualization

**Outlier Detection**
- Applied before unsupervised learning to clean the data before clustering

---

## Tools & Technologies

- **[Orange 3](https://orangedatamining.com/)** — visual data mining and machine learning platform
  - Core Orange3 for all standard widgets
  - `Orange3-Associate` add-on for association rule mining (`orangecontrib.associate`)
- Workflow format: `.ows`

> **Note:** The `Orange3-Associate` add-on must be installed separately. In Orange, go to `Options → Add-ons` and install **Associate**.

---

## How to Run

1. **Install Orange** from [https://orangedatamining.com/download/](https://orangedatamining.com/download/)

2. **Install the Associate add-on**:
   - Open Orange → `Options → Add-ons`
   - Search for `Associate` and install it
   - Restart Orange

3. **Clone or download this repository**:
   ```bash
   git clone https://github.com/andjeladimic/Churn-Telekom.git
   ```

4. **Open Orange** and load the workflow:
   - `File → Open → churn_model_comparison.ows`

5. The workflow will automatically load `churn telekom.csv` and run all analyses. Click on individual nodes to inspect results, visualizations, and model comparisons.

---

## Author

**Anđela Dimić** 
