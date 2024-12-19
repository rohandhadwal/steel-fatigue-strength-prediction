# Steel Fatigue Strength Prediction

This repository contains a comprehensive analysis and predictive modeling project focused on the fatigue strength of steel materials. Using a dataset from the National Institute for Materials Science (NIMS), this project explores factors influencing fatigue behavior, preprocessing techniques, and model evaluation to identify reliable regression techniques for prediction.

## Dataset Overview

### Introduction
The dataset is focused on predicting the fatigue strength of steel materials. Fatigue behavior refers to how a material responds to repeated cycles of stress or strain over time—critical for predicting the lifespan and performance of materials in engineering applications.

**Source:**  
The dataset is hosted on Kaggle, provided by [National Institute for Materials Science (NIMS), Japan](https://link.springer.com/article/10.1186/2193-9772-3-8#additional-information).  
**Link:** https://www.kaggle.com/datasets/chaozhuang/steel-fatigue-strength-prediction

### Features
The dataset contains **25 features**, categorized as follows:

- **Chemical Composition**: C, Si, Mn, P, S, Ni, Cr, Cu, Mo  
- **Heat Treatment Parameters**: NT, THT, THt, THQCr, CT, Ct, DT, Dt, QmT, TT, Tt, TCr  
- **Processing Parameters**: RedRatio (Reduction Ratio)  
- **Inclusion Parameters**: dA, dB, dC  

### Challenges and Limitations
- **Risk of Overfitting**: With 437 samples and 27 features, the low sample-to-feature ratio increases overfitting risk.  
- **Curse of Dimensionality**: The sparsely populated data space affects distance-based algorithms.  
- **Feature Selection/Reduction**: Techniques like PCA or Recursive Feature Elimination (RFE) are critical to address these issues.

## Data Preprocessing

1. **Handling Missing Data:** Imputed missing values using statistical methods.  
2. **Outlier Removal:** Utilized Isolation Forest to identify and exclude anomalies.  
3. **Scaling:** Applied Standard Scaler to standardize the features.  
4. **Feature Selection:** 
   - ANOVA F-statistic for linear dependencies.  
   - Mutual Information (MI) scores for non-linear relationships.  
5. **Feature Reduction:** Principal Component Analysis (PCA) to retain 95% variance while reducing dimensionality.

## Model Selection and Evaluation

### Regression Techniques
The following regression techniques were evaluated:  
- Gradient Boosting  
- Random Forest  
- Support Vector Regression (SVR)  
- Linear Regression  
- K-Nearest Neighbors (KNN)  

### Key Observations
- Models were evaluated on their balance between **generalization** and **memorization** using **Mean Absolute Error (MAE)**.  
- **KNN and SVR** emerged as the most reliable techniques due to:  
  - Smaller MAE gap between training and testing datasets.  
  - High cross-validation score (~94%).  

### Performance Comparison
- While Gradient Boosting and Random Forest achieved lower training MAE, their higher testing MAE indicated potential overfitting.  
- **KNN and SVR demonstrated better generalization, making them more suitable for this task.**

## Additional Analysis

### 1. Impact of Training Dataset on Generalization Performance
- Both KNN and SVR improved with larger training datasets, reflected in decreasing MAE and increasing R² scores.  
- SVR consistently outperformed KNN with higher R² and lower MAE, proving its effectiveness in capturing underlying patterns.  

### 2. Best Preprocessing Sequence
The sequence of preprocessing techniques significantly impacts model performance:  
- **Optimal Sequence:** [Scaling → Feature Selection → PCA]  
- **Suboptimal Sequence:** [Scaling → PCA → Feature Selection]  

Performing feature selection before PCA ensures that only the most relevant features are retained, enhancing predictive performance.

## Results Summary

- **Most Reliable Models:** KNN & SVR  
- **Best Preprocessing Sequence:** [Scaling → Feature Selection → PCA]  
- **SVR Outperforms KNN:** Achieved higher R² and lower MAE with increasing training dataset sizes.  

## Author
Rohan Dhadwal
