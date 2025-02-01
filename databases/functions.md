# Functions

## ISNULL()

Return the specified value IF the expression is NULL, otherwise return the expression.

```sql 
SELECT IFNULL(NULL, "W3Schools.com"); -- returns NULL

SELECT IFNULL("Hello", "W3Schools.com"); -- returns "Hello"
```


A field with a NULL value is a field with no value. It is not possible to test for NULL values with comparison operators, such as =, <, or <>. We will have to use the `IS NULL` and `IS NOT NULL` operators instead.

```sql 
SELECT email  
FROM customers
WHERE email IS NULL;
```

## COALESCE()

Return the first non-null value in a list.

```sql 
SELECT COALESCE(NULL, NULL, NULL, 'W3Schools.com', NULL, 'Example.com'); 
-- returns "W3Schools.com"
```

