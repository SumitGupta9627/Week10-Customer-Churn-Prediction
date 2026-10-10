# Preprocessing Report — Customer Churn Prediction

## Project overview
The objective is to prepare customer records for a machine-learning model that predicts whether a customer will churn. The supplied dataset has **500 rows and 9 columns**. The target is `Churn` (1 = churn, 0 = retained).

## Data audit
- Rows: 500
- Columns: 9
- Missing values by column: {"CustomerID": 0, "Tenure": 0, "MonthlyCharges": 0, "TotalCharges": 0, "Contract": 0, "PaymentMethod": 0, "PaperlessBilling": 0, "SeniorCitizen": 0, "Churn": 0}
- Churn counts: {"0": 447, "1": 53}
- Overall churn rate: 10.6%
- `CustomerID` is an identifier and is excluded from model inputs.

## Preprocessing decisions
1. **Missing data:** numeric columns use median imputation; categorical columns use most-frequent imputation inside the pipeline.
2. **Categorical encoding:** OneHotEncoder handles nominal fields (`Contract`, `PaymentMethod`, `PaperlessBilling`). OrdinalEncoder is used for ordered `TenureBand`. LabelEncoder is demonstrated for the target labels only.
3. **Scaling:** StandardScaler is used in the main model pipeline. MinMaxScaler is demonstrated and compared separately in the notebook.
4. **Outliers:** IQR and Z-score are used to flag possible outliers in `Tenure`, `MonthlyCharges`, and `TotalCharges`. The project reports outlier counts instead of deleting valid customer rows automatically.
5. **Feature engineering:** creates `TenureYears`, `EstimatedLifetimeValue`, `AverageMonthlySpend`, `MonthlyChargeToAverageRatio`, `LongTenureFlag`, `MonthToMonthFlag`, `ElectronicPaymentFlag`, and `TenureBand`.
6. **Feature selection:** numeric correlation and mutual information are explored. These are diagnostic methods and do not prove causation.
7. **Leakage prevention:** the train/test split is performed before fitting the final preprocessing pipeline; imputers, scalers, and encoders are fitted using training data only.

## Model and validation
A Random Forest classifier is placed after a ColumnTransformer in a single scikit-learn Pipeline. The notebook reports accuracy, precision, recall, F1-score, classification report and a confusion matrix. It also runs three basic validation assertions.

## Run instructions
1. Install Python 3.10 or newer.
2. Extract the project ZIP.
3. Open a terminal in the extracted folder.
4. Run `pip install -r requirements.txt`.
5. Run `jupyter notebook` and open `churn_prediction_pipeline.ipynb`.
6. Select **Kernel → Restart & Run All** and confirm that all cells complete.

## Important limitations
This dataset is small (500 records), so results may vary with the train/test split and should not be treated as production-grade. Validate the model on additional, representative data before business use.
