**Table: micro o4mini span6 – Summary of Predictive Performance Metrics**

| Metric                | Value                         | Description / Note                                  |
| --------------------- | ----------------------------- | --------------------------------------------------- |
| MAE                   | 24.844                        | Mean Absolute Error (lower is better)               |
| RMSE                  | 34.653                        | Root Mean Squared Error (lower is better)           |
| Pearson Correlation   | 0.007                         | Linear correlation; p = 0.778                       |
| R^2                   | -0.091                        | Coefficient of determination                        |
| Accuracy              | 0.595                         | Proportion of correct directional predictions       |
| Precision             | 0.644                         | Positive predictive value                           |
| Recall                | 0.824                         | True positive rate (sensitivity)                    |
| F1 Score              | 0.723                         | Harmonic mean of precision and recall               |
| ROC AUC               | 0.499                         | Area under ROC curve; classification discrimination |
| DirACC                | 0.595                         | Directional accuracy; binomial p = 5.18e-15         |
| Calibration Intercept | 12.318                        | Intercept of calibration regression (SE = 1.039)    |
| Calibration Slope     | 0.028                         | Slope of calibration regression (SE = 0.110)        |
| Calibration R^2       | 0.0000                        | R^2 of calibration regression                       |
| Logit Accuracy        | 0.641                         | Hit rate from logistic regression (directional)     |
| Logit ROC AUC         | 0.499                         | ROC AUC from logistic regression                    |
| Logit Slope           | 0.000 (SE = 0.006, p = 0.957) | Slope from logit regression                         |