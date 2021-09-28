---
layout : post
title: Query relational data in Azure
---

### Introduction to SQL
* SQL -> Structured Query Language
* Used to communicate with a relational database
* update data in a database, or retrieve data from a database
* SQL include Microsoft SQL Server, MySQL, PostgreSQL, MariaDB, and Oracle.
* SELECT, INSERT, UPDATE, DELETE, CREATE, and DROP
* Security management and programmability
* Microsoft SQL Server -> uses Transact-SQL -> writing stored procedures and triggers and managing user accounts
* Popular dialects of SQL include:
  * Transact-SQL (T-SQL) -> Microsoft SQL Server and Azure SQL Database.
  * pgSQL -> PostgreSQL.
  * PL/SQL  -> Oracle -> Procedural Language/SQL.

### SQL statement types
  * SQL statements are grouped into two main logical groups, and they are:
   * Data Manipulation Language (DML)
   
  <table align="center">
  <tr><th align="center">Statement</th><th align="center">Description</th><th align="center">Applied</th></tr>
  <tr>SELECT<td></td><td>Select/Read rows from a table</td><td>By Default, Every Row at a time</td></tr>
   <tr>INSERT<td></td><td>Insert new rows into a table</td><td>One Row at a time</td></tr>
   <tr>UPDATE<td></td><td>Edit/Update existing rows</td><td>By Default, Every Row at a time</td></tr>
   <tr>DELETE<td></td><td>Delete existing rows in a table</td><td>By Default, Every Row at a time</td></tr>
 <tr>DROP<td></td><td>all the rows in that table are lost.</td><td>By Default, Every Row at a time</td></tr>
  </table>
  
  #### Data Types :
  1) INT 2) VARCHAR 3) NOT NULL
 
   * Data Definition Language (DDL)

#### Retrieve connection information for Azure SQL Database
Tools to query data held in Azure SQL Database:
* The query editor in the Azure portal
* The sqlcmd utility from the command line or the Azure Cloud Shell
* SQL Server Management Studio
* Azure Data Studio
* SQL Server Data Tools

[Find the details about using the tools](https://docs.microsoft.com/en-us/learn/modules/query-relational-data/3-sql-database)

### Retrieve connection information for Azure Database for PostgreSQL

* **psql** psql utility is available in the Azure Cloud Shell -> to query a database

### ### Retrieve connection information for Azure Database for MySql
* Use MySql Benchmark.
   
