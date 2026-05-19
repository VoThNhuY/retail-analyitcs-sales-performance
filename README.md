# Retail Business Performance Analytics

* This project analyzes the 2014 sales performance of the Obvience Retail Chain compared to the previous year (2013).
* The dashboard tracks monthly sales trends, monitors sales variances, and evaluates product category performance. 

## 📂 Dataset
- Microsoft Retail Analysis Sample Dataset: [Obvience Retail](https://drive.google.com/drive/folders/1_pkgQIkvdNeuolH-MOb2JS3VCbu0ici_?usp=drive_link)
- The database includes six tables:
  -  Sales
  -  Store
  -  Item
  -  Time
  -  District

## 📈 DAX Measures
These DAX measures calculate sales performance and variances:

- **This Year Sales (TY Sales):** Calculates the total revenue for the current year.
   ```dax
   This Year Sales = CALCULATE([TotalSales], Sales[ScenarioID]=1)
   ```

- **Last Year Sales (LY Sales):** Calculates the total revenue for the previous year.
   ```dax
   Last Year Sales = CALCULATE([TotalSales], Sales[ScenarioID]=2)
   ```

- **Total Sales Variance:** Calculates the sales difference between this year and last year.
   ```dax
   Total Sales Variance = [This Year Sales]-[Last Year Sales]
   ```

- **Total Sales Variance %:** Shows the sales difference as a percentage. It uses DIVIDE to avoid errors if last year sales are zero.
   ```dax
   Total Sales Variance % = DIVIDE( [Total Sales Variance],[Last Year Sales])
   ```

## 📊 Dashboards
### 1. Store Sales Overview
<img width="1270" height="712" alt="image" src="https://github.com/user-attachments/assets/d9c704c4-c5a9-4b92-91d0-11c9d268ad42" />

*  **Overview:**
    * This dashboard monitors retail business operations. It tracks total sales, store locations, and regional performance.

* **Metrics:** Total Sales, New Stores Count, Total Active Stores, Sales Per Sq Ft, Total Sales Variance %.

* **Visuals:**

  * **This Year Sales by Chain (Pie Chart):**
    * The business has two brands.
      * **Fashions Direct** generates the highest revenue, contributing **$15.66M** (about 71% of total sales).
      * **Lindseys** contributes **$6.39M** (about 29%).
    * The system operates **104 total stores**, including **10 new stores** opened this year.
    
  * **Total Sales Variance by Fiscal Month and District Manager (Column Chart):**
    * This chart tracks the monthly sales changes for each District Manager.
      * **In March**, sales growth was strong. Almost all managers increased their sales, and manager Tina Lassila recorded the highest growth.
      * **In January, April, and July**, there were large sales drops. Manager Andrew Ma and Manager Carlos Grilo recorded the lowest sales performance.
      
  * **This Year Sales by PostalCode and Store Type (Map):**
    * This map shows store locations.
      * Red dots are old stores (Same Store).
      * Blue dots are new stores (New Store).
      * Most stores come from states in the East and South-East of the US, like Ohio (OH), Pennsylvania (PA), and North Carolina (NC).
    
  * **Total Sales Variance %, Sales Per Sq Ft and This Year Sales by District (Scatter Chart):**
    * This chart compares sales per sq ft and variance percentage for each district. The bubble size shows this year's sales volume. 
      * **FD-01** has the highest efficiency ($14.59 per sq ft), but its sales dropped by -4.92% compared to last year. 
      * **FD-02** has a large sales volume and its sales are the most stable (closest to last year's sales at -0.98%).
      * **LI-01** shows the lowest performance. Its sales dropped heavily (-9.15%), and it has a low sales efficiency ($12.47 per sq ft).

### 2. District Monthly Sales
<img width="1274" height="715" alt="image" src="https://github.com/user-attachments/assets/8fa3d67d-1e0e-49d2-97b9-4f0aba5988d4" />

* **Overview:**
    * This page tracks sales performance over time. It helps us monitor store metrics, seasonal changes, and product sales drops.
    
* **Metrics:** This Year Sales (TY Sales), Last Year Sales (LY Sales), Total Sales Variance % by Fiscal Month.

* **Visuals:**

  * **This Year Sales by StoreNumberName (Bar Chart):**
    * This chart tracks the total sales of 104 individual stores.
      * **Store 13 - Charles** records the highest sales (**$0.64M**).
      * **Store 565 - Pasadena Lindseys** has the lowest sales (**$18K**).
    
  * **Total Sales Variance % by FiscalMonth (Column Chart):**
    * This chart shows monthly growth trends.
      * March grew the fastest (nearly 35%). However, January, April, and July **dropped significantly. Sales in July dropped by more than 20%**.
    
  * **Last Year Sales and This Year Sales by FiscalMonth (Area Chart):**
    * This area chart compares This Year (Red) and Last Year (Blue) sales trends over time.
      * **The Trend:** February and March this year were higher than last year. But **from April to August, sales this year were lower than last year**.
      
  * **Total Sales Variance %, Avg $/Unit TY and This Year Sales by Category (Scatter Chart):**
    * This chart shows product performance. The horizontal axis (X-axis) shows the percentage of variance. The vertical axis (Y-axis) shows the average unit price. The bubble size represents this year's sales volume.
      * **020-Mens (Largest Volume):** This is the largest bubble on the chart, generating the highest sales of **$4.45M**. It is located almost exactly on the 0% baseline (-0.02% variance).
      * **050-Shoes (Highest Unit Price):** This bubble is at the top of the chart because it has the highest average price ($13.84). It has a large sales volume ($3.57M) and a small negative variance of -1.80%.
      * **010-Womens (Lowest Variance):** This bubble is located farthest to the left because it has the lowest performance. It recorded a large negative variance of **-33.30%**.
      * **080-Accessories & 090-Home (Positive Variance):** These categories are on the right side of the chart because they achieved positive variance. Accessories recorded **+8.34%** and Home recorded **+4.79%**.

### 3. New Stores Analysis
<img width="1275" height="715" alt="image" src="https://github.com/user-attachments/assets/64b20d9f-6d28-4afb-b833-97496449280b" />

* **Overview:**
    * This page tracks the performance, sales growth, and space usage of our 10 new stores.
    
* **Metrics:** Number of new stores, Sales per square foot ($/Sq Ft), and Monthly sales growth.

* **Visuals:**

  * **Open Store Count by Open Month and Chain (Stacked Column Chart):**
    * This chart tracks open store timelines by chain.
      * **Fashions Direct** (Blue) opened stores early (Jan-Apr).
      * **Lindseys** (Red) opened stores later (May and July).
    
  * **Sales Per Sq Ft by Name (Bar Chart):**
    * This chart tracks store efficiency by calculating sales per square foot.
      *  **Winchester Fashions Direct** achieves the highest efficiency ($21.22/sq ft).
      *  **Pasadena Lindseys** has the lowest efficiency ($10.92/sq ft).
    
  * **This Year Sales by FiscalMonth (Line Chart):**
    * This chart shows the total revenue trend for all new stores. Sales increased every month from January to August as the new stores became fully operational.

## 🔍 Business Insights

Based on the performance data visualized in the dashboards, here are **3 business problems**:

### 1. District Sales Efficiency
* **Observation:** 
  * On the Scatter Chart (*Sales Per Sq Ft vs. Total Sales Variance %*), store **FD - 01** has the highest efficiency ($14.5 per sq ft) but shows a negative sales variance (nearly -5%).
  * In contrast, **FD-02** has a lower efficiency (**$12.97** per sq ft) but its sales variance is close to zero (**-0.98%**)
  
* **Issue:**
  * **FD-01** makes the most money from its store space but is losing sales compared to last year.
  * **FD-02** keeps its sales stable compared to last year, but its store space efficiency is low.
  
* **Recommendation:**
  * **For FD-01:** Change the product mix and focus on high-priced items to grow sales.
  * **For FD-02:** Check store space usage and improve sales efficiency per sq ft.

### 2. Monthly Sales Drop (July)
* **Observation:** 
    * In July, sales dropped heavily to **$2.33M** (compared to **$3.75M** in March). The sales variance in July was **-27.99%** compared to last year.
  
* **Issue:** 
    * This big drop shows that summer sales are weak, or competitors are attracting customers with better promotions.
  
* **Recommendation:**
    * Review summer discounts and launch new marketing campaigns (like flash sales or working with local KOCs/KOLs) to increase sales in July

### 3. Low-Price Categories
* **Observation:**
    * On the Scatter Chart, **100-Groceries** and **090-Home** have a very low average price per unit (**$1.47** and **$3.93**), even though their sales grew compared to last year (**+2.42%** and **+4.79%**)
  
* **Issue:**
    * These categories sell many products but make very little money per item. This can increase delivery and logistics costs but brings low profit for the business.
  
* **Recommendation:**
    * Create product combo (for example: group low-price groceries with high-price items like **050-Shoes**) to increase the total bill value.

## 🛠️ Tools
* **Power BI Desktop:** Data Modeling, DAX (Data Analysis Expressions), Data Visualization.
* **Excel:** 
Used for basic data checking and calculations.
