# JOINS

Joins are one of the most important features that SQL offers. Joins allow us to make use of the relationships we have set up between our tables. In short, joins allow us to query multiple tables at the _same time._

##  INNER JOIN

The simplest and most common type of join in SQL is the `INNER JOIN`. By default, a `JOIN` command is an `INNER JOIN`. An `INNER JOIN` returns all of the records in `table_a` that have matching records in `table_b` as demonstrated by the following Venn diagram.

```sql
SELECT *
FROM employees
INNER JOIN departments ON employees.department_id = departments.id;
```
![image](https://github.com/user-attachments/assets/880df339-9520-4a06-bfee-4d4b4ee52d09)

## FULL JOIN  

A `FULL JOIN` combines the result set of the `LEFT JOIN` and `RIGHT JOIN` commands. It returns _all_ records from both from `table_a` and `table_b` regardless of whether or not they have matches.

![image](https://github.com/user-attachments/assets/7690549f-de04-4331-8413-c10b4a6802d7)

## RIGHT JOIN

A `RIGHT JOIN` is, as you may expect, the opposite of a `LEFT JOIN`. It returns all records from `table_b` regardless of matches, and all matching records between the two tables.

![image](https://github.com/user-attachments/assets/3fabd6ac-ef15-4250-b6c3-d0aa8edd5236)

## LEFT JOIN

A `LEFT JOIN` will return every record from `table_a` regardless of whether or not any of those records have a match in `table_b`. A left join will _also_ return any matching records from `table_b`. Here is a Venn diagram to help visualize the effect of a `LEFT JOIN`.

![image](https://github.com/user-attachments/assets/59f40123-07a3-4581-a457-a1547cb7d633)
