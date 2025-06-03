**Table: macro 4o span12 – Summary of Predictive Performance Metrics**

| Metric                | Value  | Description / Note                                  |
| --------------------- | ------ | --------------------------------------------------- |
| MAE                   | 7.570  | Mean Absolute Error (lower is better)               |
| RMSE                  | 10.231 | Root Mean Squared Error (lower is better)           |
| Pearson Correlation   | -0.027 | Linear correlation; p = 0.276                       |
| R^2                   | -0.135 | Coefficient of determination                        |
| Accuracy              | 0.602  | Proportion of correct directional predictions       |
| Precision             | 0.696  | Positive predictive value                           |
| Recall                | 0.749  | True positive rate (sensitivity)                    |
| F1 Score              | 0.721  | Harmonic mean of precision and recall               |
| ROC AUC               | 0.530  | Area under ROC curve; classification discrimination |
| DirACC                | 0.602  | Directional accuracy; binomial p = 3.6e-16          |
| Calibration Intercept | 3.769  | Intercept of calibration regression (SE = 0.299)    |
| Calibration Slope     | -0.113 | Slope of calibration regression (SE = 0.122)        |
| Calibration R^2       | 0.0007 | R^2 of calibration regression                       |
| Logit Accuracy        | 0.688  | Hit rate from logistic regression (directional)     |
| Logit ROC AUC         | 0.530  | ROC AUC from logistic regression                    |
| Logit Slope           | 0.039  | Slope from logit regression (SE = 0.023, p = 0.083) |