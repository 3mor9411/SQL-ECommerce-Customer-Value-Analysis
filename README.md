# E-Commerce Customer Value & Order Metrics Analysis (SQL)

## 📌 Project Overview
This project demonstrates the use of relational database query logic to solve a standard business intelligence problem: identifying high-value customers by merging isolated data tables. The final query aggregates transactional revenue and transaction volume to calculate total lifetime value per customer.

## 🛠️ SQL Concepts Demonstrated
* **Relational Mapping:** Table linking via `INNER JOIN` logic.
* **Data Aggregation:** Revenue summation via `SUM()` and volume tracking via `COUNT()`.
* **Row Consolidation:** Dimensional grouping using `GROUP BY`.
* **Data Ordering:** Metrics sorting via `ORDER BY ... DESC` for immediate stakeholder visibility.

## 💾 The SQL Code

```sql
-- Query to join tables, aggregate total spend, count total orders, and sort by top-spending customers
SELECT 
    c.CustomerName,
    c.Country,
    SUM(o.TotalAmount) AS Total_Spent,
    COUNT(o.OrderID) AS Total_Orders
FROM Customers c
INNER JOIN Orders o ON c.CustomerID = o.CustomerID
GROUP BY c.CustomerName, c.Country
ORDER BY Total_Spent DESC;
