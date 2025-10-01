🔹 1. Databricks & Spark Fundamentals
- What is Databricks, and how is it different from plain Apache Spark?
- Explain the Databricks Lakehouse architecture.
- What is the difference between Spark RDD, DataFrame, and Dataset?
- How does Spark handle lazy evaluation?
- Explain narrow vs. wide transformations in Spark.
- What is a DAG in Spark? How is it created?

🔹 2. Delta Lake
- What is Delta Lake, and why is it important in Databricks?
- Difference between Delta tables and Parquet tables.
- What is schema enforcement and schema evolution?
- Explain the ACID guarantees in Delta Lake.
- How would you implement Slowly Changing Dimensions (SCD Type 2) in Delta?
- What is time travel in Delta Lake?

🔹 3. Data Engineering / ETL
- How do you design an ETL pipeline in Databricks?
- How would you ingest batch data vs. streaming data?
- What’s the difference between structured streaming and batch in Spark?
- How do you optimize joins in Spark?
- How do you handle small file problems in Databricks?
- How would you load data from Kafka into Databricks?

🔹 4. SQL & Performance
- How do you optimize queries in Databricks SQL?
- What’s the difference between Databricks SQL, Spark SQL, and Delta SQL?
- What are Z-ORDER and OPTIMIZE in Databricks?
- How do you handle skewed data in Spark?
- What’s the difference between broadcast join and shuffle join?

🔹 5. Cloud & Integrations
- Have you used Databricks on Azure vs. AWS? Differences?
- How would you connect Databricks with Snowflake / Synapse / BigQuery?
- What’s the difference between Azure Data Factory and Databricks?
- How do you implement CI/CD for Databricks notebooks/jobs?
- How do you monitor jobs in Databricks?

🔹 6. Real-time / Streaming
- Explain the difference between batch, micro-batch, and continuous streaming in Databricks.
- How would you implement a real-time data pipeline with Kafka + Databricks + Delta Lake?
- What is watermarking in Spark Structured Streaming?

🔹 7. Security & Governance
- How does Databricks handle data security (RBAC, ABAC)?
- What’s Unity Catalog in Databricks?
- How do you manage table access in Databricks?

🔹 8. Scenario / Troubleshooting
- A job is running very slowly – how would you debug it?
- You see out-of-memory errors in Spark – what would you do?
- How do you handle schema drift in incoming data?
- A downstream team complains about duplicates – how do you fix it?

## Questions & answers

1) Databricks and Spark fundamentals

- What is Databricks, and how is it different from plain Apache Spark?
  - Databricks is a managed platform built around Apache Spark that adds collaborative notebooks, managed clusters, job orchestration, Delta Lake, Unity Catalog, governance, and the Photon engine for high-performance SQL. 
  - Compared to running open-source Spark yourself, Databricks handles cluster lifecycle, autoscaling, secure networking, credential passthrough, optimized runtimes, and offers features like Delta Lake ACID transactions, data skipping, Z-ORDER, and serverless SQL Warehouses.

- Explain the Databricks Lakehouse architecture.
  - The Lakehouse unifies data lake flexibility with data warehouse reliability and performance: a single storage layer (object store) with Delta Lake for ACID and schema management, a governance layer (Unity Catalog) for security/lineage, and multiple engines (Spark, Photon, ML runtimes) over the same data.
  - It supports medallion architecture (Bronze raw, Silver refined, Gold curated), enabling BI, ML, and streaming on one platform without data copies.

- Difference between Spark RDD, DataFrame, and Dataset
  - RDD: low-level, typed as JVM objects, resilient distributed collections; offers fine-grained control but no automatic optimization.
  - DataFrame: distributed tables with a schema; optimized by Catalyst; best for SQL-style operations and performance; untyped in Python.
  - Dataset: typed API (Scala/Java) combining compile-time type safety with Catalyst optimizations; not available in PySpark.

- How does Spark handle lazy evaluation?
  - Transformations build a logical plan lazily; nothing executes until an action (e.g., count, collect, write). 
  - Catalyst and Tungsten optimize the plan before execution; Spark materializes a DAG and executes stages only when required. This reduces unnecessary work and enables whole-stage codegen.

- Explain narrow vs. wide transformations in Spark.
  - Narrow: each output partition depends on a single input partition (e.g., map, filter). They don’t require shuffles and are cheaper.
  - Wide: output partitions depend on multiple input partitions (e.g., groupBy, join, distinct). They trigger shuffles, new stages, and are common performance bottlenecks.

- What is a DAG in Spark? How is it created?
  - The DAG (Directed Acyclic Graph) represents the lineage of RDD/DataFrame transformations. Spark breaks the DAG into stages at shuffle boundaries.
  - It’s created when you apply transformations; an action triggers the DAG scheduler to optimize and schedule tasks across executors.

2) Delta Lake

- What is Delta Lake, and why is it important in Databricks?
  - Delta Lake is a storage layer that brings ACID transactions, schema enforcement/evolution, time travel, and scalable metadata (transaction log) to data lakes.
  - It enables reliable batch and streaming, upserts/merges, and consistent reads/writes in multi-user pipelines, removing common data lake pitfalls.

- Difference between Delta tables and Parquet tables.
  - Delta tables store data in Parquet but add a transaction log (_delta_log) that tracks snapshots, schema, and operations for ACID and time travel.
  - Delta enables MERGE, DELETE, UPDATE, OPTIMIZE, Z-ORDER, CDF (Change Data Feed), and concurrent writes; plain Parquet lacks these.

- What is schema enforcement and schema evolution?
  - Enforcement: Delta rejects writes that don’t match the table schema (e.g., wrong types/columns) unless permitted.
  - Evolution: Controlled updates to the schema (e.g., new columns) via mergeSchema or ALTER TABLE; can be automatic with Auto Loader or explicit in batch.

- Explain the ACID guarantees in Delta Lake.
  - Atomicity: a write is all-or-nothing via atomic commits to the log.
  - Consistency: readers see a consistent snapshot; constraints can be enforced.
  - Isolation: snapshot isolation via optimistic concurrency control.
  - Durability: committed files and logs are persisted in object storage.

- How would you implement Slowly Changing Dimensions (SCD Type 2) in Delta?
  - Use MERGE INTO on the dimension table keyed by business key.
  - On match and changed attributes: set current_flag=false and end_date=current_ts for existing record; insert a new row with current_flag=true, start_date=current_ts.
  - On not matched: insert as a new record. Use generated columns for audit timestamps, and optionally use Delta CDF to drive downstream changes.

- What is time travel in Delta Lake?
  - The ability to query or restore previous table versions by timestamp or version number (VERSION AS OF or TIMESTAMP AS OF).
  - Useful for reproducibility, debugging, and rollback. Subject to VACUUM retention.

3) Data Engineering / ETL

- How do you design an ETL pipeline in Databricks?
  - Use medallion layers (Bronze/Silver/Gold); ingest raw with schema capture and expectations; refine with dedup, cleansing, and business logic; curate for analytics.
  - Use Delta for all layers; orchestrate with Databricks Workflows or DLT; add unit/integration tests and data quality rules; enable autoscaling and cost controls.

- How would you ingest batch data vs. streaming data?
  - Batch: read files from cloud storage using Auto Loader or spark.read; schedule jobs; use OPTIMIZE to compact.
  - Streaming: Spark Structured Streaming with Auto Loader for files or format "kafka" for Kafka; use checkpoints, watermarks, and idempotent sinks (Delta). Keep SLAs via triggers and autoscaling.

- What’s the difference between structured streaming and batch in Spark?
  - Structured Streaming runs a continuous/triggered query over an unbounded table with incremental state, checkpointing, and exactly-once sinks (Delta). 
  - Batch processes a static dataset and produces a one-time result. APIs are similar; streaming requires careful state and latency management.

- How do you optimize joins in Spark?
  - Choose join strategy: broadcast small dimension tables (auto or hint), avoid Cartesian products.
  - Co-locate/join on well-partitioned keys; reduce data volume early (select, filter).
  - Enable AQE for skew and dynamic partition coalescing; consider bucketing for repeated joins; use correct join type and meaningful predicates.

- How do you handle small file problems in Databricks?
  - Write with optimized file sizes (OptimizeWrite, Auto Compact); use foreachBatch to control partition sizes.
  - Periodically run OPTIMIZE on Delta tables; use Auto Loader with file aggregation; avoid over-partitioning.

- How would you load data from Kafka into Databricks?
  - Read stream with format "kafka" (bootstrap.servers, subscribe, startingOffsets), parse key/value (JSON/Avro), and manage schema (schema registry if needed).
  - Use withWatermark for dedup and state; writeStream to Delta with checkpointLocation; design Bronze (raw bytes) then Silver (parsed) tables.

4) SQL and Performance

- How do you optimize queries in Databricks SQL?
  - Use Delta with OPTIMIZE and Z-ORDER on common filters/joins; maintain statistics; prune columns/partitions.
  - Leverage Photon engine, result cache, and materialized views where suitable; avoid UDFs in hot paths; monitor query profile for skew/shuffles.

- Difference between Databricks SQL, Spark SQL, and Delta SQL?
  - Spark SQL: SQL engine within Spark for DataFrames; supports ANSI SQL plus Spark extensions.
  - Databricks SQL: serverless/managed SQL Warehouses, Photon, governance integration, dashboards, alerts; same core dialect with platform features.
  - Delta SQL: SQL commands specific to Delta (MERGE, OPTIMIZE, ZORDER BY, VACUUM, DESCRIBE HISTORY, CLONE, CDF functions).

- What are Z-ORDER and OPTIMIZE in Databricks?
  - OPTIMIZE compacts many small files into larger ones for better scan efficiency.
  - Z-ORDER co-locates data by specified columns within files to improve data skipping on multi-dimensional filters (e.g., device_id, event_date).

- How do you handle skewed data in Spark?
  - Enable AQE skew join handling; salting keys; repartitioning by a composite key; filtering hot keys separately.
  - Broadcast the small side, pre-aggregate before join, or increase parallelism; use skew hints when necessary.

- Difference between broadcast join and shuffle join?
  - Broadcast join sends a small table to all executors to avoid shuffles on the big side; best when the small side fits broadcast threshold.
  - Shuffle join hashes both sides by key and shuffles data across the cluster; more expensive, but necessary for large-large joins.

5) Cloud and Integrations

- Have you used Databricks on Azure vs. AWS? Differences?
  - Storage and identity differ: ADLS Gen2 + AAD/Entra ID and Credential Passthrough on Azure; S3 + IAM roles/instance profiles on AWS.
  - Secret scopes and key management: Azure Key Vault-backed vs. AWS Secrets Manager/KMS. Networking differs (Private Link, VPC/VNet peering). Feature parity is high; workspace provisioning and billing differ by cloud.

- How would you connect Databricks with Snowflake / Synapse / BigQuery?
  - Use native connectors/JDBC with secure secrets; for Snowflake, the Databricks Snowflake connector (write DataFrames via sfOptions). 
  - For Synapse, use Azure Synapse connector or COPY into external tables via ADLS; for BigQuery, use the Spark BigQuery connector with service account keys or workload identity.
  - Ensure network egress, IAM/AAD auth, and pushdown settings; validate data types and partitioning.

- Difference between Azure Data Factory and Databricks?
  - ADF is an orchestration and data movement service (pipelines, mapping data flows, connectors). 
  - Databricks is a compute/processing platform for transformations, streaming, ML, and SQL analytics. Often ADF orchestrates Databricks notebooks/jobs and handles files/metadata moves.

- How do you implement CI/CD for Databricks notebooks/jobs?
  - Store code in Git via Databricks Repos; use branch-based workflows and pull requests.
  - Use Databricks Asset Bundles or Terraform/Provider to define jobs, clusters, DLT pipelines as code; deploy via CI runners (GitHub Actions/Azure DevOps).
  - Test with pytest + local Spark, run integration tests in ephemeral jobs, and promote across workspaces (dev/stage/prod) with environment-specific configs.

- How do you monitor jobs in Databricks?
  - Jobs UI, run history, and alerts; Spark UI and Ganglia metrics for performance; driver/executor logs for troubleshooting.
  - System tables and audit logs for lineage and governance; Overwatch accelerator for cost/usage; metrics to Datadog/Prometheus via sinks.

6) Real-time / Streaming

- Explain batch, micro-batch, and continuous streaming in Databricks.
  - Batch: finite input, one-off execution.
  - Micro-batch: default Structured Streaming mode; processes small batches at a configured trigger interval with exactly-once Delta sinks.
  - Continuous: low-latency processing (milliseconds) with some operation limitations; useful when sub-second latency is required.

- How would you implement a real-time data pipeline with Kafka + Databricks + Delta Lake?
  - Ingest Kafka with readStream, parse and validate schema, apply withWatermark and deduplication, write Bronze Delta with checkpoints.
  - Transform to Silver with business logic and joins to dimensions (broadcasted) and write to Delta; serve Gold tables to BI with Databricks SQL.
  - Use autoscaling clusters, trigger Once/AvailableNow for catch-up, and CDF for downstream incremental consumption.

- What is watermarking in Spark Structured Streaming?
  - A way to bound state by declaring event-time lateness (withWatermark). Records older than watermark for a given key can be dropped from state.
  - Enables scalable aggregations and deduplication while handling late events.

7) Security and Governance

- How does Databricks handle data security (RBAC, ABAC)?
  - Unity Catalog provides centralized RBAC across catalogs/schemas/tables/functions with fine-grained privileges. 
  - Attribute-based access via tags/classifications and dynamic masking/row filters; cluster policies, credential passthrough, network isolation, and audit logs reinforce security.

- What’s Unity Catalog in Databricks?
  - A unified governance layer with a metastore for all data assets (tables, views, volumes, ML models), fine-grained permissions, lineage, data discovery, and cross-workspace sharing.
  - Supports row/column-level security, masking policies, constraints, and data classification tags.

- How do you manage table access in Databricks?
  - Use GRANT/REVOKE on Unity Catalog objects; manage ownership and privileges via roles and groups.
  - Implement dynamic views with row filters and masking policies; tag data and apply policies; audit with system tables.

8) Scenario / Troubleshooting

- A job is running very slowly – how would you debug it?
  - Inspect Spark UI for long stages, shuffles, and skew; check query plan for expensive operators; look for narrow-to-wide transitions.
  - Reduce data early (projection/filter), right-size partitions, enable AQE, broadcast small sides, and review Z-ORDER/OPTIMIZE status on Delta tables.
  - Check cluster sizing, autoscaling, Photon usage, I/O bottlenecks (small files), and any UDF hotspots.

- You see out-of-memory errors in Spark – what would you do?
  - Avoid collect and large shuffles; increase executor memory/cores cautiously; persist to disk or uncache unused data.
  - Repartition to increase parallelism; broadcast smaller tables instead of shuffling; prune columns; use Kryo serialization; limit state in streaming with watermarks.

- How do you handle schema drift in incoming data?
  - Use Auto Loader with schemaLocation and allow schema evolution; route unknown fields to a rescue column.
  - For Delta, use mergeSchema or ALTER TABLE ADD COLUMN with governance controls; log changes and backfill where necessary; validate with expectations in DLT.

- A downstream team complains about duplicates – how do you fix it?
  - Identify source (retries, late arrivals, upserts). In batch, deduplicate using window functions on business keys and latest timestamp.
  - In streaming, use dropDuplicates with watermarks; at write time, use MERGE to ensure idempotency; enforce constraints or expectations and add audits/primary key checks in the Silver layer.

Pro tip
- Expect broad platform questions first, then deeper dives into Spark plans, Delta operations (MERGE/OPTIMIZE/Z-ORDER), and pipeline patterns (Bronze/Silver/Gold, streaming). Be ready to discuss join strategies, skew mitigation, file sizing, and governance with Unity Catalog, plus a short PySpark or SQL example if asked.