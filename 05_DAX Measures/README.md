# KPI & Measures
## 1. Sales and Financial KPIs
**Revenue DAX Formula:**
```DAX
Revenue =
    CALCULATE(SUM(olist_order_items_clean[price]),
    olist_orders_clean[order_status] = "Delivered")
```
*Business Question Answered:*
What is the total revenue from completed sales?

**Total Order DAX Formula:**
```DAX
Total Order =
    DISTINCTCOUNT(olist_order_items_clean[order_id])
```
*Business Question Answered:*
What is the total number of orders received?

**Unit Sold DAX Formula:**
```DAX
Unit Sold =
    CALCULATE(DISTINCTCOUNT(olist_order_items_clean[order_id]),
    olist_orders_clean[order_status] = "Delivered")
```
*Business Question Answered:*
How many products were successfully sold?

**Average Order Value DAX Formula:**
```DAX
AOV =
    DIVIDE([Revenue], [Delivered Orders], 0)
```
*Business Question Answered:*
What is the average amount a customer spends per order?

## 2. Operation, Logistic, and Shipping KPI
**Completion Rate DAX Formula:**
```DAX
Completion Rate =
    DIVIDE([Delivered Orders], [Total Order], 0)
```
*Business Question Answered:*
What is the success rate of an order, from placement until it is received by the customer?

**Completed Order DAX Formula:**
```DAX
Completed Order =
    CALCULATE(DISTINCTCOUNT(olist_orders_clean[order_id]),
    olist_orders_clean[order_status] = "Delivered",
    TREATAS(VALUES(olist_order_items_clean[order_id]),
    olist_orders_clean[order_id]))
```
*Business Question Answered:*
How many orders were successfully delivered to and received by customers?

*On Time Rate DAX Formula:*
```DAX
On Time Rate =
    DIVIDE([Delivered Early Orders] + [Ontime Orders], 
    [Delivered Orders], 0)
```
*Business Question Answered:*
What percentage of orders are delivered on time and ahead of the estimated time?

**Late Rate DAX Formula:**
```DAX
Late Rate =
    DIVIDE([Late Orders],
    [Delivered Orders], 0)
```
*Business Question Answered:*
What percentage of orders are delivered later than the estimated time?

**Average Delivery Days DAX Formula:**
```DAX
Avg. Delivery Days =
    AVERAGE(olist_orders_clean[Delivery Days])
```
*Business Question Answered:*
What is the average time it takes to deliver an order?

**Realized Freight DAX Formula:**
```DAX
Realized Freight =
    CALCULATE(SUM(olist_order_items_clean[freight_value]),
    olist_orders_clean[order_status]="Delivered")
```
*Business Question Answered:*
What is the total shipping cost paid by the customer for a delivered order?

## 3. Retention and Customer Behavior
**Total Unique Customer DAX Formula:**
```DAX
Total Customer =
    DISTINCTCOUNT(olist_customers_clean[customer_unique_id])
```
*Business Question Answered:*
How many people carry out transactions on the Olist platform?

**Total Delivered Customer DAX Formula:**
```DAX
Delivered Customer =
    CALCULATE(DISTINCTCOUNT(olist_customers_clean[customer_unique_id]),
    olist_orders_clean[order_status]=”Delivered”)
```
*Business Question Answered:*
How many customers actually ever complete a purchase?

**One-Time Customers DAX Formula:**
```DAX
One-Time Customers =
    CALCULATE( COUNTROWS(CustomerSummary),
    CustomerSummary[Delivered Order Count] = 1)
```
*Business Question Answered:*
How many customers have made only a single transaction?

**Repeat Customer DAX Formula:**
```DAX
Repeat Customer =
    CALCULATE( COUNTROWS(CustomerSummary),
    CustomerSummary[Delivered Order Count] >= 2)
```
*Business Question Answered:*
How many customers place repeat purchase?

**Repeat Purchase Rate DAX Formula:**
```DAX
Repeat Purchase Rate =
    DIVIDE([Repeat Customers], [Unique Customers], 0)
```
*Business Question Answered:*
What percentage of customers place repeat purchase?

**Orders per Customer DAX Formula:**
```DAX
Orders per Customer =
    DIVIDE(SUM(CustomerSummary[Delivered Order Count]),
    [Delivered Customers], 0)
```
*Business Question Answered:*
What is the average number of orders placed by each customer?
