# Predictive Performance Summary

## Micro-level – Summary of Predictive Performance Metrics

| Scenario | MAE | RMSE | R² | Accuracy | DirACC | ROC AUC | Calib. Intercept | Calib. Slope | Logit Accuracy | Logit ROC AUC |
|----------|-----|------|----|----------|--------|---------|------------------|--------------|----------------|---------------|
| 4o span 6  | 25.400 | 35.482 | −0.144 | 0.554 | 0.554 | 0.485 | 13.108 | −0.246 | 0.641 | 0.515 |
| 4 o span 12 | 24.711 | 34.643 | −0.136 | 0.578 | 0.578 | 0.505 | 13.199 | −0.113 | 0.647 | 0.505 |
| o4 mini span 6  | 24.844 | 34.653 | −0.091 | 0.595 | 0.595 | 0.499 | 12.318 |  0.028 | 0.641 | 0.499 |
| o4 mini span 12 | 24.350 | 33.946 | −0.090 | 0.586 | 0.586 | 0.487 | 12.621 |  0.040 | 0.647 | 0.513 |

## Macro-level – Summary of Predictive Performance Metrics

| Scenario | MAE | RMSE | R² | Accuracy | DirACC | ROC AUC | Calib. Intercept | Calib. Slope | Logit Accuracy | Logit ROC AUC |
|----------|-----|------|----|----------|--------|---------|------------------|--------------|----------------|---------------|
| 4o span 6  | 7.870 | 10.610 | −0.117 | 0.587 | 0.587 | 0.514 | 3.369 | −0.163 | 0.668 | 0.514 |
| 4o span 12 | 7.570 | 10.231 | −0.135 | 0.602 | 0.602 | 0.530 | 3.769 | −0.113 | 0.688 | 0.530 |
| o4 mini span 6  | 7.929 | 10.886 | −0.168 | 0.599 | 0.599 | 0.516 | 3.227 |  0.003 | 0.671 | 0.516 |
| o4 mini span 12 | 7.482 | 10.281 | −0.144 | 0.619 | 0.619 | 0.526 | 3.356 |  0.080 | 0.687 | 0.526 |

### Notes

- **DirACC** = Directional Accuracy (share of correct up/down forecasts).
- **Calib. Intercept** and **Calib. Slope** stem from calibration regression of predictions on outcomes; ideal values are 0 and 1.
- “Logit” columns report classification performance when probability outputs are thresholded at 0.5.
