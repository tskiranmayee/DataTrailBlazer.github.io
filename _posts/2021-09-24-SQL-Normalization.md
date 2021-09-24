---
layout: post
title: Description of normalization
---

**Normalization:** 
* The process of organizing data in a database.
* Creating tables and establishing relationships between those tables according to rules designed both to protect the data 
* Make the database more flexible by **eliminating redundancy and inconsistent dependency**.
* **Redundant data** -> wastes disk space and creates maintenance problems.
* **Problem of redundancy :** If data that exists in more than one place must be changed, the data must be changed in exactly the same way in all locations.
* **Inconsistency Dependancy:** can make data difficult to access because the path to find the data may be missing or broken.

#### Rules of Normalization
##### 1NF
1. Eliminate repeating groups in individual tables.
2. Create a separate table for each set of related data.
3. Identify each set of related data with a primary key.
##### 2NF
1. Create separate tables for sets of values that apply to multiple records.
2. Relate these tables with a foreign key.
##### 3NF
1. Eliminate fields that do not depend on the key.

[Normazlization Example](https://docs.microsoft.com/en-us/office/troubleshoot/access/database-normalization-description)

