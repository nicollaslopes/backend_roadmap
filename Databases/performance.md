# Performance

## SQL Indexes

An index is an in-memory structure that ensures that queries we run on a database are performant, that is to say, they run quickly. If you can remember back to the data structures course, most database indexes are just binary trees or B-trees! The binary tree can be stored in ram as well as on disk, and it makes it easy to lookup the location of an entire row.

`PRIMARY KEY` columns are indexed by default, ensuring you can look up a row by its `id` very quickly. However, if you have other columns that you want to be able to do quick lookups on, you'll need to _index_ them. It's fairly common to name an index after the column it's created on with a suffix of `_idx`.

```sql
CREATE INDEX index_name ON table_name (column_name);
```

## Shouldn't we index everything? We can make the database ultra-fast!

While indexes make specific kinds of lookups much faster, they also add performance overhead - they can slow down a database in other ways. Think about it, if you index every column, you could have hundreds of binary trees in memory! That needlessly bloats the memory usage of your database. It also means that each time you _insert_ a record, that record needs to be added to _many_ trees - slowing down your insert speed.

*References*: https://www.codecademy.com/article/sql-indexes