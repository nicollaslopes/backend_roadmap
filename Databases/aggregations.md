# Aggregations

## SUM

The `sum` aggregation function returns the sum of a set of values. For example, the query below returns a single record containing a single field. The returned value is equal to the _total_ salary being collected by all of the `employees` in the `employees` table.

```sql
SELECT sum(salary)
FROM employees;
```

## MAX

As you may expect, the `max` function retrieves the _largest_ value from a set of values. For example:

```sql
SELECT max(price)
FROM products;
```

## MIN

The `min` function works the same as the `max` function but finds the _lowest_ value instead of the _highest_ value.

```sql
SELECT product_name, min(price)
FROM products;
```

## GROUP BY

SQL offers the `GROUP BY` clause which can group rows that have similar values into "summary" rows. It returns one row for each group. The interesting part is that each group can have an aggregate function applied to it that operates only on the grouped data.

Imagine that we have a database with songs and albums, and we want to see how many songs are on each album. We can use a query like this:

```sql
SELECT album_id, count(song_id)
FROM songs
GROUP BY album_id;
```

## Average

Just like we may want to find the minimum or maximum values within a dataset, sometimes we need to know the average. SQL offers us the `AVG()` function. Similar to `MAX()`, `AVG()` calculates the average of all non-NULL values.

```sql
SELECT avg(song_length)
FROM songs;
```

## HAVING 

When we need to filter the results of a `GROUP BY` query even further, we can use the `HAVING` clause. The `HAVING` clause specifies a search condition for a group. The `HAVING` clause is similar to the `WHERE` clause, but it operates on groups _after_ they've been grouped, rather than rows _before_ they've been grouped.

```sql
SELECT album_id, count(id) as count
FROM songs
GROUP BY album_id
HAVING count > 5;
```

## ROUND

Sometimes we need to round some numbers, particularly when working with the results of an aggregation. We can use the `ROUND()` function to get the job done. The SQL `round()` function allows you to specify both the value you wish to round and the precision to which you wish to round it:

```sql
SELECT ROUND(235.415, 2) AS RoundValue;

Result:
RoundValue:
235.420
```

## Count

We can use a `SELECT` statement to get a _count_ of the records within a table. This can be very useful when we need to know _how many_ records there are, but we don't particularly care what's in them.

```sql
SELECT COUNT(*) FROM employees;
```