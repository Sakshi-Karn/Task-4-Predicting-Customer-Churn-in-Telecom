📌 Objective

The goal of this project is to predict customer churn (whether a customer will leave the telecom service) using machine learning.
The dataset used:
WA_Fn-UseC_-Telco-Customer-Churn.csv

📂 Project Workflow
1. Data Loading

Used pandas to load the CSV dataset.

Removed the customerID column since it does not contribute to prediction.

2. Data Cleaning

Converted TotalCharges to numeric (it contained some non-numeric values).

Filled missing values in TotalCharges using the median.

3. Feature Preparation

Split data into:

Target variable: Churn (Yes/No → converted to 1/0)

Features: All other columns

Identified:

Categorical features → OneHotEncoded

Numerical features → Scaled using StandardScaler

Used a ColumnTransformer to apply encoding and scaling in one step.

4. Train/Test Split

Data split into 80% training and 20% testing

Used stratify=y to maintain class balance.

5. Models Used

Two machine learning models were trained:

🔹 Logistic Regression

Good baseline for classification.

Performs well when relationships are linear.

🔹 Random Forest Classifier

Handles non-linear relationships.

Naturally identifies important features.

Works well for mixed data types.

Both models were built using a Pipeline:

preprocessing  →  model training


This ensures consistent preprocessing for both training and prediction.

6. Model Evaluation

Models were evaluated using:

Classification Report (Precision, Recall, F1-score)

Confusion Matrix

Accuracy

Random Forest generally gave better performance, especially on the churn class.

7. Feature Importance (Random Forest)

RandomForest provides .feature_importances_, which helps identify the most influential factors.

Some of the commonly important features:

MonthlyCharges

Tenure

Contract Type

InternetService

Payment Method

A bar chart was plotted showing the Top 15 most important features.

8. Model Saving

Both trained models were saved using:

joblib.dump()


Saved files:

churn_random_forest_model.joblib

churn_logistic_model.joblib

These can be loaded later for deployment or predictions.

📝 Conclusion

This project successfully builds a churn prediction model using industry-standard preprocessing and machine learning techniques. The RandomForest classifier performs strongly and reveals the key factors influencing customer churn. The entire workflow is reproducible, modular, and ready for further improvement or deployment.
