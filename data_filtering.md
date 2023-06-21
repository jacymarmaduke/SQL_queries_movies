# Filtering data using WHERE and HAVING clauses
```
/* Create a list of films rated PG or G */

SELECT film_id, title, description
FROM film
WHERE rating = 'PG' OR rating = 'G'
```
# Using aliases
```
/* Generate summary statistics for the PG and G movies with descriptive labels*/
SELECT
COUNT(film_id) AS count_of_movies,
AVG(rental_rate) AS average_movie_rental_rate,
MAX(rental_duration) AS maximum_rental_duration,
MIN(rental_duration) AS minimum_rental_duration
FROM film
WHERE rating = 'PG' OR rating = 'G'
```

# Grouping filtered and summarized data
```
/* Group the summary statistics by rating */
SELECT rating,
COUNT(film_id) AS count_of_movies,
AVG(rental_rate) AS average_movie_rental_rate,
MAX(rental_duration) AS maximum_rental_duration,
MIN(rental_duration) AS minimum_rental_duration
FROM film
WHERE rating = 'PG' OR rating = 'G'
GROUP BY rating
```
