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
  <tr><th align="center">Statement</th><th align="center">Description</th></tr><th align="center">Applied</th></tr>
  <tr>SELECT<td></td><td>Select/Read rows from a table</td><td>By Default, Every Row at a time</td></tr>
   <tr>INSERT<td></td><td>Insert new rows into a table</td><td>One Row at a time</td></tr>
   <tr>UPDATE<td></td><td>Edit/Update existing rows</td><td>By Default, Every Row at a time</td></tr>
   <tr>DELETE<td></td><td>Delete existing rows in a table</td><td>By Default, Every Row at a time</td></tr>
  </table>
   * Data Definition Language (DDL)
   
