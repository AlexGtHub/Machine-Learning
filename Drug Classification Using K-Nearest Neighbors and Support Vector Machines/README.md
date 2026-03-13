# Drug Classification with KNN and SVM

## Project Overview

This project analyzes patient features such as age, blood pressure, cholesterol level, and the sodium-to-potassium ratio in order to predict which drug is the most appropriate for a patient.
The goal is to build K-Nearest Neighbors (KNN) and Support Vector Machine (SVM) models and determine which model fits the dataset better and provides the highest prediction accuracy.

## Dataset

The dataset contains health information about individuals, including:

* Age
* Sex
* Blood presure (BP)
* Cholesterol
* Na_to_K

Each row represents a single individual along with the drug associated with their condition.

## Exploratory Data Analysis

Exploratory analysis was performed to understand the relationships between variables. Key observations include:

* Na_to_K shows a strong influence on the prediction in this dataset.
* DrugY and DrugX are the most commonly used drugs, showing a strong relationship with high and low Na_to_K values, respectively.
* The dataset contains more observations from individuals with varying Na_to_K levels.

Several visualizations were used, including:

* Correlation matrix
* Pairplots
* Drug distribution histogram

## Data Preprocessing

Before training the models, the following preprocessing steps were applied:

* One-Hot Encoding for categorical variables
* Train-test split
* Feature scaling using StandardScaler

## Models Used

Two models were implemented and compared:

* K-Nearest Neighbors (KNN)
* Support Vector Machine (SVM)

## Model Evaluation

Model performance was evaluated using:

* Accuracy

Results:

| Model             | Accuracy |
| ----------------- | -------- |
| KNN               | 0.925    |
| SVM               | 0.9      |

The K-Nearest Neighbors (KNN) model fits the dataset better, with 1 false positive, while the SVM model produced 2 false positives.

## Key Insights

* The sodium-to-potassium ratio is the most influential feature for predicting which drug a patient should take.
* Older individuals are more susceptible to unstable blood pressure and varying levels of Na_to_K.
* KNN fits slightly better in this dataset, with more true positives and fewer false positives.

## Conclusion

The analysis shows that both KNN and SVM achieved good accuracy in predicting the drug, but KNN performed slightly better.
KNN produced fewer false positives and a slightly higher accuracy score. These results suggest that KNN is the most suitable model for this dataset.

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn