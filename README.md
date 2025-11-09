# Commodity Price Forecasting Using Machine Learning

## Project Overview

This project predicts the **next-month average prices** of key commodities in Kenya, using historical data, seasonality trends, and lag-based features. The goal is to provide **actionable forecasts** for stakeholders such as businesses, government agencies, and supply chain managers, helping them make informed procurement, pricing, and risk management decisions.

The modeling approach focuses on:

- High-quality **real-world price data** across multiple commodity types (food, energy, utilities, rent, etc.)
- Awareness of **seasonality and market cycles**
- **Unit normalization**, e.g., electricity in kWh
- Explainable and interpretable machine learning models, primarily **Random Forest**, with metrics to track predictive accuracy



## Project Objectives

1. **Forecast Commodity Prices**  
   Predict the next month’s average price for each commodity variant, enabling better planning and cost management.

2. **Understand Price Dynamics**  
   Quantify short-term and seasonal trends, volatility, and persistence using lag, rolling averages, and change features.

3. **Support Decision-Making**  
   Generate actionable insights for businesses, policymakers, and investors using interpretable ML models.

4. **Provide Robust and Scalable Tools**  
   Implement per-commodity modeling pipelines that scale to hundreds of items with automated evaluation and reporting.



## Data

The project uses historical commodity prices from 2012–2025. The dataset includes:

| Column | Description |
|--------|-------------|
| `commodity_name` | Name of the commodity (e.g., Tomatoes, Electricity) |
| `units_of_measure` | Unit for the price (e.g., kg, litre, 50 KWh) |
| `current_average_price` | Monthly average market price |
| `year`, `month`, `quarter` | Time-based features for seasonality capture |
| `price_lag_1`, `price_lag_2`, `price_lag_3` | Lag features for last 1–3 months |
| `price_rolling_mean_3`, `price_rolling_std_3` | Rolling mean and volatility |
| `price_change_1m`, `price_change_2m` | Percentage price changes |
| `is_rainy_season`, `is_harvest_season` | Binary flags for seasonality |
| Encoded categorical columns | e.g., `commodity_name_encoded`, `category_encoded`, `units_encoded` |

> Data is preprocessed to handle missing values, normalize units, and encode categorical variables, ensuring model-ready inputs.



## Modeling Pipeline

1. **Data Preprocessing**
   - Sorting and organizing by commodity and date
   - Feature engineering (lags, rolling statistics, percentage changes)
   - Categorical encoding and normalization where necessary

2. **Per-Commodity Modeling**
   - Each commodity is modeled individually using **Random Forest Regressor**
   - 80/20 time-based train-test split to respect temporal structure

3. **Evaluation Metrics**
   - **MAE (Mean Absolute Error)** – absolute deviation between actual and predicted prices
   - **Normalized MAE (%)** – error as a percentage of mean price
   - **R² (Coefficient of Determination)** – goodness-of-fit metric

4. **Forecast Generation**
   - Uses the latest available data to predict the next month
   - Outputs include predicted prices, confidence measures, and evaluation summaries



## Example Outputs

### Model Performance

| Commodity Variant      | Records | MAE   | MAE_% | R²  |
|------------------------|---------|-------|-------|-----|
| Electricity - 200 kWh  | 52      | 3124  | 9.0   | 0.91|
| Tomatoes               | 109     | 2.7   | 4.2   | 0.88|
| Sugar                  | 95      | 7.35  | 3.9   | 0.59|

### Forecast Results

| Commodity Variant         | Predicted Price Next Month | Based On   | Forecast For |
|---------------------------|---------------------------|------------|--------------|
| Electricity - 200 kWh     | 5469.35                  | 2025-09-01 | 2025-10     |
| Tomatoes                  | 2.67                      | 2025-09-01 | 2025-10     |
| Milk - Fresh Packeted     | 61.20                     | 2025-09-01 | 2025-10     |



## Key Features

- Next-month forecasting for each commodity variant
- Handles multiple units with proper normalization
- Skips insufficient history automatically
- Generates performance tables for MAE, R², and normalized errors
- Visualizes actual vs predicted prices for better interpretation
- Outputs forecast results in a structured DataFrame or CSV



## Installation

### Prerequisites

- Python ≥ 3.9
- pip or conda
- Jupyter Notebook or Google Colab

### Setup
 **```bash
git clone https://github.com/yourusername/commodity-forecasting.git**

## Running the Notebook

1. Open `notebooks/forecast_model.ipynb` in Jupyter or Google Colab.  
2. Ensure `data/commodities.csv` is in place.  
3. Steps to run:
   - Preprocess data
   - Train per-commodity Random Forest models
   - Evaluate model performance
   - Generate next-month forecasts



## Future Improvements

- Integrate **Prophet** for advanced seasonal time series forecasting  
- Compare performance against **XGBoost** and ensemble methods  
- Incorporate economic indicators (fuel prices, inflation, rainfall) for richer features  
- Build a **dashboard** for stakeholders to view forecasts interactively  
- Implement **real-time alerts** for significant commodity price movements  


## Deployment & Access

### Hugging Face Model Deployment
The forecasting models are deployed on **Hugging Face Spaces** for interactive use.  
- **Access the live model here:** [Hugging Face Space - Commodity Forecasting](https://huggingface.co/spaces/yourusername/commodity-forecasting)  
- Users can input commodity data and view **next-month predictions** directly in the web interface.

### Tableau Dashboard
A **Tableau dashboard** has been created to visualize historical and forecasted commodity prices.  
- Tracks **actual vs predicted prices** over time  
- Highlights **seasonal trends and volatility**  
- Filters by commodity type, units, and date range  
- **Access the dashboard here:** [Tableau Public - Commodity Forecasting](https://public.tableau.com/app/profile/yourusername)](https://public.tableau.com/app/profile/stanley.njihia/viz/Inflation_Tracker/CommodityDashboard?publish=yes )

### Presentation Slides
A set of **slides summarizing the project, methodology, and key insights** has been prepared for stakeholders.  
- Includes model performance comparisons (Random Forest, Prophet, XGBoost)  
- Highlights **business insights, actionable recommendations, and seasonal trends**  


## Contact & Support

For questions, feedback, or collaboration:  
- **Author:** Shilingi_AI 

