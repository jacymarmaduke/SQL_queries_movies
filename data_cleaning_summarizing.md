# SQL commands for cleaning and summarizing data

## To find duplicates in the data

SELECT title, description, release_year, language_id, rental_duration
FROM film
GROUP BY title, description, release_year, language_id, rental_duration
HAVING COUNT (*) >1
SELECT first_name, last_name, email
FROM customer
GROUP BY first_name, last_name, email
HAVING COUNT (*) >1

## To view only distinct records 

SELECT DISTINCT title,
                release_year,
                language_id,
                rental_duration
FROM film

## To find missing values in a table

SELECT
COUNT(customer_id) AS customer_id_count, 
COUNT(store_id) AS store_id_count,
COUNT(first_name) AS first_name_count,
COUNT(last_name) AS last_name_count, 
COUNT(email) AS email_count, 
COUNT(address_id) AS address_id_count, 
COUNT(activebool) AS activebool_count, 
COUNT(create_date) AS create_date_count, 
COUNT(active) AS active_count, 
COUNT(last_update) AS last_update_count,
COUNT(*) AS row_count
FROM customer

## To find non-uniform data

SELECT DISTINCT release_year, language_id, rental_duration, rental_rate, rating
FROM film

## To correct non-uniform data

UPDATE film 
SET rating = ‘G’ 
WHERE rating IN ('gen',
                 'g',
                 'General')
                 
## To generate summary statistics
SELECT 
MIN(release_year) AS release_year_min, 
MAX(release_year) AS release_year_max,
AVG(release_year) AS release_year_avg, 
MIN(rental_duration) AS rental_duration_min, 
MAX(rental_duration) AS rental_duration_max,
AVG(rental_duration) AS rental_duration_avg,
MIN(rental_rate) AS rental_rate_min, 
MAX(rental_rate) AS rental_rate_max, 
AVG(rental_rate) AS rental_rate_avg, 
MIN(length) AS length_min, 
MAX(length) AS length_max,
AVG(length) AS length_avg,
MIN(replacement_cost) AS replacement_cost_min, 
MAX(replacement_cost) AS replacement_cost_max,
AVG(replacement_cost) AS replacement_cost_avg,
MODE() WITHIN GROUP (ORDER BY rating) AS rating_mode, 
MODE() WITHIN GROUP (ORDER BY special_features) AS special_features_mode,
MODE() WITHIN GROUP (ORDER BY language_id) AS language_mode
FROM film
