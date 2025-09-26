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

### 2. Inserting Sample Data
![Inserting Sample Data](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/code%20za%20insertion.png)
*Caption: Screenshot of inserting sample data into `customers`, `products`, and `transactions` tables.*

### 3. Table Creation Scripts
![Table Creation Scripts](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/inserting.png)
*Caption: Screenshot of SQL scripts creating `customers`, `products`, `transactions`, and `returns_discounts` tables.*

### 4.  Also Included an ER diagram: which consists of the following;
Entity 'Customers' (rectangle): attributes in ovals - customer_id (PK), name, region.
Entity 'Products' (rectangle): attributes in ovals - product_id (PK), sku (unique), name, category.
Entity 'Transactions' (rectangle): attributes in ovals - transaction_id (PK), customer_id (FK), product_id (FK), sale_date, quantity, unit_price, amount (computed), region.
Entity 'Returns_Discounts' (rectangle): attributes in ovals - rd_id (PK), transaction_id (FK), rd_date, rd_amount, reason.
![ER Diagram](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/ERDIAGRAM.png)

## Implementation of SQL Window Functions 🛠️

### 1. Ranking: ROW_NUMBER(), RANK(), DENSE_RANK(), PERCENT_RANK() 📊
These functions assign ranks or row numbers to rows based on ordering, useful for identifying top performers like top N customers by revenue, handling ties differently.
![Code Screenshot](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/code%20za%20ranking.png)
![Table Screenshot](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/Ranking.png)

### 2. Aggregate: SUM(), AVG(), MIN(), MAX() with frame comparisons (ROWS vs RANGE) 📈
Aggregate functions compute cumulative or windowed values like sums or averages over partitions, with ROWS for physical rows and RANGE for logical value ranges, ideal for running totals and trends.
![Code Screenshot](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/code%20za%20aggregate.png)
![Table Screenshot](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/aggregate.png)

### 3. Navigation: LAG(), LEAD(), growth % calculations 🔄
Navigation functions access data from previous (LAG) or next (LEAD) rows in a partition, enabling calculations like month-over-month growth for period-to-period analysis.
![Code Screenshot](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/code%20za%20navigation.png)
![Table Screenshot](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/Navigation.png)

### 4. Distribution: NTILE(4), CUME_DIST() 📉
Distribution functions divide rows into buckets (NTILE) or compute cumulative distribution (CUME_DIST), perfect for segmenting data like customers into quartiles based on spending.
![Code Screenshot](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/code%20za%20distribution.png)
![Table Screenshot](https://github.com/KimGakuba/plsql-window-functions-Gakuba-NGABONZIZA-Kim/blob/main/images/distribution.png)

## Results Analysis 📊

### 1. Descriptive – What Happened? (Patterns, Trends, Outliers)
- **Sales Patterns**: The top-selling SKU was Salted Chips 50g with 40 units sold and 1,200 revenue, far ahead of Coffee Beans 250g (20 units, 500 revenue) and Cooking Oil 2L (6 units, 72 revenue). This sets snacks as the top FMCG demand in the data set.
- **Regional Trends**: Ruhengeri experienced the most drastic increase, with revenues increasing from 0 in early 2024 to 800 in total (with a peak of 600 in April). Kigali led in volume (450 in total) but dropped from 250 in January to 50 in March. Butare remained low-volume (522 in total) but consistent.
- **Customer Spending**: Most was spent by Amina Uwizeyimana (Ruhengeri) at 800, followed by Paul Kagabo (Butare) at 522 and John Doe (Kigali) at 450. One glitch: Kigali's March sales dropped 79% from February, perhaps a regional downturn.
- **Inventory Trends**: The present inventories are generally in good health (Coffee: 80 units, Chips: 60, Oil: 94), although Chips are drying out fastest at 40% of starting stock, while Oil is at 94% capacity.

---

### 2. Diagnostic – Why? (Causes, Comparisons, Influencing Factors)
- **Product Demand Drivers**: Snack items like Chips seem to have impulse buys and premium unit price (30 vs. Oil's 12), responsible for 62% of total revenue although with the same initial stock. Beverages (Coffee) show steady but low take-up, possibly seasonal effects, while Oil lags as it is in volume (only 6 units were sold), showing that it is a standard with occasional bulk buying.
- **Regional Differences**: Ruhengeri's 300% April boost (over Kigali's decline) is perhaps a result of local promotion or rural increases in economics, as opposed to urban Kigali's potential saturation or competition. Butare stability indicates consistent low-end demand but thin market penetration.
- **Customer Influences**: Top spenders (Amina and Paul) are linked with high-volume zones (Ruhengeri/Butare), with product mix driving them—Amina's purchase of 20 units of Chips topped the list. Kigali's outlier drop could be attributed to fewer purchases (only 3 compared with Ruhengeri's 2 high-value ones), which could have been due to supply problems or external events.
- **Inventory Factors**: Sudden drawing down in Chips (as opposed to excess Oil) uncovers out-of-balance replenishment levels; sales rate (40 units/4 months) overrides Oil's (1.5/month), risking impending stockouts if left unchecked.

---

### 3. Prescriptive – What Next? (Recommendations, Business Actions)
- **Inventory Replenishment**: Stock up Chips forward to 80+ units immediately (target 20% cushion on sales rate); re-allocate 20 units of Oil from Butare/Kigali warehouses to Ruhengeri to balance loads and prevent ageing stock.
- **Promotions & Redistribution**: Launch targeted snacks promotions in Kigali (e.g., bundle Chips with Coffee at 10% discount) to reverse the 79% decline; redirect excess Oil inventory via cross-regional discounts to Butare, expecting 15% sales increase in staples.
- **Customer Strategies**: Segment big spenders like Amina into a loyalty program (e.g., 5% repeat-purchase discount) to get them to stay; investigate Kigali's drop via POS audits and re-target John Doe with tailor-made promotions to recover 20% of the lost volume.
- **Monitoring Actions**: Develop bi-monthly SKU-by-SKU dashboards tracking MoM growth and 3-month averages; set alarms for >30% regional fluctuation to enable anticipatory redistribution, targeting 10-15% stockout/excess reduction.

## References
1. MySQL 8.0 Reference Manual — Window Functions
2. Oracle Documentation: RANK, NTILE.
3. Mode Analytics — SQL Window Functions Tutorial
4. Youtube videos - helping me to turke the challengee 
5. SQL Window Functions in Practice — Blog series
6. Kimball R. — The Data Warehouse Toolkit
7. Gartner — Inventory Optimization Primer
8. Moving Averages and Reorder Points — Supply Chain texts
9. Edrawmax- for drawing the ER Diagram
10. Academic papers on demand forecasting and inventory management
### “All sources were properly cited. Implementations and analysis represent original work. No AIgenerated content was copied without attribution or adaptation.”


# “Whoever is faithful in very little is also faithful in much.” – Luke 16:10
