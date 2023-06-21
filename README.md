# SQL_queries_movies
## About
This repository contains a range of SQL queries generated for a movie rental company's database of inventory, customers and rental transactions.

## Objective
A video company is preparing for a pivot to streaming. To inform the company's business strategy, the business intelligence team requested data analysis and answers to ad-hoc questions about its inventory and customer base. I used SQL to query the database for these answers, using techniques such as Common Table Expressions (CTEs), table joins, data-filtering and subqueries.

## Data
The dataset contains 15 tables holding information about:

    -Movie inventory, including titles, actors, descriptions and release information
  
    -Customers, including location and rental history
  
    -Rental transactions, including timing and payment information
  
    -Stores, including transactions and locations

The sample database is from PostgreSQLTutorial.com. See more information about the database [here](https://www.postgresqltutorial.com/postgresql-getting-started/postgresql-sample-database/).


## Tableau analysis
I created Tableau visualizations to illustrate the results of some of my SQL queries. View more of these on my [Tableau Public page](https://public.tableau.com/app/profile/jacquelyn.marmaduke/viz/SQLVisualizations/topcustomers?publish=yes).

![Top customers and countries map produced in Tableau](https://github.com/jacymarmaduke/SQL_queries_movies/blob/cfc4631c962a880c6e81c52fc0d6bdf2d57380f5/customer%20map.png)

## Contents
**data_cleaning_summarizing.md:** Contains queries for cleaning and summarizing data, including finding missing data, inconsistent data and duplicates and calculating summary statistics such as mean, minimum, maximum and mode. Includes clauses such as SELECT, SELECT DISTINCT, HAVING, COUNT and UPDATE.

**data_filtering.md:** Contains queries for filtering, grouping, aliasing and aggregating data, using clauses such as WHERE, HAVING, AS, GROUP BY and ORDER BY.

**table_joins.md:** Contains queries for joining tables in a database and applying the joins to analyze data, using the INNER JOIN clause.

**subqueries.md:** Contains queries that use subqueries to analyze data.

**CTEs.md:** Contains queries that use common table expressions to analyze data, using the WITH clause.

