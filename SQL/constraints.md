# Constraints 

## Null Values

In SQL, a cell with a `NULL` value indicates that the value is missing. A `NULL` value is very different from a zero value.

## Constraints

A `constraint` is a rule we create on database that enforces some specific behavior. For example, setting a `NOT NULL` constraint on a column ensures that the column will not accept `NULL` values. If we try to insert a `NULL` value into a column with the `NOT NULL` constraint, the insert will fail with an error message.

The `NOT NULL` constraint can be added directly to the `CREATE TABLE` statement.

```sql
CREATE TABLE employees(
    id INTEGER PRIMARY KEY,
    name TEXT UNIQUE,
    title TEXT NOT NULL
);
```

## Primary Keys

A key defines and protects relationships between tables. A **primary key** is a special column that uniquely identifies records within a table. Each table can have one, and only one primary key. It's very common to have a column named `id` on each table in database, and that `id` is the primary key for that table. No two rows in that table can share and `id`.

## Foreign Keys

Foreign keys are what makes relational databases relational! Foreign keys define the relationships between tables. Simply but, a `FOREIGN KEY` is a field in one that table references another table's `PRIMARY KEY`. Creating a `FOREIGN KEY` happens at table creation. After we define the table fields and constraints we add a named `CONSTRAINT` where we  define the `FOREIGN KEY` column and its `REFERENCES`.

```sql
CREATE TABLE departments (
    id INTEGER PRIMARY KEY,
    department_name TEXT NOT NULL
);

CREATE TABLE employees (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    department_id INTEGER,
    CONSTRAINT fk_departments
    FOREIGN KEY (department_id)
    REFERENCES departments(id)
);
```

In this example, an `employee` has a `department_id`. The `department_id` must be the same as the `id` field of a record from the `departments` table. `fk_departments` is the specified name of the `constraint`.
