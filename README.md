# NBA_Win_Percentage
## Predictive modeling • Feature engineering • Random Forest • Linear Regression • Data Visualization

Built an end-to-end machine learning pipeline using 10 seasons of NBA team box-score data (2015–2024) to analyze which performance metrics best predict a team’s season win percentage.

## Tools & Libraries

R, tidyverse, tidymodels, hoopR, ranger, vip, ggplot2

## Project Steps & Methods

Data Acquisition: Pulled 10 years of NBA team box score data using the hoopR API.

Data Cleaning & Aggregation: Converted play-by-play stats into per-game team-season averages; removed data leakage variables.

Exploratory Data Analysis:

Computed summary statistics for win percentage

Built correlation rankings for all numeric features

Visualized key relationships (e.g., 3-pt percentage vs. win%)

## Modeling:

Split data into training/testing sets using stratified sampling

Built a Random Forest regression model with cross-validation and hyperparameter tuning

Built a Linear Regression baseline model for comparison

## Model Evaluation:

Assessed RMSE, R², and test-set predictive performance

Extracted variable importance to identify which stats drive winning

## Key Findings:

Three-point efficiency was the strongest predictor of win percentage

Opponent scoring, defensive rebounds, and turnovers were major drivers

Random Forest outperformed linear regression in predictive accuracy despite moderate R²

## Result Summary

Developed a reliable model capable of estimating NBA team win percentage based on aggregated season performance metrics, providing interpretable insights into the modern game's statistical drivers.
