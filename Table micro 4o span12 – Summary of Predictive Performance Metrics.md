**Table: micro 4o span12 – Summary of Predictive Performance Metrics**

| Metric                | Value  | Description / Note                                  |
| --------------------- | ------ | --------------------------------------------------- |
| MAE                   | 24.711 | Mean Absolute Error (lower is better)               |
| RMSE                  | 34.643 | Root Mean Squared Error (lower is better)           |
| Pearson Correlation   | -0.019 | Linear correlation; p = 0.441                       |
| R^2                   | -0.136 | Coefficient of determination                        |
| Accuracy              | 0.578  | Proportion of correct directional predictions       |
| Precision             | 0.656  | Positive predictive value                           |
| Recall                | 0.731  | True positive rate (sensitivity)                    |
| F1 Score              | 0.692  | Harmonic mean of precision and recall               |
| ROC AUC               | 0.505  | Area under ROC curve; classification discrimination |
| DirACC                | 0.578  | Directional accuracy; binomial p = 4.45e-10         |
| Calibration Intercept | 13.199 | Intercept of calibration regression (SE = 0.960)    |
| Calibration Slope     | -0.113 | Slope of calibration regression (SE = 0.159)        |
| Calibration R^2       | 0.0004 | R^2 of calibration regression                       |
| Logit Accuracy        | 0.647  | Hit rate from logistic regression (directional)     |
| Logit ROC AUC         | 0.505  | ROC AUC from logistic regression                    |
| Logit Slope           | 0.004  | Slope from logit regression (SE = 0.009, p = 0.657) |