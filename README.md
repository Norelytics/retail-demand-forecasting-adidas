# Retail Demand Forecasting — Adidas US Sales Dataset

## Overview
Demand forecasting project applied to real retail sales data (Adidas US, 2020–2021),
comparing 3 forecasting methods and evaluating performance using industry-standard 
KPIs used in demand planning: MAPE, SMAPE, BIAS, MASE and Forecast Accuracy.

## Objectives
- Clean and transform raw sales data using Power Query and Python
- Aggregate daily transactions into monthly time series by product
- Compare 3 forecasting methods: Naive, Rolling MA(3m) and Exponential Smoothing
- Evaluate accuracy using MAPE, SMAPE, RMSE, BIAS, MASE and Forecast Accuracy
- Apply the same methodology in two different tools to demonstrate versatility

## Product Selection

For Python, products were ranked by total units sold across 24 months.
Men's Street Footwear was selected as the highest-selling product with 593,320 units.

| Product | Total Units Sold |
|---|---|
| Men's Street Footwear | 593,320 |
| Men's Athletic Footwear | 435,526 |
| Women's Apparel | 433,827 |
| Women's Street Footwear | 392,269 |
| Women's Athletic Footwear | 317,236 |
| Men's Apparel | 306,683 |

For Excel, products were ranked by total revenue. Women's Apparel was selected 
as the second highest-revenue product with $179M, using a different metric 
to complement the Python analysis.

| Product | Total Sales |
|---|---|
| Men's Street Footwear | $208M |
| Women's Apparel | $179M |
| Men's Athletic Footwear | $153M |
| Women's Street Footwear | $128M |
| Men's Apparel | $123M |
| Women's Athletic Footwear | $106M |

## Tools
| Tool | Product | Selection Criteria |
|---|---|---|
| Python (pandas, numpy, matplotlib) | Men's Street Footwear | Highest units sold |
| Excel + Power Query | Women's Apparel | Second highest revenue |

## Results Summary

### Men's Street Footwear — Python
| Method | MAE | MAPE | SMAPE | RMSE | BIAS | MASE | Forecast Accuracy |
|---|---|---|---|---|---|---|---|
| Naive | 3935 | 10.0% | 9.7% | 4781 | +1.4% | 0.83 | 90.0% |
| Rolling MA(3m) | 4949 | 12.8% | 12.1% | 5583 | +3.6% | 1.05 | 87.2% |
| Exp. Smoothing | 5073 | 11.8% | 12.6% | 5858 | -8.4% | 1.07 | 88.2% |

Best method: Naive — MAPE 10.0%, MASE 0.83 (beats naive benchmark)

### Women's Apparel — Excel
| Method | MAE | MAPE | SMAPE | RMSE | BIAS | Forecast Accuracy |
|---|---|---|---|---|---|---|
| Naive | 2125.7 | 7.6% | 7.2% | 2713.4 | +5.1% | 92.4% |
| Rolling MA(3m) | 1788.3 | 6.4% | 6.0% | 2387.6 | +4.2% | 93.6% |
| Exp. Smoothing | 2629.1 | 8.4% | 9.0% | 3320.0 | -8.2% | 91.6% |

Best method: Rolling MA(3m) — MAPE 6.4%, Forecast Accuracy 93.6%

## Key Insights
- Naive performs best for Men's Street Footwear — the series behaves like a
  stable plateau after the post-COVID structural break in early 2021
- Rolling MA(3m) performs best for Women's Apparel — stable demand responds
  well to recent history
- Exponential Smoothing shows negative BIAS in both products — systematic
  overforecast — excess stock risk
- Both products show a structural break in January 2021, likely driven by
  post-COVID demand recovery
- The same methodology applied in Python and Excel produced consistent results

## Business Interpretation
A positive BIAS indicates systematic underforecast — stockout risk.
A negative BIAS indicates systematic overforecast — excess stock risk.
MASE below 1 means the model outperforms the naive benchmark.

## Dataset
- Source: Adidas US Sales Dataset — Kaggle
- Period: January 2020 — December 2021 (24 months)
- Products: 6 footwear and apparel categories
- Rows: 9,562 transactions

## Project Structure
retail-demand-forecasting-adidas/
├── adidas_retail_demand_forecasting.ipynb   / Python analysis (Google Colab)
├── Adidas_Demand_Forecasting.xlsx           / Excel + Power Query analysis
├── demand_forecasting_dashboard.html        / Interactive dashboard
├── screenshots/
│   ├── 01_power_query_transformation.png    / Power Query data cleaning
│   ├── 02_excel_forecast_womens_apparel.png / Excel forecast chart
│   └── 03 colab forecast_men_street_footwear.png / Python colab forecast chart
└── README.md
