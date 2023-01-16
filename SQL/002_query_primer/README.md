<!-- HEADER -->
<div align="center">
  <h1 align="center">2. Query Primer</h1>
</div>

# Query Clauses
> Clouse name / Purpose
> 
> SELECT - Determines which columns to include in the query's result set
> 
> FROM - Identifies the tables from which to retrieve data and how the tables should be joined
> 
> WHERE - Filters out unwanted data
> 
> GROUP BY - Used to group rows together by common column values
> 
> HAVING - Filters out unwanted groups
> 
> ORDER BY - Sorts the rows of the final result set by one or more columns

# Usage of query

## The SELECT Clause
```shell
SELECT *
FROM language; ## select all record from a language table
```
```shell
SELECT language_id, name, last_update
FROM language; ## select multiple records from a language table
```
```shell
SELECT language_id,
  'COMMON' language_usage, ## assign 'COMMON' value to the all record
  language_id * 3.1415927 lang_pi_value,
  upper(name) language_name, ## built-in function
FROM language;
```
```shell
SELECT DISTINCT actor_id
FROM film_actor
ORDER BY actor_id ## default: ASC
```

## The FROM Clause

### Tables
> Types of tables
> 
> * Permanent tables (i.e., created using the CREATE TABLE statement)
> * Derived tables (i.e., rows returned by a subquery and held in memory)
> * Temporary tables (i.e., volatile data held in memory)
> * Virtual tables (i.e., created using the CREATE VIEW statement)

#### Derived (subquery-generated) tables
> Subquery are surrounded by parentheses.
```shell
SELECT concat(cust.last_name, ', ', cust.first_name) full_name ## built-in function
FROM
  (SELECT first_name, last_name, email
    FROM customer
    WHERE first_name = 'JESSIE'
  ) cust;
```

#### Temporary tables
> * In general, a temporary table will disappear at the end of a transaction or when database session is closed 

#### Views
> * When the view is created, no additional data is generated or stored
```shell
> Create a view
CREATE VIEW cust_vw AS
SELECT customer_id, first_name, last_name, active
FROM customer;
```
```shell
> Show a view
SELECT first_name, last_name
FROM cust_vw
WHERE active = 0;
```

### Defining Table Aliases
```shell
SELECT c.first_name, c.last_name, time(r.rental_date) rental_time
FROM customer c
  INNER JOIN rental r
  ON c.customer_id = r.customer_id
WHERE date(r.rental_date) = '2005-06-14';
```
