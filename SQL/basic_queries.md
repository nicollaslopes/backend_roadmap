# Basic Queries

## As clause in SQL

Sometimes we need to structure the data we return from our queries in a specific way. An `AS` clause allows us to "alias" a piece of data in our query. The alias only exists for the duration of the query.

```sql
SELECT employee_id AS id, employee_name AS name
FROM employees;
```

## Count

We can use a `SELECT` statement to get a _count_ of the records within a table. This can be very useful when we need to know _how many_ records there are, but we don't particularly care what's in them.

```sql
SELECT COUNT(*) FROM employees;
```

## Between

We can check if values are `between` two numbers using the `WHERE` clause in an intuitive way. We can also query results that are `NOT BETWEEN` two specified values.

```sql
SELECT employee_name, salary
FROM employees
WHERE salary BETWEEN 30000 and 60000;


SELECT product_name, quantity
FROM products
WHERE quantity NOT BETWEEN 20 and 100;
```

## Distinct 

Sometimes we want to retrieve records from a table without getting back any duplicates.

```sql
SELECT DISTINCT previous_company
FROM employees;
```

## Logical Operators 

The logical `AND` operator can be used to narrow down our result sets even more.

```sql
SELECT product_name, quantity, shipment_status
FROM products
WHERE shipment_status = 'pending'
AND quantity BETWEEN 0 and 10;
```

As you've probably guessed, if the logical `AND` operator is supported, the `OR` operator is probably supported as well.

```sql
SELECT product_name, quantity, shipment_status
FROM products
WHERE shipment_status = 'out of stock'
OR quantity BETWEEN 10 and 100;
```

Another variation to the `WHERE` clause we can utilize is the `IN` operator. `IN` returns `true` or `false` if the first operand matches _any_ of the values in the second operand. The `IN` operator is a shorthand for multiple `OR` conditions.

```sql
SELECT product_name, shipment_status
FROM products
WHERE shipment_status IN ('shipped', 'preparing', 'out of stock');
```

Sometimes we don't have the luxury of knowing _exactly_ what it is we need to query. Have you ever wanted to look up a song or a video but you only remember _part_ of the name? SQL provides us an option for when we're in situations `LIKE` this.

The `LIKE` keyword allows for the use of the `%` and `_` wildcard operators. Let's focus on `%` first. The `%` operator will match zero or more characters. We can use this operator within our query string to find more than just exact matches depending on where we place it. The first select will fetch everything that starts with "banana". The second one will fetch everything that ends with "banana". The third one will fetch everything that starts and end with "banana".

```sql
SELECT * FROM products
WHERE product_name LIKE 'banana%';

SELECT * FROM products
WHERE product_name LIKE '%banana';

SELECT * FROM products
WHERE product_name LIKE '%banana%';
```

## Subqueries

Sometimes a single query is not enough to retrieve the specific records we need. Subqueries can be very useful in a number of situations when trying to retrieve specific data that wouldn't be accessible by simply querying a single table.

```sql
SELECT id, song_name, artist_id
FROM songs
WHERE artist_id IN (
    SELECT id
    FROM artists
    WHERE artist_name LIKE 'Rick%'
);
```

