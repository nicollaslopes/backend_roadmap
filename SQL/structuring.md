# Structuring

## LIMIT

Sometimes we don't want to retrieve _every_ record from a table. For example, it's common for a production database table to have millions of rows, and `SELECT`ing all of them might crash your system. The `LIMIT` keyword can be used at the end of a select statement to reduce the number of records returned.

```sql
SELECT * FROM products
WHERE product_name LIKE '%berry%'
LIMIT 50;
```

## ORDER BY

SQL also offers us the ability to sort the results of a query using `ORDER BY`. By default, the `ORDER BY` keyword sorts records by the given field in ascending order, or `ASC` for short. However, `ORDER BY` does support descending order as well with the keyword `DESC`.

```sql
SELECT * FROM products
ORDER BY price DESC
```

