**Table: macro 4o span6 – Summary of Predictive Performance Metrics**

| Metric                | Value  | Description / Note                                           |
| --------------------- | ------ | ------------------------------------------------------------ |
| MAE                   | 7.87   | Mean Absolute Error (lower is better)                        |
| RMSE                  | 10.61  | Root Mean Squared Error (lower is better)                    |
| Pearson Correlation   | -0.039 | Linear correlation; not significant (p = 0.117)              |
| R^2                   | -0.117 | Coefficient of determination; negative indicates fit worse than mean |
| Accuracy              | 0.587  | Proportion of correct directional predictions                |
| Precision             | 0.671  | Positive predictive value                                    |
| Recall                | 0.748  | True positive rate (sensitivity)                             |
| F1 Score              | 0.708  | Harmonic mean of precision and recall                        |
| ROC AUC               | 0.514  | Area under ROC curve; classification discrimination          |
| DirACC                | 0.587  | Directional accuracy; p < 0.001 (significant over random)    |
| Calibration Intercept | 3.369  | Intercept of calibration regression (SE = 0.296, p < 0.001)  |
| Calibration Slope     | -0.163 | Slope of calibration regression (SE = 0.123, p = 0.188, not significant) |
| Calibration R^2       | 0.0015 | R^2 of calibration regression (very weak fit)                |
| Logit Accuracy        | 0.668  | Hit rate from logistic regression (directional)              |
| Logit ROC AUC         | 0.514  | ROC AUC from logistic regression                             |
| Logit Slope           | 0.028  | Slope from logit regression (SE = 0.021, p = 0.191, not significant) |