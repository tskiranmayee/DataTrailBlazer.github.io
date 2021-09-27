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
### Azure File Storage
*  Azure File Storage enables you to create files shares in the cloud, and access these file shares from anywhere with an internet connection. 
*  Azure File Storage exposes file shares using the **Server Message Block 3.0 (SMB)** protocol.
*  Control access to shares in Azure File Storage using authentication and authorization services available through Azure Active Directory Domain Services.
* Share up to 100 TB of data in a single storage account.
* Data can be distributed across any number of file shares in the account.
* Maximum size of a single file is 1 TB.
* Supports up to 2000 concurrent connections per shared file.
* Upload files to Azure File Storage using 1) the Azure portal 2) tools such as the AzCopy utility .
* Azure File Sync service to synchronize locally cached copies of shared files with the data in Azure File Storage.
* Two performance tiers:
       1) **Standard** tier uses hard disk-based hardware in a datacenter, and the Premium tier uses solid-state disks.
       2) **Premium** tier offers greater throughput, but is charged at a higher rate.

#### Use cases and management benefits of using Azure File Storage
* Migrate existing applications to the cloud.
* Share server data across on-premises and cloud.
* Integrate modern applications with Azure File Storage.
* Simplify hosting High Availability (HA) workload data.

### Important Points
* Don't use Azure File Storage for files that can be written by multiple concurrent processes simultaneously. Multiple writers require careful synchronization, otherwise the changes made by one process can be overwritten by another. 
* The alternative solution is to lock the file as it is written, and then release the lock when the write operation is complete. However, this approach can severely impact concurrency and limit performance.

* A fully managed service.
* Shared data is replicated locally within a region, but can also be geo-replicated to a second region.
* 300 MB/second of throughput for a single Standard file share, but you can increase throughput capacity by creating a Premium file share, for additional cost.
* All data is encrypted at rest.
* Can enable encryption for data in-transit between Azure File Storage and your applications.
### Azure Cosmos DB
* NOSQL -> documents, graphs, key-value stores, and column family stores.
* Azure Cosmos DB is a multi-model NoSQL database management system. Cosmos DB manages data as a partitioned set of documents. A document is a collection of fields, identified by a key. The fields in each document can vary, and a field can contain child documents.
* Many document databases use JSON (JavaScript Object Notation) to represent the document structure.
* A document can hold up to 2 MB of data, including small binary objects. 
* If you need to store larger blobs as part of a document, use Azure Blob storage, and add a reference to the blob in the document.
* Cosmos DB provides APIs(Application Programming Interface) to access these documents using a set of well-known interfaces.
  1. SQL API. ->realtional DB
  2. Table API.  -> key-value pair
  3. MongoDB API. -> document database
  4. Cassandra API. -> column family database management system. 
  5. Gremlin API. -> graph database

* CosmosDB database -> The documents in a container are grouped together into partitions. 
* A set of documents that share a common partition key.
* Helps to reduce the amount of I/O (disk reads) that queries might need to perform when retrieving a set of documents for a given entity.

### Use cases and management benefits
* Highly scalable DBMS
* Automatically allocates space in a container for your partitions, and each partition can grow up to 10 GB in size.
* Indexes are created and maintained automatically. 
* Virtually no administrative overhead
* To ensure availability, all databases are replicated within a single region.
* Replication is transparent, and failover from a failed replica is automatic.
* Guarantees 99.99% high availability.
* Replicate anywhere in the world (additional cost).
* All replicas are synchronized.
* Types of Consistency:
    * Strong -> Linearizability refers to serving requests concurrently.
    * Bounded staleness-> The reads are guaranteed to honor the consistent-prefix guarantee.
        The "staleness" can be configured in two ways:
          * The number of versions (K) of the item
          * The time interval (T) reads might lag behind the writes
    * Session -> a single client session reads are guaranteed to honor the consistent-prefix, monotonic reads, monotonic writes, read-your-writes, and write-follows-reads guarantees.
    * consistent prefix -> 
    *  and eventual.
