
# Crop Yield Prediction with Machine Learning

Machine learning project that forecasts crop yield using **Random Forest** and **XGBoost**, trained on a merged **FAO** and **World Bank** dataset.

Academic project, Faculty of Engineering, Lebanese University (Branch I), supervised by Dr. Amani Raad.

## Team
- Mariam Ali
- Sali Al Homsi

## Overview
The goal is to predict crop yield from agricultural and country-level indicators, and to compare two tree-based models.

- **Data:** FAO agricultural data merged with World Bank indicators
- **Models:** Random Forest, XGBoost
- **Pipeline:** data cleaning, merging, imputation, feature preparation, training, evaluation
- **Demo:** static HTML site with embedded FAO data

## Project structure
```
.
├── notebooks/
│   └── crop_yield_pipeline.ipynb    # Google Colab pipeline
├── data/                            # FAO and World Bank source files (or download links)
├── demo/
│   └── index.html                   # HTML demo site
└── README.md
```
Adjust the folder names to match what you actually upload.

## Data notes
FAO files use ".." as a placeholder for missing values. These are converted to `NaN` and cast to numeric types before imputation, otherwise `SimpleImputer` raises a `ValueError`.

## How to run
1. Open the notebook in Google Colab
2. Upload the data files (or update the paths in the first cells)
3. Run all cells

Main libraries: `pandas`, `numpy`, `scikit-learn`, `xgboost`, `matplotlib`

## Setup
- **Data:** 50,051 rows after merging (10 crops, 1990 to 2013)
- **Target:** crop yield in tonnes per hectare
- **Features:** Year, average rainfall, average temperature, pesticides (tonnes), plus one-hot encoded Area and Item
- **Missing values:** median imputation (rainfall 14.6%, temperature 20.5%, pesticides 25.7% missing)
- **Time-based split:** train up to 2008, validation 2009 to 2011, test 2012 to 2013

## Results (test set)
| Model | R² | RMSE (t/ha) | MAE (t/ha) |
|---|---|---|---|
| Random Forest | 0.8649 | 3.182 | 1.754 |
| XGBoost | 0.9075 | 2.633 | 1.517 |

XGBoost gives the lowest error on the held-out years.

## Data sources
- FAO (FAOSTAT)
- World Bank Open Data

## License
MIT
