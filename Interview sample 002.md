## Here’s a focused, role‑aligned list of likely interview questions for the Azure Databricks Engineer position.

- Walk us through a recent Azure Databricks project you led end-to-end.
- What data volumes, SLAs, and team setup did you work with?
- How do you prioritize reliability, cost, and speed when building pipelines?

Databricks fundamentals and architecture
- Explain the differences between all-purpose clusters, job clusters, and SQL warehouses. When use each?
- How do you structure a Databricks workspace (Repos, Workflows, UC objects) for a multi-team environment?
- What are best practices for dependency management in Databricks (wheels, %pip, cluster libraries)?

Apache Spark and PySpark
- DataFrame vs SQL vs RDDs: when and why?
- Narrow vs wide transformations; how do shuffles happen and how do you minimize them?
- Join strategies (broadcast, sort-merge, shuffle hash): selection criteria and hints.
- Handling data skew (salting, skew join hints, AQE skew optimization).
- UDF vs Pandas UDF vs native functions: trade-offs and performance.
- Explain Catalyst, Tungsten, and Adaptive Query Execution and how they affect performance.
- Partitioning and file sizing (repartition vs coalesce) and their impact on downstream performance.

Delta Lake and Lakehouse
- What problems does Delta Lake solve? Key features (ACID, time travel, CDF).
- Implement SCD Type 2 using MERGE INTO on Delta; pitfalls to avoid.
- OPTIMIZE and Z-ORDER: when to use and how to measure effectiveness.
- VACUUM: retention, safety, table history, and data recovery considerations.
- Schema enforcement vs evolution; handling unexpected schema changes safely.
- Change Data Feed (CDF): use cases and limitations.
- Medallion architecture (bronze/silver/gold): how you’ve applied it.

Unity Catalog and governance
- UC object model (metastore, catalogs, schemas, tables) and migration considerations.
- Permission model and securing external locations, volumes, and credentials.
- Row-level and column-level security; masking strategies.
- Integrating with Microsoft Purview for lineage and governance.
- Delta Sharing: when and how to use it.

Streaming and real-time
- Structured Streaming architecture: micro-batch vs continuous, triggers, exactly-once semantics.
- Checkpointing, state management, watermarking, late data handling.
- Designing an Event Hubs → Databricks → Delta pipeline with deduplication and schema evolution.
- Idempotency strategies for sinks (Delta, SQL, external systems).
- Auto Loader vs custom ingestion for streaming/semi-batch.

ETL/ELT, SQL, and data modeling
- Designing CDC ingestion from operational DBs to Delta (e.g., using CDF, MERGE, DLT).
- Dedupe strategies (window functions, row_number) at scale.
- Window functions: practical examples you’ve optimized.
- Choosing partition columns for Delta tables; avoiding small files.
- When to use SQL Warehouses vs Spark clusters for analytics.

Azure integration
- ADLS Gen2 access patterns (ABFS direct vs mounts); service principals vs managed identities.
- Secrets and configuration management with Azure Key Vault and Databricks secrets scopes.
- Networking: VNet injection, Private Link, no-public-IP workspaces, firewall rules.
- Event-driven architectures with Event Grid/Event Hubs; orchestrating with ADF vs Workflows.
- Trade-offs: Databricks Serverless SQL vs classic; Photon benefits and limitations.
- Integrating Databricks with AKS-based microservices; when to serve models via AKS vs Databricks Model Serving.

DevOps, CI/CD, and IaC
- Your CI/CD approach for Databricks (Repos, Azure DevOps/GitHub Actions, databricks-cli, dbx).
- Packaging and versioning code (wheels), environment pinning, and reproducibility.
- Terraform for Databricks (workspaces, clusters, UC objects, permissions). Show a module you designed.
- Promotion across envs (dev/test/prod): data, schema, and job configuration migrations.
- Orchestrating multi-task jobs with Databricks Workflows; failure handling and retries.

Performance tuning and cost optimization
- Methodology for diagnosing slow jobs (Spark UI, Ganglia/metrics, event logs).
- Tuning cluster sizing, autoscaling, and instance pools; spot vs on-demand.
- Techniques to reduce shuffles and small files; compaction strategies.
- Photon engine: when it helps and when it doesn’t.
- Reducing DBU costs in continuous pipelines and SQL workloads.

Security and compliance
- Implementing least privilege with AAD, SCIM, UC grants, and service principals.
- Column-level encryption/masking and PII handling in the lakehouse.
- Audit logging and monitoring access to sensitive datasets.
- Private endpoints and egress restrictions for secure data exfiltration control.

Testing, quality, and observability
- Unit/integration testing for PySpark (pytest, chispa) and DLT expectations.
- Data quality frameworks (Great Expectations/Deequ) and how you wire them into pipelines.
- Building reproducible test datasets and golden data patterns.
- Logging/metrics strategy; integrating with Azure Monitor/Log Analytics.

Collaboration with data scientists and ML
- Feature engineering at scale in Spark; Feature Store usage.
- MLflow tracking, model registry, and CI/CD for models.
- Deciding between batch scoring in Databricks vs real-time serving on AKS or Model Serving.

Agile and team practices
- How you “own the code” in a Scrum team: reviews, standards, and on-call/incident response.
- Refinement and estimation approaches for data engineering work.
- Handling conflicting priorities from product, DS, and platform stakeholders.
- Example of proactively improving a pipeline or platform process.

Scenario/design questions
- Design a robust ingestion pipeline from a transactional SQL DB to a curated Delta table with CDC, schema evolution, and backfills. Discuss SLAs and recovery.
- Build a near real-time pipeline from Event Hubs to a gold Delta table with deduplication and late-arriving data handling; include checkpointing and exactly-once semantics.
- Migrate a legacy Hive/Parquet lake to Delta with Unity Catalog, minimizing downtime and ensuring lineage and permissions are preserved.
- Secure a Databricks workspace for a regulated environment (no public IPs, private endpoints, Key Vault-backed secrets, UC permissions).
- Optimize a nightly PySpark job that doubled in runtime after data growth; walk through your diagnostic and tuning steps.
- Choose between ADF, Databricks Workflows, and Azure Functions for orchestration in an event-driven architecture; justify trade-offs.

Language and communication
- Describe a complex technical concept from your last project to a non-technical stakeholder (in English).
- Example of cross-team collaboration where Polish and English communication both mattered.

Availability and ways of working
- Preferred tooling for code reviews and branching strategy in Databricks Repos.
- Experience working fully remotely across time zones and handling on-call/production support.

## Below are longer, simple sample answers to the most important questions for this Azure Databricks Engineer role.

General and background
- Walk us through a recent Azure Databricks project you led end-to-end.
  A: I built a lakehouse on Azure using ADLS Gen2, Databricks, and Delta Lake with a Bronze/Silver/Gold design. Files arrived in ADLS and were ingested with Auto Loader, then cleaned and joined in PySpark, and finally modeled for analytics in Delta tables. We orchestrated with Databricks Workflows and exposed results through SQL Warehouses and Power BI. I set up CI/CD, testing, and monitoring so deployments were repeatable and issues were easy to spot and fix.

- How do you prioritize reliability, cost, and speed when building pipelines?
  A: I start with reliability because bad or missing data hurts the business most. I make pipelines idempotent, add retries, checkpoints, and data quality checks to catch issues early. Then I focus on cost by right-sizing clusters, using autoscaling and Photon, and compacting small files. Speed comes next through query tuning, partitioning, broadcasting small joins, and using OPTIMIZE/Z-ORDER where it helps.

Databricks fundamentals and architecture
- Explain all-purpose clusters vs job clusters vs SQL warehouses.
  A: All-purpose clusters are for development and exploratory work; they’re shared and interactive. Job clusters spin up just for a scheduled job and shut down after, which is great for cost control and clean, reproducible environments. SQL Warehouses are for BI/SQL use cases with fast startup and high concurrency. I use all-purpose in dev, job clusters in production ETL, and SQL Warehouses for dashboards and analysts.

- How do you structure a Databricks workspace for multi-team use?
  A: I separate environments (dev/test/prod) and use Unity Catalog for clear data boundaries (catalog/schema/table). Code lives in Databricks Repos connected to Git, with one repo per service or domain. Jobs are defined in Workflows with clear naming and tags, and permissions follow least privilege so teams only see what they need. I also standardize folder and table naming so navigation is easy.

- Dependency management best practices?
  A: I package Python code as wheels and pin versions in requirements files or lock files for reproducibility. For jobs, I install dependencies with %pip at job start so each run is consistent. I avoid manual cluster libraries where possible to prevent drift. I also test upgrades in lower environments before promoting.

Apache Spark and PySpark
- DataFrame vs SQL vs RDDs: when and why?
  A: I prefer DataFrame and SQL APIs because the optimizer (Catalyst) can speed them up automatically. SQL is great for readable transformations and joins; DataFrames give more programmatic control. I use RDDs only when I need low-level control or non-relational operations, which is rare in modern ETL.

- How do you reduce shuffles and handle joins efficiently?
  A: I filter and project early to shrink data sizes before wide operations. I broadcast small dimension tables to avoid large shuffles and use sort-merge joins for large, sorted datasets. I pick join keys with good cardinality and ensure they’re clean and trimmed to reduce skew.

- Handling data skew?
  A: I detect skew in the Spark UI by looking for tasks that run much longer than others on join or groupBy stages. I use techniques like salting (adding a random key), skew join hints, or pre-aggregations to spread work evenly. Adaptive Query Execution (AQE) also helps by splitting skewed partitions automatically.

- UDF vs Pandas UDF vs native functions?
  A: I use native Spark SQL functions first because they’re fastest and easiest for the optimizer. Pandas UDFs are my second choice when I need vectorized Python logic on columns. Regular Python UDFs are last resort due to serialization overhead and weaker optimization.

- Partitioning and file sizing best practices?
  A: I partition by columns that people filter on often, like event_date, but avoid over-partitioning. I aim for output files around 100–512 MB to balance parallelism and metadata overhead. I use repartition or coalesce to control partition counts, and run Delta OPTIMIZE to compact small files.

Delta Lake and Lakehouse
- What problems does Delta Lake solve?
  A: Delta brings database-like reliability to data lakes. It gives ACID transactions, so concurrent reads/writes are safe, and schema enforcement so bad data doesn’t sneak in. Time travel and Change Data Feed make backfills and incremental processing much easier. It’s the backbone of a robust lakehouse.

- Implement SCD Type 2 with MERGE; pitfalls?
  A: I use MERGE INTO to close out old records (set end_date and current_flag = false) and insert new versions. I make sure there’s a unique business key and a reliable “last updated” timestamp to order changes. I watch for duplicates and late-arriving data, and I validate that the MERGE condition is deterministic to avoid duplicate history rows.

- OPTIMIZE and Z-ORDER: when to use and how to verify?
  A: I run OPTIMIZE on Delta tables that receive many small files to improve read and write performance. I use Z-ORDER on columns frequently used in filters to increase data skipping. I measure benefits by tracking query latency and by checking the data skipping metrics in the query profile.

- VACUUM retention and recovery considerations?
  A: I keep the default 7-day retention unless storage is a real problem and we fully understand the risk. Shorter retention reduces the ability to time travel or recover from accidental deletes. Before changing it, I confirm downstream dependencies and have backups or recovery plans.

- Schema enforcement vs evolution; how to handle safely?
  A: I enforce schema to block unexpected or bad fields. When new columns are expected, I enable evolution in controlled jobs and add data quality checks. I document changes and make sure downstream models and dashboards are updated before rollout.

Unity Catalog and governance
- UC object model and migration considerations?
  A: UC organizes data as metastore > catalog > schema > table, which keeps things clean across environments and teams. For migration, I plan naming, external locations, storage credentials, and permissions carefully. I convert legacy Hive/Metastore tables to UC, test access patterns, and update code to fully qualified names.

- Securing external locations and credentials?
  A: I use storage credentials (managed identity or service principal) with least privilege access to specific containers or folders. I register these as external locations in UC and grant access only to required groups. This centralizes control and avoids spreading keys in code.

- Row-level and column-level security; masking strategies?
  A: I build dynamic views that filter rows based on user groups or attributes, and I mask sensitive columns using functions or views. Where supported, I use UC’s row/column-level security features to manage this centrally. I log and audit access to sensitive datasets.

Streaming and real-time
- Structured Streaming basics and exactly-once writes to Delta?
  A: Structured Streaming processes data in small micro-batches with checkpoints to track progress. With Delta Lake, writes are transactional, which gives exactly-once semantics when using checkpoints correctly. I design streams to be idempotent so replays don’t duplicate results.

- Checkpointing, state, and watermarking for late data?
  A: Checkpoints store offsets and state so a stream can resume safely after failures. Watermarking sets how long to keep state so the job doesn’t grow memory endlessly. I choose a watermark that balances accuracy (accepting some late events) and resource usage.

- Auto Loader vs custom ingestion for streams and files?
  A: I prefer Auto Loader for file-based ingestion because it lists files efficiently and handles schema inference/evolution. It’s simpler and cheaper than custom listing for large folders. I only build custom ingestion when I have special needs that Auto Loader can’t handle.

ETL/ELT, SQL, and data modeling
- CDC ingestion from operational DBs to Delta?
  A: I land change files or events (with LSN or timestamps), dedupe, and apply them using MERGE into Bronze and Silver tables. I keep a bookmark of the last processed change to support restarts. For downstream tables, I read incrementally using Delta CDF to avoid full reloads.

- Dedupe strategies at scale?
  A: I use window functions like row_number over partitioned keys and order by the latest timestamp, then keep only the first row. For streaming, I combine keys with watermarking to remove duplicates within a time window. I add unique constraints at the business logic level when possible.

- Choosing partition columns for Delta tables?
Azure integration
  A: I pick columns with moderate cardinality that match common filters, usually a date or region. Too many partitions create tiny files and slow down queries. I test with sample queries and adjust based on actual read patterns.

- ADLS Gen2 access: ABFS vs mounts; identities?
  A: I use direct abfss:// paths for simplicity, performance, and fewer mount management issues. For authentication, I prefer managed identities on Azure so we don’t store secrets. When that’s not possible, I use service principals with secrets stored in Key Vault and referenced via Databricks secret scopes.

- Secrets and configuration management?
  A: Secrets live in Azure Key Vault and are surfaced in Databricks through secret scopes. I keep configuration files per environment and inject them at runtime so code doesn’t change across environments. This makes deployments safer and repeatable.

- Networking basics for secure setups?
  A: I use workspaces without public IPs, set up Private Link for control and data planes, and add private endpoints to storage accounts. I lock down storage with firewalls to only trusted networks. This prevents data exfiltration and meets compliance needs.

- Event-driven architectures and orchestration choices?
  A: For events, I use Event Hubs or Event Grid to trigger processing and move data. For orchestration, Databricks Workflows is great for Databricks-native jobs; ADF is better for moving data across many Azure services. I keep the design simple and observable with clear alerts and dashboards.

DevOps, CI/CD, and IaC
- CI/CD approach for Databricks?
  A: I sync users/groups from Azure AD to Databricks using SCIM, then grant access to only what each group needs in Unity Catalog. Service principals handle automation with tightly scoped permissions. Regular reviews remove unused access and keep audits clean.

- PII handling and masking in the lakehouse?
  A: I minimize who can see PII and store it in restricted schemas. I mask or tokenize sensitive fields in views and apply row/column-level security where needed. Access and queries are logged and monitored for unusual patterns.

- Audit logging and monitoring access to sensitive datasets?
  A: I enable workspace and Unity Catalog audit logs and send them to Log Analytics or a SIEM. I create alerts for key actions like permission changes or large data exports. This provides traceability for compliance and incident response.

Testing, data quality, and observability
- Unit/integration testing for PySpark and DLT?
  A: I write unit tests with pytest and chispa for transformations and edge cases. For DLT, I use expectations to enforce data rules and fail fast on bad data. Integration tests run on small sample datasets to validate end-to-end logic.

- Data quality frameworks in pipelines?
  A: I use Great Expectations or similar to define rules like uniqueness, non-null, and ranges. Failing rows can be quarantined to a separate table for review. Quality metrics are reported to dashboards so stakeholders see data health.

- Logging/metrics strategy; integrating with Azure Monitor?
  A: I log structured events from jobs, capture metrics like throughput and latency, and send them to Azure Monitor/Log Analytics. I add alerts for failures, SLA breaches, and backlog growth. Clear dashboards help the team act before users notice issues.

Collaboration with data scientists and ML
- Feature engineering at scale and Feature Store usage?
  A: I build features with Spark so they’re consistent for training and serving. The Feature Store lets us register, document, and reuse features across teams. This avoids “train/serve skew” and speeds up model development.

- MLflow tracking and model deployment?
  A: I track experiments with MLflow, logging parameters, metrics, and artifacts. Models move through a registry with stages (Staging/Production) and CI/CD gates. For serving, I choose batch in Databricks for large volumes or real-time endpoints when latency matters.

Agile and team practices
- How you “own the code” in a Scrum team?
  A: I write clean, tested code, do thorough PR reviews, and add documentation and runbooks. I join on-call rotations and fix root causes, not just symptoms. I also look for small improvements that reduce cost or failure risk.

- Handling conflicting priorities from product, DS, and platform teams?
  A: I make trade-offs visible with clear estimates and risks, and align on business impact. If needed, I propose phased delivery with a minimal, safe first version. I keep communication open and confirm decisions in writing.

Scenario/design questions
- Design a robust CDC pipeline from SQL DB to curated Delta with backfills.
  A: I capture changes with timestamps/LSNs, land them in Bronze, dedupe, and apply upserts with MERGE into Silver. I track high-water marks so restarts are safe and use Delta CDF for incremental downstream reads. For backfills, I run parameterized jobs that replay historical ranges without breaking current state.

- Build a near real-time Event Hubs → Delta pipeline with dedup and late data handling.
  A: I read from Event Hubs with Structured Streaming, parse and validate messages, and use a watermark with a unique key to deduplicate. I write to Delta with checkpoints for exactly-once semantics. I monitor lag and set autoscaling to keep latency within SLA.

- Migrate a legacy Hive/Parquet lake to Delta with Unity Catalog.
  A: I inventory tables, convert Parquet to Delta, and register them in Unity Catalog with proper permissions. I test queries and lineage, then plan a cutover window where old tables are read-only. Documentation and communication keep consumers aligned during the switch.

- Secure a Databricks workspace for a regulated environment.
  A: I use a no-public-IP workspace, Private Link, and private endpoints for storage. Secrets are in Key Vault, synced via secret scopes, and identities are managed with AAD. Unity Catalog enforces least privilege, and audit logs go to a central SIEM with alerts.