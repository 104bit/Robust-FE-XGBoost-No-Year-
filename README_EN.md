# F1 Pit Stop Prediction with XGBoost
[English README](README_EN.md)

This project aims to predict whether a Formula 1 car will make a pit stop on the next lap using race-related data. The model is built with the XGBoost algorithm, class imbalance is handled, and the `Year` variable is removed to reduce temporal overfitting.

## Project Objective

The main objective is to predict the `PitNextLap` target variable using in-race features. The model focuses on strategic variables such as tyre age, stint information, lap time changes, and race progress to estimate pit stop probability.

## Methodology

The project follows these main steps:

- Loading and preparing the dataset
- Transforming categorical variables into a suitable format for XGBoost
- Handling class imbalance with the `scale_pos_weight` parameter
- Removing the `Year` variable to reduce temporal overfitting
- Creating additional engineered features
- Training and validating the XGBoost model
- Analyzing feature importance
- Generating predictions for the test dataset
- Creating the final submission file

## Feature Engineering

The following features were created to improve model performance and generalization:

- `Rolling_3Lap_Time`: Average lap time over the last 3 laps
- `Stint_Position_Change`: Cumulative position change within the stint
- `Tyre_Stress_Ratio`: Ratio of tyre age to the average lifespan of the compound

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib

## Installation

Install the required libraries with:

```bash
pip install pandas numpy scikit-learn xgboost matplotlib
```

## Usage

Run the notebook to perform model training, feature engineering, evaluation, and submission generation:

```bash
jupyter notebook robust-fe-xgboost-no-year.ipynb
```

## Output

After running the model, a submission file containing pit stop probabilities for the test data is generated:

```text
f1_pitstop_submission.csv
```

## Note

The `Year` variable is intentionally excluded from the model. This helps prevent the model from memorizing past seasons and supports a more general prediction structure based on race strategy.
