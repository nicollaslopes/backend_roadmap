
# What is SQL?

Structured Query Language or SQL, is the primary language used to manage and interact with relational databases. SQL is a language that we use to communicate with most databases.

### Select Statement

We can retrieve data from a table using "Select". In this case, we use "id" as a selected column which we want to get the data.

```SELECT id FROM users; ```

If you want to select more than one field, you can specify multiple fields separated by commas.

```SELECT id, name FROM users;```

We can select every fields using the shorthand * syntax

```SELECT * FROM users;```

### NoSQL vs SQL

When we talk about SQL Databases, we have to mention about NoSQL. In short, NoSQL is a database that doesn't use SQL (Structured Query Language). Each NoSQL has its own way of writing and executing queries. For exemple, MongoDB uses MQL (MongoDB Query Language).

While most relational databases are very similar, NoSQL databaes tend to be very unique and are used for more specific purposes. 
SQL Databases examples: PostgreSQL, MySQL, SQLite, SQLServer, etc.
NoSQL Databases examples: MongoDB, Redis, ElasticSearc, etc.


