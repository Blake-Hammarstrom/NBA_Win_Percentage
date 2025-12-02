# NBA Win Percentage Prediction (2015–2024)

## Machine Learning • R • Random Forest • Linear Regression • Feature Engineering

This project analyzes 10 seasons of NBA team performance data (2015–2024) and builds machine learning models to predict team win percentage using season-long box-score statistics.

Data is collected directly through the hoopR API, cleaned and aggregated using tidyverse, and modeled using tidymodels.

## Project Structure
### NBA-Win-Percentage-Project/
### │
### ├── nba_win_percentage.Rmd              # Source code (R Markdown)
### ├── nba_win_percentage_report.html      # Knitted report (PDF)
### ├── README.md                           # Project documentation (this file)


## Objectives

Explore statistical drivers of NBA team success

Model win percentage using machine learning

Compare model performance between Random Forest and Linear Regression

Identify the most important features influencing wins

Visualize relationships between key performance metrics

## Data Source

Data is loaded using the hoopR package:

df_raw <- load_nba_team_box(seasons = 2015:2024)


The raw data includes:

Team info

Game outcomes (win/loss)

Box-score statistics

Shooting percentages

Rebounding & possession metrics

Data is aggregated into per-game team season averages.

## Data Cleaning & Feature Engineering

Filtered for regular-season games

Grouped by season + team

Computed:

games played

wins + win percentage

per-game averages for all numeric box-score statistics

Removed ID columns and any data leakage variables from modeling

## Exploratory Data Analysis

Key analyses include:

Summary statistics of win percentage

Correlation with numeric predictors

Visualizations such as:

3-Point % vs Win % scatterplot with regression line

ggplot(aes(three_point_field_goal_pct, win_pct)) + geom_point() + ...


Top correlated variables are listed and ranked.

Modeling Approach
Train/Test Split
nba_split <- initial_split(df_model, prop = 0.8, strata = win_pct)

## Preprocessing

Using a recipe():

Remove ID columns

Impute missing values

Normalize numeric predictors

## Models Built

1. Random Forest (Tuned using Cross-Validation)

Ranger engine

Grid search over mtry + min_n

Extracted variable importance

2. Linear Regression (Baseline)

Standardized predictors

Interpretable coefficient magnitudes

Model Evaluation

Metrics evaluated:

RMSE (Root Mean Square Error)

R²

Prediction error on test set

Variable importance was extracted using:

vip(rf_fit_ranger, num_features = 20)

## Key Findings
1. Three-point efficiency is the strongest predictor of win percentage

Across all seasons from 2015–2024, 3-point field goal percentage consistently ranked as the most important factor.

2. Defensive performance matters greatly

Opponent points

Defensive rebounds

Blocks

Turnovers forced

These were strong predictors of success.

3. Random Forest outperformed Linear Regression

RF provided lower RMSE and better generalization, though R² remained moderate due to the inherent complexity of NBA performance.

## Technologies Used

R

tidyverse

tidymodels

hoopR

ranger

vip

ggplot2

## How to Run the Project

Clone the repository

Install required R packages:

install.packages(c("tidyverse", "janitor", "lubridate", "tidymodels", "vip", "finetune", "hoopR"))


Open the .Rmd file in RStudio / Posit Workbench

Click Knit to generate the report
