# SQL

## What is SQL?

Structured Query Language or SQL, is the primary language used to manage and interact with relational databases. SQL is a language that we use to communicate with most databases.

### Select Statement

We can retrieve data from a table using "Select". In this case, we use "id" as a selected column which we want to get the data.

```SELECT id FROM users; ```

If you want to select more than one field, you can specify multiple fields separated by commas.

```SELECT id, name FROM users;```

We can select every fields using the shorthand * syntax

```SELECT * FROM users;``` 