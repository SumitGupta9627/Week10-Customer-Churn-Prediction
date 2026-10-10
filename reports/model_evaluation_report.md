# Model Evaluation Report

## Test setup
- Dataset: `churn_data.csv`
- Dataset size: 500 rows, 9 original columns
- Train/test split: 80% / 20%
- Split method: stratified, with `random_state=42`
- Model: `RandomForestClassifier` with 250 trees and `class_weight="balanced"`
- Preprocessing: numeric median imputation and StandardScaler; categorical most-frequent imputation; One-Hot Encoding and Ordinal Encoding in a scikit-learn `Pipeline`.

## Results from the notebook execution
| Metric | Score |
|---|---:|
| Accuracy | 0.96 (96.0%) |
| Precision (churn class) | 1.00 (100.0%) |
| Recall (churn class) | 0.636 (63.6%) |
| F1-score (churn class) | 0.778 (77.8%) |

Classification report for the test split:
- Retained (class 0): precision 0.96, recall 1.00, F1-score 0.98, support 89.
- Churn (class 1): precision 1.00, recall 0.64, F1-score 0.78, support 11.
- Overall accuracy: 0.96 across 100 test records.

## Interpretation
The model correctly classified 96 of 100 test records. It identified the churn cases it predicted with high precision, but recall of about 63.6% means it missed some actual churn cases. Accuracy alone is not sufficient because the dataset is imbalanced (447 retained and 53 churned records).

## Limitations
This is a small single-split evaluation. Results are not a guarantee of performance on new data. For a stronger evaluation, use cross-validation, compare a baseline model, and test on a larger representative dataset.
