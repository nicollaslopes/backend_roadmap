# ACID

One of the things we don't want to happen is any data integrity issues, losing data is the worst scenario ever. Thankfully, the databases we use already handle this kind of thing. Most modern SQL DBs use transactional standards like ACID to ensure data integrity. 

### But what's ACID?

ACID is an acronym for four different words, the principles are: completeness and concurrency. 

* **Atomicity**:  the “all or nothing” rule — the transaction either happens completely or doesn’t happen at all;

* **Consistency**: data is consistent before and after a transaction without any missing steps;

* **Isolation**: multiple transactions can happen concurrently without reading the wrong data;

* **Durability**: transactional success is robust to system failure.

It makes sure that the transactions can fail without hurting data integrity and multiple transactions can occur concurrently without reading and writing the wrong data.


*References*:
https://retool.com/blog/whats-an-acid-compliant-database

https://fauna.com/blog/what-is-acid-compliance-atomicity-consistency-isolation

https://www.youtube.com/watch?v=yaQ5YMWkxq4

https://www.youtube.com/watch?v=GAe5oB742dw