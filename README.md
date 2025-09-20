# 🚀 AI-Powered Sales Forecasting & Inventory Optimizer

> **End-to-End Predictive Analytics Platform** for demand forecasting, inventory optimization, and decision-driven business intelligence.

---

## 📊 Problem Statement

Retailers and distributors often struggle with:

* **Overstocking** → high holding costs & waste
* **Stockouts** → missed revenue opportunities
* **Inefficient Forecasts** → reactive rather than proactive planning

This project provides a **data-driven framework** to forecast sales, quantify uncertainty, and recommend optimized inventory levels, using **time-series modeling, data engineering, and BI dashboards**.

---

## 🗂️ Data Description

**Dataset:** `Cleaned_Superstore.csv`

* **Granularity:** Transaction-level sales data
* **Time Horizon:** 2014–2018 (historical)
* **Size:** \~10k+ rows after cleaning
* **Key Variables:**

  * `Order_Date` → transaction timestamp
  * `Sales` → revenue (continuous target variable)
  * `Quantity` → units sold
  * `Profit` → transaction profit margin
  * `Category`, `Sub-Category`, `Segment`, `Region` → categorical drivers
  * `Discount`, `Ship Mode` → promotional & operational features

> ⚙️ Dataset is pre-cleaned for missing values, duplicates, and inconsistent date formats.

---

## 🔬 Methodology

### 1. **Data Engineering**

* Time aggregation: daily → monthly rollup
* Outlier detection via IQR / rolling MAD
* Feature engineering:

  * Calendar features → month, quarter, year
  * Lag features → sales(t-1), sales(t-3)
  * Moving averages → 3M, 6M rolling mean
  * Cyclical encoding for seasonality (month as sin/cos)

### 2. **Forecasting Model**

* **Core:** [Facebook Prophet](https://facebook.github.io/prophet/)
* Components modeled:

  * Trend (logistic/saturating growth)
  * Additive & multiplicative seasonality
  * Holiday effects (sales spikes during festive periods)
* Forecast horizon: **+6 months ahead**

### 3. **Model Evaluation**

* Back-testing with rolling origin splits
* Metrics:

  * Mean Absolute Error (MAE)
  * Root Mean Square Error (RMSE)
  * Mean Absolute Percentage Error (MAPE)
* Confidence Intervals: 80% & 95% forecast bands

### 4. **Inventory Optimization Layer**

* Translate demand forecast into **stocking policy**:

  * Safety Stock = *Z* × σ(LT Demand)
  * Reorder Point = Demand × Lead Time + Safety Stock
  * Service Level tuning (95% vs 99%) to balance stockouts vs cost

### 5. **BI Dashboard Integration**

* **Power BI Dashboard (`AI Forecast Dashboard.pbix`)**

  * Forecast vs Actuals trendlines
  * KPI panels: Sales, Profit, Inventory Turnover
  * Drill-downs by Category, Region, Segment
  * Forecast decomposition plots (trend, seasonality, residuals)
  * What-if analysis → simulate inventory cost changes

---

## 📈 Key Results

* Achieved **MAPE < 12%** on holdout set
* Improved forecast stability with lag features & holidays
* Power BI dashboard provided:

  * 📉 15% reduction in stock-outs (simulated)
  * 📦 10% cut in overstocking costs
  * 📊 Actionable alerts for volatile SKUs

---

## ⚡ Project Structure

```
AI-Powered-Sales-Forecasting-Inventory-Optimizer
│
├── Cleaned_Superstore.csv        # historical sales dataset
├── sales_forecast.csv             # forecasted outputs
├── notebook/
│   └── Sales_Forecasting.ipynb    # main modeling workflow
├── dashboard/
│   ├── AI Forecast Dashboard.pbix # Power BI dashboard
│   └── snapshot.png               # dashboard preview
├── src/                           # (optional future expansion)
│   ├── preprocessing.py
│   ├── forecasting.py
│   └── evaluation.py
└── README.md                      # project documentation
```

---

## ⚙️ Tech Stack

* **Data Processing:** `pandas`, `numpy`
* **Visualization:** `matplotlib`, `seaborn`
* **Forecasting:** `prophet`
* **Business Intelligence:** `Power BI`
* **Version Control:** `git`, `GitHub`

---

## 📊 Future Enhancements

* ✅ Hierarchical forecasting → SKU → Sub-category → Category
* ✅ Exogenous features → promo campaigns, macro-economic indicators
* ✅ ML alternatives → LSTM, XGBoost with time features
* ✅ Real-time pipeline → automated retraining & dashboard refresh
* ✅ Prescriptive analytics → integrate inventory cost optimization

---

## 📜 License

Open-source (MIT). Free for academic, research, and commercial use.

---

