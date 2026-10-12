# Databricks-Credit-Risk-Lakehouse

![Databricks Dashboard](images/standardized-view-creation.png)

## Project Introduction
This project is inspired by Rabobank's credit analytics case, focusing on data cleaning, standardization, and governance using Databricks, Unity Catalog, and Delta Lake.

## Data Source

- Kaggle: Credit Risk Dataset
- Link: https://www.kaggle.com/datasets/laotse/credit-risk-dataset
- Records: 32,581 loan records
- Key Fields:
  - `person_age`: Applicant's age
  - `person_income`: Applicant's annual income
  - `person_home_ownership`: Home ownership status
  - `loan_intent`: Purpose of the loan
  - `loan_grade`: Loan risk grade (A–G)
  - `loan_amnt`: Requested loan amount
  - `loan_int_rate`: Loan interest rate
  - `loan_status`: Loan default status (0 = Non-default, 1 = Default)


The credit risk dataset was uploaded to a Databricks Unity Catalog Volume and saved as a table. SQL was used to standardize loan default definitions, check data quality, and clean the dataset. The cleaned data was saved as a Delta Table, and Unity Catalog was used to explore data lineage.

## Tools

- Databricks Free Edition
- SQL
- PySpark
- Delta Lake
- Unity Catalog

## Analysis Process

1. Upload the raw CSV dataset to a Unity Catalog Volume.
2. Read the dataset into Databricks and register it as a table.
3. Standardize loan default definitions using SQL.
4. Check missing values, identify potential duplicates, and remove out-of-range records.
5. Save the cleaned dataset as a Delta Table.
6. Explore data lineage using Unity Catalog.

## Standardization

### Random Forest Classification

Used scikit-learn to train a Random Forest classifier to predict loan approval outcomes based on credit score, annual income, and loan amount.

![Model Training](images/model-training-code.png)

## Model Evaluation

### Model Performance

Evaluated the model using Accuracy, F1 Score, Precision, and Recall. The model achieved approximately 94% accuracy and an F1 Score of 0.94.

![Model Evaluation](images/model-evaluation-results.png)

### Confusion Matrix

Visualized the prediction results to identify correctly classified applications and two types of errors: false approvals and false rejections.

![Confusion Matrix](images/confusion_matrix.png)

### Feature Importance

Analyzed feature importance to identify the key factors influencing loan approval predictions.

![Feature Importance](images/feature_importance.png)

### Classification Report

Generated a classification report to compare Precision, Recall, and F1 Scores for Approved and Rejected applications.

![Classification Report](images/classification_report.png)

## Delta Table

Saved model evaluation metrics, including Accuracy, F1 Score, Precision, and Recall, as a Delta Table in Databricks.

![Model Metrics Delta Table](images/model-metrics-delta-table.png)


## Business Recommendation

Credit score is the core variable in the approval process (77.5% importance) and warrants priority attention; the decision threshold should be adjusted based on the confusion matrix to balance risk and approval rates.

## Notebook File

Databricks notebook available in the `notebooks` folder.

## Author

- Name: Lingxi Li
- GitHub: lingxiquq-cpu
