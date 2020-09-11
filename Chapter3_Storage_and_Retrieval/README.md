# Chapter3 Storage and Retrieval

## concept of `OnLine Transactional Processing` and `OffLine Analytics Processing` (or Data Warehouse)
- OLTP is real time production system, it is expected to be highly available, low latency and etc. Typical use case is read, write and bye.
- OLAP is for internal analytics use, it usually tries to retrieve large amounts of data, it is not expected to be as fast as OLTP. 

These 2 different use cases and requirements eventually lead to different types of databases. And OLAP takes up the form of Data Warehouse.

## Columnized Data
### argument for use case 
Rarely do ppl need all columns of a row (in a relational database) in single query, how do we store data more efficiently then?

**Instead of** storing columns of the same `row` together, store all values from the same `column` together.

### benefit on `read`
1) smaller data (which can be made even ever smaller with compression omg..) fits better in the RAM.
2) vectorized processing can be easily applied.

### downside on `write`
writes first go somewhere in the memory, after enough writes have been accumulated, they will be merged with the column files on disk in bulk.

### cached materialized view
a copy of the results of some query (in relatinal database term)

