# Atomacity
All the queries of a transaction should succeed. Otherwise the database rollback to the state before the transaction even begin.

# Isolation

![telegram-cloud-photo-size-2-5301042847010644007-y](https://github.com/user-attachments/assets/0a827aa7-c390-4178-b536-20ebf1839d05)


![telegram-cloud-photo-size-2-5301042847010644015-y](https://github.com/user-attachments/assets/5fb20526-cded-4884-be13-eaa9766f55c9)

![telegram-cloud-photo-size-2-5301042847010644024-y](https://github.com/user-attachments/assets/398583c5-c698-4694-ad44-907461c3c902)

In Postgres `Repeatable Reads` are actually `Snapshots`. This is why we don't get phantom reads in that case

# Consistency

## Consistency in Data
- Logical consistencies. Defined by the user
- Keys Constraints
- Atomicity insure Consisency in Data
- Isolation insure Consisency in Data

## Consistency in Reads
- If a transaction commited a change, will a new transaction see the change ?
- Affects the system as a whole, even if we have master and slaves databases
- Relational and NoSQL Databases suffers of it both (horizental scaling)m and add caching
- Eventual Consistency

# Durability
 Changes made by committed transactions must be persistedin a durable non-volatile storage.

 ## Durability Techniques
 - WAL - Write ahead log (compressed versionnig). Used in Postgres
 - Asynchronous Snapshots: In the background snapshot everything at once
 - AOF: Append Only Files

## Durability OS Cache
 A Write request usually goes to the OS cache. If the OS crache when writtting to the cache, the data could be lost. This is why DBMS uses the `Fsync commend` to persist directy on disk. Fsync can be expensive and slows down commits
