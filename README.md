# AFM-244-quiz-code
AFM 244 quiz code
# Tuesday July 14 Participation — Revenue Regression Analysis

## Overview
This notebook builds and compares several linear regression models to predict a company's **revenue** using production volume and weather-related variables (cooling degree days and heating degree days). Models are trained on a training split and evaluated on a hold-out testing split using **Mean Absolute Percentage Error (MAPE)**.

## Data
- **Source file:** `AICPA_regressionAnalysisData.csv` (must be in the same directory as the notebook)
- **Split:** the dataset contains a `type` column that separates rows into `dt4training` and `dt4testing`
- **Key variables:**
  - `revenue` — dependent variable
  - `production` — production volume
  - `coolDD` — cooling degree days
  - `heatDD` — heating degree days
  - `date` — used for plotting predicted vs. actual revenue over time

## Requirements
```
numpy
pandas
matplotlib
statsmodels
```

## Structure
The notebook fits seven OLS regression models on the training data, generates predictions on the testing data, and computes MAPE for each:

| Model | Predictors | MAPE |
|---|---|---|
| Model 1 | production + coolDD | 21.7% |
| Model 2 | production | 25.4% |
| Model 3 | coolDD | 29.6% |
| Model 4 | heatDD | 21.6% |
| Model 5 | production + heatDD | **13.86%** |
| Model 6 | coolDD + heatDD | 13.87% |
| Model 7 | production + coolDD + heatDD | 14.3% |

For each model the notebook:
1. Fits an OLS regression on the training set (`statsmodels.api.OLS`)
2. Displays the fitted coefficients / regression equation
3. Applies the model to the testing set to generate predicted revenue
4. Computes absolute percentage error per observation, then the mean (MAPE)

## Result
**Model 5 (Production + heatDD)** is selected as the best model, with the lowest MAPE (~13.6–13.86%) among all models tested. A final chart compares actual vs. predicted revenue over time using this model.

## How to Run
1. Place `AICPA_regressionAnalysisData.csv` in the same directory as the notebook.
2. Run all cells in order (each model depends on `dt4training` / `dt4testing`, created in the first two cells).
3. Review the printed MAPE for each model and the final comparison chart/conclusion at the end.

