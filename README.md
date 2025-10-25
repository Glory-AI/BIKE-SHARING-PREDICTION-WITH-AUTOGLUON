# BIKE-SHARING-PREDICTION-WITH-AUTOGLUON
This project leverages AWS AutoGluon to predict bike-sharing demand using tabular data from  Kaggle. The workflow covers data cleaning, feature engineering, model training, and hyperparameter optimization to improve prediction accuracy over multiple iterations.  This project is under the AWS Machine Learning Fundamentals sponsored by Udacity x AWS.



This project predicts bike-sharing demand using AutoGluon’s Tabular Prediction module.
The dataset comes from the Kaggle Bike Sharing Demand competition.

The goal is to accurately forecast the number of bikes rented per hour based on historical data and weather conditions — a task relevant to businesses like Uber, Lyft, and DoorDash, which depend on understanding demand patterns to optimize resource allocation.

### Project Overview
----

The workflow includes:

* Loading and cleaning the tabular data.
* Using AutoGluon to automatically train multiple models.
* Performing feature engineering for improvement.
* Conducting hyperparameter optimization (HPO) on selected models.
* Comparing performance across iterations (initial → feature engineering → tuning).
* Submitting predictions to Kaggle and analyzing leaderboard scores.

### Project Iterations
---
1. Initial Training

Observation:
The model initially performed poorly (RMSE around -115). Predictions were off-scale due to underfitting and lack of feature understanding.

Top model: WeightedEnsemble_L3

2. Exploratory Data Analysis (EDA) and Feature Engineering

During EDA:

* Explored relationships between temperature, humidity, and count.

* Added new features, e.g., difference between actual and felt temperature (temp - atemp).

Impact:
Improved performance by ~65%. The model captured better patterns due to richer input features.

3. Hyperparameter Optimization (HPO)

Used AutoGluon’s built-in tuning for:

* XGBoost

* CatBoost

* LightGBM

Also performed Randomized Search over selected hyperparameters (num_leaves, learning_rate, depth, etc.).

Best result:
CatBoost with tuned parameters achieved the highest Kaggle test performance.

### Results Summary
Validation Score Improvements

Model Version	Validation Score (RMSE ↓)

+ Initial	-115.84
+ Features	-33.59
+ HPO	-34.14


### Insights & Lessons Learned

* AutoGluon’s TabularPredictor made it easy to test many models quickly and automatically choose the best one.

* Feature engineering had the biggest single impact on improving accuracy.

* Hyperparameter tuning refined the best models further.

* Learned the importance of model interpretability and performance tracking.

* RMSE is sensitive to outliers : data cleaning and scaling are crucial.


### Tech Stack

* Language: Python

* Libraries: AutoGluon, Pandas, Matplotlib

* Environment: Jupyter Notebook

* Data Source: Kaggle Bike Sharing Demand
