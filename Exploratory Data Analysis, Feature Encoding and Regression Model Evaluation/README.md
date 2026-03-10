# Medical Insurance Cost Prediction

## Project Overview

This project analyzes a medical insurance dataset and builds machine learning models to predict healthcare charges based on personal and health-related attributes.
The goal is to understand which features influence insurance costs and compare the performance of different regression models.

## Dataset

The dataset contains demographic and health information about individuals, including:

* Age
* Sex
* Body Mass Index (BMI)
* Number of children
* Smoking status
* Region
* Insurance charges

Each row represents one individual and their associated medical insurance cost.

## Exploratory Data Analysis

Exploratory analysis was performed to understand the relationships between variables. Key observations include:

* Smoking status shows a strong relationship with higher insurance charges.
* BMI and age also appear positively correlated with healthcare costs.
* The dataset contains slightly more observations from the Southeast region.

Several visualizations were used, including:

* Correlation matrix
* Pairplots
* Regional distribution histograms

## Data Preprocessing

Before training the models, the following preprocessing steps were applied:

* One-Hot Encoding for categorical variables
* Train-test split
* Feature scaling using StandardScaler

## Models Used

Two regression models were implemented and compared:

* Multiple Linear Regression (MLR)
* Support Vector Regression (SVR) with hyperparameter tuning using GridSearchCV

## Model Evaluation

Model performance was evaluated using:

* Root Mean Squared Error (RMSE)
* R² Score (Coefficient of Determination)

Results:

| Model             | RMSE | R²   |
| ----------------- | ---- | ---- |
| Linear Regression | 5796 | 0.78 |
| SVR               | 6922 | 0.69 |

The Linear Regression model produced better predictions overall, especially for higher charge values.

## Key Insights

* Smoking is the most influential factor affecting insurance charges.
* Higher BMI values are associated with slightly higher healthcare costs.
* Linear Regression performs better for predicting higher insurance charges, while SVR shows more variability in predictions.

## Conclusion

The analysis shows that simple linear models can perform well when predicting medical insurance costs in this dataset. Smoking status, BMI, and age appear to be the most influential variables affecting healthcare charges.

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
