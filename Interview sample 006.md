Below are the kinds of questions a Databricks Engineer is commonly asked in a screening/technical interview. They’re grouped by topic to help you prep quickly.

How screens usually run
- Quick intro and your recent projects (5–10 min)
- Core Spark/Delta/Databricks platform questions (15–25 min)
- Scenario/problem-solving or light coding/SQL (10–20 min)
- Cloud/security/governance and DevOps (5–15 min)
- Questions for them (2–5 min)

Databricks platform basics
- Explain the Lakehouse and the medallion (bronze/silver/gold) architecture.
- When do you use all-purpose clusters vs Jobs clusters vs SQL Warehouses?
- What are cluster pools and cluster policies, and why use them?
- What is Photon and when does it help?
- Explain DBR versions, LTS runtimes, and how you choose a runtime.
- When would you use DBSQL vs notebooks vs DLT?
- Describe Unity Catalog’s 3-level namespace and how it changes governance.
- Mounts vs direct cloud paths (abfss/s3/gs) pros/cons.

Apache Spark fundamentals and performance
- Narrow vs wide transformations; give examples.
- What is a shuffle and how do you reduce its cost?
- Explain join strategies and when to broadcast. How do you handle skewed joins?
- spark.sql.shuffle.partitions tuning guidelines.
- Repartition vs coalesce and when to use each.
- Caching/persisting: when it helps and when it hurts.
- Adaptive Query Execution: what it does and how it helps.
- Common causes of OOM or spills and how you’d fix them.
- Explain pandas UDFs, Arrow, and when to prefer them over regular UDFs.
- Bucketing vs partitioning; when either helps.
- How do you size clusters (driver/executors/cores/memory) for a given workload?
- Explain task vs stage vs job; how you read Spark UI to diagnose slowness.

Delta Lake essentials
- Key Delta features: ACID, schema enforcement/evolution, time travel.
- How do you do CDC/UPSERT with MERGE INTO? Show the basic pattern.
- Change data feed (CDF): what it is and when to use it.
- OPTIMIZE and file compaction; ideal file sizes; small file problem.
- Z-ORDER vs liquid clustering; when and why.
- VACUUM retention rules and safety check; when lowering retention is risky.
- Generated columns, constraints, and expectations for data quality.
- Delta log internals at a high level (JSON/Parquet checkpoints).
- Handling schema drift safely in production.
- How would you roll back a bad write or deployment (time travel, restore, backups)?

Streaming, Auto Loader, and DLT
- Structured Streaming micro-batch vs continuous; common triggers.
- Checkpointing, exactly-once semantics, and idempotent sinks.
- Watermarks and late data handling; typical window use.
- Auto Loader vs COPY INTO vs custom ingestion; when to choose each.
- Auto Loader schema evolution and handling unexpected columns.
- Deduplication strategies in streaming (keys + watermarks).
- Designing a robust bronze → silver streaming pipeline.
- DLT: expectations (fail/drop/warn) and orchestration benefits.
- Managing backfills and replay in streaming pipelines.
- Common streaming failure patterns and mitigation (checkpoint corruption, stuck progress).

Orchestration and Jobs
- Databricks Workflows vs external orchestrators (Airflow/ADF/SFN).
- Task dependencies, retries, alerts, and conditional execution.
- Multi-task job best practices (shared clusters vs job clusters).
- How you parameterize jobs and manage environments.
- Scheduling and handling overlapping runs.

Security, governance, and access control
- Unity Catalog: catalogs/schemas/tables, privileges, grants.
- Row-level and column-level security with dynamic views/policies.
- External locations, storage credentials, and managed vs external tables.
- Secrets management (Secret Scopes) and key rotation.
- Credential passthrough vs instance profiles/managed identities/service accounts.
- Private link/secure cluster connectivity and no-public-IP designs.
- Audit/logging and lineage; what you capture and why.
- Data masking or tokenization approaches in the lakehouse.

DevOps, CI/CD, and testing
- Git integration with Repos; branch strategy.
- Infrastructure as code with Terraform and the Databricks provider.
- Databricks CLI/REST APIs for deployments.
- How you promote code/configs across dev/test/prod with UC catalogs.
- Unit/integration testing for PySpark/SQL (pytest, lakefs/synthetic data, DLT expectations).
- Observability and job/cluster metrics; alerting you set up.

SQL and data modeling
- Star vs Data Vault vs wide tables; when to use each.
- Window functions for dedup, top-N, and SCD patterns.
- SCD Type 2 approach in Delta (MERGE patterns, effective/expiry dates).
- Handling slowly changing dimensions vs rapidly changing facts.
- Surrogate keys, natural keys, and late arriving dimensions.
- Data quality KPIs for bronze/silver/gold and how you enforce them.
- How to design for interactive BI in DBSQL (indexes/no indexes, file layout, caching).
- When to use materialized views or Delta Live Tables for serving.

Cloud-specific (tailor to their stack if you know it)
- Azure: ABFS, ADLS Gen2, service principals/managed identities, AAD passthrough, VNet injection.
- AWS: S3, instance profiles/assume-role, cross-account access, PrivateLink, Kinesis/MSK.
- GCP: GCS, service accounts/impersonation, VPC SC, Pub/Sub.
- Storage performance considerations (throughput, parallelism, multipart uploads).
- Networking gotchas (DNS, firewall, egress paths to storage, token lifetimes).

Cost, reliability, and monitoring
- Reducing cost: Photon, autoscaling, spot/preemptible, pools, SQL warehouse sizing.
- Small files and compaction strategy at each layer.
- Job SLAs and backpressure; how you design for reliability.
- System tables and audit/usage for cost and access reviews.
- When to use SQL Warehouses vs Jobs clusters for BI cost efficiency.

Troubleshooting scenarios they may hand you
- A streaming job stopped making progress; how do you investigate and recover?
- Duplicate records appear in silver; where do you look and how do you fix pipeline logic?
- A MERGE is very slow; what do you change (file sizes, clustering, predicates, partitioning, join strategy)?
- Performance regressed after schema evolution; why and how to fix?
- Users can’t see a table after UC migration; what permissions or lineage checks?
- VACUUM removed files needed for time travel; how do you handle and prevent it?
- Skewed key causes one task to run 10x longer; mitigation options.
- S3/ADLS permission errors in jobs but not in notebooks; what’s different?
- SQL dashboard is slow; what do you check (warehouse size, caches, query plan, Z-ORDER/liquid clustering)?
- Checkpoint got corrupted; safe recovery steps.

Be ready to do small tasks live
- Write a PySpark job that reads raw JSON with Auto Loader into Delta, handling schema drift.
- Merge CDC into a silver Delta table with deduplication using window functions or MERGE.
- Tune a join using broadcast and explain the plan improvements.
- Write a SQL window query for dedup (row_number over partition by … order by …).

## Here are concise answers to the common Databricks Engineer screening questions.

Databricks platform basics
- Lakehouse & medallion: Single system for BI + AI on open formats; bronze=raw, silver=cleaned/conformed, gold=serving/BI.
- All-purpose vs Jobs clusters vs SQL Warehouses: Interactive dev vs scheduled batch/stream vs SQL BI serving.
- Cluster pools/policies: Pools cut startup time/cost; policies enforce safe, standardized cluster configs.
- Photon: Vectorized engine for SQL/DataFrame; speeds ETL/BI on modern CPUs, lower cost.
- DBR versions/LTS: Choose latest LTS for stability, match features (Photon, UC), and libs (Scala/Python).
- DBSQL vs notebooks vs DLT: BI/Ad-hoc SQL vs code-centric pipelines vs declarative pipeline with built-in quality/orchestration.
- Unity Catalog (UC): catalog.schema.table with centralized permissions, lineage, sharing across workspaces.
- Mounts vs direct cloud paths: Mounts simplify paths but add auth coupling; direct abfss/s3/gs is simpler with UC external locations.

Apache Spark fundamentals and performance
- Narrow vs wide: Narrow = no shuffle (map/filter); wide = shuffle (join/groupBy).
- Shuffle cost reduction: Prune early, filter, select needed cols, broadcast small side, salting/skew handling, partition pruning.
- Join strategies: Broadcast small tables; sort-merge for large sorted; shuffle-hash sometimes; handle skew with hints/salting.
- spark.sql.shuffle.partitions: Set close to total parallelism and data size (e.g., 2–4x executors cores); don’t leave default for big jobs.
- Repartition vs coalesce: Repartition increases/decreases with shuffle; coalesce only decreases without shuffle.
- Cache/persist: Cache reused, expensive, stable intermediates; uncache when done; avoid caching huge rarely reused data.
- AQE: Auto adjusts partitions, coalesces shuffles, picks broadcast; keep on for dynamic optimization.
- OOM/spills: Caused by large shuffles, skew, big partitions, caching too much; fix via filtering, partitioning, broadcast, memory sizing.
- Pandas UDFs/Arrow: Use for vectorized Python ops; faster than regular UDFs; prefer native SQL/DataFrame when possible.
- Bucketing vs partitioning: Partition for pruning on high-cardinality, query predicates; bucket to speed specific joins/aggregations.
- Cluster sizing: Ensure driver fits metadata/shuffle; executors sized for parallelism (cores ~2–5 per task), memory for shuffle.
- Job/stage/task & Spark UI: Job=action, stage=shuffle boundary, task=per-partition work; use UI for skew, spills, long tasks.

Delta Lake essentials
- Key features: ACID, schema enforcement/evolution, time travel, CDF, constraints, performant upserts.
- MERGE INTO: Merge target using source on keys; when matched update/delete; not matched insert. Partition/prune to speed.
- Change data feed (CDF): Emits row-level changes since version; ideal for CDC downstream syncs.
- OPTIMIZE/compaction: Combines small files into ~128–512MB; fix small-file problem; improves read performance.
- Z-ORDER vs liquid clustering: Z-ORDER co-locates data on columns for pruning; liquid clustering auto-maintains clustering without partitions.
- VACUUM: Removes old files after retention (default 7d). Lower only with guarantees you won’t need time travel/recovery.
- Generated columns/constraints/expectations: Enforce quality/derivations; DLT expectations for declarative checks.
- Delta log internals: JSON commits + Parquet checkpoints; query uses log to build table state.
- Schema drift: Use evolve with control (columns allowlist, staging), test and document changes.
- Rollback: Time travel (VERSION AS OF/TIMESTAMP AS OF), RESTORE TABLE to known good version.

Streaming, Auto Loader, and DLT
- Micro-batch vs continuous: Micro-batch is default/reliable; continuous for ultra-low latency with limitations. Triggers: once, processingTime, availableNow.
- Checkpointing/exactly-once: Checkpoints track progress; combine with idempotent sinks (Delta MERGE/append with dedup) for exactly-once semantics.
- Watermarks/late data: With event-time + watermark to drop too-late data; manage windows accordingly.
- Auto Loader vs COPY INTO vs custom: Auto Loader for scalable directory-based ingestion with schema evo; COPY INTO for batch loads; custom for niche sources.
- Auto Loader schema evolution: cloudFiles schemaLocation + options to add new cols; quarantine unexpected types.
- Dedup streaming: Key + event-time + watermark + window/last value; or MERGE with unique keys.
- Bronze→silver design: Bronze append-only raw, silver cleaned/dedup/enriched, idempotent logic, CDF for changes.
- DLT: Declarative pipelines with expectations (drop/warn/fail), lineage, auto-orchestration, simpler ops.
- Backfills/replay: Use availableNow/trigger once, clone checkpoints per backfill, parameterize time ranges.
- Common failures: Checkpoint corruption (restore/copy), schema drift (evolution policies), source permission/timeouts; add retries/alerts.

Orchestration and Jobs
- Workflows vs external: Use Databricks Workflows for native pipelines; use Airflow/ADF/SFN when cross-system orchestration required.
- Dependencies/retries/alerts: Model DAGs, set retries with exponential backoff, alerts on failure and SLA breach.
- Multi-task jobs: Prefer job clusters per task for isolation; share cluster if tasks are light and need warm cache.
- Parameterization/environments: Use widgets/params and UC catalog routing; secrets for creds; per-env configs.
- Overlapping runs: Enable concurrency with isolation or disallow; guard with idempotent writes/locks.

Security, governance, and access control
- UC namespaces/privileges: GRANT on catalogs/schemas/tables; manage via groups and least privilege.
- Row/column security: Dynamic views and column masks; attribute-based policies using current_user() or entitlements.
- External locations/managed vs external: External locations map storage + credential; managed tables in UC-managed storage; external tables in your storage.
- Secrets: Use Databricks secrets/scopes; rotate with KMS/Key Vault; avoid in code.
- Credentials: Passthrough (user identity) for interactive; instance profiles/managed identities/service accounts for jobs.
- Private networking: Private Link/SCC/no public IPs; restrict egress to storage; secure cluster connectivity.
- Audit/lineage: Use system tables, UC lineage, cloud audit logs; review access and usage regularly.
- Masking/tokenization: Hashing, format-preserving encryption, reversible vaults depending on use case.

DevOps, CI/CD, and testing
- Git Repos: Feature branches + PRs; trunk-based if mature CI; pin libs.
- IaC: Terraform with Databricks provider for workspaces, UC, clusters, jobs, permissions.
- Deployments: Databricks CLI/REST or bundle tooling; promote via env-specific configs.
- Promotion across envs: Separate UC catalogs (dev/test/prod); use mountless external locations; parametrize.
- Testing: Pytest for PySpark, SQL unit tests, DLT expectations, synthetic data/lakeFS for integration tests.
- Observability: Job/cluster metrics, event logs, system tables; alerts on failures, lag, cost anomalies.

SQL and data modeling
- Star vs Data Vault vs wide: Star for BI simplicity/perf; Data Vault for agility/audit; wide for ML features/ELT simplicity.
- Window functions: row_number/dense_rank/lag-lead for dedup, top-N, SCD logic.
- SCD Type 2: MERGE using business key; update current to set end_date/flag=false; insert new with start_date/flag=true.
- SCD vs rapidly changing facts: Keep facts immutable; update dimensions SCD2; use snapshot facts if needed.
- Keys: Use surrogate keys for joins; keep natural keys for business logic; handle late arriving dims via inferred members.
- Data quality: Null rates, dedup rate, schema conformance, referential integrity, freshness; enforce with expectations/constraints.
- BI performance: Optimize/compact, cluster on common filters, limit columns, cache strategic tables in DBSQL.
- Materialized views/DLT: Use for pre-computation and freshness SLAs; DLT for declarative refresh + quality.

Cloud-specific
- Azure: ADLS Gen2 (abfss), managed identity/SPN, AAD passthrough, VNet injection, Private Link to storage.
- AWS: S3, instance profiles/assume-role, cross-account IAM, PrivateLink, Kinesis/MSK ingestion.
- GCP: GCS, service accounts/impersonation, VPC SC, Pub/Sub ingestion.
- Storage perf: Use larger files, parallelism, multipart upload, avoid small files; tune throughput limits.
- Networking: Ensure DNS/private endpoints; avoid egress bottlenecks; token lifetimes for cloud APIs.

Cost, reliability, and monitoring
- Cost reduction: Photon, autoscaling, spot/preemptible, pools, SQL warehouse sizing, compact files, pruning.
- Small files: Batch writes, AUTOSIZE in OPTIMIZE, merge conditionally, Auto Loader with file notification.
- SLAs/backpressure: Size for peak, apply rate limits, monitor lag; build retry/idempotent pipelines.
- System tables: Use for audit, cost allocation, job usage, lineage; drive tagging/chargeback.
- SQL Warehouses vs Jobs: Warehouses for interactive BI; Jobs clusters for ETL/ML; pick smallest that meets latency.

Troubleshooting scenarios
- Streaming stuck: Check UI state progress, source availability, checkpoint; restart from clean checkpoint if corrupted; verify triggers/watermarks.
- Duplicates in silver: Trace bronze→silver; enforce keys + window dedup or MERGE with MATCHED/NOT MATCHED; fix idempotency.
- Slow MERGE: Add predicates on join keys, optimize/cluster target, compact files, use predicate pushdown, broadcast small side, handle skew.
- Perf regressed after schema evo: New columns breaking pruning? Re-optimize/cluster, update stats, review read schema, adjust partitioning.
- UC visibility issue: Check grants on catalog/schema/table; ownership, current catalog; workspace-to-UC metastore binding.
- VACUUM removed needed files: Restore from backup/snapshots; increase retention; set dataRetentionDurationCheck to true; time travel no longer available.
- Skewed key: Salting, skew join hints, partial aggregation, increase skew partitions, cap reduce tasks.
- S3/ADLS perms: Interactive uses user creds; jobs use service principals/instance profiles; verify role bindings/passthrough.
- Slow SQL dashboard: Increase/auto scale warehouse, enable Photon, cache, optimize/cluster tables, review query plan and filters.
- Corrupt checkpoint: Stop job, backup/delete checkpoint, restart from last good version/time window if idempotent.

Be ready to do small tasks live
- Auto Loader JSON to Delta (schema drift):
  - spark.readStream.format("cloudFiles").option("cloudFiles.format","json").load(path) → writeStream to Delta with checkpoint, schemaLocation, and schemaEvolutionMode addNewColumns.
- CDC MERGE with dedup:
  - Use ROW_NUMBER over key+event_time to pick latest, then MERGE INTO target USING filtered source ON key WHEN MATCHED UPDATE WHEN NOT MATCHED INSERT.
- Tune join with broadcast:
  - spark.conf set autoBroadcastJoinThreshold; or broadcast() hint on small df; confirm with EXPLAIN and fewer shuffle stages.
- Dedup window SQL:
  - SELECT * FROM (SELECT *, row_number() over (partition by key order by event_time desc) rn FROM t) WHERE rn=1.

## Here are expanded, interview-ready answers grouped by topic. Each one gives a clear explanation, examples, and a quick best practice.

Databricks platform basics
- Lakehouse and medallion architecture: The Lakehouse unifies data lakes (low cost, open formats) and warehouses (governance, performance) so you can do ETL, BI, and ML on the same open Delta tables. The medallion model structures pipelines: bronze stores raw/ingested data unchanged, silver cleans/deduplicates and applies business logic, and gold serves analytics-ready aggregates and marts. This layering makes lineage, testing, and rollbacks easier.
- All-purpose clusters vs Jobs clusters vs SQL Warehouses: All-purpose clusters are for interactive development and collaborative notebooks. Jobs clusters are ephemeral, scoped to a task run, and ideal for scheduled ETL/streaming for better isolation and reproducibility. SQL Warehouses are elastic, auto-managed compute for BI/SQL dashboards; they optimize for concurrency and short queries with Photon.
- Cluster pools and policies: Pools pre-warm VMs so jobs start faster and reduce DBU/VM idle cost by reusing instances. Policies enforce safe, standardized cluster settings (node types, max size, libraries) so teams don’t overspend or break security rules. Use pools for jobs and interactive environments with frequent spin-up; apply policies across all clusters for governance.
- Photon: Photon is a vectorized, cache-aware execution engine for SQL/DataFrame operations built in C++. It accelerates scans, filters, joins, and aggregations—especially on Delta/Parquet—and reduces cost by finishing faster on the same hardware. It requires compatible DBR runtimes (generally 9.x+), and shines in ETL and BI workloads; UDF-heavy or exotic operations may see less benefit.
- DBR versions and LTS: Choose the latest Long-Term Support (LTS) runtime for production to balance features and stability (library/Scala/Python compatibility). Make sure it supports required features like Photon, Unity Catalog, and your Python/Scala libraries. Standardize runtimes per environment to avoid “works on my cluster” issues.
- When to use DBSQL, notebooks, or DLT: Use DBSQL for interactive SQL, BI dashboards, and governed access with warehouses. Use notebooks for exploratory analysis, complex ETL/ML, and mixed-language workflows. Use DLT when you want declarative pipelines with built-in expectations, automatic orchestration, lineage, and simpler operations for medallion flows.
- Unity Catalog (UC): UC introduces a centralized metastore with catalog.schema.table namespaces and unified access controls across all workspaces. It standardizes permissions, lineage, auditing, and cross-workspace data sharing while managing external locations for storage. It also supports row/column masking policies and simplifies least-privilege access at scale.
- Mounts vs direct cloud paths: Mounts (dbfs:/mnt/…) make paths simple but can couple auth to the workspace and complicate multi-env promotion. Direct cloud URIs (abfss/s3/gs) with UC external locations decouple auth, ease cross-env portability, and are preferred for production. Mounts can still be fine for dev-only scenarios.

Apache Spark fundamentals and performance
- Narrow vs wide transformations: Narrow transformations (map, filter, withColumn) operate within a partition; wide transformations (groupBy, join, distinct) trigger shuffles across the network. Shuffles are expensive due to disk I/O and network, so design pipelines to reduce them. Push filters and column selection early and avoid unnecessary wide ops.
- Reducing shuffle cost: Prune columns early, filter input, and pre-aggregate where possible. Use broadcast joins for small dimension tables, adjust partitions sensibly, and handle skew (salting, skew hints, or partial aggregations). Partition pruning, bucketing, and clustering can further reduce data movement.
- Join strategies and skew handling: Broadcast the smaller side (below autoBroadcastJoinThreshold or with a broadcast hint) to avoid shuffle joins. For large-large joins, sort-merge is typical; ensure join keys are clean and well-distributed. Skew can be mitigated by salting keys, using skew join hints, or aggregating before joining.
- spark.sql.shuffle.partitions: Set partitions based on data size and cluster cores (as a guideline, 2–4× total executors’ cores). Too high causes overhead; too low creates big partitions and spill/stragglers. AQE can coalesce partitions at runtime—keep it enabled.
- Repartition vs coalesce: repartition(n) increases or decreases partitions with a shuffle and balances data; use for wide downstream ops. coalesce(n) only reduces partitions without a shuffle; it’s faster but can create skewed large partitions. Prefer repartition before wide transformations or significant writes.
- Cache/persist use: Cache data that is reused multiple times and expensive to recompute; persist with the right storage level if you need disk or serialization. Always unpersist when done to free memory. Don’t cache massive datasets you only use once; consider checkpointing for repeated lineage truncation.
- Adaptive Query Execution (AQE): AQE dynamically changes plans at runtime—coalesces shuffle partitions, switches join strategies (e.g., to broadcast), and handles skew. This reduces manual tuning and helps with variable data sizes. Keep it on unless you have a specific regression to troubleshoot.
- OOM/spills and fixes: Out-of-memory often comes from skewed shuffles, exploding joins, or overly large partitions. Fix by filtering earlier, properly partitioning, broadcasting small tables, increasing executor memory, or adjusting shuffle partitions. Monitor Spark UI for spilled bytes, skewed tasks, and long stages.
- Pandas UDFs and Arrow: Pandas UDFs use Apache Arrow for vectorized data transfer between Spark and Python, improving performance over standard UDFs. Use them for operations not expressible in SQL/DataFrames; prefer native Spark functions first for optimization and pushdown. Watch memory per batch and avoid excessive serialization.
- Bucketing vs partitioning: Partitioning splits data into directories by partition column, enabling pruning for common filters but can hurt if cardinality is high. Bucketing hashes by a column into fixed buckets, speeding up joins/aggregations on that key but requires writing with the same bucket spec. Delta’s liquid clustering or Z-ORDER can be more flexible for read performance without rigid constraints.
- Cluster sizing: Size to match data volume and SLA. Keep tasks per core reasonable (1 per core), ensure drivers have enough memory for metadata/shuffle planning, and set autoscaling with sensible min/max. For streaming, allocate enough steady-state resources to handle peaks and avoid long backlogs.
- Jobs, stages, tasks and Spark UI: A job is triggered by an action, stages are separated by shuffles, and tasks run per partition. Use the UI to spot long-running tasks, skew, spilled/shuffled data, and inefficient joins. The DAG and SQL tab show where to optimize predicates, joins, and partitioning.

Delta Lake essentials
- Core features: Delta adds ACID transactions, schema enforcement/evolution, time travel, and efficient upserts to parquet, making production pipelines reliable. It maintains a transaction log and checkpoints for consistent reads/writes. These features simplify CDC, backfills, and rollback.
- MERGE INTO patterns: Use MERGE to upsert or implement SCD2 by matching on business keys; update when matched, insert when not matched. Filter source to latest row per key (using row_number over event time) before merging to avoid duplicates. Partition/cluster target on join/filter columns and broadcast small source sides to speed merges.
- Change Data Feed (CDF): CDF emits row-level changes since version/time with change_type (insert/update/delete), enabling downstream syncs without full scans. It’s useful for pushing changes to warehouses or microservices. Keep retention and versioning aligned with consumer SLAs.
- OPTIMIZE and compaction: OPTIMIZE consolidates many small files into larger ones (~128–512MB), improving scan and shuffle efficiency. Schedule compaction for heavy-write bronze/silver tables and after large merges. Combine with VACUUM to clean up obsolete files safely.
- Z-ORDER vs liquid clustering: Z-ORDER co-locates data by columns to improve pruning on multi-dimensional filters; good for static clustering. Liquid clustering automates maintenance and adapts over time without rigid partitions; better for evolving workloads and high-cardinality columns. Choose based on query patterns and write rates.
- VACUUM and retention: VACUUM deletes older files no longer referenced by the Delta log after retention (default 7 days). Lowering retention risks breaking time travel and downstream readers; only do it with backups and clear SLAs. Keep dataRetentionDurationCheck enabled in production unless you fully understand the risks.
- Generated columns, constraints, expectations: Generated columns derive values (e.g., date from timestamp) to simplify partitioning and queries. Constraints and DLT expectations enforce data quality, failing or quarantining bad records early. This improves trust in silver/gold layers.
- Delta log internals: Each commit writes JSON actions (add/remove files, metadata), and periodic Parquet checkpoints speed up table state reconstruction. Readers reconstruct table state from checkpoints + recent JSON. Understanding this helps with debugging and recovery.
- Handling schema drift: Allow controlled schema evolution (additive columns) and quarantine unexpected changes. Use evolve policies in Auto Loader or MERGE with explicit column allowlists. Communicate schema changes with downstream consumers and update contracts.
- Rollbacks and recovery: Use time travel (VERSION AS OF/TIMESTAMP AS OF) or RESTORE TABLE to revert to a known good version. If bad writes occurred, restore and re-run idempotent pipelines. Keep backups/snapshots for disaster recovery beyond retention windows.

Streaming, Auto Loader, and DLT
- Micro-batch vs continuous: Micro-batch is the default and reliable, with processingTime, once, or availableNow triggers for latency vs cost trade-offs. Continuous processing targets sub-second latency but supports fewer sinks and ops. Choose micro-batch unless you need very low latency and accept constraints.
- Checkpointing and exactly-once: Checkpoints record offsets, progress, and state so a stream resumes correctly. Pair with idempotent sinks (Delta MERGE or dedup on unique keys) to achieve exactly-once semantics end-to-end. Store checkpoints in reliable, isolated paths per stream.
- Watermarks and late data: Watermarks establish how long to wait for late events; after the watermark, very late records are dropped to control state size. Use event-time windows to aggregate correctly; set watermark conservatively based on data arrival variance. Monitor dropped-late metrics to tune.
- Auto Loader vs COPY INTO vs custom: Auto Loader scales file discovery (notifications/listing) and handles schema inference/evolution—best for ongoing ingestion from cloud storage. COPY INTO is simple for batch loads or one-time backfills. Custom connectors are for sources like Kafka/MSK/Kinesis or REST APIs where Auto Loader doesn’t apply.
- Auto Loader schema evolution: Use cloudFiles.schemaLocation and set schemaEvolutionMode to addNewColumns; direct unexpected types to quarantine. Control column naming and types to avoid silent drift. Reconcile new columns in silver with defaulting and documentation.
- Deduplication in streaming: Use key + event time with a watermark and window/row_number to keep latest record. Alternatively, write to Delta and MERGE into silver with dedup logic for idempotency. Keep the dedup state bounded and monitor state store size.
- Bronze to silver design: Bronze is append-only raw with minimal transformations; silver cleans, casts, dedups, and enforces quality; gold aggregates for BI. Make silver/gold idempotent so replays/backfills are safe. Use CDF for incremental downstream consumption.
- DLT advantages: DLT defines pipelines declaratively with expectations (drop/warn/fail), lineage, and built-in orchestration and recovery. It simplifies stream/batch unification and manages dependencies. Great for standardized medallion pipelines and governed teams.
- Backfills and replay: Use trigger-availableNow or trigger-once with bounded inputs; clone or parameterize checkpoints for backfills to avoid corrupting main streams. Re-run silver/gold idempotently for specific date ranges. Document replay procedures to meet audit requirements.
- Common streaming failures: Checkpoint corruption (restore/clone), schema evolution mismatches, source permission or throttling issues, and long-running state growth. Implement alerting (lag, failure), retries, and circuit breakers. Keep dependencies (e.g., target table schema) stable or versioned.

Orchestration and Jobs
- Workflows vs external orchestrators: Databricks Workflows is native, with tasks, dependencies, retries, and alerts; great for most pipelines. Use Airflow/ADF/Step Functions if you orchestrate many non-Databricks systems or need enterprise-wide DAG visibility. Hybrid models are common: external triggers Databricks jobs via API.
- Dependencies, retries, alerts: Model DAGs with clear inputs/outputs; set retries with exponential backoff for transient failures. Configure email/webhook/on-call alerts and set SLAs on critical tasks. Use conditional tasks for success/failure branches (e.g., notify/quarantine).
- Multi-task jobs and clusters: Job clusters isolate dependencies and reduce env conflicts; they also ensure predictability. Shared clusters can help when tasks need warm cache or share libs but risk coupling and contention. Pools speed startup across both.
- Parameterization and environments: Use job parameters/widgets and UC catalog routing (e.g., catalog=dev/test/prod). Externalize config in files or secrets. Avoid hardcoding storage paths; use environment variables or workspace/context.
- Overlapping runs: For idempotent pipelines, allow multiple concurrent runs with partitioned outputs or locks. Otherwise, disallow concurrent runs to prevent data corruption. Use optimistic concurrency or transactional writes with Delta.

Security, governance, and access control
- UC namespaces and privileges: Organize data as catalog.schema.table, grant privileges to groups at the highest sensible level, and follow least privilege. Use ownership transfer carefully and avoid granting on system catalogs. Automate grants via Terraform/CLI for consistency.
- Row/column security: Implement row filters with dynamic views (e.g., filter on current_user’s entitlements) and column masking policies for sensitive fields. Centralize policies in UC so they apply across workspaces. Test performance and caching behavior for secure views.
- External locations and managed vs external tables: External locations map cloud storage paths + credentials, controlled by UC. Managed tables are stored in UC-managed locations; external tables live in your buckets/containers. Use external for cross-system access or data residency needs; managed for simplicity.
- Secrets: Store creds in secret scopes backed by Key Vault/KMS and reference them in configs; never embed secrets in notebooks. Rotate regularly and audit access. Prefer identity-based access (instance profiles/managed identities) over static keys where possible.
- Credentials and access modes: Use credential passthrough for interactive access with user identity; use instance profiles/managed identities/service accounts for jobs. Enforce single access mode (UC-enabled) clusters for consistent governance. Minimize role sprawl and use group-based grants.
- Private networking: Deploy with Private Link or secure cluster connectivity, without public IPs, and restrict egress to storage endpoints. Ensure DNS resolution for private endpoints. Validate firewall rules for artifact repos, logging, and metastore connectivity.
- Audit and lineage: Use UC lineage and system tables for who accessed what, when, and how. Stream audit logs to SIEM for monitoring and compliance. Tie lineage to change management and incident response.
- Masking/tokenization: Use irreversible hashing for analytics where joins on raw values aren’t needed; use reversible tokenization with a vault if recoverability is required. Combine with column policies in UC to enforce at query time.

DevOps, CI/CD, and testing
- Git and branch strategy: Use Databricks Repos integrated with Git; adopt PR reviews and automated checks. Trunk-based development with short-lived branches works well if CI is strong; otherwise, feature branches. Pin library versions to avoid runtime drift.
- Infrastructure as code: Provision workspaces, UC objects, clusters, jobs, and permissions with Terraform (Databricks provider) for reproducibility. Parameterize per environment and keep state secure. Review changes via PRs.
- Deployments and tooling: Use Databricks CLI/REST or bundle tooling to deploy jobs, notebooks, DLT pipelines, and permissions. Separate build (package wheels) from deploy (attach to clusters/jobs). Keep environment configs outside code.
- Promotion across envs: Isolate with UC catalogs (dev/test/prod) and external locations per env. Promote data via Delta sharing or DLT materialization, and code via Git tags/releases. Avoid mounts; prefer direct cloud URIs with UC governance.
- Testing strategy: Write unit tests for PySpark with pytest and Spark local; add SQL unit tests for views/procs. For integration, use synthetic data or lakeFS/Delta clones; validate expectations and SLAs. Include performance and cost regression checks for critical queries.
- Observability: Monitor job outcomes, runtime, shuffle/spill metrics, and cost with system tables and cluster logs. Set alerts on failure, lag, and cost anomalies. Create SLO dashboards for critical pipelines.

SQL and data modeling
- Modeling approaches: Star schemas are best for BI simplicity and performance with clear facts/dimensions. Data Vault emphasizes agility and auditability over strict performance; good for complex, changing domains. Wide tables can serve ML/features or simple ELT but may sacrifice governance and reuse.
- Window functions: Use row_number/dense_rank/lag/lead for deduplication, top-N, and change detection. Example: dedup by selecting rn=1 over partition by key ordered by event_time desc. They are essential for SCD logic and time-based analytics.
- SCD Type 2 in Delta: Implement with MERGE by matching on business key; when matched and changes detected, expire current row (end_date, is_current=false) and insert a new row (start_date, is_current=true). Maintain unique constraints logically via merge conditions and dedup sources. Z-ORDER or liquid clustering on business keys can help.
- Dimensions vs facts: Keep facts immutable and additive; update dimensions as SCDs to track history. Use snapshot facts for periodic status if needed. Generate surrogate keys for joins and keep natural keys for business traceability.
- Data quality KPIs: Track schema conformance, null/validity rates, dedup count, referential integrity, and freshness. Enforce via DLT expectations or SQL constraints and persist metrics in gold for monitoring. Alert on breaches.
- BI performance in DBSQL: Optimize Delta tables (compaction), cluster on common filters, and select only needed columns. Right-size warehouses, enable serverless or Photon, and leverage result/query caching for repeated dashboards. Precompute heavy aggregations as materialized views or gold tables.
- Materialized views and DLT: Use MVs or streaming live tables to precompute expensive queries with freshness SLAs. DLT ensures orchestration, quality, and lineage, simplifying maintenance. Choose based on update cadence and governance needs.

Cloud-specific notes
- Azure: Use ADLS Gen2 (abfss) with managed identities or service principals; enable AAD passthrough for interactive users. VNet injection and Private Link secure access; ensure Key Vault for secrets. Watch RBAC + ACL combinations on storage.
- AWS: Use S3 with instance profiles or assume-role for cross-account; prefer PrivateLink and no-public-IP workspaces. For streaming, integrate with Kinesis/MSK; watch IAM policy size and STS session durations. Use S3 requester-pays and multipart uploads for large writes.
- GCP: Use GCS with service accounts/impersonation; consider VPC Service Controls for data exfiltration protection. Pub/Sub streams integrate well with Structured Streaming. Watch token lifetimes and HMAC setup when needed.
- Storage performance: Aim for fewer, larger files (128–512MB), parallel I/O, and avoid excessive small files by batching writes and using OPTIMIZE. Tune parallelism based on throughput limits. Consider file notification mode for Auto Loader at scale.
- Networking gotchas: Ensure DNS for private endpoints, allowlist artifact repos, and avoid unintended egress paths. Validate credential lifetimes for cloud APIs (tokens/roles). Test cross-region latency if applicable.

Cost, reliability, and monitoring
- Cost reduction: Use Photon, autoscaling with sensible mins, spot/preemptible nodes where safe, and cluster pools. Compact files, prune early, and broadcast joins to reduce compute. Right-size SQL warehouses and pause idle ones; consider serverless if available.
- Small-file management: Ingest with Auto Loader batching, write with larger batch sizes, and run OPTIMIZE regularly. Avoid writing per-record outputs; combine micro-batches. For merge-heavy tables, compact after large upserts.
- SLAs and backpressure: Design for peak loads with buffers; control source ingestion rates and monitor streaming lag. Retry transient failures and build idempotent operations to allow safe reruns. Use dead-letter queues or quarantine tables for bad records.
- System tables and tagging: Use system tables for job usage, query history, and cost visibility. Tag jobs/clusters with cost centers and owners for chargeback. Regularly review idle/over-provisioned resources.
- SQL Warehouses vs Jobs clusters: Warehouses are optimized for interactive/concurrent SQL; Jobs clusters are better for long ETL/ML runs. Choose based on query patterns and concurrency needs. Consolidate workloads thoughtfully to avoid contention.

Troubleshooting scenarios
- Streaming stuck: Check the streaming UI for last progress, input rate, and state ops; verify source availability and checkpoint health. If the checkpoint is corrupted, stop the job, back it up, and restart from a cloned or cleaned checkpoint if the sink is idempotent. Review watermarks/windows and target table locks.
- Duplicates in silver: Trace lineage from bronze and confirm dedup logic keys and event-time ordering. Implement window-based dedup or MERGE with unique keys; ensure idempotent writes and deterministic ordering. Lock down multi-writer scenarios or use transactional MERGE into Delta.
- Slow MERGE: Ensure join predicates are selective and align with partitioning/clustering; pre-filter source to latest per key. OPTIMIZE target to reduce small files, Z-ORDER/liquid cluster on join keys, and broadcast the small side. Increase shuffle parallelism or handle skew with salting.
- Performance regressed after schema evolution: New columns can reduce pruning or change file layout; re-OPTIMIZE and update clustering. Validate that readers select only needed columns and that stats are refreshed. Check that downstream code handles defaults and types correctly.
- UC visibility issues: Confirm the correct metastore binding, current catalog, and user/group grants at catalog/schema/table levels. Verify ownership and inheritance; check if the table is view-governed or masked. Use SHOW GRANTS and lineage to diagnose.
- VACUUM deleted needed files: If time travel is broken, restore from backups/snapshots or DR copies. Increase retention and re-enable safety checks; communicate SLAs for time travel. Implement policies around VACUUM scheduling and dependencies.
- Skewed key causing stragglers: Identify skew via Spark UI stage/task times and distribution. Apply key salting, skew join optimizations, or pre-aggregation; increase parallelism cautiously. Sometimes rekeying or windowing by time helps distribute load.
- Cloud storage permission mismatch: Interactive notebooks may use user creds, while jobs use service principals/roles—permissions can differ. Align IAM/RBAC and ensure correct role assumption and external locations. Test both paths explicitly.
- Slow SQL dashboard: Scale/auto-scale the warehouse, enable Photon, and ensure result/query caching is effective. Optimize/compact source tables and cluster on filter columns; reduce data scanned with selective queries. Review the query plan for broadcast opportunities and unnecessary cross joins.
- Corrupt checkpoint recovery: Stop the stream, copy the checkpoint aside, and restart from a clean checkpoint or previous table version if your sink is idempotent. For stateful ops, consider replaying with a bounded range (availableNow) to rebuild state. Harden pipelines to avoid mixed code/logic changes mid-stream.

Be ready to do small tasks live
- Auto Loader JSON to Delta with schema drift:
  - Read: spark.readStream.format("cloudFiles").option("cloudFiles.format","json").option("cloudFiles.schemaLocation","/chk/schema/myfeed").load("/raw/myfeed")
  - Write: .writeStream.format("delta").option("checkpointLocation","/chk/bronze/myfeed").outputMode("append").toTable("bronze.myfeed")
  - Enable evolution: set cloudFiles.schemaEvolutionMode="addNewColumns"; quarantine unexpected types; promote to silver with casting and dedup.
- CDC MERGE with dedup:
  - Stage latest per key: SELECT key, … FROM (SELECT *, row_number() over (partition by key order by event_time desc) rn FROM source) WHERE rn=1
  - MERGE INTO target USING staged_source ON target.key = staged_source.key WHEN MATCHED THEN UPDATE SET … WHEN NOT MATCHED THEN INSERT …
  - Partition/cluster target on key or date; broadcast staged_source if small; run OPTIMIZE after heavy merges.
- Tune a join with broadcast:
  - If dim is small: SELECT /*+ BROADCAST(dim) */ … FROM fact JOIN dim USING (key)
  - Confirm in EXPLAIN that a BroadcastHashJoin is used and shuffles are reduced. Monitor shuffle read/write in the UI.
- Window-based dedup SQL:
  - SELECT * FROM (SELECT t.*, row_number() over (partition by business_key order by event_time desc) rn FROM t) WHERE rn=1

If you share their cloud (AWS/Azure/GCP), whether they use Unity Catalog or DLT, and your target seniority, I can tailor this to the most likely deep-dive areas and provide a one-page cram sheet.