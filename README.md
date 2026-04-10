# Home Credit Default Risk Prediction 📊

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-LightGBM%20%7C%20XGBoost-orange.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

## 📌 Project Overview

This repository contains a machine learning pipeline developed to predict clients' repayment abilities for the [Home Credit Default Risk](https://www.kaggle.com/competitions/home-credit-default-risk/overview) competition on Kaggle. The goal is to ensure that clients capable of repayment are not rejected and that loans are given with a principal, maturity, and repayment calendar that will empower them to be successful.

## 🎯 The Challenge

Home Credit provides loans to people with little or no credit history. The main challenge of this dataset is its highly relational nature and massive size. It requires merging multiple large-scale datasets (application, bureau, previous applications, and installments) to extract meaningful temporal features.

## 🚀 Key Approach & Technical Highlights

### 1. Advanced Feature Engineering

- Aggregated historical data from multiple tables (`bureau.csv`, `installments_payments.csv`, etc.) using pandas.
- Created domain-specific features (e.g., credit-to-income ratio, annuity-to-income ratio).

### 2. Memory Management Optimization

Processing multiple gigabytes of data often leads to Out-Of-Memory (OOM) errors, especially in restricted environments like Google Colab. To resolve this, the pipeline includes:

- **Data Downcasting:** Custom functions to dynamically reduce numerical data types (e.g., `float64` to `float32`, `int64` to `int8`) without losing information.
- **Garbage Collection:** Strategic use of `gc.collect()` and deleting temporary dataframes immediately after merging to free up RAM.

### 3. Model Training

Trained and evaluated advanced gradient boosting models to maximize the AUC (Area Under the ROC Curve) metric:

- **LightGBM:** Used for its fast training speed and low memory usage on large datasets.
- **XGBoost & CatBoost:** Utilized to capture complex non-linear relationships.

## 📂 Repository Structure

```text
home-credit-default-risk/
├── data/                           # (Not tracked by Git) Put Kaggle raw data here
├── notebooks/
│   ├── eda.ipynb                # Exploratory Data Analysis
│   └── feature_engineering.ipynb# Feature creation & Memory optimization
├── requirements.txt                # Project dependencies
├── .gitignore                      # Git ignore rules
└── README.md                       # Project documentation
```

## ⚙️ How to Run

1. **Clone the repository:**

   ```bash
   git clone https://github.com/Nhb170405/Home-credit-default-risk.git
   cd Home-credit-default-risk
   ```

2. **Install dependencies:**
   Bash
   pip install -r requirements.txt
   Download Data:

3. **Download Data:**
   Download the dataset from the Kaggle Competition Page.

Extract all .csv files into the data/ folder.

4.  **Run Notebooks:**
    Open and execute the notebooks in the notebooks/ directory sequentially, starting from eda.ipynb.
