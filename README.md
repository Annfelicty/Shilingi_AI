# 🧠 Commodity Price Forecasting using Random Forest

## 📘 Overview
This project predicts the **next-month average price** for various commodities in Kenya using **machine learning**.  
The model leverages **historical price data**, **seasonality**, and **lag-based features** to understand trends, volatility, and relationships between time and market prices.

It’s built with a focus on:
- **Real-world price data** (food, rent, fuel, utilities, etc.)
- **Seasonality awareness**
- **Unit-level normalization** (e.g., Electricity per kWh)
- **Explainable ML (MAE, R²)** to track performance

---

## ⚙️ Key Features

✅ Predicts the **next month’s price** for each commodity  
✅ Handles multiple **units of measure** (e.g., 50 KWh, 200 KWh)  
✅ Automatically skips commodities with insufficient history  
✅ Produces a **performance summary table** (MAE, normalized MAE %, R²)  
✅ Visualizes **Actual vs Predicted** trends  
✅ Outputs **forecast results** in a single DataFrame

---

## 📂 Project Structure
📦 commodity-forecasting
├── data/
│ └── commodities.csv # Input dataset
├── models/
│ └── trained_models.pkl # (Optional) Saved models
├── notebooks/
│ └── forecast_model.ipynb # Main development notebook
├── results/
│ └── forecast_results.csv # Generated forecasts
├── README.md # You are here
└── requirements.txt # Python dependencies📦 commodity-forecasting
├── data/
│ └── commodities.csv # Input dataset
├── models/
│ └── trained_models.pkl # (Optional) Saved models
├── notebooks/
│ └── forecast_model.ipynb # Main development notebook
├── results/
│ └── forecast_results.csv # Generated forecasts
├── README.md # You are here
└── requirements.txt # Python dependencies

---

## 🧩 Data Columns Used

| Column | Description |
|--------|--------------|
| `commodity_name` | The product being tracked (e.g., Tomatoes, Electricity) |
| `units_of_measure` | Measurement unit (e.g., kg, litre, 50 KWh) |
| `current_average_price` | Current month's average market price |
| `year`, `month`, `quarter` | Date-based features |
| `price_lag_1`, `price_lag_2`, `price_lag_3` | Previous 1–3 month prices |
| `price_rolling_mean_3`, `price_rolling_std_3` | 3-month rolling average and volatility |
| `price_change_1m`, `price_change_2m` | 1-month and 2-month percentage changes |
| `is_rainy_season`, `is_harvest_season` | Binary seasonal flags |
| Encoded categorical columns | e.g., `commodity_name_encoded`, `category_encoded`, `units_encoded` |

---

## 🧮 Model Pipeline

1. **Data Preprocessing**
   - Sort by `commodity_name` and `date`
   - Generate lag, rolling, and percentage-change features
   - Encode categorical fields
   - Normalize prices when necessary (e.g., per kWh for electricity)

2. **Per-Commodity Modeling**
   - Trains a **Random Forest Regressor** for each commodity variant
   - Uses an 80/20 **time-aware split** (no shuffling)

3. **Evaluation Metrics**
   - **MAE (Mean Absolute Error):** Measures prediction deviation
   - **Normalized MAE (%):** Error as a percentage of mean price
   - **R² (Coefficient of Determination):** Measures fit quality (1 = perfect)

4. **Forecasting**
   - Uses the latest record of each commodity
   - Simulates next-month prediction
   - Produces output table with forecasted prices

---

## 📊 Example Output

### 🔧 Model Performance
| Commodity Variant | Records | MAE | MAE_% | R² |
|------------------|----------|------|--------|-----|
| Electricity - 200 kWh | 52 | 3124.0 | 9.0 | 0.91 |
| Tomatoes | 109 | 2.7 | 4.2 | 0.88 |
| Sugar | 95 | 7.35 | 3.9 | 0.59 |

### 🔮 Forecast Example
| Commodity Variant | Predicted Price Next Month | Based On | Forecast For |
|------------------|-----------------------------|-----------|---------------|
| Electricity - 200 kWh | 5469.35 | 2025-09-01 | 2025-10 |
| Tomatoes | 2.67 | 2025-09-01 | 2025-10 |
| Milk - Fresh Packeted | 61.20 | 2025-09-01 | 2025-10 |

---

## 💻 Installation

### Prerequisites
- Python ≥ 3.9
- pip or conda
- Jupyter Notebook or Google Colab

### Setup
```bash
git clone https://github.com/yourusername/commodity-forecasting.git
cd commodity-forecasting
pip install -r requirements.txt

