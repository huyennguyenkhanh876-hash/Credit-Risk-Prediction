# Credit-Risk-Prediction
To develop a binary classifier using Logistic Regression for predicting customer credit risk.
--------
# Project Overview
This project focuses on solving a cost-sensitive Binary Classification problem within the financial sector. The primary objective is to build a Logistic Regression model to predict whether a customer poses a high credit risk.  

Beyond model training, this project deeply explores the Precision-Recall trade-off and the strategic selection of classification thresholds to optimize risk management decisions. 

--------
# Dataset
The project utilizes the Australian Credit Dataset (australian.dataset).  
- Size: 690 observations and 15 columns (14 independent features (A1 to A14) and 1 target variable).
- Target Variable (Target):
  + 1: High credit risk (Default).
  + 0: Low credit risk (Non-default).
- Data Quality: The dataset is perfectly clean with 0 missing values.
--------
# Methodology
1. Data Preprocessing
   - Feature Scaling: Applied StandardScaler to normalize the input variables, ensuring optimal convergence and performance for the Logistic Regression algorithm.
2. Model Training & Validation
   - Data Splitting: Divided the dataset into training (80%) and testing (20%) sets using train_test_split.
   - Cross-Validation: Implemented StratifiedKFold (3 splits) to ensure robust model evaluation and maintain the class distribution ratio across all folds.
   - Algorithm: Trained a Logistic Regression classifier (random_state=42).
3. Model Evaluation

   The model's performance was evaluated using cross-validated metrics:
- Overall Performance: Achieved an Accuracy of ~86.9%, a Precision of ~0.848, a Recall of 0.875, and an F1-score of ~0.861.
- Confusion Matrix Analysis: The model correctly identified 224 high-risk customers (True Positives) and 256 low-risk customers (True Negatives). However, it misclassified 32 high-risk customers as low-risk (False Negatives) and 40 low-risk customers as high-risk (False Positives).
- Business Insight: The report highlights why Accuracy is a misleading metric for imbalanced, cost-sensitive credit risk problems. In banking, missing a bad credit (False Negative) causes significantly higher financial damage than mistakenly rejecting a good customer (False Positive).
4. Threshold Optimization & Trade-off Analysis

  Extracted prediction probabilities using predict_proba and analyzed the Precision-Recall trade-off by dynamically adjusting the decision threshold:
- Threshold 0.5: Precision ~0.814, Recall ~0.859. A balanced approach suitable for market expansion.
- Threshold 0.7: Precision ~0.901, Recall ~0.753.
- Threshold 0.9: Precision ~0.942, Recall ~0.449. A strict risk-averse approach that ensures high reliability of rejected applications but misses over half of the actual defaults.  
