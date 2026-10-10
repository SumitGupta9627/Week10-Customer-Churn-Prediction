# Week 10: Customer Churn Prediction — Data Preprocessing & Feature Engineering

## Project overview
This project demonstrates an end-to-end preprocessing and feature-engineering workflow for a customer churn classification task. It uses the supplied CSV dataset (500 rows, 9 original columns) and predicts `Churn` (1 = churn, 0 = retained).

## Project files
- `churn_prediction_pipeline.ipynb` — exploration, encoding demonstrations, feature engineering, outlier analysis, scaling, feature inspection, preprocessing pipeline, model training, evaluation, and validation checks.
- `churn_data.csv` — dataset used by the notebook.
- `preprocessing_report.md` — data audit, preprocessing choices, leakage prevention, model workflow, and limitations.
- `feature_engineering_documentation.md` — definitions and rationale for eight engineered features.
- `requirements.txt` — Python dependencies.
- `screenshots/` — dataset visualization images.
- `reports/model_evaluation_report.md` — recorded evaluation results from the notebook test run.
- `reports/validation_evidence.md` — execution and validation checklist.

## Requirements covered
- **Encoding:** One-Hot Encoding, Ordinal Encoding, and Label Encoding (for target labels).
- **Scaling:** StandardScaler in the model pipeline and a separate MinMaxScaler demonstration.
- **Feature engineering:** eight derived features.
- **Outlier analysis:** IQR and Z-score checks.
- **Pipeline:** train/test split followed by a scikit-learn preprocessing and Random Forest pipeline.
- **Evaluation:** accuracy, precision, recall, F1-score, classification report, and confusion matrix.
- **Validation:** three assertions checking prediction count, valid binary labels, and handling of an unseen category.

## Setup and run in VS Code (Windows)
1. Install Python 3.10 or newer.
2. Extract this ZIP and open the extracted project folder in VS Code.
3. Open **Terminal → New Terminal** and run:
   ```powershell
   python -m venv .venv
   .venv\Scripts\Activate.ps1
   python -m pip install -r requirements.txt
   ```
4. Open `churn_prediction_pipeline.ipynb`.
5. Select the `.venv` Python kernel, then choose **Run All**.
6. Confirm every cell finishes without a red error and review the metrics and confusion matrix.

If PowerShell blocks environment activation, use Command Prompt and run `.venv\Scripts\activate.bat`, then install the requirements.

## Setup and run in a terminal
```bash
python -m pip install -r requirements.txt
jupyter notebook
```
Open `churn_prediction_pipeline.ipynb` and choose **Kernel → Restart & Run All**.

## Important interpretation
The dataset is small and imbalanced. The test split contains relatively few churn cases, so metrics—especially recall—can change with the split. The reported result is a demonstration, not evidence that the model is production-ready. Evaluate it on more representative data before real-world use.
