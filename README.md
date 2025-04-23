# MODEL INTERPRETABILITY

# Interpretable Models for Chicago Traffic Crashes

This project focuses on predicting the **primary contributory cause** of traffic crashes in Chicago using both traditional and neural network models. Emphasis is placed on **interpretability** to help public safety stakeholders understand the factors influencing crash causes.

---
## Table of Contents

* Objective
* Dataset
* Data Preparation
* Models Used
* Evaluation Metrics
* Interpretability
* Results Summary
* Conclusion

## Objectives
* Predict the primary contributory cause in Chicago City
* Identification of patterns in crash timing and location for faster response and rescue.
* Use behavior and demographics to classify driver risk.
* Analyze how device type and road condition affect crash occurrence.

---

## Dataset

Data was sourced from the [Chicago Data Portal](https://data.cityofchicago.org/):
- `Traffic Crashes - Crashes.csv`
- `Traffic Crashes - Vehicles.csv`
- `Traffic Crashes - People.csv`
  
# Data Understanding
- Crashes dataset - 934135 rows and 19 columns
- People dataset - 2052949 rows and 13 columns
- Vehicle dataset - 1906958 rows and 6 columns

---

## Data Preparation

- Merged datasets on `CRASH_RECORD_ID`
  df_driver = pd.merge(df_vehicles, df_people1, on='CRASH_RECORD_ID', how='inner')
  merged_df = pd.merge(df_crashes, df_driver, on='CRASH_RECORD_ID', how='inner')
  
- Filtered for drivers only (`PERSON_TYPE == 'DRIVER'`)
- Removed rows with null values for essential columns
- Grouped and reduced rare categories for modeling
- Applied:
     - One-Hot Encoding to categorical variables
     - Scaled numeric features

---

## Models Used

### Baseline Models and their Performance
- Naive Bayes
  - Accuracy: 25.8%     
  - F1 score: 26.5% 

- Decision Tree
   - Accuracy: 86.1%
   - Weighted Average: 70:3%
- Random Forest
   - Accuracy: 92%
   - Weighted average: 92%
- XGBoost
   - Accuracy: 92%
   - Weighted Average: 92%
- KNN
   - Accuracy: 87%
   - Weighted Average: 87%
  
### Neural Network Models
- Artificial Neural Network (ANN)
  - 5 layers with Dropout and Batch Normalization
  - Early stopping to prevent overfitting
  - Accuracy: 25.8%
  - F1 score: 26.5%
- XGBoost and Random Forest are  the better performing model.
- XGBoost being the better one because of higher F1 score for the different categories.

---

## Evaluation

Each model was evaluated using:
- **Accuracy**
- **Precision**
- **Recall**
- **F1 Score**

Cross-validation was used to ensure generalizability.

---

## Interpretability

### Global Interpretability
- Feature importances from Random Forest and XGBoost
# Random Forest 
- ![image](https://github.com/user-attachments/assets/cda84dbf-880f-4ec1-9caf-c42b00abe755)
- ![image](https://github.com/user-attachments/assets/5e1e9634-c867-4678-8be2-bf102fedd4f5)
# XGBoost
 - ![image](https://github.com/user-attachments/assets/7b9daef9-3718-431e-8d9d-9e16897f8f2a)
 - ![image](https://github.com/user-attachments/assets/65e4be63-f004-4c58-94b2-28fe42335dfb)

- Top Features included:
  - Driver condition (Fatigue, intoxication)
  - Lighting condition
  - Vehicle type
  -Maneuver and travel direction

### Local Interpretability
- **SHAP (SHapley Additive Explanations)** for neural network predictions
- Visualized how specific features influenced individual predictions
- Helped uncover hidden patterns in "preventable" vs "non-preventable" crashes
  
---

## Results Summary

- **Best Model:** 
- **Top Accuracy:** 
- **Key Features Identified:**
  - Driver condition (e.g. alcohol use, distracted driving)
  - Lighting conditions
  - Vehicle type/age
  - Road surface and defects
---

## Conclusion

- This project demonstrates how interpretable machine learning models can uncover key risk factors behind traffic crashes in Chicago.
- These insights can provide valuable inputs for:
  - Designing safer road systems
  - Targeted traffic enforcement
  - Public education campaigns

---

## Next Steps

- Integrate geospatial analysis (e.g., mapping crash hotspots)
- Explore time-series trends in crash causes
- Build a dashboard or deploy as an API
- Incorporate additional data such as traffic flow or enforecement presence
