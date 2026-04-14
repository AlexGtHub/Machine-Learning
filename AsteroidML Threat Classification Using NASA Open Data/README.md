# Asteroid Classification with Machine Learning

## Project Overview

This project analyzes physical and orbital features of near Earth asteroids from NASA's dataset to predict whether an asteroid is potentially hazardous.

The goal is to build and compare multiple machine learning models — including regression and classification approaches — to determine which model best predicts asteroid hazard status.

**Author:** Juan Manuel Candela | **Date:** April 2026
**Dataset:** [NASA: Asteroids Classification — Kaggle](https://www.kaggle.com/datasets/lovishbansal123/nasa-asteroids-classification/data)

---

## Dataset

The original dataset contains 4,687 asteroid records with 40 features. After feature selection, the following 5 features were retained:

| Feature | Description |
| --- | --- |
| Absolute Magnitude | Intrinsic brightness of the asteroid |
| Est Dia in KM (min) | Minimum estimated diameter in kilometers |
| Est Dia in KM (max) | Maximum estimated diameter in kilometers |
| Miss Dist. (kilometers) | Closest approach distance to Earth |
| Relative Velocity km per sec | Speed of the asteroid relative to Earth |

**Target variable for regression:** `Relative Velocity km per sec` — Speed of the asteroid relative to Earth (number).
**Target variable for classification:** `Hazardous` — whether the asteroid is potentially dangerous (boolean).

> **Note:** The dataset is imbalanced — the majority of asteroids are non-hazardous, which affects model evaluation.

---

## Project Structure

- Data import and exploration (`df.info()`, `df.describe()`)
- Feature selection (40 → 5 relevant features)
- Train/test split (80/20, `random_state=42`)
- Feature scaling with `StandardScaler`
- Regression models (predicting `Relative Velocity`)
- Classification models (predicting `Hazardous`)
- Model evaluation and comparison

---

## Data Preprocessing

1. **Feature selection:** Removed redundant columns (duplicate unit representations, identifiers, dates) and retained the 5 most informative features.
2. **Train/test split:** 80% training, 20% test with `random_state=42`.
3. **Feature scaling:** Applied `StandardScaler` fitted only on training data to avoid data leakage.

---

## Models

### Regression (predicting Relative Velocity)

Three regression models were trained to predict `Relative Velocity km per sec`:

| Model | RMSE | MSE | R² |
| --- | --- | --- | --- |
| Linear Regression | 6.60 | 43.55 | 0.24 |
| Decision Tree | 9.03 | 81.56 | -0.43 |
| Random Forest | 6.63 | 43.99 | 0.23 |

> The low R² scores suggest that relative velocity is not well-predicted from the selected features alone — which makes sense, as velocity is largely independent of size or distance.

### Classification (predicting Hazardous)

Three classification models were trained to predict asteroid hazard status:

| Model | Accuracy | F1-score |
| --- | --- | --- |
| Logistic Regression | 0.8433 | 0.1170 |
| K-Nearest Neighbors (k=6) | 0.8305 | 0.2564 |
| Support Vector Machine (RBF) | 0.7004 | 0.4501 |

**KNN** achieved the highest accuracy. used k=6, selected by plotting training vs. test accuracy across k=1 to k=24

---

## Exploratory Data Analysis

A correlation heatmap was generated on the training features to understand relationships between variables. Key observations:

- `Est Dia in KM (min)` and `Est Dia in KM (max)` are perfectly correlated (redundant features).
- `Absolute Magnitude` shows a negative correlation with diameter (brighter = smaller).
- `Miss Dist.` and `Relative Velocity` show low correlation with other features.

---

## Key Insights

- **KNN with 6 neighbors** is the best-performing classifier on this dataset.
- The dataset is **imbalanced** — accuracy alone can be misleading. Future iterations should also report F1-score.
- The regression task (predicting velocity) is poorly suited to the available features — R² never exceeds 0.24.
- The `class_weight='balanced'` parameter in SVM helps compensate for the class imbalance in hazard prediction.

---

## Possible Improvements

- Add **F1-score, precision, and recall** to classification evaluation (especially relevant for imbalanced data).
- Include **confusion matrices** for each classifier.
- Apply **SMOTE** or other resampling techniques to handle class imbalance.
- Add more features (e.g., eccentricity, inclination) to improve regression performance.
- Use `scoring='f1'` in `GridSearchCV` instead of default accuracy for SVM tuning.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn