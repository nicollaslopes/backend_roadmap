# JOINS

Joins are one of the most important features that SQL offers. Joins allow us to make use of the relationships we have set up between our tables. In short, joins allow us to query multiple tables at the _same time._

##  INNER JOIN

The simplest and most common type of join in SQL is the `INNER JOIN`. By default, a `JOIN` command is an `INNER JOIN`. An `INNER JOIN` returns all of the records in `table_a` that have matching records in `table_b` as demonstrated by the following Venn diagram.

```sql
SELECT *
FROM employees
INNER JOIN departments ON employees.department_id = departments.id;
```

![[Pasted image 20241205211220.png]]

## FULL JOIN  

A `FULL JOIN` combines the result set of the `LEFT JOIN` and `RIGHT JOIN` commands. It returns _all_ records from both from `table_a` and `table_b` regardless of whether or not they have matches.

![[Pasted image 20241205211400.png]]

## RIGHT JOIN

A `RIGHT JOIN` is, as you may expect, the opposite of a `LEFT JOIN`. It returns all records from `table_b` regardless of matches, and all matching records between the two tables.

![[Pasted image 20241205211444.png]]

## LEFT JOIN

A `LEFT JOIN` will return every record from `table_a` regardless of whether or not any of those records have a match in `table_b`. A left join will _also_ return any matching records from `table_b`. Here is a Venn diagram to help visualize the effect of a `LEFT JOIN`.

![[Pasted image 20241205211706.png]]

