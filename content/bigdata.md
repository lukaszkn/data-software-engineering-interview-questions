# Big Data Engineering
Big Data engineering concepts and tools.

* [What is Apache Spark?](#What-is-Apache-Spark)
* [What is Hadoop?](#What-is-Hadoop)
* [What are the limitations of MapReduce in Hadoop?](#What-are-the-limitations-of-MapReduce-in-Hadoop)
* [How does Hadoop compare to Spark?](#How-does-Hadoop-compare-to-Spark)
* [What are RDDs in Spark?](#What-are-RDDs-in-Spark)
* [What is Spark SQL?](#What-is-Spark-SQL)
* [What is Spark Streaming?](#What-is-Spark-Streaming)
* [What is GraphX in Spark?](#What-is-GraphX-in-Spark)
* [What is Apache Kafka?](#What-is-Apache-Kafka)
* [What is the difference between OLAP and OLTP?](#What-is-the-difference-between-OLAP-and-OLTP)
* [What is a data warehouse?](#What-is-a-data-warehouse)
* [What are the goals of a data warehouse?](#What-are-the-goals-of-a-data-warehouse)
* [What is the difference between a database and a data warehouse?](#What-is-the-difference-between-a-database-and-a-data-warehouse)
* [What is a data lake?](#What-is-a-data-lake)
* [How does a data lake differ from a data warehouse?](#How-does-a-data-lake-differ-from-a-data-warehouse)
* [What is a data mart?](#What-is-a-data-mart)
* [What is the difference between Kimball and Inmon data warehouse architectures?](#What-is-the-difference-between-Kimball-and-Inmon-data-warehouse-architectures)
* [What are the main data modeling approaches in data engineering?](#What-are-the-main-data-modeling-approaches-in-data-engineering)
* [What is anchor modeling?](#What-is-anchor-modeling)
* [What is Data Vault modeling?](#What-is-Data-Vault-modeling)
* [Why is data modeling important for a data warehouse?](#Why-is-data-modeling-important-for-a-data-warehouse)
* [What is a dataflow?](#What-is-a-dataflow)
* [What are SCDs?](#What-are-SCDs)
* [What is the difference between ETL and ELT?](#What-is-the-difference-between-ETL-and-ELT)
* [What do data engineers do?](#What-do-data-engineers-do)
* [What is Apache NiFi?](#What-is-Apache-NiFi)
* [What is a data lakehouse?](#What-is-a-data-lakehouse)
* [What are the five base functions of big data platforms?](#What-are-the-five-base-functions-of-big-data-platforms)
* [What is data governance?](#What-is-data-governance)
* [What are the V's of Big Data?](#What-are-the-V-s-of-Big-Data)
* [What is Amazon Athena?](#What-is-Amazon-Athena)
* [What is Amazon Redshift?](#What-is-Amazon-Redshift)
* [What is Amazon Aurora?](#What-is-Amazon-Aurora)
* [What is AWS Glue?](#What-is-AWS-Glue)
* [What are AWS Step Functions?](#What-are-AWS-Step-Functions)
* [What is Amazon EMR?](#What-is-Amazon-EMR)
* [What is Azure HDInsight?](#What-is-Azure-HDInsight)
* [What is ZooKeeper?](#What-is-ZooKeeper)
* [What is YARN in Hadoop?](#What-is-YARN-in-Hadoop)
* [What is HDFS?](#What-is-HDFS)
* [What is HBase?](#What-is-HBase)
* [What is Hue?](#What-is-Hue)
* [What is Apache Hive?](#What-is-Apache-Hive)
* [What is Impala?](#What-is-Impala)
* [What is Oozie?](#What-is-Oozie)
* [What are Solr and Sqoop?](#What-are-Solr-and-Sqoop)
* [What is Apache Kudu?](#What-is-Apache-Kudu)
* [What is the difference between normalized and dimensional data storage?](#What-is-the-difference-between-normalized-and-dimensional-data-storage)
* [What is the difference between star and snowflake schemas?](#What-is-the-difference-between-star-and-snowflake-schemas)
* [Describe the architecture of HDFS.](#Describe-the-architecture-of-HDFS)
* [What is a DataFrame in Spark?](#What-is-a-DataFrame-in-Spark)
* [What is a Spark Session?](#What-is-a-Spark-Session)
* [What is a Spark Context?](#What-is-a-Spark-Context)
* [What is a DAG in Spark?](#What-is-a-DAG-in-Spark)
* [What is shared-nothing architecture in Spark?](#What-is-shared-nothing-architecture-in-Spark)
* [What is a partition in Spark?](#What-is-a-partition-in-Spark)
* [What is a shuffle operation in Spark?](#What-is-a-shuffle-operation-in-Spark)
* [What is a narrow transformation in Spark?](#What-is-a-narrow-transformation-in-Spark)
* [What is a wide transformation in Spark?](#What-is-a-wide-transformation-in-Spark)
* [What is Spark SQL used for?](#What-is-Spark-SQL-used-for)
* [What is a temporary view in Spark SQL?](#What-is-a-temporary-view-in-Spark-SQL)
* [What is a global view in Spark SQL?](#What-is-a-global-view-in-Spark-SQL)
* [What is a metastore in Spark?](#What-is-a-metastore-in-Spark)
* [What is Unity Catalog in Databricks?](#What-is-Unity-Catalog-in-Databricks)
* [What is predicate pushdown in Spark?](#What-is-predicate-pushdown-in-Spark)
* [What is AQE in Spark?](#What-is-AQE-in-Spark)
* [What is caching in Spark?](#What-is-caching-in-Spark)
* [What does coalesce do in Spark?](#What-does-coalesce-do-in-Spark)
* [What is Structured Streaming in Spark?](#What-is-Structured-Streaming-in-Spark)
* [What is a micro-batch in Spark Structured Streaming?](#What-is-a-micro-batch-in-Spark-Structured-Streaming)
* [What is a watermark in Spark Structured Streaming?](#What-is-a-watermark-in-Spark-Structured-Streaming)
* [What is Delta Lake?](#What-is-Delta-Lake)
* [What is time travel in Delta Lake?](#What-is-time-travel-in-Delta-Lake)
* [What is a Delta Live Table?](#What-is-a-Delta-Live-Table)
* [What is a DataFrameWriter in Spark?](#What-is-a-DataFrameWriter-in-Spark)
* [What is a DataFrameReader in Spark?](#What-is-a-DataFrameReader-in-Spark)
* [What is a UDF in Spark?](#What-is-a-UDF-in-Spark)
* [What is a Pandas UDF in Spark?](#What-is-a-Pandas-UDF-in-Spark)
* [How would you minimize shuffling when joining two large datasets in Spark?](#How-would-you-minimize-shuffling-when-joining-two-large-datasets-in-Spark)
* [How do you handle missing values in Spark DataFrames?](#How-do-you-handle-missing-values-in-Spark-DataFrames)
* [What is an accumulator in Spark?](#What-is-an-accumulator-in-Spark)
* [How do you process streaming data from Kafka in Spark?](#How-do-you-process-streaming-data-from-Kafka-in-Spark)
* [How do you optimize Spark job performance?](#How-do-you-optimize-Spark-job-performance)
* [How do you ensure data consistency in a distributed system?](#How-do-you-ensure-data-consistency-in-a-distributed-system)
* [How do you design a data pipeline for both batch and real-time processing?](#How-do-you-design-a-data-pipeline-for-both-batch-and-real-time-processing)
* [How do you migrate data from on-premise to the cloud?](#How-do-you-migrate-data-from-on-premise-to-the-cloud)
* [How do you secure sensitive data in a data lake?](#How-do-you-secure-sensitive-data-in-a-data-lake)
* [How do you monitor data quality in a data pipeline?](#How-do-you-monitor-data-quality-in-a-data-pipeline)
* [How do you handle schema evolution in a data warehouse?](#How-do-you-handle-schema-evolution-in-a-data-warehouse)
* [How do you orchestrate complex ETL workflows?](#How-do-you-orchestrate-complex-ETL-workflows)
* [How do you process unstructured data in Big Data systems?](#How-do-you-process-unstructured-data-in-Big-Data-systems)
* [How do you implement data lineage tracking?](#How-do-you-implement-data-lineage-tracking)
* [How do you ensure high availability in a Big Data cluster?](#How-do-you-ensure-high-availability-in-a-Big-Data-cluster)
* [How do you reduce storage costs in a data lake?](#How-do-you-reduce-storage-costs-in-a-data-lake)
* [How do you design a scalable data pipeline?](#How-do-you-design-a-scalable-data-pipeline)
* [How do you implement real-time analytics in Big Data?](#How-do-you-implement-real-time-analytics-in-Big-Data)
* [How do you handle late-arriving data in a streaming pipeline?](#How-do-you-handle-late-arriving-data-in-a-streaming-pipeline)
* [How do you integrate data from multiple sources in Big Data?](#How-do-you-integrate-data-from-multiple-sources-in-Big-Data)
* [How do you implement data governance in Big Data?](#How-do-you-implement-data-governance-in-Big-Data)
* [How do you optimize query performance in a data warehouse?](#How-do-you-optimize-query-performance-in-a-data-warehouse)

## What is Apache Spark?
Apache Spark is an open-source distributed computing system designed for fast processing of large-scale data, supporting batch and real-time analytics.

[Top](#top)

## What is Hadoop?
Hadoop is an open-source framework for distributed storage and processing of large datasets using the MapReduce programming model.

[Top](#top)

## What are the limitations of MapReduce in Hadoop?
MapReduce in Hadoop is limited by high disk I/O, slow performance for iterative tasks, and complex programming requirements.

[Top](#top)

## How does Hadoop compare to Spark?
Hadoop is disk-based and batch-oriented, while Spark is memory-based and supports both batch and real-time processing, making Spark faster and more flexible.

[Top](#top)

## What are RDDs in Spark?
RDDs (Resilient Distributed Datasets) are immutable, distributed collections of objects that can be processed in parallel in Apache Spark.

[Top](#top)

## What is Spark SQL?
Spark SQL is a Spark module for structured data processing using SQL queries, DataFrames, and Datasets.

[Top](#top)

## What is Spark Streaming?
Spark Streaming is a Spark component for processing real-time data streams.

[Top](#top)

## What is GraphX in Spark?
GraphX is Spark's API for graphs and graph-parallel computation.

[Top](#top)

## What is Apache Kafka?
Apache Kafka is a distributed event streaming platform used for building real-time data pipelines and streaming applications.

[Top](#top)

## What is the difference between OLAP and OLTP?
OLAP (Online Analytical Processing) is used for complex queries and analysis, while OLTP (Online Transaction Processing) is used for transactional systems with frequent read/write operations.

[Top](#top)

## What is a data warehouse?
A data warehouse is a centralized repository for storing integrated data from multiple sources, optimized for analytics and reporting.

[Top](#top)

## What are the goals of a data warehouse?
The main goals of a data warehouse are to consolidate data, support business intelligence, enable historical analysis, and improve decision-making.

[Top](#top)

## What is the difference between a database and a data warehouse?
A database is optimized for transactional processing (OLTP), while a data warehouse is optimized for analytical processing (OLAP).

[Top](#top)

## What is a data lake?
A data lake is a centralized repository that stores raw, unstructured, semi-structured, and structured data at any scale.

[Top](#top)

## How does a data lake differ from a data warehouse?
A data lake stores raw data in its native format, while a data warehouse stores processed, structured data optimized for analytics.

[Top](#top)

## What is a data mart?
A data mart is a subset of a data warehouse, focused on a specific business line or team.

[Top](#top)

## What is the difference between Kimball and Inmon data warehouse architectures?
Kimball's architecture uses dimensional modeling and data marts, while Inmon's uses normalized modeling and an enterprise data warehouse.

[Top](#top)

## What are the main data modeling approaches in data engineering?
Normalized modeling (Inmon) organizes data to reduce redundancy, denormalized modeling (Kimball) optimizes for query performance, and data vault modeling uses hubs, links, and satellites for flexibility and scalability.

[Top](#top)

## What is anchor modeling?
Anchor modeling is a database modeling technique for evolving data structures, using anchors, attributes, and ties.

[Top](#top)

## What is Data Vault modeling?
Data Vault modeling is a hybrid approach combining normalized and denormalized techniques, using hubs, links, and satellites to provide scalability and auditability.

[Top](#top)

## Why is data modeling important for a data warehouse?
Data modeling is crucial for ensuring data consistency, quality, and efficient querying in a data warehouse.

[Top](#top)

## What is a dataflow?
A dataflow is the movement and transformation of data from source to destination through various processing steps.

[Top](#top)

## What are SCDs?
Slowly Changing Dimensions (SCDs) are dimensions in data warehouses that change slowly over time, such as customer addresses.

[Top](#top)

## What is the difference between ETL and ELT?
ETL (Extract, Transform, Load) extracts data, transforms it, and loads it into a target system. ELT (Extract, Load, Transform) loads data first, then transforms it in the target system.

[Top](#top)

## What do data engineers do?
Data engineers design, build, and maintain data pipelines and infrastructure to enable data analysis and machine learning.

[Top](#top)

## What is Apache NiFi?
Apache NiFi is a data integration tool for automating the flow of data between systems.

[Top](#top)

## What is a data lakehouse?
A data lakehouse combines the features of data lakes and data warehouses, supporting both structured and unstructured data with ACID transactions.

[Top](#top)

## What are the five base functions of big data platforms?
The five base functions of big data platforms are: data ingestion, storage, processing, analysis, and visualization.

[Top](#top)

## What is data governance?
Data governance is the management of data availability, usability, integrity, and security in an organization.

[Top](#top)

## What are the V's of Big Data?
The V's of Big Data are Volume, Velocity, Variety, Veracity, and Value.

[Top](#top)

## What is Amazon Athena?
Amazon Athena is an interactive query service that allows you to analyze data in Amazon S3 using standard SQL.

[Top](#top)

## What is Amazon Redshift?
Amazon Redshift is a fully managed, petabyte-scale data warehouse service in the cloud.

[Top](#top)

## What is Amazon Aurora?
Amazon Aurora is a MySQL- and PostgreSQL-compatible relational database built for the cloud, combining performance and availability.

[Top](#top)

## What is AWS Glue?
AWS Glue is a serverless data integration service for discovering, preparing, and combining data for analytics, machine learning, and application development.

[Top](#top)

## What are AWS Step Functions?
AWS Step Functions is a serverless orchestration service that lets you coordinate multiple AWS services into serverless workflows.

[Top](#top)

## What is Amazon EMR?
Amazon EMR (Elastic MapReduce) is a cloud big data platform for processing vast amounts of data using open-source tools such as Apache Spark, Hadoop, and Hive.

[Top](#top)

## What is Azure HDInsight?
Azure HDInsight is a fully managed, open-source analytics service for enterprises, supporting Hadoop, Spark, and other big data frameworks.

[Top](#top)

## What is ZooKeeper?
ZooKeeper is a centralized service for maintaining configuration information, naming, and providing distributed synchronization.

[Top](#top)

## What is YARN in Hadoop?
YARN (Yet Another Resource Negotiator) is Hadoop's cluster resource management layer.

[Top](#top)

## What is HDFS?
HDFS (Hadoop Distributed File System) is a distributed file system designed to run on commodity hardware, providing high-throughput access to data.

[Top](#top)

## What is HBase?
HBase is a distributed, scalable, NoSQL database built on top of HDFS.

[Top](#top)

## What is Hue?
Hue is an open-source SQL Assistant for querying databases and data warehouses.

[Top](#top)

## What is Apache Hive?
Hive is a data warehouse software that facilitates reading, writing, and managing large datasets residing in distributed storage using SQL.

[Top](#top)

## What is Impala?
Impala is a massively parallel processing (MPP) SQL query engine for data stored in Hadoop clusters.

[Top](#top)

## What is Oozie?
Oozie is a workflow scheduler system to manage Hadoop jobs.

[Top](#top)

## What are Solr and Sqoop?
Solr is an open-source enterprise search platform, and Sqoop is a tool for transferring data between Hadoop and relational databases.

[Top](#top)

## What is Apache Kudu?
Apache Kudu is a storage system for fast analytics on fast data, complementing HDFS and HBase.

[Top](#top)

## What is the difference between normalized and dimensional data storage?
Normalized data storage reduces redundancy and improves data integrity, while dimensional storage is optimized for analytical queries.

[Top](#top)

## What is the difference between star and snowflake schemas?
Star schema has a central fact table connected to dimension tables, while snowflake schema normalizes dimension tables into multiple related tables.

[Top](#top)

## Describe the architecture of HDFS.
HDFS architecture consists of a NameNode (master) and DataNodes (workers) for distributed storage.

[Top](#top)

## What is a DataFrame in Spark?
A DataFrame in Spark is a distributed collection of data organized into named columns, similar to a table in a relational database.

[Top](#top)

## What is a Spark Session?
A Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.

[Top](#top)

## What is a Spark Context?
A Spark Context is the entry point for low-level Spark functionality, such as RDDs.

[Top](#top)

## What is a DAG in Spark?
A DAG (Directed Acyclic Graph) in Spark represents a sequence of computations performed on data, where each node is an RDD partition and edges represent operations.

[Top](#top)

## What is shared-nothing architecture in Spark?
Spark's shared-nothing architecture means each node is independent and self-sufficient, improving scalability and fault tolerance.

[Top](#top)

## What is a partition in Spark?
A partition in Spark is a logical division of data, allowing parallel processing across the cluster.

[Top](#top)

## What is a shuffle operation in Spark?
The shuffle operation in Spark is the process of redistributing data across partitions, often required for wide transformations like groupBy and join.

[Top](#top)

## What is a narrow transformation in Spark?
A narrow transformation in Spark is an operation where each input partition contributes to only one output partition (e.g., map, filter).

[Top](#top)

## What is a wide transformation in Spark?
A wide transformation in Spark is an operation where input partitions contribute to multiple output partitions, requiring a shuffle (e.g., groupBy, join).

[Top](#top)

## What is Spark SQL used for?
Spark SQL allows you to run SQL queries on structured data using DataFrames and Datasets.

[Top](#top)

## What is a temporary view in Spark SQL?
A temporary view in Spark SQL is a session-scoped table that can be queried using SQL.

[Top](#top)

## What is a global view in Spark SQL?
A global view in Spark SQL is accessible across all sessions and clusters.

[Top](#top)

## What is a metastore in Spark?
A metastore in Spark is a repository that stores metadata about tables, databases, and schemas.

[Top](#top)

## What is Unity Catalog in Databricks?
Unity Catalog is a unified governance solution for all data assets in Databricks, providing fine-grained access control and auditing.

[Top](#top)

## What is predicate pushdown in Spark?
Predicate pushdown is an optimization technique where filters are applied as early as possible, reducing the amount of data read.

[Top](#top)

## What is AQE in Spark?
AQE (Adaptive Query Execution) in Spark dynamically optimizes query plans at runtime based on actual data statistics.

[Top](#top)

## What is caching in Spark?
Caching in Spark stores intermediate results in memory for faster access in subsequent actions.

[Top](#top)

## What does coalesce do in Spark?
The coalesce operation in Spark reduces the number of partitions in a DataFrame, minimizing data movement.

[Top](#top)

## What is Structured Streaming in Spark?
Structured Streaming in Spark is a scalable and fault-tolerant stream processing engine built on the Spark SQL engine.

[Top](#top)

## What is a micro-batch in Spark Structured Streaming?
A micro-batch in Spark Structured Streaming is a small batch of data processed at regular intervals.

[Top](#top)

## What is a watermark in Spark Structured Streaming?
A watermark in Spark Structured Streaming is a threshold that specifies how late data can arrive and still be processed.

[Top](#top)

## What is Delta Lake?
Delta Lake is an open-source storage layer that brings ACID transactions to Apache Spark and big data workloads.

[Top](#top)

## What is time travel in Delta Lake?
Time travel in Delta Lake allows you to query previous versions of data for auditing or rollback.

[Top](#top)

## What is a Delta Live Table?
A Delta Live Table is a managed pipeline that automates ETL workflows in Databricks using Delta Lake.

[Top](#top)

## What is a DataFrameWriter in Spark?
A DataFrameWriter in Spark is used to write DataFrames to external storage systems.

[Top](#top)

## What is a DataFrameReader in Spark?
A DataFrameReader in Spark is used to read data from external storage systems into DataFrames.

[Top](#top)

## What is a UDF in Spark?
A UDF (User Defined Function) in Spark allows you to define custom functions for use in DataFrame operations.

[Top](#top)

## What is a Pandas UDF in Spark?
A Pandas UDF in Spark is a user-defined function that uses Pandas APIs and is optimized for vectorized operations.

[Top](#top)

## How would you minimize shuffling when joining two large datasets in Spark?
A scenario: You need to join two large datasets in Spark. What join type would you use to minimize shuffling? Broadcast join, if one dataset is small enough to fit in memory.

[Top](#top)

## How do you handle missing values in Spark DataFrames?
In Spark, you can handle missing values using functions like dropna(), fillna(), or by filtering out nulls.

[Top](#top)

## What is an accumulator in Spark?
A Spark accumulator is a variable that workers can only add to, used for aggregating information across the cluster.

[Top](#top)

## How do you process streaming data from Kafka in Spark?
A scenario: You need to process streaming data from Kafka in Spark. Use Spark Structured Streaming with the Kafka source connector.

[Top](#top)

## How do you optimize Spark job performance?
A scenario: You need to optimize Spark job performance. Tune the number of partitions, use caching, and avoid wide transformations when possible.

[Top](#top)

## How do you ensure data consistency in a distributed system?
A scenario: You need to ensure data consistency in a distributed system. Use ACID-compliant storage like Delta Lake or transactional databases.

[Top](#top)

## How do you design a data pipeline for both batch and real-time processing?
A scenario: You need to design a data pipeline for both batch and real-time processing. Use a Lambda architecture combining batch and speed layers.

[Top](#top)

## How do you migrate data from on-premise to the cloud?
A scenario: You need to migrate data from an on-premise database to the cloud. Use tools like AWS DMS, Azure Data Factory, or Google Dataflow.

[Top](#top)

## How do you secure sensitive data in a data lake?
A scenario: You need to secure sensitive data in a data lake. Use encryption at rest and in transit, and implement fine-grained access controls.

[Top](#top)

## How do you monitor data quality in a data pipeline?
A scenario: You need to monitor data quality in a pipeline. Implement data validation checks, logging, and alerting for anomalies.

[Top](#top)

## How do you handle schema evolution in a data warehouse?
A scenario: You need to handle schema evolution in a data warehouse. Use schema-on-read technologies and versioned schemas.

[Top](#top)

## How do you orchestrate complex ETL workflows?
A scenario: You need to orchestrate complex ETL workflows. Use Apache Airflow or similar workflow orchestration tools.

[Top](#top)

## How do you process unstructured data in Big Data systems?
A scenario: You need to process unstructured data. Use tools like Hadoop, Spark, or NoSQL databases that support unstructured data.

[Top](#top)

## How do you implement data lineage tracking?
A scenario: You need to implement data lineage tracking. Use tools like Apache Atlas or built-in features in cloud data platforms.

[Top](#top)

## How do you ensure high availability in a Big Data cluster?
A scenario: You need to ensure high availability in a Big Data cluster. Use redundant master nodes, data replication, and failover mechanisms.

[Top](#top)

## How do you reduce storage costs in a data lake?
A scenario: You need to reduce storage costs in a data lake. Use data compression, tiered storage, and data lifecycle management.

[Top](#top)

## How do you design a scalable data pipeline?
A scenario: You need to design a scalable data pipeline. Use distributed processing frameworks, decoupled components, and autoscaling infrastructure.

[Top](#top)

## How do you implement real-time analytics in Big Data?
A scenario: You need to implement real-time analytics. Use streaming platforms like Kafka, Spark Streaming, or Flink.

[Top](#top)

## How do you handle late-arriving data in a streaming pipeline?
A scenario: You need to handle late-arriving data in a streaming pipeline. Use watermarks and windowing functions to manage late data.

[Top](#top)

## How do you integrate data from multiple sources in Big Data?
A scenario: You need to integrate data from multiple sources. Use ETL tools, data integration platforms, and standardized data formats.

[Top](#top)

## How do you implement data governance in Big Data?
A scenario: You need to implement data governance. Define data ownership, policies, and use data cataloging tools.

[Top](#top)

## How do you optimize query performance in a data warehouse?
A scenario: You need to optimize query performance in a data warehouse. Use indexing, partitioning, and query optimization techniques.

[Top](#top)
