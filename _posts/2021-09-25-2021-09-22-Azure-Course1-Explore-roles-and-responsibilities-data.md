---
layout: post
title: Explore job roles in the world of data
---

## 3 Key Roles


* **Database Administrators** manage databases, assigning permissions to users, storing backup copies of data 
and restore data in case of any failures.
* **Data Engineers** are vital in working with data, applying data cleaning routines, identifying business rules,
and turning data into useful information.
* **Data Analysts** explore and analyze data to create visualizations and charts to enable organizations 
to make informed decisions

#### Azure Database Administrator
* The **design, implementation, maintenance, and operational aspects** of on-premises and cloud-based database solutions
* Overall **availability and consistent performance and optimizations** of the database solutions.
* work with stakeholders to implement policies, tools, and processes for **backup and recovery plans** to recover following a natural disaster or human-made error.
* Managing the **security** od data, **granting privileges** over the data, **granting or denying access** to users as appropriate.

##### Tasks and Responsibilties
* **Installing and upgrading** the database server and application tools.
* Allocating **system storage and planning storage** requirements for the database system.
* **Modifying the database structure**, as necessary, from information given by application developers.
* **Enrolling users and maintaining system security**.
* Ensuring **compliance with database vendor license agreement**.
* **Controlling and monitoring user** access to the database.
* **Monitoring and optimizing the performance** of the database.
* Planning for **backup and recovery of database** information.
* Maintaining **archived** data.
* **Backing up and restoring** databases.
* **Contacting database vendor** for technical support.
* Generating **various reports by querying** from database as per need.
* Managing and monitoring **data replication**.

##### Tools
###### Azure Data Studio
* Graphical user interface for managing many different database systems.
* Connection ->SQL Server databases, Azure SQL Database, PostgreSQL, Azure SQL Data Warehouse, and SQL Server Big Data Clusters
* Extensible tool -> 1. Download and install extensions from third-party developers that connect to other systems
                     2. Provide wizards that help to automate many administrative tasks.
###### SQL Server Management Studio
* A graphical interface, enabling you to query data, perform general database administration tasks, and generate scripts for automating database maintenance and support operations.
* Generate Transact-SQL scripts -> DBA the ability to schedule and automate many common tasks.
* **Transact-SQL** is a set of programming extensions from Microsoft that adds several features to the Structured Query Language (SQL), 
   including transaction control, exception and error handling, row processing, and declared variables.

###### Azure Portal
* Database services in Azure.
* SQL Server on cloud
* Configuration tasks -> Increasing the database size, creating a new database, and deleting an existing database 


#### Azure Data Engineer
* **Design and implement** data-related assets that include data ingestion pipelines, cleansing and transformation activities, and data stores for analytical workloads.
* **Data platform technologies** - relational and nonrelational databases, file stores, and data streams.
* Ensuring **privacy of data** 
* **Management and monitoring** of data stores and data pipelines to ensure that data loads perform as expected.

##### Tasks and Responsibilties

* Developing, constructing, testing, and maintaining databases and data structures.
* Aligning the data architecture with business requirements.
* Data acquisition.
* Developing processes for creating and retrieving information from data sets.
* Using programming languages and tools to examine the data.
* Identifying ways to improve data reliability, efficiency, and quality.
* Conducting research for industry and business questions.
* Deploying sophisticated analytics programs, machine learning, and statistical methods.
* Preparing data for predictive and prescriptive modeling.
* Using data to discover tasks that can be automated.

##### Tools
* A relational database management system -> SQL
* SQL to create databases, tables, indexes, views, and the other objects required by the database.
* SQL Server Management Studio -> create and query tables visually, but you can also create your own SQL scripts manually.
* **sqlcmd utility** (Command Line) to connect to Microsoft SQL Server and Azure SQL Database, and run ad-hoc queries and commands.
* SQL server professional -> data manipulation tool might be Transact-SQL.
* Azure Databricks -> a data analytics platform optimized for the Microsoft Azure cloud services platform. Azure Databricks offers three environments for developing data intensive applications: Databricks SQL, Databricks Data Science & Engineering, and Databricks Machine Learning.
* Azure HDInsight to generate and test predictive models. 
  * Azure HDInsight is a cloud distribution of Hadoop components. Azure HDInsight makes it easy, fast, and cost-effective to process massive amounts of data. You can use the most popular open-source frameworks such as Hadoop, Spark, Hive, LLAP, Kafka, Storm, R, and more. With these frameworks, you can enable a broad range of scenarios such as extract, transform, and load (ETL),
    data warehousing, machine learning, and IoT.
* **Azure Data Factory**  is a managed cloud service that's built for these complex hybrid extract-transform-load (ETL), extract-load-transform (ELT), and data integration projects.
  * It is the cloud-based ETL and data integration service that allows you to create data-driven workflows for orchestrating data movement and transforming data at scale.
  *  Create and schedule data-driven workflows (called pipelines) that can ingest data from disparate data stores. 
  *  Build complex ETL processes that transform data visually with data flows or by using compute services such as Azure HDInsight Hadoop, Azure Databricks, and Azure SQL Database.
  *  Publish your transformed data to data stores such as **Azure Synapse Analytics** for business intelligence (BI) applications to consume. 
  *  Raw data can be organized into meaningful data stores and data lakes for better business decisions.
  *  **How does it work?**
    * Data Factory contains a series of interconnected systems that provide a complete end-to-end platform for data engineers.
    * **Connect and collect** -> 1. The first step in building an information production system is to connect to all the required sources of data and processing, such as software-as-a-service (SaaS) services, databases, file shares, and FTP web services.
                                 2. To move the data as needed to a centralized location for subsequent processing.
                                 3. Use the **Copy Activity** in a data pipeline to move data from both on-premises and cloud source data stores to a centralization data store in the cloud for further analysis.
                                 4. Collect data in **Azure Data Lake Storage** and transform the data later by using an Azure Data Lake Analytics compute service. 
                                 5. Collect data in Azure Blob storage and transform it later by using an Azure HDInsight Hadoop cluster.
    * **Transform and enrich** -> 1. Data is present in a centralized data store in the cloud, process or transform the collected data by using ADF mapping data flows. 
                                  2. Data flows enable data engineers to build and maintain data transformation graphs that execute on Spark without needing to understand Spark clusters or Spark programming.
                                  3. ADF supports external activities for executing your transformations on compute services such as HDInsight Hadoop, Spark, Data Lake Analytics, and Machine Learning.
    * **CI/CD and publish** -> 1. Data pipelines using Azure DevOps and GitHub, allowing you to incrementally develop and deliver your ETL processes before publishing the finished product.
                               2. After the raw data has been refined into a business-ready consumable form, load the data into Azure Data Warehouse, Azure SQL Database, Azure CosmosDB, or whichever analytics engine your business users can point to from their business intelligence tools.
    * **Monitor** -> Azure Data Factory has built-in support for pipeline monitoring via Azure Monitor, API, PowerShell, Azure Monitor logs, and health panels on the Azure portal.
* **Top-level concepts**
  * **Pipelines** -> A pipeline is a logical grouping of activities that performs a unit of work. Together, the activities in a pipeline perform a task.
  * **Data Flows** -> Create and manage graphs of data transformation logic that you can use to transform any-sized data. You can build-up a reusable library of data transformation routines and execute those processes in a scaled-out manner from your ADF pipelines. Data Factory will execute your logic on a Spark cluster that spins-up and spins-down when you need it. 
  * **Activities** -> Activities represent a processing step in a pipeline. Data Factory supports three types of activities: data movement activities, data transformation activities, and control activities.
  * **Datasets** -> Datasets represent data structures within the data stores, which simply point to or reference the data you want to use in your activities as inputs or outputs.
  * **Linked services** -> Connection strings, which define the connection information that's needed for Data Factory to connect to external resources. 
  * **Linked services are used for two purposes in Data Factory**:
        * A **data store** that includes, a SQL Server database, Oracle database, file share, or Azure blob storage account. For a list of supported data stores, see the copy activity article.
        * A **compute resource** that can host the execution of an activity. For example, the HDInsight, Hive activity runs on an HDInsight Hadoop cluster. 
        * For a list of transformation activities and supported compute environments, see the transform data article.
  
  * **Integration Runtimes** -> An activity defines the action to be performed. A linked service defines a target data store or a compute service. An integration runtime provides the bridge between the activity and linked Services.
  


*  The non-relational field -> Azure Cosmos DB. 
*  To manipulate and query the Cosmos DB data -> HiveQL, R, or Python.



#### Data Analyst
* **Maximize the value** of their data assets.
* **Designing and building scalable models, cleaning and transforming data, 
and enabling advanced analytics** capabilities through reports and visualizations.

###### Tasks and Responsibilities
* Making large or complex data more accessible, understandable, and usable.
* Creating charts and graphs, histograms, geographical maps, and other visual models that help to explain the meaning of large volumes of data, and isolate areas of interest.
* Transforming, improving, and integrating data from many sources, depending on the business requirements.
* Combining the data result sets across multiple sources. For example, combining sales data and weather data provides a useful insight into how weather influenced sales of certain products such as ice creams.
* Finding hidden patterns using data.
* Delivering information in a useful and appealing way to users by creating rich graphical dashboards and reports.

###### Common data visualization tools
* Microsoft Office Apps such as **Microsoft Excel** for creating rich visual reports.
* **Microsoft Power BI**, a powerful visualization platform, to create rich, graphical dashboards and reports over data that can vary dynamically.
* Power BI is a collection of software services, apps, and connectors that work together to turn your unrelated sources of data into coherent, visually immersive, and interactive insights. 
* Your data might be held somewhere local such as an Excel spreadsheet, or in a collection of cloud-based and on-premises databases, or some other set of data sources. 
* Power BI -> lets you easily connect to your data sources, discover what's important in that data, and share your findings with others in the organization.

