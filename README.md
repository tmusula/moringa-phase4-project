# MODEL INTERPRETABILITY

# Interpretable Models for Chicago Traffic Crashes

This project focuses on predicting the **primary contributory cause** of traffic crashes in Chicago using both traditional and neural network models. Emphasis is placed on **interpretability** to help public safety stakeholders understand the factors influencing crash causes.

---

## Objective

To build accurate and interpretable machine learning models that identify why traffic crashes happen—particularly from driver and vehicle-related factors—and to generate insights that support data-driven road safety interventions.

---

## Dataset

Data was sourced from the [Chicago Data Portal](https://data.cityofchicago.org/):
- `Traffic Crashes - Crashes.csv`
- `Traffic Crashes - Vehicles.csv`
- `Traffic Crashes - People.csv`

These were merged and filtered to focus on:
- Drivers involved in crashes
- Incidents with valid vehicle and driver data

---

## Data Preparation

- Merged datasets on `CRASH_RECORD_ID`
- Filtered for drivers only (`PERSON_TYPE == 'DRIVER'`)
- Removed rows with null values for essential columns
- Grouped and reduced rare categories for modeling
- Applied One-Hot Encoding to categorical variables
- Scaled numeric features

---

## Models Used

### Baseline Models
- Naive Bayes
- Decision Tree
- Random Forest
- XGBoost
- KNN

### Neural Network Models
- Artificial Neural Network (ANN)
  - 5 layers with Dropout and Batch Normalization
  - Early stopping to prevent overfitting

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

### Local Interpretability
- **SHAP (SHapley Additive Explanations)** for neural network predictions
- Helped understand how individual features (e.g. driver impairment, vehicle type, lighting conditions) influenced specific predictions

---

## Results Summary

- **Best Model:** 
- **Top Accuracy:** 
- **Key Features Identified:**
  - Driver condition (e.g. alcohol use, distracted driving)
  - Lighting conditions
  - Vehicle type/age

---

## Conclusion

This project demonstrates how interpretable machine learning models can uncover key risk factors behind traffic crashes in Chicago. These insights can support better traffic safety planning, policy, and public education.

---

## Next Steps

- Integrate geospatial analysis (e.g., mapping crash hotspots)
- Explore time-series trends in crash causes
- Build a dashboard or deploy as an API
