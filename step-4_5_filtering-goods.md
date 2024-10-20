---
description: Відфільтруйте рядки, де середня кількість товару більша за 21.
---

# Step 8. Filtering goods

```sql
SELECT 
    categories.id AS category_id,
    categories.name AS category_name,
    COUNT(products.id) AS product_count,
    FLOOR(AVG(order_details.quantity)) AS avg_product_count
FROM
    order_details
        INNER JOIN
    products ON order_details.product_id = products.id
        INNER JOIN
    categories ON products.category_id = categories.id
GROUP BY categories.id , categories.name
HAVING avg_product_count > 21;
```

#### ResultSet
![Resultset](img/p4_5.png)

