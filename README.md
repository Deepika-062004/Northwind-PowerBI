# Northwind-PowerBI
Power BI project using Northwind dataset with interactive dashboard

---

##  Project Objective

To analyze the Northwind dataset and create an interactive Power BI dashboard with drill-down features to explore employee and product performance in depth.

---

##  Dataset Used

- Northwind CSV
- Contains data related to:
  - Orders
  - Customers
  - Employees
  - Products
  - Shipments
- Created **additional tables** for:
  - `Employee Table`
  - `Product Table`

---

##  Key Features of the Dashboard

 **KPIs:**
- **Total Sales**: `$44.7M`
- **Total Cost**: `$24.44M`
- **Total Profit**: `$20.23M`
- **Total Shipments**: `8K`
- **LBS Count**: `458`
- **Profit %**: Based on salesperson

 **Filters:**
- Category: Bars, Bites, Other
- Country: Australia, India, UK, etc.
- Time Period: Jan 2023 – Jul 2024

 **Visuals Used:**
- KPI Cards
- Line Graph: Monthly Sales/Profit/Shipments
- Histogram: Shipment count by box
- Table: Salesperson-wise metrics
- Slicers for interactivity

---

##  Interactive Navigation Feature

  This dashboard includes **image-based page navigation**:

- 🧍‍♂️ **Click on Employee Image** → Navigates to **Employee Table Page**  
  View employee-wise sales, shipment count, and profit %
 **![Northwind Dashborard(Employee table)](https://github.com/user-attachments/assets/cdfad348-da00-4134-b834-7e405d5b8f2c)**
 
- 📦 **Click on Box Image** → Navigates to **Product Table Page**  
  Explore product details, categories, and total sales by product
**![Northwind Dashboared(Product table)](https://github.com/user-attachments/assets/6a2d534c-7e8f-44af-9274-368ce2dd30aa)**

✨ *These navigation buttons are implemented using Power BI’s **bookmark/page navigation** feature.*

---

##  DAX Measures Created

Below are the key DAX measures used in the Power BI dashboard:

- **Total Sales**:
  ```DAX
  Total Sales = SUM(Orders[Sales])
  ```

- **Total Cost**:
  ```DAX
  Total Cost = SUM(Orders[Cost])
  ```

- **Total Profit**:
  ```DAX
  Total Profit = [Total Sales] - [Total Cost]
  ```

- **Profit %**:
  ```DAX
  Profit % = DIVIDE([Total Profit], [Total Sales], 0)
  ```

- **Total Shipments**:
  ```DAX
  Total Shipments = DISTINCTCOUNT(Orders[Shipment ID])
  ```

- **LBS Count**:
  ```DAX
  LBS Count = SUM(Orders[LBS])
  ```

- **Sales by Employee**:
  ```DAX
  Sales by Employee = CALCULATE([Total Sales], ALLEXCEPT(Orders, Employees[Employee Name]))
  ```

  These DAX measures help drive the KPIs and visuals in the main dashboard and sub-pages.

---

## DAX Measures Created

Below are the DAX measures used in the Power BI Northwind Dashboard:


- **Latest Month**:
  ```DAX
  Latest Month = MAX('d_calendar'[Month])
  ```

- **LBS Count**:
  ```DAX
  LBS Count = SUM('Orders'[LBS])
  ```

- **MoM Sales (%)** (Month-over-Month Sales Growth %):
  ```DAX
  MoM Sales (%) = 
  VAR CurrentMonth = [Total Sales (Month)]
  VAR PreviousMonth = [Total Sales (Previous Month)]
  RETURN DIVIDE(CurrentMonth - PreviousMonth, PreviousMonth, 0)
  ```

- **Profit %**:
  ```DAX
  Profit % = DIVIDE([Total Profit], [Total Sales], 0)
  ```

- **Sales Target**:
  ```DAX
  Sales Target = [Total Sales] * 1.05  -- Example: 5% growth target
  ```

- **Sales_Target_Achieved**:
  ```DAX
  Sales_Target_Achieved = IF([Total Sales] >= [Sales Target], "Achieved", "Not Achieved")
  ```

- **Total Cost**:
  ```DAX
  Total Cost = SUM('Orders'[Cost])
  ```

- **Total Profit**:
  ```DAX
  Total Profit = [Total Sales] - [Total Cost]
  ```

- **Total Sales**:
  ```DAX
  Total Sales = SUM('Orders'[Sales])
  ```

- **Total Sales (Last Month)**:
  ```DAX
  Total Sales (Last Month) = 
  CALCULATE([Total Sales], PREVIOUSMONTH('d_calendar'[Date]))
  ```

- **Total Sales (Month)**:
  ```DAX
  Total Sales (Month) = 
  CALCULATE([Total Sales], MONTH('d_calendar'[Date]) = MONTH(TODAY()))
  ```

- **Total Sales (Previous Month)**:
  ```DAX
  Total Sales (Previous Month) = 
  CALCULATE([Total Sales], DATEADD('d_calendar'[Date], -1, MONTH))
  ```

- **Total Shipments**:
  ```DAX
  Total Shipments = DISTINCTCOUNT('Orders'[Shipment ID])
  ```

These measures are used to drive KPIs, conditional formatting, targets, and dynamic visuals across the dashboard.

##  Process Followed

1. Imported and cleaned `northwind.csv` in Power Query
2. Created **separate tables for Employees and Products**
3. Built data model relationships
4. Created DAX measures:
   - `Total Sales`, `Total Profit`, `Profit %`, etc.
5. Designed main dashboard and sub-pages
6. Added **image buttons for navigation** to product and employee pages

---

## Insights from Dashboard

- Products in categories like **Bars** and **Bites** generate most revenue
- Shipment distribution shows majority are low-weight boxes
- Monthly sales trend shows consistent growth

---

##  Final Conclusion

This Power BI project not only highlights analytical capabilities but also focuses on user experience through interactive navigation. Users can explore employee and product-specific insights easily through image-based buttons.

---
