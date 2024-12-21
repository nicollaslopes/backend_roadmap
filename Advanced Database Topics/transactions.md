# Transactions

A database transaction is a sequence of multiple operations performed on a database, and all served as a single logical unit of work - taking place wholly or not at all. In other words, there’s never a case that _only half of the operations_ are performed and the results saved.

When a database transaction is in flight, the database state may be temporarily inconsistent, but when the transaction is committed or ends, the changes are applied.

Let's suppose that a power outage occurs in the middle of a transaction, at that moment the transaction can be undone, so the database is reverted to its original state. The term _rollback_ is used to refer to the process of undoing the changes made by the transaction. The term _commit_ refers to permanent changes made by the transaction.

Database transactions are very necessary because system failures are inevitable and cannot be predicted. So transactions can provide a way to ensure that data is consistent. Another reason is that many concurrent requests can simultaneously change information, so transactions must isolate requests from each other to avoid conflicts.

During its lifecycle, a database transaction goes through multiple states. These states are called **transaction states** and are typically one of the following:

1. **Active states:** It is the first state during the execution of a transaction. A transaction is _active_ as long as its instructions (read or write operations) are performed.
2. **Partially committed:** A change has been executed in this state, but the database has not yet committed the change on disk. In this state, data is stored in the memory buffer, and the buffer is not yet written to disk.
3. **Committed:** In this state, all the transaction updates are permanently stored in the database. Therefore, it is not possible to rollback the transaction after this point.
4. **Failed:** If a transaction fails or has been aborted in the active state or partially committed state, it enters into a _failed_ state.
5. **Terminated state:** This is the last and final transaction state after a committed or aborted state. This marks the end of the database transaction life cycle.


_References:_

https://fauna.com/blog/database-transaction