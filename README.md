# Loan Default Risk Analysis and Prediction

## Project Overview
This project aims to develop a machine learning model to predict loan default risk by analyzing customer profiles and characteristics. The goal is to help financial institutions anticipate and prevent loan defaults by identifying high-risk clients.

## Key Features
- Comprehensive data analysis of loan applicant characteristics
- Exploration of numerical and categorical variables
- Advanced machine learning prediction techniques
- Handling of class imbalance using SMOTE
- Comparative model performance evaluation

## Dataset Characteristics
- Total records: 252,000
- Risk distribution:
  - Low-risk clients (0): 87.7%
  - High-risk clients (1): 12.3%

## Data Variables
### Numerical Variables
- Income
- Age
- Professional Experience
- Current Job Years
- Current House Years

### Categorical Variables
- Marital Status
- House Ownership
- Profession
- City
- State

## Methodology
1. **Data Preprocessing**
   - One-hot encoding of categorical variables
   - SMOTE for handling class imbalance

2. **Machine Learning Models**
   - Logistic Regression
   - Random Forest Classifier (Best Performing)

## Model Performance
### Logistic Regression
- Accuracy: ~53%
- Limited predictive power

### Random Forest Classifier
- Accuracy: ~95%
- Excellent precision and recall
- Best hyperparameters: max_depth = 50

## Key Insights
- Clients with less professional experience tend to have higher default risk
- Renters show higher default probability compared to homeowners
- Marital status shows subtle influence on default risk

## Requirements
- Python 3.x
- Libraries: 
  - pandas
  - numpy
  - scikit-learn
  - imbalanced-learn
  - matplotlib
  - seaborn