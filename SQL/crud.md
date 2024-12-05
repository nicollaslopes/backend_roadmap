# CRUD

CRUD is an acronym that stands for `CREATE`, `READ`, `UPDATE`, and `DELETE`. These four operations are the foundation of nearly every database you will create.

`INSERT Statement`

```sql
INSERT INTO employees(id, name, title)
VALUES (1, 'Nico', 'Engineer');
```

`DELETE Statement`

```sql
DELETE FROM employees WHERE id = 251;
```

`UPDATE Statement`

```sql
UPDATE employees SET name = "Bob" WHERE id = 251;
```

`SELECT Statement`

```sql
SELECT * FROM employees
```
