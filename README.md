# Samsung Global Product Sales: Predictive Analytics & Power BI Dashboard

This project combines exploratory data analysis, advanced time-series forecasting, and an interactive business intelligence reporting suite to evaluate Samsung's global retail performance, regional demand patterns, and product lifecycles.

## 📋 Dataset Architecture & Attribute Dictionary

The analysis is built upon transactional, product-level, market-level, and customer-level attributes from the Samsung Global Product Sales dataset. 
Below is the complete data dictionary defining each field:

| Field Name | Field Description |
| --- | --- |
| **Sale_ID** | Unique identifier for each sales transaction |
| **Sale_date** | Date of the sale |
| **Year** | Year extracted from `sale_date` |
| **Quarter** | Quarter of the year (e.g., Q2, Q4) |
| **Month** | Month of the sale, sometimes shown as % distribution |
| **Country** | Country where the sale occurred |
| **City** | City where the sale occurred |
| **Product_name** | Name/model of the Samsung product sold |
| **Category** | Product category (e.g., Galaxy S, Accessories, Monitor) |
| **Storage** | Storage capacity of the device (e.g., 128 GB, 1 TB) |
| **Color** | Color of the product |
| **Is_5g** | Whether the device supports 5G (true/false or Yes/No) |
| **Unit_price_usd** | Price per unit in USD |
| **Discount_pct** | Discount percentage applied to the sale |
| **Units_sold** | Number of units sold in the transaction |
| **Discounted_price** | Price after discount applied |
| **Revenue_usd** | Total revenue in USD (`units_sold` $\times$ `discounted_price`) |
| **Currency** | Currency used for the transaction (e.g., EUR, NOK, ARS) |
| **Sales_channel** | Channel through which the sale was made (e.g., E-commerce Platform, Corporate/B2B, Carrier Store) |
| **Payment_method** | Method of payment (e.g., Cash, EMI, Debit Card, BNPL) |
| **Customer_segment** | Customer type (e.g., Government, Individual, Enterprise, Education) |
| **Customer_age_group** | Age range of the customer (e.g., 18-24, 25-34, 55+) |
| **Previous device** | Previous device owned by the customer (e.g., Android/Samsung, New User, N/A) |
| **Customer_rating** | Customer satisfaction rating (2.5 to 5.0 scale) |
| **Return_status** | Whether the product was kept or returned |
| **Exchange_rate** | Implied exchange rate used to convert local currency to USD (e.g., 907.0 ARS per USD) |
| **Local_currency_price** | Price in local currency before conversion to USD |
| **Local_currency_revenue** | Revenue in local currency (`units_sold` $\times$ discounted price in local currency) |

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

📊 **Key Findings from Power BI Dashboards**

* **Regional Market Positioning**:
  * Europe and Asia emerge as dominant core revenue drivers, capturing the highest volume of total sales and unit distribution.
  * Emerging regions show high growth momentum but lower absolute market size, highlighting clear expansion opportunities for targeted marketing campaigns.

* **Product Tier & Portfolio Dynamics**:
  * Mid-range and budget devices drive the highest transaction volumes and unit sales, while premium flagship devices (such as foldable and Galaxy S series) contribute disproportionately to total revenue value.
  * Accessories and wearable ecosystems demonstrate strong cross-selling potential when bundled with smartphone purchases.

* **Pricing & Discounting Efficiency**:
  * Moderate promotional discounting effectively boosts unit velocity, but excessive discounting on premium tiers yields diminishing returns on overall net revenue.

## 🛠️ Tech Stack & Libraries
* **Python:** Pandas, NumPy, Statsmodels (`SARIMAX`, `seasonal_decompose`), Matplotlib
* **Business Intelligence:** Power BI Desktop (Power Query, DAX, Interactive Slicers)
