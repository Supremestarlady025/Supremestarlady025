
# 📊 Kultra Mega Stores Inventory Analysis (2009–2012)

This repository contains SQL-style analysis performed on order data from Kultra Mega Stores (KMS), focusing on sales performance, customer value, and shipping cost optimization.

---

## 🧠 Case Scenario I

### 1. Product Category with the Highest Sales
```sql
SELECT "Product Category", SUM(Sales) AS Total_Sales
FROM kms_inventory
GROUP BY "Product Category"
ORDER BY Total_Sales DESC
LIMIT 1;
```
➡️ Result: **Technology** — ₹5,984,248.18

---

### 2. Top 3 and Bottom 3 Regions by Sales
```sql
SELECT Region, SUM(Sales) AS Total_Sales
FROM kms_inventory
GROUP BY Region
ORDER BY Total_Sales DESC
LIMIT 3;
```
➡️ Top 3: West, Ontario, Prarie

```sql
SELECT Region, SUM(Sales) AS Total_Sales
FROM kms_inventory
GROUP BY Region
ORDER BY Total_Sales ASC
LIMIT 3;
```
➡️ Bottom 3: Yukon, Northwest Territories, Nunavut

---

### 3. Total Sales of Appliances in Ontario
```sql
SELECT SUM(Sales)
FROM kms_inventory
WHERE "Product Category" = 'Appliances' AND Region = 'Ontario';
```
➡️ Result: ₹202,346.84

---

### 4. Advice for Bottom 10 Customers
```sql
SELECT "Customer Name", SUM(Sales) AS Total_Sales
FROM kms_inventory
GROUP BY "Customer Name"
ORDER BY Total_Sales ASC
LIMIT 10;
```
➡️ Strategy:
- Personalized marketing
- Promotions and bundles
- Re-engagement campaigns

---

### 5. Shipping Method with the Most Cost
```sql
SELECT "Ship Mode", SUM("Shipping Cost") AS Total_Shipping
FROM kms_inventory
GROUP BY "Ship Mode"
ORDER BY Total_Shipping DESC
LIMIT 1;
```
➡️ Result: **Delivery Truck**

---

## 🔍 Case Scenario II

### 6. Most Valuable Customers and Their Purchases
```sql
SELECT "Customer Name", SUM(Sales) AS Total_Sales
FROM kms_inventory
GROUP BY "Customer Name"
ORDER BY Total_Sales DESC
LIMIT 5;
```
Then group their purchases by category.

---

### 7. Small Business Customer with Highest Sales
```sql
SELECT "Customer Name", SUM(Sales) AS Total_Sales
FROM kms_inventory
WHERE "Customer Segment" = 'Small Business'
GROUP BY "Customer Name"
ORDER BY Total_Sales DESC
LIMIT 1;
```
➡️ Result: Dennis Kane — ₹75,967.59

---

### 8. Corporate Customer with Most Orders
```sql
SELECT "Customer Name", COUNT(*) AS Order_Count
FROM kms_inventory
WHERE "Customer Segment" = 'Corporate'
GROUP BY "Customer Name"
ORDER BY Order_Count DESC
LIMIT 1;
```
➡️ Result: Adam Hart — 27 Orders

---

### 9. Most Profitable Consumer
```sql
SELECT "Customer Name", SUM(Profit) AS Total_Profit
FROM kms_inventory
WHERE "Customer Segment" = 'Consumer'
GROUP BY "Customer Name"
ORDER BY Total_Profit DESC
LIMIT 1;
```
➡️ Result: Emily Phan — ₹34,005.44

---

### 10. Customers Who Returned Items
➡️ ❌ No column for return data available

---

### 11. Shipping Cost vs Order Priority
```sql
SELECT "Order Priority", "Ship Mode", AVG("Shipping Cost") AS Avg_Shipping_Cost
FROM kms_inventory
GROUP BY "Order Priority", "Ship Mode";
```
➡️ Finding: Shipping cost **not aligned** with priority. Express Air used broadly, even for Low priority.

---

## 📁 Files Included
- `kms_inventory_analysis_with_sql.md`: Full analysis summary with SQL
- `kms_inventory_data.csv`: Source dataset

---
