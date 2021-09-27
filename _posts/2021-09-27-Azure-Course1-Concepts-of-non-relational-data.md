---
layout: post
title: Describe concepts of non-relational data
---
#### Introduction
* Video, audio, images, temporal information, large volumes of free text, encrypted information etc.

##### Azure Table storage
*  NoSQL key-value model ->Semi-structure data
*  The data for an item is stored as a set of fields, and the item is identified by a unique key.
*  Items are referred to as **rows**, and fields are known as **columns**.
*  No concept of relationships, stored procedures, secondary indexes, or foreign keys. 
*  Denormalized, with each row holding the entire data for a logical entity. 
*  Faster access -> NO Joins
*  Partitioning is a mechanism for grouping related rows, based on a common property -> _partition key_.
*  Partition Advantage -> 1. improve scalability and performance.
                          2. Grow and Shrink
                          3. Improves performance on search ->  reducing the amount of I/O (reads and writes) needed to locate the data.
*  2 elements : 1) the partition key that identifies the partition containing the row
                2) a row key that is unique to each row in the same partition.

* **Point queries** that identify a single row, and Range queries that fetch a contiguous block of rows in a partition.
* The partition key and row key effectively define a clustered index over the data.
* The columns in a table can hold numeric, string, or binary data up to 64 KB in size. A table can have up to 252 columns, apart from the partition and row keys. The maximum row size is 1 MB.
##### Advantages
* It's simpler to scale.An Azure storage account can hold up to 5 PB of data.
* Holds semi-structured data
* No need to map and maintain the complex relationships(no normalization).
* Row insertion is fast
* Data retrieval is fast(the partition and row keys pair for queries).

##### Disadvantages:
* Consistency aren't guaranteed
* No referential integrity
* Difficult to filter and sort on non-key data.

##### Excellent for:
* Storing TBs of structured data capable of serving web scale applications.
* Storing datasets that don't require complex joins, foreign keys, or stored procedures, and that can be denormalized for fast access. 
* Capturing event logging and performance monitoring data.
* Provides high-availability guarantees in a single region.
* Each table is replicated three times within an Azure region.
* Create tables in geo-redundant storage -> additional costs.
* Azure will transparently switch to a working replica while the failed replica is recovered.
* Helps to protect your data(configure security and role-based access control)

##### Azure Blob storage

