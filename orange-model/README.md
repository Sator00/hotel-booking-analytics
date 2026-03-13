# Cancellation Prediction Model (Orange Data Mining)

This workflow predicts whether a hotel booking will be cancelled using machine learning models built in Orange Data Mining.

Dataset used:
- hotel_booking.csv

Target variable:
- is_canceled

Two classification models were tested and compared.

---

# Workflow Overview

The workflow follows these steps:

File → Select Columns → Rank → Models → Test & Score → Evaluation Visualizations

---

# Workflow Components

## File
Loads the dataset `hotel_booking.csv`.

## Select Columns
Defines the target variable `is_canceled` and selects relevant predictive features while ignoring unnecessary columns.

## Rank (Feature Importance)
This widget evaluates which variables are most important for predicting cancellations.

Important features identified include:
- deposit_type
- previous_cancellations
- required_car_parking_spaces
- booking_changes
- lead_time

These variables have the strongest relationship with booking cancellations.

## Logistic Regression
A baseline classification model used to predict whether a booking will be cancelled.

## Random Forest
An ensemble machine learning model that combines multiple decision trees to improve prediction accuracy.

## Test & Score
This widget evaluates the performance of the models using **cross-validation**.

Metrics used include:
- AUC (Area Under ROC Curve)
- CA (Classification Accuracy)
- F1 Score
- Precision
- Recall
- MCC (Matthews Correlation Coefficient)

---

# Model Performance Results

| Model | AUC | Accuracy | F1 | Precision | Recall | MCC |
|------|------|------|------|------|------|------|
| Random Forest | 0.922 | 0.862 | 0.860 | 0.862 | 0.862 | 0.700 |
| Logistic Regression | 0.863 | 0.811 | 0.804 | 0.814 | 0.811 | 0.587 |

Random Forest performed better than Logistic Regression across most evaluation metrics.

This suggests that ensemble tree models capture the booking cancellation patterns better than a linear model.

---

# Confusion Matrix Interpretation

The confusion matrix shows how many predictions were correct or incorrect.

It compares:

Actual booking outcome vs Predicted outcome.

A high number of correct predictions along the diagonal indicates strong model performance.

---

# ROC Curve Analysis

The ROC curve compares the True Positive Rate vs False Positive Rate.

Random Forest shows a higher curve and larger AUC value (0.922), indicating stronger classification ability compared to Logistic Regression.

---

# Scatter Plot Exploration

The scatter plot visualizes relationships between features such as:

- lead_time
- adr (Average Daily Rate)

Colored by:
- is_canceled

This helps explore how booking characteristics relate to cancellation behavior.

---

# Key Insights

From the machine learning analysis:

- Certain booking conditions strongly influence cancellations.
- Bookings with longer lead times tend to show higher cancellation risk.
- Ensemble models such as Random Forest provide stronger predictive performance.

---

# How to Run the Workflow

1. Open the `.ows` workflow file in Orange Data Mining.
2. In the **File widget**, select the dataset located in:

data/hotel_booking.csv

3. Run the workflow to view model performance and visualizations.
