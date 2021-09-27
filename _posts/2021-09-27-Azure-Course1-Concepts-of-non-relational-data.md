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
* Store massive amounts of unstructured data, or blobs, in the cloud.
* Create blobs using an Azure storage account.
* **Block blobs** -> 1. A block blob is handled as a set of blocks(100MB)
                2. 50000 blocks 
                3. Max of 4.7TB.
                4. Smallest amount of data that can be read or written as an individual unit.
                5. Best used to store discrete, large, binary objects that change infrequently.
 * **Page blobs** -> 1. collection of fixed size 512-byte pages.
                     2. support random read and write operations
                     3. hold up to 8 TB of data.
                     4. implement virtual disk storage for virtual machines.
  * **Append blobs** -> 1. Support append operations.
                        2. Only add blocks to the end of an append blob; updating or deleting                                    existing blocks
                        3. Each block can vary in size, up to 4 MB.
                        4. The maximum size of an append blob is just over 195 GB.
                        
 *  Azure storage account -> create blobs -> _containers_.
 *  A container provides a convenient way of grouping related blobs together, and you can organize blobs in a hierarchy of folders, similar to files in a file system on disk.
 *  Control ->read /write blobs inside containers.
 *  3 access tiers:
      * **Hot tier** -> 1. default
                         2. frequently accesses
                         3. high-performance media.
      * **Cool tier** ->1. lower performance
                         2. accessed infrequently.
                         3. create the blob in the Hot tier, but migrate it to the Cool tier later and vice-versa.
     * **Archive tier** ->1. lowest storage cost, but with increased latency.
                          2. can take hours for the data to become available.
                          3. Rehydrated

* A lifecycle management policy can automatically move a blob from Hot to Cool, and then to the Archive tier, can also arrange to delete outdated blobs.


##### Use Case and Management
* static website
* Storing files for distributed access
* Streaming video and audio
* Storing data for backup and restore, disaster recovery, and archiving
* Storing data for analysis by an on-premises or Azure-hosted service

##### Azure Blob storage include:

* **Versioning**. You can maintain and restore earlier versions of a blob.

* **Soft delete** This feature enables you to recover a blob that has been removed or overwritten, by accident or otherwise.

* **Snapshots** A snapshot is a read-only version of a blob at a particular point in time.

* **Change Feed** The change feed for a blob provides an ordered, read-only, record of the updates made to a blob. You can use the change feed to monitor these changes, and perform operations such as:

    * Update a secondary index, synchronize with a cache, search-engine, or any other content-management scenarios.
    * Extract business analytics insights and metrics, based on changes that occur to your objects, either in a streaming manner or batched mode.
    * Store, audit, and analyze changes to your objects, over any period of time, for security, compliance or intelligence for enterprise data management.
    * Build solutions to back up, mirror, or replicate object state in your account for disaster management or compliance.
    * Build connected application pipelines that react to change events or schedule executions based on created or changed objects.

