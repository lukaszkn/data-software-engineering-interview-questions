## Here are probable interview questions grouped by topic for a Databricks Data Engineer / Architect role matching the attached description:

Screening and background
- Walk us through a recent data platform you built end-to-end and your role in it.
- Which parts of Databricks have you used most extensively and why?
- What data volumes, SLAs, and concurrency requirements have you supported?
- Describe your experience across batch and streaming pipelines.
- Which public cloud have you worked with most, and what core services did you integrate with Databricks?
- How do you ensure data quality and reliability at scale?
- What tradeoffs have you made between ETL and ELT in the lakehouse?
- Share a challenging production incident you led and how you resolved it.

Databricks platform, Delta Lake, and Workflows
- Explain the lakehouse architecture and where Databricks fits compared to classic DW and data lakes.
- How do you choose between all-purpose clusters, job clusters, and SQL warehouses?
- When would you use Delta Live Tables vs. Jobs/Workflows? Pros/cons of each.
- Explain Delta Lake fundamentals: transaction log, ACID properties, time travel.
- How do you implement schema evolution and enforcement in Delta?
- What’s your strategy for small files and optimizing Delta tables (OPTIMIZE, Z-ORDER, file sizes)?
- Describe MERGE INTO for upserts and handling CDC (e.g., late-arriving data).
- How do you use Auto Loader? Key configs (cloudFiles options), schema hints, and checkpoints.
- What are your practices for table maintenance (VACUUM, retention, compaction)?
- How do you version control notebooks vs. Python packages in Databricks Repos?
- How do you structure multi-environment deployments (dev/test/prod) on Databricks?
- Explain Delta Sharing and when you’d use it.

Unity Catalog, governance, and security
- What’s the Unity Catalog hierarchy (metastore, catalogs, schemas, tables) and securable objects?
- How do external locations and storage credentials work?
- Compare managed vs. external tables under Unity Catalog.
- How do you implement row-level and column-level security or data masking in UC?
- How do you set up privileges and grants for least-privilege access?
- How do you handle cross-workspace governance and lineage with UC?
- What’s your approach to PII handling (tokenization, pseudonymization, hashing, KMS/CMK)?
- Describe migrating from Hive Metastore to Unity Catalog.

Spark fundamentals and performance tuning
- DataFrame vs. Dataset vs. RDD—when to choose each?
- Explain lazy evaluation, transformations vs. actions, and job stages.
- How do you diagnose and fix skewed joins?
- Strategies for joins at scale: broadcast joins, bucketing, partition pruning.
- When to cache/persist; tradeoffs and storage levels.
- Coalesce vs. repartition—when and why?
- Predicate pushdown and file format selection (Parquet vs. Delta vs. JSON/Avro).
- Handling nested and semi-structured data (explode, from_json, schema evolution).
- How do you profile and tune jobs (UI, query plans, AQE settings)?
- Avoiding/optimizing UDFs with built-in functions.
- Handling out-of-memory and shuffle errors in Spark jobs.

Streaming and real-time pipelines
- Structured Streaming basics: micro-batch vs. continuous, triggers, watermarking.
- Exactly-once semantics with Delta; checkpointing and idempotency.
- Stateful aggregations and late data handling.
- Designing CDC pipelines from Kafka/Debezium into Delta.
- Backfills and replay in streaming systems.
- What’s your approach to end-to-end SLAs for streaming vs. batch?
- How do you monitor and alert on streaming jobs in production?
- When would you choose Auto Loader over Kafka for ingestion?

Data modeling, warehousing, and mesh
- Explain the medallion architecture (bronze/silver/gold) and how you’ve applied it.
- Kimball star/snowflake vs. Data Vault vs. anchor modeling—tradeoffs and use cases.
- Implementing SCD Type 1/2/6 in Delta; surrogate keys and deduplication.
- Designing fact and dimension tables for high concurrency and freshness.
- Data Marts vs. Data Warehouses vs. Data Lakes vs. Data Mesh—when to use each.
- Partitioning and clustering strategies in Delta for large-scale tables.
- How do you manage slowly changing dimensions with late-arriving facts?
- Data contracts and domain ownership in a mesh model.

Cloud platform integration (AWS/GCP/Azure)
- Describe how you integrated Databricks with S3/ADLS/GCS (IAM roles, service principals, identities).
- Ingest patterns from cloud object storage; dealing with eventual consistency and listing.
- Private networking patterns (VPC/VNet, PrivateLink/Private Service Connect).
- Secrets management (Databricks secrets vs. cloud-native secret stores).
- Cost optimization: cluster sizing, auto-scaling, spot/preemptible, pools, SQL warehouse sizes.
- Storage layout best practices: partitioning, directory structure, file sizes.
- Encryption at rest/in transit and customer-managed keys.
- Orchestrating jobs with native Workflows vs. Airflow/Cloud Composer/Azure Data Factory.

DevOps, CI/CD, and testing
- Your CI/CD approach for Databricks (Repos, Databricks Asset Bundles, dbx, Terraform).
- How do you promote code and data artifacts across environments?
- Unit/integration testing for Spark (pytest, chispa, delta-rs testing, test data management).
- Versioning data schemas and handling breaking changes.
- Packaging Python code as wheels vs. notebooks; dependency management.
- Observability: logging, metrics, tracing for jobs; integrating with CloudWatch/Stackdriver/Log Analytics.
- Canary runs, feature flags, and safe deployments for pipelines.
- Using cluster policies and init scripts for standardization.

Data quality, reliability, and SLAs
- How do you implement data quality checks (Delta Live Tables expectations, Great Expectations, Deequ)?
- Designing idempotent pipelines and exactly-once processing.
- Handling retries, dead-letter queues, and poison-pill messages.
- Defining and monitoring SLIs/SLOs: latency, completeness, accuracy, freshness.
- Backfill strategy and reproducibility for historical corrections.
- Preventing data drift and schema drift.
- Governance over data contracts with producers/consumers.

Relational and NoSQL storage design
- When do you choose a relational DB vs. a NoSQL store for serving?
- Modeling access patterns for DynamoDB/Bigtable/Cosmos; partition and sort key design.
- Transaction isolation levels and implications for ETL/ELT.
- Pushing down aggregations to warehouses vs. computing in Spark.
- Using materialized views vs. Delta tables for serving marts.

Security, compliance, and auditing
- How do you implement audit logging and lineage in Databricks/UC?
- Strategies for fine-grained access controls across domains/teams.
- Meeting GDPR/CCPA/HIPAA requirements on the lakehouse.
- Secrets rotation and credential isolation for jobs.
- Data retention policies and legal hold in object storage and Delta.

Problem-solving and scenario design
- Design a pipeline to ingest high-volume JSON events into a Gold mart with 1-hour SLA.
- You have severe join skew on a 2 TB table. How do you diagnose and fix it?
- A Delta table shows frequent concurrent write conflicts. Root causes and mitigations?
- Your streaming job falls behind after a traffic spike. What do you do?
- A table has billions of small files, reads are slow. How do you remediate without long downtime?
- Design a CDC pipeline from an OLTP source to a dimensional model in Delta with SCD2.
- Migrate a workspace to Unity Catalog with minimal downtime—what’s your plan?
- How would you expose governed data to external partners?

Python and SQL competency checks (typical exercises)
- Write a Spark SQL query to compute a distinct daily active users metric with late data tolerance.
- Parse nested JSON with arrays into a normalized Delta schema in PySpark.
- Implement deduplication with window functions on a composite key and latest timestamp.
- Implement SCD Type 2 upsert logic on a dimension in Delta (SQL or PySpark).
- Optimize a slow PySpark job: given a plan snippet, propose changes.
- Write a unit test for a PySpark transformation with edge-case inputs.

Collaboration, Agile, and communication
- How do you prioritize and deliver in Kanban vs. Scrum environments?
- How do you communicate tradeoffs (cost vs. performance vs. time) to stakeholders?
- Describe a time you influenced standards or architecture across teams.
- Handling conflicting requirements between data producers and consumers.
- Estimation approach for large data engineering epics; slicing work for iterative delivery.
- Mentoring junior engineers and enforcing engineering best practices.

## Here are simple, short sample answers for the most likely questions.

Screening and background
- Walk us through a recent data platform you built end-to-end and your role in it.
  Answer: I designed and built a Databricks lakehouse on AWS using a medallion (Bronze/Silver/Gold) model. Data landed in S3 and was ingested with Auto Loader, then transformed with PySpark in Workflows, and served through Delta tables and SQL Warehouses for BI. I set up Unity Catalog for governance, access control, and lineage. I also tuned performance (OPTIMIZE, Z-ORDER, partitioning) and created monitoring with job alerts and CloudWatch logs. My role covered architecture, coding, ops, and stakeholder communication.

- Which parts of Databricks have you used most extensively and why?
  Answer: I use Delta Lake for reliable tables with ACID transactions and time travel. Auto Loader and Structured Streaming handle incremental ingestion and near-real-time feeds. Workflows orchestrate batch and streaming jobs across environments. Unity Catalog manages security, lineage, and external locations. SQL Warehouses and DB SQL are used to expose Gold marts to analysts with good performance and concurrency.

- What data volumes, SLAs, and concurrency requirements have you supported?
  Answer: I’ve handled tens of terabytes per day and billions of rows across many tables. SLAs ranged from 5–15 minutes for streaming freshness to hourly and daily for heavier batch models. For serving, I’ve supported dozens to a few hundred concurrent BI users on SQL Warehouses. We optimized with Delta OPTIMIZE/Z-ORDER, good partitioning, and caching to meet both latency and cost targets. We also managed write concurrency with partitioned writes and serialized MERGE jobs.

- Describe your experience across batch and streaming pipelines.
  Answer: I use streaming for event and CDC feeds where freshness matters, then land the output as Delta so batch jobs can reuse it. Batch is best for complex transforms, dimensional modeling, and large backfills. I design both to be idempotent, with checkpoints and MERGE logic so retries don’t duplicate records. For spikes or historical reprocessing, I temporarily scale batch jobs and keep streaming focused on catching up. Monitoring and alerting are in place for both modes.

- Which public cloud have you worked with most, and what core services did you integrate with Databricks?
  Answer: Mostly AWS: S3 for storage, IAM roles for access, KMS for encryption, CloudWatch for logs, and MSK/Kinesis for streaming. I’ve also integrated with Glue Catalog where needed and used PrivateLink for private networking. On Azure, I’ve connected to ADLS, Key Vault, and sometimes ADF for orchestration. I prefer Unity Catalog external locations and mountless access for cleaner security and auditing. Networking and credentials are set up with least-privilege in mind.

Databricks platform, Delta Lake, and Workflows
- Explain the lakehouse architecture and where Databricks fits compared to classic DW and data lakes.
  Answer: A lakehouse stores all data on cheap, scalable object storage but adds warehouse-like features. Databricks provides ACID tables (Delta Lake), governance (Unity Catalog), and fast SQL for analytics. This replaces the old split between a data lake (flexible but weak governance) and a data warehouse (governed but expensive and rigid). It supports batch and streaming in the same system. It also simplifies ML/AI by keeping data in one governed place.

- When would you use Delta Live Tables vs. Jobs/Workflows? Pros/cons of each.
  Answer: Use DLT when you want declarative pipelines with built-in quality checks, lineage, and easier operations. It’s great for medallion flows and managing expectations and auto-retries. Use Workflows when you need flexible orchestration across notebooks, Python scripts, SQL, and external tools, or complex dependencies. Workflows also fit custom packaging and CI/CD patterns. In practice, I mix them: DLT for core transforms, Workflows for orchestration and non-DLT tasks.

- Explain Delta Lake fundamentals: transaction log, ACID properties, time travel.
  Answer: Delta uses a transaction log (the _delta_log folder) to track every change, which gives ACID guarantees on object storage. That means consistent reads and safe concurrent writes. Time travel lets you query older table versions for audits, debugging, or rollback. Delta also supports schema enforcement and evolution, so bad or unexpected data doesn’t silently break downstream tables. Maintenance commands like OPTIMIZE and VACUUM keep performance and storage healthy.

- Describe MERGE INTO for upserts and handling CDC (e.g., late-arriving data).
  Answer: MERGE matches source and target records on a business key and updates or inserts as needed. For CDC, I process deletes, updates, and inserts in the right order and dedupe by latest record timestamp. I use idempotent logic so retries don’t create duplicates, and I close or version old records for SCD2 dimensions. Partitioning by date or domain helps control write conflicts and costs. I also add quality checks to drop or quarantine malformed records.

- How do you use Auto Loader? Key configs and checkpoints.
  Answer: Auto Loader incrementally discovers new files in S3/ADLS/GCS using either directory listing or notifications. I set cloudFiles options (format, schemaLocation, includeExistingFiles) and a checkpoint location for exactly-once processing. I use schema hints and evolution to handle new fields safely. For throughput, I tune maxFilesPerTrigger and parallelism and use file notification when available. The output lands in Delta so downstream jobs can be batch or streaming.

Unity Catalog, governance, and security
- What’s the Unity Catalog hierarchy and securable objects?
  Answer: UC is organized as metastore > catalog > schema > table/view, and it also governs volumes, functions, and external locations. Permissions cascade along this hierarchy. You manage access at the highest sensible level (e.g., by catalog or schema) and narrow as needed. UC centralizes governance across workspaces so policies are consistent. It also provides lineage and system tables for auditing.

- How do you set up privileges and grants for least-privilege access?
  Answer: I create groups for roles (e.g., data_engineers, data_analysts) and grant only the minimal permissions needed. I separate data ownership (full control) from consumption (read/select on views). Cluster policies and SQL warehouse permissions restrict compute use. External locations and storage credentials limit what storage paths jobs can access. Regular reviews and automated drift checks keep grants aligned with policy.

- How do you implement row-level and column-level security or data masking in UC?
  Answer: I use dynamic views that filter rows based on the user or group, using functions like is_member(). For masking, the view returns hashed or null values for sensitive columns unless the user has elevated rights. Consumers query the view, not the base table. This keeps logic centralized and auditable. Combined with UC auditing, it gives a clear record of who saw what.

- Describe migrating from Hive Metastore to Unity Catalog.
  Answer: I start by inventorying tables, locations, and permissions, then create catalogs/schemas that reflect domains. I define external locations and storage credentials, then migrate tables (often using Databricks-provided migration tools) and test select/insert/merge behaviors. I update jobs and BI to reference UC paths and run in parallel for a short period. After validation, I cut over with a rollback plan. I also clean up old mounts and tighten storage IAM to enforce UC.

Spark fundamentals and performance tuning
- Explain lazy evaluation, transformations vs. actions, and job stages.
  Answer: Spark builds a plan lazily as you add transformations; nothing runs until an action like count() or write() is called. When an action triggers, Spark optimizes the plan into stages separated by shuffles. Understanding this helps you reduce unnecessary shuffles and cache at the right spots. I review the physical plan and the Spark UI to spot wide stages and bottlenecks. Then I adjust partitions, joins, or filters to improve the DAG.

- How do you diagnose and fix skewed joins?
  Answer: I look at the Spark UI for tasks that take much longer and partitions with far more data. I identify skewed keys with data profiling. Fixes include salting (adding random buckets to hot keys), using AQE’s skew join handling, pre-aggregating, or broadcasting the small side. Sometimes changing the join key or filtering earlier reduces the impact. Repartitioning by a more balanced key can also help.

- Strategies for joins at scale: broadcast joins, bucketing, partition pruning.
  Answer: I broadcast small dimension tables so they join without shuffling large data. Bucketing and aligned partitioning can reduce shuffle, especially for repeatable joins, though they add maintenance overhead. I push down filters and prune partitions to keep data movement small. Pre-aggregating or selecting only needed columns also helps. AQE often improves join strategy automatically if inputs are well-structured.

- Coalesce vs. repartition—when and why?
  Answer: Coalesce reduces the number of partitions without a shuffle, which is handy after heavy filtering. Repartition reshuffles data to evenly spread it across a new number of partitions or by a key, which helps with parallelism for joins and writes. I coalesce before writing small outputs to avoid too many small files. I repartition before big joins or to match a desired target partition count. The choice is about avoiding unnecessary shuffles while keeping work balanced.

Streaming and real-time pipelines
- Structured Streaming basics: micro-batch vs. continuous, triggers.
  Answer: Micro-batch is the default and reliable; it processes data in small batches at a set trigger (e.g., every 1 minute) or “once”. Continuous processing aims for sub-second latency but has more limitations and is less common. I pick the simplest trigger that meets the SLA to keep operations stable. I size clusters and tune state to maintain consistent processing times. Monitoring lag and throughput is key for capacity planning.

- Exactly-once semantics with Delta; checkpointing and idempotency.
  Answer: With Delta and checkpoints, Spark can restart without losing progress or duplicating work. I design sinks to be idempotent, typically by writing to a staging table and using MERGE with unique keys. foreachBatch gives fine control over transactional writes. If a batch is retried, the keys prevent duplicate records. This keeps streams reliable during failures or restarts.

- Watermarking and late data handling.
  Answer: Watermarks bound how long state is kept, based on event-time. I set the delay to match realistic late arrivals from the business domain. Late records within the window update the aggregates; very late records go to a dead-letter table or a separate backfill path. This keeps state small and costs predictable. It also gives a clear process to correct history when needed.

Data modeling, warehousing, and mesh
- Explain the medallion architecture (bronze/silver/gold) and how you’ve applied it.
  Answer: Bronze stores raw data as-is with minimal processing, giving traceability and easy replays. Silver cleans, dedupes, and conforms data into reusable entities. Gold provides curated marts for analytics, often star schemas with SCDs. This layering isolates concerns and speeds up development. It also makes quality checks and access control easier at each layer.

- Kimball star/snowflake vs. Data Vault—tradeoffs and use cases.
  Answer: Kimball stars are easy for BI tools and deliver fast query performance. Data Vault focuses on historization and agility when sources change, but it’s more complex to query directly. I often land raw data in a DV-like structure for traceability, then publish Kimball marts for consumption. That combines agility with usability. The choice depends on change frequency, audit needs, and team skills.

- Implementing SCD Type 2 in Delta.
  Answer: I model dimensions with a business key, a surrogate key, valid_from, valid_to, and an is_current flag. A MERGE closes the current record when a change is detected and inserts a new version. Late-arriving changes use the event timestamp to set correct validity intervals. I add unique constraints (soft) and dedupe logic to avoid overlapping periods. This supports accurate point-in-time reporting.

- Partitioning and clustering strategies in Delta.
  Answer: I partition by high-cardinality columns commonly used in filters, usually date. Too many partitions create small files, so I balance partition count with file size targets. I use OPTIMIZE and Z-ORDER to cluster on secondary filter columns, like customer_id. Auto-compact small files in ingestion layers helps downstream reads. I review query patterns regularly and adjust layout as needed.

Cloud platform integration
- Describe how you integrated Databricks with S3/ADLS/GCS (IAM/identities).
  Answer: I prefer Unity Catalog external locations with storage credentials mapped to IAM roles or service principals. Jobs access storage directly (no mounts), which simplifies auditing and least-privilege control. On AWS, I use instance profiles or role-based access with STS. On Azure, I use service principals and Key Vault-backed credentials. This setup keeps storage access clear, secure, and auditable.

- Secrets management (Databricks secrets vs. cloud-native).
  Answer: I store credentials in Databricks secrets, usually backed by the cloud’s secret manager (Key Vault or Secrets Manager). Code references secrets at runtime—never hard-coded or in notebooks. Rotation is automated and audited. For external tools, I use the cloud-native store directly. Access to secret scopes is limited to specific groups and jobs.

- Cost optimization: clusters and SQL warehouses.
  Answer: I right-size clusters, enable autoscaling, and use spot/preemptible nodes where workloads are tolerant. Cluster pools shorten startup time and reduce idle costs. For SQL, I pick the right warehouse size and use serverless or auto-stop settings. I optimize Delta tables (compaction, Z-ORDER) to cut I/O. I also schedule heavy jobs off-peak and monitor cost dashboards to catch regressions early.

DevOps, CI/CD, and packaging
- Your CI/CD approach for Databricks.
  Answer: I use Git for source control (feature branches, PR reviews) and run unit/integration tests in CI. Deployments use Databricks Asset Bundles or Terraform to promote code and configs across dev/test/prod. Secrets and environment variables are injected at deploy time. I validate data migrations with smoke tests and canary runs. Rollbacks are scripted to reduce downtime risk.

- Packaging Python code and dependency management.
  Answer: Shared logic is packaged as Python wheels with pinned versions to ensure reproducibility. I manage dependencies via requirements files or Poetry and attach libraries via cluster policies or init scripts. For notebooks, I keep business logic thin and call functions from the packaged libraries. This separation makes testing and reuse easier. It also avoids dependency drift across clusters.

Data quality and reliability
- How do you implement data quality checks?
  Answer: I add checks at ingestion (schema, nullability, type) and at conformance (uniqueness, referential integrity, business rules). With DLT, I use expectations to drop or quarantine bad records and fail the pipeline if thresholds are breached. Great Expectations or similar tools document rules and produce reports. Failed records go to a quarantine table with reasons for quick triage. Quality gates are required before promoting to Gold.

- Designing idempotent pipelines and exactly-once processing.
  Answer: I use stable keys and deterministic transformations so a rerun produces the same result. Writes happen via MERGE or overwrite-on-success patterns to avoid partial output. Streaming uses checkpoints and unique keys to prevent duplicates on retries. Side effects (notifications, external calls) are moved after successful commits. This keeps pipelines safe during failures and redeployments.

- Handling retries and dead-letter queues.
  Answer: I implement retries with exponential backoff for transient failures (e.g., network hiccups). For persistent bad data, I write to a dead-letter table with full context for reprocessing. Monitoring alerts the team when DLQ volume spikes. We schedule periodic replays once upstream issues are fixed. Clear runbooks help on-call engineers resolve issues quickly.

Security and compliance
- How do you implement audit logging and lineage in Databricks/UC?
  Answer: I enable UC system tables and audit logs and stream them to the cloud logging service (CloudWatch, Log Analytics). Lineage in UC shows table-to-table dependencies and who accessed what. We review privileged actions and anomalous access regularly. These logs support compliance and incident investigations. Policies and alerts are in place for sensitive datasets.

- What’s your approach to PII handling?
  Answer: Collect only what’s needed and store PII in restricted catalogs/schemas. Mask or hash sensitive fields in shared views and use tokenization when reversible mapping is required. Enforce least-privilege with UC and encrypt at rest with CMK. Access is logged and reviewed regularly. Data retention policies ensure PII isn’t kept longer than necessary.

Problem-solving and scenarios
- You have severe join skew on a 2 TB table. How do you diagnose and fix it?
  Answer: I review the Spark UI for skewed tasks and inspect key distributions to find hot keys. Quick mitigations include salting hot keys and enabling AQE skew join handling. I also consider pre-aggregating the large side, filtering earlier, or broadcasting the small side. If skew is structural, I redesign partitioning or adjust the join strategy. Tests on a sample confirm the fix before full-scale runs.

- A Delta table shows frequent concurrent write conflicts. Root causes and mitigations?
  Answer: Optimistic concurrency fails when multiple jobs update overlapping files or partitions. I reduce overlap by partitioning wisely and ensuring one writer per partition at a time. I serialize MERGE jobs in Workflows or split them by partition keys. Narrowing update predicates and adding retries with jitter also helps. If necessary, I refactor to a staging table and a single consolidate step.

- Your streaming job falls behind after a traffic spike. What do you do?
  Answer: First, scale the cluster up/out and reduce trigger intervals to process more batches faster. I check for bottlenecks in stateful ops and optimize state (e.g., keys, watermarks). I ensure sink writes and checkpoints are efficient and not blocked by small files. If there’s heavy backlog, I do a one-time batch backfill, then let streaming keep up. Monitoring helps decide when to scale back down.

Collaboration, Agile, and communication
- How do you prioritize and deliver in Kanban vs. Scrum environments?
  Answer: In Kanban, I keep WIP limits low, focus on flow, and pull the highest-value item next. In Scrum, I define a clear sprint goal, slice work into thin verticals, and demo often for feedback. In both, I make work visible, unblock quickly, and keep stakeholders updated on risks. I use metrics like lead time and burndown to improve. Retrospectives drive continuous improvements in process.

- How do you communicate tradeoffs (cost vs. performance vs. time) to stakeholders?
  Answer: I present 2–3 options with simple pros/cons, rough cost and latency estimates, and the impact on future flexibility. I recommend a default choice and explain why it fits the SLA and budget. If needed, I propose a phased plan: quick win now, optimization later. I capture decisions in a short design note so everyone stays aligned. This avoids surprises and builds trust.