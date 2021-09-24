---
layout: post
title: Explore Core Data Concepts
---
## Part 1
* Identify how data is defined and stored
* Identify characteristics of relational and non-relational data
* Describe and differentiate data workloads
* Describe and differentiate batch and streaming data

### What is data?
Data is a collection of facts such as numbers, descriptions, and observations used in decision making. 
#### Classification of data :
* Structured,
* Semi-structured, or
* Unstructured.

### Structured data
1. **Tabular** data that is represented by **rows and columns** in a database.
2. Databases that hold tables in this form are called **relational databases** (the mathematical term relation refers to an organized set of data held as a table). 
**Note**: Each row in a table has the same set of columns.
![Relational Tables](https://raw.githubusercontent.com/TrailBlazed/trailblazed.github.io/gh-pages/assets/11-tabular-diagram.png)

### Semi-structured data
##### JSON
* It is information that doesn't reside in a relational database but still has some structure to it.
 **Example:** JavaScript Object Notation (JSON)
![JSON](https://raw.githubusercontent.com/TrailBlazed/trailblazed.github.io/gh-pages/assets/12-json.PNG = 200px) 
##### Key-Value Pair: 
* A key-value database stores Associative arrays. 
* A key-value database stores data as a single collection without structure or relation.
### Unstructured data
##### Graph Database
* A graph contains nodes (information about objects), and edges (information about the relationships between objects). 

### Data defined, stored, and accessed in cloud computing
* Structured Data -> Relational Database such as SQL server or Azure SQL Database
* Unstructured Data ->Azure Blob Storage (Blob - Binary Large Object)
* Semi-strucutred Data->Azure CosmosDB
#### Levels of Access
* Read-Only
* Read/Write
* Owner - Full Privilege
#### Scenario
* Data Analyst/Data Engineer ->Owner 
* Sales people -> Read-Only
### Data Processing Solutions
##### Transactional System (OLTP - Online Transactional Processing)
* It records Transactions ( small,discrete unit of work)
*  Splitting tables out into separate groups of columns like this is called **normalization**
*  Advantage: Normalization can enable a transactional system to cache much of the information required to perform transactions in memory, and speed throughput.
* Disadvantage:  normalized tables will frequently need to join the data held across several tables back together again. This can make it difficult for business users(Analysis) who might need to examine the data.
##### Analytical System
* Capturing raw data, and using it to generate insights for decision-making.
###### Tasks:
**Data ingestion**: the process of capturing the raw data. The repository could be a file store, a document database, or even a relational database. <br>
**Data transformation**: Filter out anomolies, required tranformation like date or address etc., perform aggregation like,sum and other KPIs(Key Performance Indicators) <br>
**Data querying:** Query to analyse the data. <br>
**Data visualization:**
* Visualizing the data can often be useful as a tool for examining data.
* Charts such as bar charts, line charts, plot results on geographical maps, pie charts, or illustrate how data changes over time.
* Microsoft Power BI - rich graphical representation of data.
### Identify types of data and data storage
#### The characteristics of relational and non-relational data
