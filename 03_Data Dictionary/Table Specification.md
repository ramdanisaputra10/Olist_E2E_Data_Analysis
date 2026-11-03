# Dataset and Data Structure
## 1. Customer Table (olist_customer_dataset.csv)
This table contains customer demographic data and serves as a primary reference for identifying unique buyers and mapping their geographic distribution.
| No | Column Name | Data Type | Description / Business Logic |
|----|-------------|-----------|-------------|
|01|customer_id|Text (Alphanumeric)|Each time a customer places an order, a new `customer_id` is created (used for joining with the `orders` table).|
|02|customer_unique_id|Text (Alphanumeric)|A unique code for each customer. This column enables the tracking of repeat purchases and the analysis of Customer Lifetime Value.|
|03|customer_zip_code_prefix|Text/Number|The first five digits of the customer's postal code.|
|04|customer_city|Text|Name of the city where the customer is located.|
|05|customer_state|Text (2 letter code)|The abbreviation for the Brazilian state where the customer resides.|

## 2. Orders Table (olist_orders_dataset.cvs)
A table that records the entire operational cycle, ordering time, and the status of orders and deliveries for every transaction on the platform.
| No | Column Name | Data Type | Description / Business Logic |
|----|-------------|-----------|-------------|
|01|order_id|Text(Alphanumeric)|A primary key that identifies each “unique” order.|
|02|customer_id|Text(Alphanumeric)|Foreign key connected to the Customer Table.|
|03|order_status|Text|Order status (Ex: Delivered, Shipped, Invoiced, Processing, Cancelled).|
|04|order_purchased_timestamp|DateTime|The time and date the customer placed an order.|
|05|order_approved_at|DateTime|Order validation time.|
|06|order_delivered_carrier_date|DateTime|The time when an order is handed over to the shipping carrier.|
|07|order_delivered_customer_date|DateTime|Date and time the package was received by the customer.|
|08|order_estimated_delivery_date|DateTime|Estimated date and time for package delivery.|

## 3. Order Items Table (olist_order_items_dataset.cvs)
A table containing details of the items and prices purchased in each order.
| No | Column Name | Data Type | Description / Business Logic |
|----|-------------|-----------|-------------|
|01|order_id|Text(Alphanumeric)|Foreign key to link data back to the main order table.|
|02|order_items_id|Integer|Order sequence number from the same order block.|
|03|product_id|Text(Alphanumeric)|Foreign Key that connects to the product table.
|04|seller_id|Text(Alphanumeric)|A foreign key that links to a specific seller for the purpose of preparing products.|
|05|shipping_limit_date|DateTime|Strict SLA deadlines established by Olist for sellers to hand over products to logistics partners.
|06|price|decimal|Selling price of a product.|
|07|freight_value|decimal|Shipping costs are based on the delivery distance and the weight of the product.|

## 4.	Order Payment Table (olist_order_payment_dataset.cvs)
This table contains details of financial transactions for each order, including payment methods, installment structures, and total payments.
| No | Column Name | Data Type | Description / Business Logic |
|----|-------------|-----------|-------------|
|01|order_id|Text(Alphanumeric)|Foreign key to link data back to the main order table.|
|02|payment_sequential|Integer|A sequence number that identifies a customer using more than one payment method for a single order.|
|03|payment_type|Text|Available payment methods (Ex: credit_card, boleto, voucher, debit_card, not_defined).|
|04|payment_installment|Integer|The installment amount paid by the customer for the credit card payment method.|
|05|payment_value|Decimal|Total bill for a single transaction.|

## 5.	Product Table (olist_product_dataset.cvs)
A master table that stores product data, including product category names and product sizes/dimensions.
| No | Column Name | Data Type | Description / Business Logic |
|----|-------------|-----------|-------------|
|01|product_id|Text(Alphanumeric)|Primary key for identifying a specific product.
|02|product_category_name|Text|Product category names in Portuguese.|
|03|product_name_length|Integer|Total characters in the product name.|
|04|product_description_length|Integer|Total characters in the product detail description.|
|05|product_photos_qty|Integer|Total number of product photos published on the platform.|
|06|product_weight_g|Integer|Product weight in Grams.|
|07|product_length_cm|Integer|Product length in Centimeters.|
|08|product_height_cm|Integer|Product height in Centimeters.|
|09|product_width_cm|Integer|Product width in Centimeters.|

## 6.	Product Category Name Translation Table (product_category_name_translation.cvs)
Table lookup for reference in translating original product names written in Portuguese.
| No | Column Name | Data Type | Description / Business Logic |
|----|-------------|-----------|-------------|
|01|product_category_name|Text|Product category names in Portuguese, linked directly to the product table.|
|02|product_category_name_english|Text|Product category names translated into English.|

## 7.	Order Review Table (olist_order_reviws_dataset.cvs)
This table contains post-delivery customer ratings and reviews.
| No | Column Name | Data Type | Description / Business Logic |
|----|-------------|-----------|-------------|
|01|review_id|Text(Alphanumeric)|Primary key for identifying a specific review.|
|02|order_id|Text(Alphanumeric)|A foreign key that references transaction data in the orders table.|
|03|review_score|Integer (1-5)|Ratings given by customers.|
|04|review_comment_title|Text|Review title provided by the customer (often left blank).|
|05|review_comment_message|Text|Detailed review provided.|
|06|review_creation_date|DateTime|Date and time the customer was sent a satisfaction survey.|
|07|review_answer_timestamp|DateTime|Date and time the customer submitted their survey response (review).|

## 8.	Seller Table (olist_seller_dataset.cvs)
A master table containing data on registered sellers, ranging from their IDs to their demographic information.
| No | Column Name | Data Type | Description / Business Logic |
|----|-------------|-----------|-------------|
|01|seller_id|Text(Alphanumeric)|A primary key for identifying a seller registered on the platform.|
|02|seller_zip_code_prefix|Text / Number|The first 5 digits of the seller's postal code.|
|03|seller_city|Text|Name of the city where the seller is located.|
|04|seller_state|Text (2 letter code)|The abbreviation for the Brazilian state where the seller resides.|
