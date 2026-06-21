# Swish Analytics NFL Sack Probability Modeling Challenge

## Overview

This project was completed as part of the Swish Analytics Football Data Modeling Challenge. The objective was to build a machine learning model that predicts whether a quarterback dropback will result in a sack using NFL play-by-play and player tracking data.

The full memo with takeaways can be found [here](https://docs.google.com/document/d/18A4LnkzcUN1UWk9ZYL2A65IWX1OQlK12fNJQZ5dCsXg/edit?usp=sharing).

The project follows a complete data science workflow:

- Data cleaning and feature engineering
- Exploratory data analysis
- Predictive modeling
- Model evaluation and interpretation

---

## Problem Statement

Given information available before a play occurs, predict the probability that a quarterback will be sacked on a passing play.

Because sacks are relatively rare events, this problem is treated as a binary classification task where:

- **1 = Sack**
- **0 = No Sack**

The final goal is to generate well-calibrated probabilities rather than simply predicting yes/no outcomes.

---

## Data Sources

The challenge dataset includes:

- NFL play-by-play data (2021–2023)
- Weekly passing statistics
- Weekly rushing statistics
- Weekly defensive statistics
- Roster information
- Game context variables

In this project I ultimately decided it was only relevant to use the play by play data and the roster information.

---

## Project Structure

```
├── 1_data_cleaning.ipynb
├── 2_eda.ipynb
├── 3_modeling.ipynb
├── inputs/
└── outputs/
```

### 1. Data Cleaning

- Merged multiple NFL datasets
- Removed data leakage variables
- Handled missing values
- Created rolling historical statistics
- Engineered quarterback and defensive sack rate features

### 2. Exploratory Data Analysis

Investigated relationships between sack rate and:

- Down 
- Distance to go
- Score differential
- Field position
- Specific quarterbacks
- Historical offensive sack rates
- Historical defensive sack rates

Each of these features show potential predictive value in a model and even show some interaction effects among one another.

### 3. Modeling

Models evaluated:

- Logistic Regression
- XGBoost

Evaluation Metrics

Because sack prediction is an imbalanced classification problem, multiple evaluation metrics were used. Ultimately, the XGBoost model was found to be slightly more effective, although the small difference indicated the features primarily contain weak, additive relationships rather than strong nonlinear interactions.


| Metric | Final XGBoost Model |
|-------|---------:|
| ROC AUC | 0.6071 |
| Log Loss | 0.2502 |

| Metric | Final XGBoost Model |
|-------|---------:|
| ROC AUC | 0.6235 |
| Log Loss | 0.2483 |

### Metric Definitions

- **ROC AUC:** Measures the model's ability to rank sacks above non-sacks.
- **Log Loss:** Measures the quality of predicted probabilities.

---

## Key Findings

- Across both models, the down was the most important feature.


- Historical sack rates (QB, offense) are among the strongest predictors of future sacks.

- Logistic Regression and XGBoost produced similar results, suggesting the problem contains mostly additive relationships rather than highly nonlinear interactions.

---

## Feature Importance

The most important predictors included:

- Rolling quarterback sack rate
- Rolling offensive sack rate
- Down and distance
- Game situation variables
- Field position
- Win probability

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## Future Improvements

Potential areas for improvement include:

- Offensive line personnel features
- Defensive line personnel features
- Pre snap blockers vs rushers count
- Ensemble methods

---

## Author

Kevin Le

- Growth Marketing Analyst
- M.S. Data Science Candidate at UT Austin
- Aspiring Sports Data Scientist

[GitHub](https://github.com/kevinkietle)

---

## Acknowledgments

Thanks to Swish Analytics for providing the data and hosting the challenge. 

