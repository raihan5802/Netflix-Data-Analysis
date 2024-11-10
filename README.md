# Netflix Data Analysis

This project involves analyzing a Netflix dataset to gain insights into the content availability, popularity, and growth trends on Netflix. The analysis includes handling missing data, feature engineering, popularity prediction, geographical availability analysis, time series forecasting, and growth pattern clustering.

## Project Overview

### Dataset
The dataset used for this project contains information on Netflix shows, including:
- **Columns**: `show_id`, `type`, `title`, `director`, `cast`, `country`, `date_added`, `release_year`, `rating`, `duration`, `listed_in`, `description`
- **File Path**: `/kaggle/input/netflix-shows/netflix_titles.csv`

### Key Objectives
1. **Data Cleaning and Preprocessing**: Handle missing values, apply feature engineering, and encode categorical variables.
2. **Popularity Prediction**: Create a synthetic popularity metric based on cast and director counts, as well as the duration of the show.
3. **Geographical Analysis**: Analyze content availability across different countries.
4. **Time Series Forecasting**: Forecast Netflix content additions over the next few years.
5. **Content Growth Patterns**: Cluster growth patterns by year using KMeans clustering.

## Project Structure

### 1. Data Loading and Exploration
- Load the Netflix dataset and display initial rows.
- Perform basic exploratory data analysis and inspect missing values.

### 2. Data Preprocessing
- **Handle Missing Values**: Replace missing values in `director`, `cast`, `country`, `date_added`, and `rating` with default values.
- **Encoding**: 
  - Label encode `type` (Movie or TV Show).
  - One-hot encode `rating` categories.
  - Frequency encode `country`.
  - Extract additional features such as `director_count`, `cast_count`, and parts of `date_added`.

### 3. Feature Engineering
- **Duration Processing**: Extract numerical values from `duration` and create new columns for `duration_int` and `duration_type`.
- **Date Processing**: Extract `year_added`, `month_added`, and `day_added` from `date_added`.

### 4. Popularity Prediction
- Define a synthetic popularity metric based on:
  - **Cast Count**: Weighted at 0.3.
  - **Director Count**: Weighted at 0.5.
  - **Duration**: Weighted at 0.2.

### 5. Model Training and Evaluation
- **Feature Selection**: Use a set of features including encoded ratings, country encoding, and derived features (e.g., director count, cast count).
- **Split Data**: Split the data into training and testing sets.
- **Train Models**:
  - Train and evaluate multiple models, including RandomForest, XGBoost, and ExtraTrees, to predict content popularity.
  - Optimize hyperparameters for XGBoost using Optuna.

### 6. Geographical Analysis of Content Availability
- Count the number of titles available in each country.
- Visualize the top 10 countries by content count.

### 7. Time Series Forecasting
- **Forecasting Model**: Fit an ARIMA model to predict Netflix content additions in the upcoming years.
- **Visualization**: Plot historical data along with forecasted values.

### 8. Content Growth Pattern Analysis
- **Clustering**: Apply KMeans clustering on the yearly content count to identify growth patterns.
- **Visualization**: Display the growth clusters over time.

## Results

### Model Performance
The best-performing model for predicting content popularity was `XGBoost`, optimized with an R² score of approximately 0.999.

### Key Findings
- **Geographical Distribution**: Countries like the United States, India, and the United Kingdom have the highest number of titles.
- **Content Growth**: The ARIMA model forecasts a steady increase in new content additions for the coming years.
- **Growth Patterns**: Three distinct growth patterns were identified through KMeans clustering, showing variability in content addition rates across different years.

## Future Work
- Enhance popularity metrics by incorporating additional features.
- Explore alternative clustering methods to identify finer growth patterns.
- Expand the forecasting model to include more complex time series algorithms.

## Requirements
- Python libraries: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`, `xgboost`, `optuna`, `statsmodels`

## Author
This analysis was conducted as part of a data science exploration on Netflix content patterns.
