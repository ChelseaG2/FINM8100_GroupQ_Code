**Table: micro o4mini span12 – Summary of Predictive Performance Metrics**

| Metric                | Value                          | Description / Note                                  |
| --------------------- | ------------------------------ | --------------------------------------------------- |
| MAE                   | 24.350                         | Mean Absolute Error (lower is better)               |
| RMSE                  | 33.946                         | Root Mean Squared Error (lower is better)           |
| Pearson Correlation   | 0.010                          | Linear correlation; p = 0.681                       |
| R^2                   | -0.090                         | Coefficient of determination                        |
| Accuracy              | 0.586                          | Proportion of correct directional predictions       |
| Precision             | 0.639                          | Positive predictive value                           |
| Recall                | 0.830                          | True positive rate (sensitivity)                    |
| F1 Score              | 0.722                          | Harmonic mean of precision and recall               |
| ROC AUC               | 0.487                          | Area under ROC curve; classification discrimination |
| DirACC                | 0.586                          | Directional accuracy; binomial p = 3.8e-12          |
| Calibration Intercept | 12.621                         | Intercept of calibration regression (SE = 1.086)    |
| Calibration Slope     | 0.040                          | Slope of calibration regression (SE = 0.113)        |
| Calibration R^2       | 0.0001                         | R^2 of calibration regression                       |
| Logit Accuracy        | 0.647                          | Hit rate from logistic regression (directional)     |
| Logit ROC AUC         | 0.513                          | ROC AUC from logistic regression                    |
| Logit Slope           | -0.002 (SE = 0.005, p = 0.649) | Slope from logit regression                         |