# Predicting Cardiovascular Disease Using NHANES Data  

## Overview  
Cardiovascular disease (CVD) is the leading cause of mortality in the United States, with coronary artery disease (CAD) contributing to a significant proportion of fatalities. This project develops a machine learning model using NHANES (National Health and Nutrition Examination Survey) data to predict heart disease risk. By leveraging demographic, clinical, and lifestyle factors, the model aims to support early detection and targeted prevention strategies.  

## Background & Significance  
- **CVD Mortality (2022):** 702,880 deaths in the U.S., with CAD responsible for 371,506 fatalities.  
- **Economic Burden:** $252.2 billion in healthcare costs and lost productivity.  
- **Risk Factors:** Poor diet, obesity, high cholesterol, hypertension, smoking, kidney disease, and genetic predisposition.  
- **Health Disparities:** Significant racial and ethnic differences in CVD risk underscore the need for inclusive predictive models.  

## Dataset & Preprocessing  
- **Data Source:** NHANES (2021-2023) from the CDC.  
- **Preprocessing Steps:**  
  - Converted NHANES data from SAS to CSV format and merged using SEQN (participant ID).  
  - Imputed missing values for lifestyle factors (smoking, alcohol use).  
  - Removed variables with excessive missing data.  
  - Engineered new features, including:  
    - **Depression Index** (PHQ-9 scale).  
    - **CVD Indicator** (aggregating heart conditions).  
  - Filtered dataset to include participants aged **40+** with complete survey and lab data.  
  - Addressed missing values, slightly reducing CVD prevalence from **12.74%** to **11.43%**.  

## Exploratory Data Analysis (EDA)  
- **Demographics:** Age and gender distributions analyzed for CVD-positive and CVD-negative groups.  
- **Statistical Tests:**  
  - **Normality Assessment:** Shapiro-Wilk, Kolmogorov-Smirnov, D’Agostino tests.  
  - **Distributions:** Box plots & histograms for key features (age, BMI, cholesterol, blood pressure).  
  - **Correlations:** Spearman heatmap identified key predictors (age, cholesterol, BMI).  
  - **Ordinal Data Analysis:** Violin plots for depression, education, and alcohol use.  

## Feature Selection & Engineering  
- **Statistical Methods:**  
  - Spearman’s Rank Correlation for numerical-ordinal relationships.  
  - Mann-Whitney U Test for CVD group comparisons.  
  - Chi-Square & Cramér’s V for categorical variables.  
  - Kruskal-Wallis H Test for multi-category comparisons.  
- **Feature Engineering:**  
  - **Mutual Information & Spearman’s Correlation** for continuous variables.  
  - **Chi-Square & F-Test** for categorical/ordinal variables.  
  - Addressed class imbalance using **ADASYN (Adaptive Synthetic Sampling)**.  
- **Scaling & Splitting:**  
  - Stratified train-test split.  
  - Standardized numerical features using **StandardScaler** to prevent data leakage.  

## Machine Learning Models  
- **Algorithms Implemented:**  
  - Logistic Regression  
  - Random Forest  
  - XGBoost  
  - Decision Tree  
  - Support Vector Machine (SVM)  
  - K-Nearest Neighbors (KNN)  
  - Neural Networks  
  - Gaussian Naïve Bayes  

### **Model Performance Evaluation**  
- **Metrics Used:**  
  - Accuracy, Precision, Recall, F1-Score  
  - ROC-AUC & Precision-Recall AUC  
  - Confusion Matrices for classification insights  
- **Key Results:**  
  - **Random Forest**: **94.55% accuracy**, highest overall performance.  
  - **XGBoost**: **93.36% accuracy**, close competitor.  
  - **SVM**: **95.8% accuracy** after hyperparameter tuning.  
  - **Neural Networks**: Improved from **90% to 93%** post-optimization.  
  - **KNN**: Enhanced from **86.3% to 88.3%** accuracy with tuning.  
  - **Logistic Regression & Naïve Bayes**: Moderate accuracy (~79%), lower predictive power.  
  - **Decision Tree**: Stable at **90% accuracy** with limited improvement potential.  
  - **AUC Scores**:  
    - **Random Forest & XGBoost**: **0.99 ROC AUC** (best).  
    - **SVM & Neural Networks**: High performance.  
    - **KNN**: Improved to **0.95 AUC** after tuning.  
    - **Logistic Regression & Naïve Bayes**: Lower scores (~0.87).  

