# **👤 Student Profile**  

🔹 **NAME:** NGABONZIZA Kim Gakuba  
🔹 **ID:** `27670`  
🔹 **GROUP:**  **D**  

---
# FMCG Sales and Inventory Analysis Project 📊

## Business Context 🏪
A mid-sized regional wholesale trader in Rwanda and neighboring districts imports and distributes Fast-Moving Consumer Goods (FMCG), including snacks, beverages, cooking oil, and toiletries. The Sales and Supply Chain teams require SKU-level visibility across regions to prevent stockouts and minimize excess inventory, enabling efficient inventory management and optimized distribution.

---

## Data Challenge 📉
The current sales and inventory data are fragmented:
- Sales data is sourced from daily Point of Sale (POS) feeds and weekly summaries.
- Product codes are inconsistent across datasets.
- Returns and discounts are recorded separately in Excel files.

This fragmentation complicates SKU-level, regional, and time-series comparisons, leading to stockouts of top-selling SKUs in some districts and overstocking of others in warehouses.

---

## Expected Outcome 🎯
The project aims to deliver actionable insights through:
- **Ranked Top SKUs**: Identify top-performing SKUs per region and quarter.
- **Monthly Sales Totals**: Aggregate sales data for each SKU on a monthly basis.
- **Month-over-Month Growth**: Calculate growth trends to highlight demand shifts.
- **Customer Spending Quartiles**: Segment customers based on spending to inform targeted promotions.
- **3-Month Moving Averages**: Smooth out fluctuations to guide replenishment and redistribution strategies.

## Success Criteria 📈

1. **Top 5 Products per Region/Quarter**: Identify the top 5 SKUs by sales volume for each region and quarter using `RANK()` to prioritize high-demand products.
2. **Running Monthly Sales Totals**: Calculate cumulative sales totals for each SKU per month using `SUM() OVER()` to track sales performance over time.
3. **Month-over-Month Growth**: Compute percentage growth in sales for each SKU compared to the previous month using `LAG()` or `LEAD()` to identify demand trends.
4. **Customer Quartiles**: Segment customers into four equal groups based on spending using `NTILE(4)` to enable targeted promotions.
5. **3-Month Moving Averages**: Calculate the average sales over a 3-month rolling window for each SKU using `AVG() OVER()` to smooth demand fluctuations for forecasting.



## Database Schema 💻

### 1. MySQL codes for creating Customer, products,transactions Tables
![Creating Customer Table](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/code%20za%20table.png)
*Caption: Screenshot of creating the `customers` table with columns for customer ID, name, and region.*

### 2. Customer Spending Quartiles
![Customer Spending Quartiles](images/customer-spend-quartiles.png)
*Caption: Screenshot of a query ranking customers by total spend and assigning quartiles per region.*

### 3. Monthly Sales and Moving Averages
![Monthly Sales and Moving Averages](images/monthly-sales-moving-avg.png)
*Caption: Screenshot of a query calculating monthly sales totals and 3-month moving averages per region.*

### 4. Sample Data Tables
![Sample Data Tables](images/sample-data-tables.png)
*Caption: Screenshot showing sample data for `customers`, `products`, and `transactions` tables.*

### 5. Table Creation Scripts
![Table Creation Scripts](images/table-creation-scripts.png)
*Caption: Screenshot of SQL scripts creating `customers`, `products`, `transactions`, and `returns_discounts` tables.*

### 6. Region-Quarter Sales Ranking
![Region-Quarter Sales Ranking](images/region-quarter-sales.png)
*Caption: Screenshot of a query ranking products by revenue per region and quarter with ranking metrics.*

### 7. Inserting Sample Data
![Inserting Sample Data](images/insert-sample-data.png)
*Caption: Screenshot of inserting sample data into `customers`, `products`, and `transactions` tables.*

### 8. Month-over-Month Percent Change
![Month-over-Month Percent Change](images/mom-percent-change.png)
*Caption: Screenshot of a query calculating month-over-month percent change in revenue per product and region.*

### 9. Updated Customer Spending with Cumulative Distribution
![Updated Customer Spending](images/updated-customer-spend.png)
*Caption: Screenshot of an updated query for customer spending with an approximate cumulative distribution.*

### 10. Refined Monthly Sales with Aggregates
![Refined Monthly Sales](images/refined-monthly-sales.png)
*Caption: Screenshot of a refined query for monthly sales with running totals and regional aggregates.*

---
