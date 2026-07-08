# Retail Demand Forecasting

Demand forecasting project using real retail sales data (Adidas US, 2020–2021). 
Comparing 3 statistical forecasting methods and evaluating performance with supply chain KPIs: MAPE, SMAPE, BIAS, MASE, and Forecast Accuracy.

---

## Objectives
- Clean and transform raw transactional data using Power Query and Python
- Aggregate daily records into monthly time series by product category
- Compare 3 methods: Naive, Rolling Moving Average (3m), and Exponential Smoothing
- Evaluate accuracy using industry-standard demand planning metrics

---

## Tool & Product Scope

| Tool | Product Selected | Selection Criteria | Key Metric |
| :--- | :--- | :--- | :--- |
| **Python** | Men's Street Footwear | Highest units sold | 593,320 Units |
| **Excel + Power Query** | Women's Apparel | Second highest revenue | $179M Revenue |

👉 [Dashboard](https://htmlpreview.github.io/?https://github.com/Norelytics/retail-demand-forecasting-adidas/blob/main/demand_forecasting_dashboard.html)

---

## Results Summary

### Python Model (Men's Street Footwear)
| Method | MAE | MAPE | SMAPE | RMSE | BIAS | MASE | Accuracy |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Naive | 3935 | 10.0% | 9.7% | 4781 | +1.4% | 0.83 | 90.0% |
| Rolling MA(3m) | 4949 | 12.8% | 12.1% | 5583 | +3.6% | 1.05 | 87.2% |
| Exp. Smoothing | 5073 | 11.8% | 12.6% | 5858 | -8.4% | 1.07 | 88.2% |

*Best method: Naive (MAPE 10.0%, MASE 0.83)*

### Excel Model (Women's Apparel)
| Method | MAE | MAPE | SMAPE | RMSE | BIAS | Accuracy |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Naive | 2125.7 | 7.6% | 7.2% | 2713.4 | +5.1% | 92.4% |
| Rolling MA(3m) | 1788.3 | 6.4% | 6.0% | 2387.6 | +4.2% | 93.6% |
| Exp. Smoothing | 2629.1 | 8.4% | 9.0% | 3320.0 | -8.2% | 91.6% |

*Best method: Rolling MA(3m) (MAPE 6.4%, Accuracy 93.6%)*

---

## Key Insights
- **Naive baseline:** Performs best for Men's Street Footwear due to stable plateau behavior after early 2021.
- **Moving Average:** Best for Women's Apparel as stable demand responds effectively to recent historical trends.
- **Bias Analysis:** Exponential Smoothing shows a systematic negative bias in both cases (overforecasting), increasing excess inventory risk.

---

## Project Structure
```text
.
├── adidas_retail_demand_forecasting.ipynb
├── Adidas_Demand_Forecasting.xlsx
├──  [Dashboard Interactivo](https://htmlpreview.github.io/?https://github.com/Norelytics/retail-demand-forecasting-adidas/blob/main/demand_forecasting_dashboard.html)
└── screenshots/
    ├── 01_power_query_transformation.png
    ├── 02_excel_forecast_womens_apparel.png
    └── 03_colab_forecast_men_street.png

