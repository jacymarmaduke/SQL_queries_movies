# Filtering data using WHERE clause
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

# Filtering aggregated data with a HAVING clause
```
/* Generate a list of film counts by rating, but only for ratings with at least 100 titles */
SELECT rating,
       COUNT(film_id) AS count_of_movies,
FROM film
GROUP BY rating
HAVING COUNT(fim_id) > 100
ORDER BY count_of_movies DESC
```
