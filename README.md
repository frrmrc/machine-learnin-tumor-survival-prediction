
<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?logo=python" alt="Python">
  <img src="https://img.shields.io/badge/ML%20Task-Regression-orange" alt="Regression">
  <img src="https://img.shields.io/badge/Data%20Cleaning-Missing%20Values%2C%20Encoding-brightgreen" alt="Data Cleaning">
  <img src="https://img.shields.io/badge/Model%20Selection-GridSearchCV%2C%20Optuna-blueviolet" alt="Model Selection">
  <img src="https://img.shields.io/badge/Project%20Status-Completed-success" alt="Project Status">
</p>

# Survival Time Prediction Using SEER Data (2018–2022)

This project investigates the prediction of survival time (in months) for cancer patients using machine learning regression models. The analysis is based on real-world data from the SEER (Surveillance, Epidemiology, and End Results) database. The dataset was filtered to include only cases of malignant tumors resulting in death, and the objective was to estimate the number of months between diagnosis and death.

This work was developed as part of my supervised machine learning exam at university, with the goal of applying increasingly refined techniques—from linear models to ensemble methods—on a clinically meaningful problem. The project involved data cleaning, feature engineering, encoding, model training, evaluation and error correction.

## Project Objectives

- Predict the **number of survival months** for cancer patients using SEER data.
- Build a **regression pipeline**, starting from baseline models and evolving toward more sophisticated solutions.
- Evaluate performance using **MAE** and interpret results through **residual analysis**.
- Explore methods to **improve predictions** by modeling the residuals of initial regressors.

## Repository Structure

```
seer-survival-regression/
│
├── README.md
├── requirements.txt
├── presentation.pdf
├── data/
│  └── instructions.md     
└── notebooks/
   ├── 0_data_cleaning.ipynb
   └── 1_modeling.ipynb


```

## Dataset

- **Source**: [SEER Program – National Cancer Institute](https://seer.cancer.gov/)
- **Time window**: 2018–2022
- **Initial shape**: 714'694 rows x 54 columns 
- **Cleaned shape**: 131'974 rows × 53 columns
- **Filtered for**: Only patients who died from malignant tumors
- **Target variable**: `survival_months`

## Features Included

- **Demographics**: age, sex, race, marital status, income, rural/urban code
- **Tumor Info**: site, histology, grade, size
- **Staging**: TNM, stage group, regional nodes
- **History**: number of prior tumors
- **Biomarkers**: ER, PR, HER2
- **Treatment**: surgery, radiation, chemotherapy

##  Methodology

1. **Data Cleaning**: handled missing values, harmonized categorical codings, filtered cases. 
2. **Encoding**: `TargetEncoder`, `OneHotEncoder` with `ColumnTransformer`and pipelines
3. **Modeling**:
   - Linear Regression
   - Random Forest with hyperparameters tuning
   - XGBoost with hyperparameters tuning 
4. **Model Selection**:
   - `GridSearchCV`
   - `RandomizedSearchCV` 
   - `Optuna`
   
5. **Residual Correction**:
   - Modeled residuals of best-performing model for final correction improving predictions both on test and trainset

## Results

| Model                               | MAE (on test set) |
|-------------------------------------|-------------------|
| Linear Regression + Target Encoding | 6.35 months       |
| Random Forest (untuned)             | 6.26 months       |
| XGBoost (tuned)                     | 5.76 months       |
| Residual correction model           | **5.74 months**   |


## Residual Analysis

A second model was applied to residuals to correct predictions.
The residual correction strategy led to a slight but measurable improvement in accuracy.


## Skills Developed
- Use of real-world clinical datasets (SEER)
- Data processing with `pandas`, `category_encoders`, `scikit-learn`
- Regression model building and selection
- Use of `ColumnTransformer`, `Pipeline`, `GridSearchCV`, `Optuna`
- Use of `Optuna` and `GridSearchCV`
- Critical performance evaluation and residual error correction



## Conclusion

This project applies rigorous methodology to a high-impact medical problem. By progressively refining the models and analyzing residuals, I was able to achieve solid prediction performance on real-world SEER data. The approach showcases technical and analytical skills and represents a complete pipeline from raw data to improved predictions.

This project represents a complete and scientifically grounded pipeline for survival time prediction in oncology, demonstrating how increasingly refined modeling strategies can improve performance on complex real-world tasks. The use of real data, attention to preprocessing, and evaluation through residual correction all highlight the practical application of machine learning in clinical research.

The work reflects both theoretical understanding and practical ability to manage all phases of a supervised ML task, from raw data to interpretable results.

---
**Author**: Marco Ferrarini — Machine Learning Student
