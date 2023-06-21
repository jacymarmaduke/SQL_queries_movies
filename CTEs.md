# Using Common Table Expressions
```
/* Calculate the average amount paid for the top five customers. */
WITH total_amount_cte (customer_id, first_name, last_name, country, city, total_amount_paid) AS
  (SELECT A. customer_id,
          A. first_name,
          A. last_name,
          D. country,
          C. city,
          SUM(E.amount) AS total_amount_paid
  FROM customer A
  INNER JOIN address B ON A.address_id = B.address_id
  INNER JOIN city C ON B.city_id = C.city_id
  INNER JOIN country D ON C.country_id = D.country_id
  INNER JOIN payment E ON A.customer_id = E.customer_id
  WHERE city IN ('Aurora', 'Acua', 'Citrus Heights', 'Iwaki', 'Ambattur', 'Shanwei', 'So Leopoldo', 
  'Teboksary', 'Tianjin', 'Cianjur')
  GROUP BY A. customer_id,
           A. first_name,
           A. last_name,
           D. country,
           C. city
  ORDER BY total_amount_paid DESC
  LIMIT 5 )
SELECT 
    AVG(total_amount_paid)
FROM total_amount_cte
```

```
/* Count the number of top-five customers in each country. */
WITH top_five_customers_cte (customer_id, first_name, last_name, country, city, total_amount_paid) AS
  (SELECT A. customer_id,
        A. first_name,
        A. last_name,
        D. country,
        C. city,
        SUM(E.amount) AS total_amount_paid
  FROM customer A
  INNER JOIN address B ON A.address_id = B.address_id
  INNER JOIN city C ON B.city_id = C.city_id
  INNER JOIN country D ON C.country_id = D.country_id
  INNER JOIN payment E ON A.customer_id = E.customer_id
  WHERE city IN ('Aurora', 'Acua', 'Citrus Heights', 'Iwaki', 'Ambattur', 'Shanwei', 'So Leopoldo', 
  'Teboksary', 'Tianjin', 'Cianjur')
  GROUP BY A. customer_id,
           A. first_name,
           A. last_name,
           D. country,
           C. city
  ORDER BY total_amount_paid DESC
  LIMIT 5 ) 
SELECT D.country,
       COUNT(A.customer_id) AS all_customer_count,
       COUNT(E.customer_id) AS top_five_customer_count
FROM customer A
INNER JOIN address B ON A.address_id = B.address_id
INNER JOIN city C ON B.city_id = C.city_id
INNER JOIN country D ON C.country_id = D.country_id
LEFT JOIN top_five_customers_cte E ON A.customer_id = E.customer_id
GROUP BY D.country
ORDER BY top_five_customer_count DESC
```
