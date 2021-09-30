---
layout : post
title:  Explore modern data warehouse analytics in Azure
---

## Common Practices For Data Loading

* In a big data system, data ingestion has to be fast enough to capture the large quantities of data that may be heading your way, 
and have enough compute power to process this data in a timely manner.
*  More popular tools used with Azure:
  * Azure Data Factory
  * PolyBase
  * SQL Server Integration Services
  * Azure Databricks.

### 1.Azure Data Factory
* **Azure Data Factory** is a data ingestion and transformation service that allows you to load raw data from many different sources, both on-premises and in the cloud. 
* Clean, transform, and restructure the data, before loading it into a repository such as a data warehouse.
* Contains a series of interconnected systems that provide a complete end-to-end platform for data engineers.
* Can load static data, but you can also ingest streaming data.
* Data Factory provides an **orchestration** engine.
* **Orchestration** is the process of directing and controlling other services, and connecting them together, to allow data to flow between them. 
* Azure Data Factory uses a number of different resources: **linked services, datasets, and pipelines**.
*  Used to ingest data into Azure Synapse Analytics

#### Linked Services
* Data Factory moves data from a data source to a destination. 
* A linked service provides the information needed for Data Factory to connect to a source or destination. 

#### Datasets
* A dataset in Azure Data Factory represents the data that you want to ingest (input) or store (output).
* A dataset connects to an input or an output using a linked service.

#### Pipelines
* A pipeline is a logical grouping of activities that together perform a task. 
* The activities in a pipeline define actions to perform on your data.
* Use a **copy activity** to transform data from a source dataset to a destination dataset. 
* **Azure Function** activity to run an Azure Function to modify and filter data.
* **Azure Databricks Notebook** activity to run a notebook that performs more advanced processing.
* **Pipelines** don't have to be linear. 
* logic activities that repeatedly perform a series of tasks while some condition is true using a **ForEach activity**.
* Follow different processing paths depending on the outcome of previous processing using an **If Condition activity**.
* You can run a pipeline manually, or you can arrange for it to be run later using a trigger.
* A **trigger** enables you to schedule a pipeline to occur according to a planned schedule.

### 2. PolyBase
* PolyBase is a feature of SQL Server and Azure Synapse Analytics that enables you to run Transact-SQL queries that read data from external data sources. 
* PolyBase, you can read data managed by Hadoop, Spark, and Azure Blob Storage, as well as other database management systems such as Cosmos DB, Oracle, Teradata, and MongoDB.
* Spark is a parallel-processing engine that supports large-scale analytics.
* Run queries that join tables in a SQL database with external data, enabling you to perform analytics that span multiple data stores.
* Azure SQL Database does not support PolyBase.

### 3. SQL Server Integration Services
* Building enterprise-level data integration and data transformations solutions. 
* SSIS is part of Microsoft SQL Server.
* SSIS can extract and transform data ->  XML data files, flat files, and relational data sources, and then load the data into one or more destinations
* A rich set of built-in tasks and transformations, graphical tools for building packages, and the Integration Services Catalog database, where you store, run, and manage packages.
* SSIS is an on-premises utility. 
* Azure Data factory allows you to run your existing SSIS packages as part of a pipeline in the cloud ->started quickly without rewrite your existing transformation logic.

### 4. Azure Databricks
* Databricks is based on Spark, and is integrated with Azure to streamline workflows.
* Databricks can process data held in many different types of storage, including Azure Blob storage, Azure Data Lake Store, Hadoop storage, flat files, SQL databases, and data warehouses, and Azure services such as Cosmos DB.
* write and run Spark code using notebooks.
* A notebook is like a program that contains a series of steps (called cells). A notebook can contain cells that read data from one or more data sources, process the data, and write the results out to a data store. 
* The scalability of Azure Databricks makes it an ideal platform for performing complex data ingestion and analytics tasks.
* Azure Data Factory can incorporate Azure Databricks notebooks into a pipeline.

### 5. Azure Synapse Analytics
* [Vedio Description](https://docs.microsoft.com/en-us/learn/modules/explore-data-ingestion-azure/3-load-data)

## Data storage and processing in Azure

### Azure Synapse Analytics

*  Azure Synapse Analytics is to extract the data from where it's currently stored, **load** this data into an **analytical data store**, and then **transform** the data, shaping it for analysis. This approach is known as ELT, for extract, load, and transform.
* Using **Apache Spark, and automated pipelines** -> it run parallel processing tasks across massive datasets, and perform _big data_ analytics.
* _Big data_ refers to data that is too large or complex for traditional database systems. Systems that process big data have to perform rapid data ingestion and processing; they must have capacity to store the results, and sufficient compute power to perform analytics over these results.
* Analyze operational data in its original location -> **hybrid transactional analytical processing (HTAP)** ->Perform analysis over data held in repositories such as Azure Cosmos DB using Azure Synapse Link.
* **Processing data in Azure:**
  * Azure Databricks
  * Azure Data Factory
  * Azure Synapse Analytics
  * Azure Data Lake. 
* Azure Synapse Analytics is a **generalized analytics service** ->read data from many sources, process this data, generate various analyses and models, and save the results.
* **Two technologies to process data:**
 * T-SQl
 * Spark

### Azure Databricks
* A **driver** is a piece of code that connects to a specific data source and enables you to read and write that source. 
* A driver -> part of a library that you can load into the Databricks environment. 
* Drivers are available -> Azure SQL Database, Azure Cosmos DB, Azure Blob storage, and Azure Data Lake storage, third-parties (such as MySQL and PostgreSQL).
* Processing engine is provided by Apache Spark.
* Spark is a parallel-processing engine that supports large-scale analytics.
* Spark application code in Python, R, Scala, Java, and SQL.
* Libraries include modules for machine learning, statistical analysis, linear and non-linear modeling, predictive analytics, and graphics.
* Databricks applications using a **Notebook** -> steps called **cells**
* In-memory model to a repository. The first line in the cell is %language. For example, %scala.
![Databricks](https://raw.githubusercontent.com/TrailBlazed/trailblazed.github.io/gh-pages/assets/2-databricks.png)

### Azure HDInsight
* Managed analytics service in the cloud.
* Apache Hadoop, a collection of open-source tools and utilities that enable you to run processing tasks over large amounts of data. 
* HDInsight uses a clustered model, similar to that of Synapse Analytics.
* Hadoop Map/Reduce uses a simple framework to split a task over a large dataset into a series of smaller tasks over subsets of the data that can be run in parallel, and the results then combined.
* **Apache Hive** provides interactive SQL-like facilities for querying, aggregating, and summarizing data.
* **Apache Kafka** is a clustered streaming service that can ingest data in real time. 
* **Apache Storm** is a scalable, fault tolerant platform for running real-time data processing applications. Streaming data.
![HDInSight](https://raw.githubusercontent.com/TrailBlazed/trailblazed.github.io/gh-pages/assets/2-hdinsight.png)

* 

 
