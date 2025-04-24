# Business_Analytics_Bootcamp_10

# (Facebook) Prophet


# 📈 Time Series Forecasting with Facebook Prophet

Welcome to the repository on **Time Series Forecasting** using **(Facebook) Prophet**! This project focuses on building and evaluating forecasting models on Udemy Wikipedia page visit data using structural time series modeling and Prophet's rich functionalities like seasonality, holidays, cross-validation, and parameter tuning.

> 🔍 This project is especially useful for anyone looking to understand Prophet's inner workings, performance evaluation, and advanced time series modeling in a business context.

---

## 📂 Repository Contents

```bash

        📁 Prophet-Time-Series/
        
        ├── Prophet.ipynb                  # Jupyter Notebook containing the complete workflow
        
        ├── Udemy_wikipedia_visits.csv    # Time Series dataset with holidays and daily visits
        
        └── README.md                      # You're here!


---

## 📌 Topics Covered

         * 📐 Structural Time Series Decomposition
          
         * ⌛ Train/Test Split for Time Series
          
         * 🔮 Prophet Forecasting Model
          
         * ➕ vs ✖️ Additive vs. Multiplicative Seasonality
          
         * 🔄 Cross Validation for Time Series
          
         * 🎛️ Hyperparameter Tuning with ParameterGrid
          
         * 🎯 Performance Metrics: MAE, RMSE

#

## 🧠 Key Learnings & Interpretations

### 🗃️ Data Overview

     * Daily Udemy Wikipedia visits were collected alongside two major holiday indicators: Easter and Black Friday.
      
     * The data was reformatted to comply with Prophet’s structure: ds for dates and y for the metric being forecasted.

#

## 🎁 Holiday Effects

Two holiday events were engineered:

     * Easter: Modeled with a 5-day lead and 2-day lag window.
      
     * Black Friday: Modeled with a 7-day lead and 5-day lag.

🧠 Interpretation: These events significantly alter visitation patterns. Prophet captures their impact via holiday effect modeling.

#

## 🤖 Model Setup

The Prophet model was built using:

     * Additive seasonality
      
     * Yearly & weekly seasonality
      
     * Custom holiday effects
      
     * Regressor: Christmas, modeled as multiplicative


Regressor Coefficients Output:

   | Regressor	|      Mode	      | Coefficient |
   |            |                 |             |
   | Christmas	| Multiplicative	|   -0.327    |


  | 📉 Interpretation: A negative coefficient indicates that "Christmas" had a suppressing effect on Udemy Wikipedia traffic during the forecast window.


## 📈 Forecast Evaluation

     * Forecast Horizon: 31 days
      
     * MAE: 187.30
      
     * RMSE: 238.80

| 📊 Interpretation: The model captured trends reasonably well, with a small error margin. Error metrics are within a manageable range for business applications.


## 🔁 Cross Validation

     * Conducted using Prophet’s cross_validation() method.
      
     * Initial training: 1450 days | Horizon: 31 days
      
     * Cross-Validation MAE: 399.33
      
     * Cross-Validation RMSE: 517.56

| 📉 Interpretation: Cross-validation errors are larger than direct testing errors—indicating temporal variance and a realistic performance snapshot.


## ⚙️ Parameter Tuning

Used sklearn’s ParameterGrid to evaluate combinations of:

     * seasonality_mode: ['additive', 'multiplicative']
      
     * seasonality_prior_scale: [5, 10, 20]
      
     * holidays_prior_scale: [5, 10, 20]
      
     * changepoint_prior_scale: [0.01, 0.05, 0.1]

| 🔍 Interpretation: Tuning helps control overfitting and captures seasonal trends more accurately. The grid approach ensures comprehensive model evaluation.


## 📊 Visuals

     * Forecast Plots: Visualized via m.plot(forecast) and m.plot_components(forecast).
      
     * Cross-Validation Metric Plot: RMSE tracked over cutoff points for detailed model insight.

| 📷 Graphs available in the notebook: Prophet.ipynb


## 💼 Business Application

This workflow is a blueprint for how companies can forecast digital traffic, manage holiday-driven anomalies, and make proactive decisions using interpretable AI models like Prophet.


## 🚀 Getting Started

To run this project:

1. Clone the repo

      git clone [https://github.com/Binny007/Business_Analytics_Bootcamp_10.git]

2. Install dependencies

      pip install pandas numpy prophet scikit-learn

3. Launch Jupyter Notebook

      jupyter notebook Prophet.ipynb


