# AI Programming Foundations – Project 1

## Project Description
This project builds a reproducible data workflow on the provided dataset. It covers:
1) loading and inspecting the raw data.  
2) cleaning and preparing the dataset for analysis/modeling.  
3) exploratory data analysis (EDA) with visualizations.  
4) interpreting results and documenting assumptions/limitations.  

The goal is to produce a clear, repeatable workflow that another person can run and obtain the same outputs.

## Dataset
**Titanic – Machine Learning from Disaster (Kaggle)**  
https://www.kaggle.com/c/titanic/data

## Reproducibility Instructions

### 1) Environment
- Python 3.x
- Common libraries used:
  - pandas
  - numpy
  - matplotlib
  - seaborn 

### 2) How to Run
1. Open the notebook file in Jupyter or VS Code.
2. Run the cells from top to bottom in order.
3. Make sure the dataset files are in the same relative path expected by the notebook.

### 3) Key Inputs / Outputs
- **Inputs:** the original dataset files as provided.
- **Outputs:** cleaned dataset in-memory as a CSV, plus EDA figures rendered in the notebook.

## Visualization Interpretation 
### Plot 1 — Fare Distribution by Survival
Passengers who survived generally paid higher fares than those who did not. The median fare is noticeably higher for survivors, and there are several high-fare outliers among them. This suggests that wealth and passenger class was strongly associated with survival.
<img width="900" height="600" alt="viz_fare_by_survival" src="https://github.com/user-attachments/assets/c5ad4979-22ef-4652-a914-da84546dae61" />

### Plot 2 — Survival Rate by Sex
Female passengers had a much higher survival rate (about 70–75%) compared to male passengers (about 18–20%). This supports the historical “women and children first” policy and shows that sex is a strong predictor of survival.
<img width="900" height="600" alt="viz_survival_by_sex" src="https://github.com/user-attachments/assets/dd8f138b-9cdd-452f-9416-0ebbfa358ed1" />

### Plot 3 — Age Distribution by Survival
Age distributions for survivors and non-survivors overlap, but younger passengers—especially children—show slightly higher survival rates. Age appears to influence survival, but less strongly than sex or fare.
<img width="1050" height="600" alt="viz_age_by_survival" src="https://github.com/user-attachments/assets/d8164dc1-bea5-47c4-ab30-c39c483adab4" />

## Future Integration Reflections

### 1) What changes would you make to the ML workflow to improve results?
For a traditional machine learning model, additional preprocessing would include:
- Train/validation splitting.
- One-hot encoding of categorical variables.
- Feature scaling for numeric features.
- Cross-validation and performance metrics.

### 2) What additional preparation would be needed for a neural network approach?
To prepare for neural networks, I would:
- All features must be numeric tensors.
- Continuous features would require normalization.
- Missingness could be handled with imputation plus missing-indicator variables.
- Feature engineering would be more critical for stable training.


### 3) Where could agentic automation help in this workflow?
Agentic automation could improve productivity and reliability in several places:
- Automatically generating data quality reports (missingness, outliers, schema drift).
- Suggesting cleaning steps based on detected issues (e.g., inconsistent categories).
- Running EDA templates and producing standardized summaries.



## Bias Awareness 

Poor data cleaning can introduce bias in multiple ways:
- **Selective row dropping:** If missing values are more common for certain groups, dropping those rows removes those groups disproportionately, skewing results.
- **Imputation bias:** Imputing with a single global mean/median can overwrite genuine group differences and reduce fairness.
- **Encoding and category merging:** Inconsistent category cleaning can erase meaningful differences, affecting downstream decisions.
- **Outlier removal:** Removing outliers without understanding context can remove valid cases that are more common in a specific subgroup, leading to under-representation.
- **Label or target leakage mistakes:** Cleaning steps that accidentally use information from the target in feature preprocessing can inflate performance and hide real-world disparities.

To reduce these risks, cleaning decisions should be documented, validated with subgroup checks, and tested with sensitivity analyses (compare results before/after key cleaning steps).



