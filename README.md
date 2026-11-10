# Samsung Global Product Sales: Predictive Analytics & Power BI Dashboard
This project combines exploratory data analysis, advanced time-series forecasting, and an interactive business intelligence reporting suite to evaluate Samsung's global retail performance, regional demand patterns, and product lifecycles.
---
## 🧠 Project Logic & Methodology

This repository is split into two core analytical tracks that move from statistical time-series forecasting to interactive commercial business intelligence:

### Track 1: Time-Series Revenue Forecasting (Python & SARIMAX)

* **Core Objective:** Project future monthly sales revenue across unified product categories to support proactive inventory and financial planning.
* **Underlying Logic:**
* **Data Preprocessing & Cleaning:** Ingests raw transactional data, parses string timestamps into valid datetimes, handles missing values, and sorts entries chronologically.
* **Monthly Aggregation & Mapping:** Resamples transaction data into monthly intervals (`freq='ME'`) and groups granular product models into unified categories (**Home Appliance**, **Smartphone**, **Tablets & Accessories**, and **Wearables**).
* **Seasonal Decomposition:** Isolates the underlying long-term trend, repeating annual seasonal cycles, and irregular residual noise.
* **SARIMAX Modeling:** Upgrades standard non-seasonal models to a **SARIMA** framework (`seasonal_order=(1, 1, 1, 12)`) to capture repeating yearly waves and generate robust 6-month revenue forecasts accompanied by 95% confidence intervals.



### Track 2: Commercial Intelligence & Multi-Dashboard Suite (Power BI)

* **Core Objective:** Translate complex transactional datasets into a dynamic, stakeholder-ready reporting suite to evaluate regional market positioning and product performance.
* **Underlying Logic:**
* **Data Modeling & Relationships:** Establishes relational links between sales transactions, regional hierarchies, and temporal attributes using Power Query and DAX.
* **Market Potential & Growth Matrix:** Plots regional revenue scale against growth momentum to segment markets into strategic quadrants (Core vs. Untapped).
* **Product & Pricing Strategy Analysis:** Evaluates revenue distribution across price bands, product tiers (Budget, Mid-range, Premium), and year-over-year tier growth.
---

## 🛠️ Tech Stack & Libraries
* **Python:** Pandas, NumPy, Statsmodels (`SARIMAX`, `seasonal_decompose`), Matplotlib
* **Business Intelligence:** Power BI Desktop (Power Query, DAX, Interactive Slicers)
