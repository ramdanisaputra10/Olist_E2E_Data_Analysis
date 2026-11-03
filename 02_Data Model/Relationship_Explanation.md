# Relationship Explanation

| No | Source Table | Destination Table | Key Column | Cardinality | Cross-filter Ditection | 
|----|--------------|------------|-------------|------------|------------|
|01|merge_product_translation|olist_products_clean|product_category_name_english|One to Many|Both|
|02|olist_customer_clean|CustomerSummary|customer_unique_id|Many to One|Single|
|03|olist_order_items_clean|olist_products_clean|product_id|Many to One|Single|
|04|olist_order_items_clean|olist_seller_clean|seller_id|Many to One|Single|
|05|olist_order_payment_clean|olist_orders_clean|order_id|Many to One|Single|
|06|olist_order_review_clean|olist_orders_clean|order_id|Many to One|Single|
|07|olist_order_review_clean|olist_order_items_clean|order_id|Many to One|Both|
|08|olist_orders_clean|olist_customer_clean|customer_id|Many to One|Both|
|09|olist_products_clean|olist_product_translation_clean|product_id|Many to One|Single|
