# Store Revenue Prediction: Regression Diagnostics and Model Validation

## Objective

In this project, I wanted to understand how well regression models predict store revenue, identify problems that affect their accuracy, and determine whether collecting more data or improving the model would lead to better predictions.

## Methodology

- Simulated a dataset of 400 stores with predictors including floor area, foot traffic, median income, and years open.
- Added irrelevant predictors and a highly correlated variable to examine multicollinearity.
- Fitted OLS regression and compared training and test performance.
- Examined residual plots to identify heteroskedasticity and nonlinear relationships.
- Calculated variance inflation factors (VIF) to measure multicollinearity.
- Compared models with different numbers of predictors and polynomial terms to explore the bias-variance tradeoff.
- Used 5-fold and nested cross-validation to select a model and estimate prediction error.
- Generated learning curves to determine whether the model would benefit more from additional observations or better features.
- Tested data leakage by comparing feature selection before cross-validation with feature selection inside a pipeline.

## Key Findings

- **OLS performance:** The original model had an R² of 0.7208, while its test R² was 0.6865.
- **Model complexity:** The four-predictor model had the lowest held-out MSE of approximately 1.225 billion.
- **Cross-validation:** Nested CV estimated an MSE of 869.4 million, with an approximate 95% interval of 629.7 million to 1.109 billion.
- **Heteroskedasticity:** Larger stores had greater forecasting errors, with mean absolute error increasing from $9,338.64 for small stores to $31,072.56 for very large stores.
- **Multicollinearity:** Store activity had a VIF of 14,710.70, showing substantial overlap with floor area and foot traffic.
- **Learning curve:** Training MSE was 833.3 million and validation MSE was 861.1 million, suggesting that additional data alone might offer limited improvements.
- **Data leakage:** Using 300 random predictors, the original feature-selection method produced an R² of 0.0605, compared with -0.3746 when feature selection was correctly performed inside cross-validation.

## Conclusion

This project helped me understand why a model that performs well on training data might struggle with new observations. I found that model complexity, multicollinearity, nonlinear relationships, and data leakage can all affect how we interpret regression results.

Overall, I would prioritize improving the model's functional form, particularly how it handles floor area, rather than simply collecting more stores. I would also continue using cross-validation and residual diagnostics before trusting a model's reported performance.
