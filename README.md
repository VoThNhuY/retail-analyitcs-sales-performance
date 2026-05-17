# Retail Business Performance Analytics

* This project analyzes the 2014 sales performance of the Obvience Retail Chain compared to the previous year (2013).
* The dashboard tracks monthly sales trends, monitors budget variances, and evaluates product category performance 

## 📂 Dataset
- Microsoft Retail Analysis Sample Dataset: [Obvience Retail](https://drive.google.com/drive/folders/1_pkgQIkvdNeuolH-MOb2JS3VCbu0ici_?usp=drive_link)
- The database includes six tables:
  -  Sales
  -  Store
  -  Item
  -  Time
  -  District

## 📈 DAX Measures
To calculate business performance metrics and drive the variance analysis, the following key DAX measures were developed in the Data Model:

- **This Year Sales (TY Sales):** Calculates the baseline revenue for the current fiscal period.
   ```dax
   This Year Sales = CALCULATE([TotalSales], Sales[ScenarioID]=1)
   ```

- **Last Year Sales (LY Sales):** Uses Time-Intelligence to dynamically fetch the sales performance of the exact same period in the previous year.
   ```dax
   Last Year Sales = CALCULATE([TotalSales], Sales[ScenarioID]=2)
   ```

- **Total Sales Variance:** Measures the absolute dollar difference between this year's actual performance against the previous year (or target).
   ```dax
   Total Sales Variance = [This Year Sales]-[Last Year Sales]
   ```

- **Total Sales Variance %:** Expresses the performance gap as a percentage. Uses `DIVIDE` to safely handle potential division-by-zero errors (e.g., if a store had zero sales last year).
   ```dax
   Total Sales Variance % = DIVIDE( [Total Sales Variance],[Last Year Sales])
   ```

## 📊 Dashboards
### 1. Store Sales Overview
<img width="1299" height="716" alt="image" src="https://github.com/user-attachments/assets/00a2ec6c-cc54-451b-8856-df213a0aa4e4" />

*  **Purpose:** Provides a high-level summary of total sales, new store openings, and total retail stores.
*  **Metrics:** Total Sales, New Stores Count, Total Active Stores, Sales Per Sq Ft, Total Sales Variance %.
*  **Visuals:** Sales breakdown by Chain (*Fashions Direct* vs. *Lindseys*), geographic distribution map (Postal Code analysis), and a Bubble/Scatter Chart crossing **Sales Per Sq Ft** against **Total Sales Variance %** to isolate operational efficiency.

### 2. District Monthly Sales
<img width="1304" height="731" alt="image" src="https://github.com/user-attachments/assets/8dbe4880-4d01-42e3-ba3b-ec6184fa96bf" />

* **Purpose:** Deep dives into monthly sales trends, operational variations by District Managers, and product performance.
* **Metrics:** This Year Sales (TY Sales), Last Year Sales (LY Sales), Total Sales Variance % by Fiscal Month.
* **Visuals:** Dual-axis line and shaded area chart comparing TY vs. LY Sales trends, comprehensive breakdown by Store Number/Name, and a category matrix (Womens, Mens, Children, Groceries, Accessories) to detect underperforming lines.

### 3. New Stores Analysis
<img width="1296" height="723" alt="image" src="https://github.com/user-attachments/assets/30a8d381-0785-4281-b574-0c30f0b56686" />

* **Purpose:** Evaluates the launch velocity, productivity, and space efficiency of recently opened retail outlets.
* **Metrics:** Open Store Count by Month, Sales Per Sq Ft by Location Name, Projected Volume Growth.
* **Visuals:** Open store timelines by chain, product sales distribution charts, and filter matrices to support **Demand Forecasting** and logistical supply alignment.

## 🔍 Business Insights

Based on the performance data visualized in the dashboards, here are **3 business problems**:

### 1. High Value vs. Low Efficiency Stores (Store Sales Overview)
* **Observation:** 
On the Scatter Chart (*Sales Per Sq Ft vs. Total Sales Variance %*), store **FD - 01** achieves the highest sales productivity (over $14.5 per Sq Ft) but carries a **negative Sales Variance of around -5%**. Conversely, store **FD - 02** has a positive variance (close to 0%) but very low retail space productivity ($13 per Sq Ft).
  
* **Commercial Impact:**
  - **FD - 01** is a high-potential premium location, but its target budget was set too aggressively, or it is losing local traction.
  - **FD - 02** is meeting its low target simply because the bar was set too low, leading to hidden underperformance and wasted square footage.
  
* **Action:**
  - **For FD - 01:** Review the pricing matrix and product mix (SKU optimization) to shift focus toward high-margin items to close the target gap.
  - **For FD - 02:** Readjust the sales forecasting models for the next fiscal period. Lift the target threshold and introduce aggressive performance metrics to maximize floor-space efficiency.

### 2. Sales Drop in July
* **Observation:** 
Looking at the *Last Year vs. This Year Sales* line chart, there is a severe sales drop in **July** (This Year Sales plummeted to around $2.4M compared to nearly $3.4M in March). The *Total Sales Variance %* chart confirms that July suffered a **negative variance of nearly 30%** against targets.
  
* **Commercial Impact:** 
This drop reveals a substantial seasonal bottleneck or aggressive mid-summer promotional plays by key competitors that successfully captured market share.
  
* **Action:** The Performance Executive must coordinate with Sales to review regional **Trade Discounts** or deploy hyper-targeted marketing campaigns (e.g., localized KOC/KOL networks, flash sales) specifically timed for mid-summer to protect volume and hit monthly minimum targets.

### 3. Category Underperformance: Groceries & Home Essentials
* **Observation:** In the Product Category Scatter Chart, **090-Home** and **100-Groceries** are clustered in the bottom-right corner. They exhibit very low average dollars per unit (Avg $/Unit TY is under $3) along with flat or negative sales variance.
  
* **Commercial Impact:** These low-ticket categories drag down the company's overall **Gross Profit Margin**. They utilize supply chain capacity and incur heavy logistics costs relative to their retail price without generating the required sales volume velocity.
  
* **Action:** Initiate a thorough **P&L review** for the Groceries category. If Cost of Goods Sold (COGS) and fixed logistics costs are squeezing margins, negotiate higher bulk-volume purchase agreements with B2B distributors, or implement product bundling strategies (e.g., cross-promoting or bundling low-margin groceries with high-margin categories like ***050-Shoes*** or premium accessories) to protect the net profit bottom line.

## 🛠️ Tools
* **Power BI Desktop:** Data Modeling, DAX (Data Analysis Expressions), Data Visualization.
* **Excel:** 
Initial data exploration and commercial calculation validation 
