|       Row based               |    Column based          |
|-------------------------------|--------------------------|
| Optimal for read and writes   | Writes are slowe         |
| Good for transactions         |  Worse at transactions   |
| Compression isn't efficient   | Great at Compression     |
| Aggregation isn't efficient   | Great at Aggregation     |
| Efficient queries with multi columns  | NOT Efficient queries with multi columns |


In Summary, Row-based databases are best suied in commun CRUD applications. 
On the other hand, Column-based databases are optimal for applications where data  do not change oftenm like warehouses managments systems, and a lot of analitical operations are applied on it.
