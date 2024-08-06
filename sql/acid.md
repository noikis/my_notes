# Atomacity
All the queries of a transaction should succeed. Otherwise the database rollback to the state before the transaction even begin.

# Isolation

![telegram-cloud-photo-size-2-5301042847010644007-y](https://github.com/user-attachments/assets/0a827aa7-c390-4178-b536-20ebf1839d05)


![telegram-cloud-photo-size-2-5301042847010644015-y](https://github.com/user-attachments/assets/5fb20526-cded-4884-be13-eaa9766f55c9)

![telegram-cloud-photo-size-2-5301042847010644024-y](https://github.com/user-attachments/assets/398583c5-c698-4694-ad44-907461c3c902)

In Postgres `Repeatable Reads` are actually `Snapshots`. This is why we don't get phantom reads in that case
