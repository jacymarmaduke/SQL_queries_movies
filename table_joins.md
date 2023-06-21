# Queries using INNER JOIN

```
/* List the top 10 countries by customer count */
SELECT D. country,
       COUNT(customer_id) AS customer_count
FROM customer A
INNER JOIN address B ON A.address_id = B.address_id
INNER JOIN city C ON B.city_id = C.city_id
INNER JOIN country D ON C.country_ID = D.country_ID
GROUP BY country
ORDER BY COUNT(customer_id) DESC
LIMIT 10
```

```
/* List the top 10 cities for customer count within the top 10 countries */
SELECT D. country, 
       C. city,
       COUNT(customer_id) AS customer_count
FROM customer A
INNER JOIN address B ON A.address_id = B.address_id
INNER JOIN city C ON B.city_id = C.city_id
INNER JOIN country D ON C.country_id = D.country_id
WHERE country IN ('India', 'China', 'United States', 'Japan', 'Mexico', 'Brazil', 'Russian Federation', 
'Philippines', 'Turkey', 'Indonesia')
GROUP BY country, city
ORDER BY COUNT(customer_id) DESC
LIMIT 10
```

```
/* Find the top 5 customers by money spent within the top 10 cities */
SELECT A. customer_id,
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
LIMIT 5
```
