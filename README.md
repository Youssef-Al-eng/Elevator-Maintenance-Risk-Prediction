# Elevator Maintenance Risk Analysis

## Overview
This project analyzes maintenance and safety data from elevator equipment to predict **risk levels** and identify critical risk factors. Using historical inspection data, machine learning models classify risk into **Low, Medium, High, and Critical** categories, helping maintenance teams prioritize actions and improve safety compliance.

## Dataset
- **Source:** Maintenance inspections of elevator equipment  
- **Format:** Excel (`maintenance_dataset.xlsx`)  
- **Records:** 23,617 entries  
- **Features:** 46 safety and equipment check questions (Yes/No/N/A)  
- **Target:** `maintenance_needed` (converted to risk levels using computed `Risk_Score`)  

## Preprocessing
- Converted categorical answers: `yes → 1`, `no → 0`, `n/a → NaN`  
- Dropped columns with >40% missing values  
- Filled remaining missing values with mode of each column  
- Computed `Risk_Score` (electrical and machinery hazards weighted higher)  
- Categorized `Risk_Score` into `Risk_Level` bins: Low, Medium, High, Critical  

## Exploratory Data Analysis (EDA)
- **Countplots** for distribution of risk levels  
- **Correlation heatmaps** to highlight feature relationships  
- **Violin and KDE plots** to show feature distributions across risk levels  
- **Stacked bar charts** to visualize categorical feature trends  

## Machine Learning Models
### 1. Random Forest
- Trained on full feature set  
- Evaluated before and after **SMOTE** balancing  
- Hyperparameters tuned with RandomizedSearchCV  
- Achieved **accuracy ~0.87** after balancing  

### 2. Random Forest (Top Features)
- Top 15 features selected based on feature importance  
- Achieved **accuracy ~0.83**, highlighting key risk factors  

### 3. XGBoost
- Trained on top features  
- Achieved **accuracy ~0.84**  
- Confusion matrices visualize prediction performance  

## Key Visualizations
- **Confusion Matrices**: Pre- and post-balancing for Random Forest and XGBoost  
- **Feature Importance Barplots**: Identify the most influential safety checks  
- **Distribution Plots**: Compare feature distributions across risk levels  

## Installation
```bash
pip install tensorflow pandas numpy matplotlib seaborn scikit-learn imbalanced-learn xgboost

## Usage
- Upload `maintenance_dataset.xlsx`  
- Run preprocessing steps to clean and encode data  
- Compute `Risk_Score` and categorize `Risk_Level`  
- Train ML models (Random Forest / XGBoost)  
- Visualize risk distributions, feature importance, and model performance  

## Outcome
- Provides predictive insights on elevator maintenance risk  
- Highlights critical risk factors to prioritize preventive actions  
- Supports data-driven maintenance planning and safety improvements

