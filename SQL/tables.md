# Tables

## Creating a table

To create a new table in a database, you can use the `CREATE TABLE` statement followed by the name of the table and the fields you want in the table.

```sql
CREATE TABLE employees(
    id INTEGER,
    name TEXT,
    age INTEGER,
    is_manager BOOLEAN,
	salary INTEGER);
```

## Altering tables

We often need to alter our database schema without deleting it and re-creating it. We can use the `ALTER TABLE` to make changes in place without deleting any data.

1 - Rename a table or column
```sql
ALTER TABLE employees
RENAME TO contractors;
```

2 - ADD or DROP a column
```sql
ALTER TABLE contractors
ADD COLUMN job_title TEXT;

ALTER TABLE contractors
DROP COLUMN is_manager;
```

## Migrations

Migrations are helpful when transitioning from one state to another, fixing mistakes, or adapting a database to changes. When writing reversible migrations, we use the terms "up" and "down" migrations. An "up" migration is simply the set of changes you want to make, like altering/removing/adding/editing a table in some way. A "down" migration includes the changes what would revert any of the "up" migrations's changes.

## SQL Data Types

SQL as a language can support many different data types. However, the datatypes that your database management system (DBMS) supports will depending on the specific database you're using.

1. `NULL` - Null value.
2. `INTEGER` - A signed integer stored in 0,1,2,3,4,6, or 8 bytes.
3. `REAL` - Floating point value stored as an 64-bit [IEEE floating point number](https://en.wikipedia.org/wiki/IEEE_754).
4. `TEXT` - Text string stored using database encoding such as [UTF-8](https://en.wikipedia.org/wiki/UTF-8)
5. `BLOB` - Short for [Binary large object](https://en.wikipedia.org/wiki/Binary_large_object) and typically used for images, audio or other multimedia.
6. `BOOLEAN` - Boolean values are written in SQLite queries as `true` or `false`, but are recorded as `1` or `0`.
