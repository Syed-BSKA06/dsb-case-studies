# Bike Demand Prediction using Logistic Regression

## Project Overview
This project analyzes the factors affecting bike rental demand and builds a machine learning model to predict whether bike demand will be **high or low** during a given hour.

The analysis includes:
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Logistic Regression Model
- Model Evaluation
- Feature Importance Interpretation

The goal is to help bike-sharing companies **predict demand patterns and optimize bike availability**.

---

# Dataset Description

The dataset used is the **Bike Sharing Dataset**, which contains hourly rental data along with environmental and seasonal variables.

Key features include:

| Feature | Description |
|------|------|
| season | Season of the year |
| yr | Year (0: 2011, 1: 2012) |
| mnth | Month |
| hr | Hour of the day |
| holiday | Whether the day is a holiday |
| weekday | Day of the week |
| workingday | Whether it is a working day |
| weathersit | Weather situation |
| temp | Normalized temperature |
| atemp | Feels-like temperature |
| hum | Humidity |
| windspeed | Wind speed |
| cnt | Total bike rentals |

---

# Problem Statement

The objective of this project is to **predict high bike demand hours**.
A binary target variable was created:
high_demand = 1 if cnt ≥ 200
high_demand = 0 otherwise

This transforms the problem into a **binary classification problem**.

---

# Project Workflow

The project follows a complete **Data Science pipeline**:
Data Loading
↓
Exploratory Data Analysis
↓
Outlier Detection
↓
Feature Engineering
↓
Train-Test Split
↓
Logistic Regression Model
↓
Model Evaluation
↓
Feature Importance Interpretation


---

# Exploratory Data Analysis (EDA)

EDA was performed to understand the distribution of variables and relationships with bike demand.

Key analyses included:

- Temperature distribution
- Seasonal demand patterns
- Hourly demand trends
- Weather impact on rentals
- Correlation analysis between features

A **correlation heatmap** was used to identify relationships between variables.

---

# Outlier Detection

Boxplots were used to identify potential outliers in numerical variables:

- Temperature
- Humidity
- Wind speed
- Bike demand

Although some outliers were present, they were retained because they likely represent **real-world demand spikes or extreme weather conditions** rather than data errors.

---

# Feature Engineering

The following preprocessing steps were performed:

### Target Variable Creation
high_demand = cnt ≥ 200

### Feature Removal (to avoid data leakage)

The following columns were removed:

- `casual`
- `registered`
- `cnt`
- `instant`
- `dteday`

These variables were excluded because they either contained **direct information about the target variable or were redundant identifiers**.

---

# Model Building

A **Logistic Regression model** was used because the task is a **binary classification problem**.
Logistic regression estimates the probability of high demand using the sigmoid function:


# Train-Test Split

The dataset was divided into:

- **80% training data**
- **20% testing data**

This ensures the model is evaluated on **unseen data**.

---

# Model Evaluation

The model was evaluated using multiple classification metrics.

### Confusion Matrix
[[1882 327]
[ 443 824]]


Interpretation:

| Metric | Meaning |
|------|------|
True Negative | 1882 |
False Positive | 327 |
False Negative | 443 |
True Positive | 824 |

---

### Performance Metrics

| Metric | Score |
|------|------|
Accuracy | 0.778 |
Precision | 0.716 |
Recall | 0.650 |
F1 Score | 0.681 |
AUC Score | 0.832 |

Interpretation:

- The model correctly predicts **77.8% of cases**
- High demand predictions are correct **71.6% of the time**
- The model detects **65% of actual high-demand situations**
- AUC score of **0.83 indicates strong classification performance**

---

# Feature Importance Analysis

Logistic regression coefficients were analyzed to determine which variables influence bike demand.

### Most Important Positive Factors

- **Feels-like temperature (atemp)**
- **Actual temperature (temp)**
- **Year (system growth)**

### Most Important Negative Factor

- **Humidity**

Key insight:

Bike demand increases in **warm and comfortable weather conditions** and decreases in **humid environments**.

---

# Business Insights

The analysis reveals several important patterns:

- **Warmer temperatures significantly increase bike demand**
- **High humidity reduces bike usage**
- **Demand increases during commuting hours**
- **Bike-sharing adoption increased between 2011 and 2012**

These insights can help bike-sharing companies:

- Allocate bikes efficiently
- Predict peak demand periods
- Improve operational planning

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

---

# Project Structure
bike-demand-prediction
│
├── data
│ └── hour.csv
│
├── notebook
│ └── bike_demand_case_study.ipynb
│
├── requirements.txt
│
└── README.md


---

# Conclusion

This project demonstrates how machine learning can be used to analyze and predict bike-sharing demand. Logistic regression provided interpretable insights into the environmental and temporal factors influencing rental patterns.

The model achieved an **AUC score of 0.83**, indicating strong ability to distinguish between high and low demand periods.

Future improvements could include:

- Trying tree-based models (Random Forest, XGBoost)
- Hyperparameter tuning
- Adding external data such as events or traffic conditions