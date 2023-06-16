What is Snowflake ?
=======================

- Cloud Native (AWS/Azure/GCP)
- Data Platform
- SaaS
  
  So, `Snowflake is cloud native data platform offered as a service`

  The idea behind calling `Snowflake a data platform` instead of strictly a data warehouse, 
  as is quite commonly said, 
  is to point out that `Snowflake has features and capabilities beyong what you'd expect from a traditional warehouse`.

  E.g. - It has support for additional workloads such as data science and features such as native processing 
        of semi-structured data like you'd find in a data lake.

    Let's run through six key workloads Snowflake support.

Data Platform
-----------------
 - Data Warehouse
   - Structured and relational Data
   - ANSI Standard SQL
   - ACID compliant transactions
   - Data stored in databases, sechemas, tables

 - Data Lake
   - scalable storage and compute
   - Schema does not need to be defined upfonrt
   - Native processing of semi-structured data formats
  
 - Data Engineering
   - COPY INTO and Snowpipe (Batch and Streaming)
   - Separata compute clusters
   - Tasks and Streams
   - All data encrypted ans rest in transit
  
 - Data Science
   - Remove data management roadblocks with centralised storage
   - Partner eco-system includes data science tooling
     - SageMaker
     - DataRobot
     - Dataiku
 
 - Data Sharing
   - Secure Data sharing
   - DataMarketplace
   - DataExchange
   - BI with Snowflake partner ecosystem tools
 
 - Data Applications
   - Connectors and Drivers
   - UDFs and Stored Procedures
   - External UDFs (Azure Functions / AWS Lambdas)
   - Preview features such as Snowflake

Cloud-Native
-------------
 - Snowflake's software is purpose build for the cloud(not retrofitted from an existing technology like Hadoop/MSSQL)
   - Snowflake is designed to run on cloud, query engine, storage file format, the metadata store.
   - Architecture was desgined with cloud infrastructure in mind.
   - It is not a cloud-wash solution(older technology plugged into cloud)
 - All Snowflake infrastructure runs on the Cloud in either AWS,GCP or Azure
 - Snowflake makes use of Cloud's elasticity, scalability, high availability, cost efficiency and durability

Software as a Service (SaaS)
------------------------------
   *  Hosted service in the cloud can be provided to the user in various delivery models.
   *  Have virtual machines hosted remotely, which are accessed and managed by user like EC2 instance in AWS
  
 - `Its a pure SAAS product.` Snowflake is slighly different from that.
   - As users there is no management of our current infrastructure at all, so no SSHing into instances or checking data files once loaded into snowflake tables.
   - Limited management of software with the real thing to configure being snowflake connectors like SnowSQL command line tool
  
 - `Tranparent updates and patches`, as user dont have to perform all those, and there are no visible downtimes.

 - Snowflake is `flexible pay as you use subscription model`.
   - Pay only for the resources that are needed and its therefore generally cheaper and large upfront capital expenditure costs required to setup your own hardware and software.
 
 - `Ease of access`. 
   - No need to setup any software for it.
   - Interact with snowflake user and password authentication.
   - Optionaly can be extended with connectors and drivers for programmatic access.
 
 - `Automattic optimiztion`
   - Optimizations like partitioning of data are done automatically so there's no longer need to specify things like static partitioning, keys, or indexes.
   - These optimization activities are done automatically as part of the loading process.

