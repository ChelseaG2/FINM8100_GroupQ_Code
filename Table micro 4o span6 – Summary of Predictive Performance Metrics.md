**Table: micro 4o span6 – Summary of Predictive Performance Metrics**

| Metric                | Value  | Description / Note                                  |
| --------------------- | ------ | --------------------------------------------------- |
| MAE                   | 25.400 | Mean Absolute Error (lower is better)               |
| RMSE                  | 35.482 | Root Mean Squared Error (lower is better)           |
| Pearson Correlation   | -0.045 | Linear correlation; p = 0.067                       |
| R^2                   | -0.144 | Coefficient of determination                        |
| Accuracy              | 0.554  | Proportion of correct directional predictions       |
| Precision             | 0.639  | Positive predictive value                           |
| Recall                | 0.701  | True positive rate (sensitivity)                    |
| F1 Score              | 0.668  | Harmonic mean of precision and recall               |
| ROC AUC               | 0.485  | Area under ROC curve; classification discrimination |
| DirACC                | 0.554  | Directional accuracy; binomial p = 1e-05            |
| Calibration Intercept | 13.108 | Intercept of calibration regression (SE = 0.931)    |
| Calibration Slope     | -0.246 | Slope of calibration regression (SE = 0.149)        |
| Calibration R^2       | 0.0020 | R^2 of calibration regression                       |
| Logit Accuracy        | 0.641  | Hit rate from logistic regression (directional)     |
| Logit ROC AUC         | 0.515  | ROC AUC from logistic regression                    |
| Logit Slope           | -0.006 | Slope from logit regression (SE = 0.008, p = 0.502) |