# Feature Engineering Documentation

## Engineered features

| Feature | Definition | Rationale / caution |
|---|---|---|
| `TenureYears` | `Tenure / 12` | Converts tenure into a more interpretable unit. |
| `EstimatedLifetimeValue` | Current `TotalCharges` used as a proxy | Represents charges accumulated so far; it is **not** a prediction of future customer value. |
| `AverageMonthlySpend` | `TotalCharges / Tenure` | Estimates historical average monthly spend; zero tenure is treated as missing. |
| `MonthlyChargeToAverageRatio` | `MonthlyCharges / AverageMonthlySpend` | Highlights whether the current charge differs from historical average. |
| `LongTenureFlag` | 1 if tenure is at least 24 months, else 0 | Captures a simple tenure threshold. |
| `MonthToMonthFlag` | 1 if contract is `Month-to-month`, else 0 | Captures a contract type that may relate to retention. |
| `ElectronicPaymentFlag` | 1 if payment method is `Electronic check`, else 0 | Encodes a potentially useful payment pattern. |
| `TenureBand` | New (≤12 months), Established (13–36), Loyal (>36) | Ordinal tenure grouping; category order is explicitly defined. |

## Validation choices
- Features are derived only from input columns, never from `Churn`.
- `CustomerID` is excluded because it is an identifier, not a customer behavior signal.
- Division by zero is guarded by replacing zero denominators with missing values; the pipeline imputes missing numeric values.
- The labels and thresholds are simple examples and should be checked with domain experts before real-world deployment.
