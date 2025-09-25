## Interview sample 1

Here’s a focused list of likely interview questions based on the role and context (migrating a home‑brew Postgres setup to Databricks on AWS, being the sole Data Engineer, end‑to‑end ownership).

Migration and architecture
- Walk us through how you’d design and phase a migration from Postgres to a Databricks lakehouse on AWS.
- How would you choose between batch backfill vs CDC for this migration? What tooling would you consider (e.g., AWS DMS, Debezium/MSK, Kinesis)?
- Propose a medallion (bronze/silver/gold) layout for our datasets and how you’d structure catalogs/schemas in Unity Catalog.
- How would you ensure functional parity when rewriting Go-based transformation logic into PySpark/SQL/Java? How do you validate it?
- What’s your approach to schema evolution and data contracts during migration?
- How do you plan a safe cutover, rollback, and backfill strategy?
- How would you handle idempotency, deduplication, and late-arriving data?
- What minimal viable architecture would you suggest for a 10-person startup to keep complexity and cost down?

Databricks and Spark
- Explain when and why you use DataFrames vs SQL vs UDFs vs Pandas UDFs.
- How do you handle skewed joins and large shuffles? (e.g., salting, broadcast, AQE, bloom filters)
- What is your partitioning strategy for Delta tables? How do you mitigate small files?
- Describe Delta Lake features you’ve used (MERGE INTO, time travel, change data feed, constraints, VACUUM).
- Structured Streaming: checkpointing, watermarks, stateful aggregations, and exactly-once semantics—how do you design for these?
- How do you choose cluster types/configs (job vs all-purpose, autoscaling, Photon, instance pools, spot)?
- How do you use Databricks Workflows vs Jobs vs external orchestrators?
- Unity Catalog: managed vs external locations, permissions model, volumes—how would you set it up securely?
- How do you profile and debug a slow Spark job (explain plan, stage metrics, skew, spill)?
- Notebooks vs repos/packages—how do you organize code for maintainability?

AWS (data platform on AWS)
- How would you set up S3 for a lakehouse (naming, prefixes, encryption SSE-KMS, bucket policies, lifecycle, object ownership)?
- IAM design for Databricks (instance profiles/role assumption, least privilege, credential passthrough).
- Networking considerations (VPC, PrivateLink/VPC endpoints for S3, egress control).
- Glue Catalog vs Unity Catalog—how do they compare and when to use each?
- What ingestion options would you consider (DMS, MSK/Kinesis, batch with Auto Loader) and trade-offs?
- How do you monitor and alert on jobs, costs, and data quality using CloudWatch/Databricks metrics?
- How do you control and tag costs across environments and teams?

SQL and data modeling
- Write or explain a SQL query using window functions (e.g., latest record per entity, sessionization).
- How would you implement SCD Type 2 in Delta with MERGE and handle late updates/deletes?
- Star schema vs wide tables in a lakehouse—when do you choose either? Any experience with Data Vault?
- How do you design for time-travel, slowly changing dimensions, and reproducibility?
- How do you optimize queries in Databricks SQL (materialized views, caching, indexes like Z-ORDER/Liquid Clustering)?

Orchestration, CI/CD, Terraform, and Git
- How would you manage Databricks resources with Terraform (workspaces, clusters, UC objects, jobs, secret scopes)?
- Describe your CI/CD setup for PySpark/SQL pipelines (tests, packaging, databricks-cli/dbx, GitHub Actions).
- How do you version-control notebooks and manage dependencies (repos, wheels, lockfiles)?
- Secrets management: Databricks secrets vs AWS Secrets Manager/KMS—what’s your approach?
- Deployment strategy across dev/test/prod (workspaces, catalog per env, Terraform workspaces, role assumptions).
- How do you design job dependencies, retries, SLAs, and failure notifications?

Data quality, testing, and observability
- How do you test data pipelines (unit tests for UDFs, PySpark tests, data validation with Great Expectations/Deequ)?
- What checks do you implement for data contracts (schema, nullability, ranges, referential integrity)?
- How do you reconcile and verify migrated datasets (row counts, checksums, sample diffs, invariants)?
- How do you implement lineage and documentation (Unity Catalog lineage, OpenLineage, ADRs)?
- How do you handle PII (masking, tokenization, row/column-level security, GDPR/retention)?

Performance and cost optimization
- What are your best practices to control Databricks costs (cluster sizing, instance pools, spot, Photon, caching)?
- Techniques to avoid small files and optimize Delta tables (OPTIMIZE, auto-compaction, target file sizes).
- How do you decide when to cache vs materialize a gold table?
- How do you use AQE, dynamic partition pruning, and broadcast joins to speed up queries?
- Storage vs compute trade-offs in Delta (vacuum retention, CDF overhead, Z-ORDER vs Liquid Clustering).

Working as the sole Data Engineer
- Tell us about an end-to-end data platform you built and the decisions you owned.
- How do you operate as the only DE—setting standards, prioritizing, and collaborating with SWE/DS?
- Describe a time you made an architectural decision with incomplete information. What trade-offs did you make?
- How do you communicate complex data topics to non-data stakeholders and get buy-in?
- A production incident you led—what happened, your diagnosis, and prevention measures.
- How do you balance speed vs correctness vs cost in a startup?

Language and collaboration
- Explain a recent data migration you led in English; how would you present it to execs vs engineers?
- How do you approach async work and documentation in a remote/hybrid setup?
- Example of cross-team collaboration friction and how you resolved it.

Go and cross-language migration (nice to have)
- Have you read or written Go? How would you translate Go data transformation logic into PySpark/SQL and validate it?
- Any pitfalls when mapping Go types/time handling to Spark/Delta?

Practical/whiteboard-style exercises you might face
- Write a MERGE INTO statement to apply CDC (insert/update/delete) to a Delta table with audit columns.
- Given two large tables with skew on a key, show a Spark approach to join them efficiently.
- Implement a Structured Streaming job with watermarking and deduplication by a composite key.
- Design a Terraform snippet to provision a Databricks job cluster with an instance profile and a job.
- Optimize a slow query on a partitioned Delta table; describe steps and metrics you’d check.
- Draft a cutover plan for moving a critical dataset from Postgres to Delta with rollback and validation steps.



## Below are concise, plain-language answers to the earlier questions.

Migration and architecture
- Q: How would you design and phase a migration from Postgres to a Databricks lakehouse on AWS?
  A: Stand up S3 + Delta + Unity Catalog, backfill historical data, then stream changes (CDC). Run old and new in parallel, validate, cut over consumers, and keep a rollback snapshot.

- Q: Batch backfill vs CDC—what and why?
  A: Do a one-time batch backfill for history, then CDC for ongoing changes to avoid reloading everything. Use AWS DMS or Debezium for CDC.

- Q: Medallion layout and catalog structure?
  A: Bronze = raw, Silver = cleaned/conformed, Gold = analytics. Unity Catalog: catalog per environment, schemas per domain, clear naming and permissions.

- Q: Ensure parity when rewriting Go logic to PySpark/SQL/Java?
  A: Create golden input/outputs, write unit tests, and diff results (counts, checksums, spot checks). Run both pipelines in parallel until the results match.

- Q: Schema evolution and data contracts?
  A: Define schemas in code, allow additive changes, block breaking changes. Use Delta constraints and versioned contracts.

- Q: Cutover, rollback, and backfill strategy?
  A: Shadow run, validate, snapshot at T0, cut traffic, monitor. Roll back via Delta time travel/snapshots; rerun backfills by partition if needed.

- Q: Idempotency, dedup, late data?
  A: Use deterministic keys and MERGE for upserts, watermarks + dedup for streams, and partition overwrite for reprocessing.

- Q: Minimal viable architecture for a startup?
  A: Databricks + S3 + Unity Catalog, Auto Loader/DMS for ingest, Workflows for orchestration, CloudWatch/DB audit logs for monitoring. Keep few clusters and simple IAM.

Databricks and Spark
- Q: DataFrames vs SQL vs UDFs vs Pandas UDFs?
  A: Prefer SQL/DataFrames for optimizer benefits. Use UDFs only when built-ins can’t; Pandas UDFs for vectorized custom logic.

- Q: Handle skewed joins and shuffles?
  A: Broadcast small tables, enable AQE skew join, salt keys, use bloom filters, and repartition appropriately.

- Q: Partitioning and small files?
  A: Partition by low-cardinality, commonly filtered columns (often date). Use Auto Optimize/compaction, OPTIMIZE, and target file sizes.

- Q: Delta features you use?
  A: MERGE INTO for upserts, time travel for debugging, CDF for downstream CDC, constraints for quality, VACUUM/OPTIMIZE for maintenance.

- Q: Structured Streaming design (checkpointing, watermarks, exactly-once)?
  A: Use Delta sink with checkpoints for exactly-once, set watermarks for late data, and manage state via TTL.

- Q: Cluster choices?
  A: Job clusters for prod, all-purpose for dev. Autoscale with instance pools, Photon for ETL/SQL, spot where safe with on-demand fallback.

- Q: Workflows vs Jobs vs external orchestrators?
  A: Start with Databricks Workflows/Jobs. Use an external orchestrator only if you have many non-DB dependencies.

- Q: Unity Catalog secure setup?
  A: Managed/external locations with KMS, least-privilege grants via groups, volumes for files, and enable lineage.

- Q: Profiling/debugging slow Spark jobs?
  A: Check explain plan and stage metrics, look for skew and spill, reduce shuffles, tune partitions, and broadcast small joins.

- Q: Notebooks vs repos/packages?
  A: Prototype in notebooks; productionize as repos/wheels. Keep configs separate and test in CI.

AWS (data platform on AWS)
- Q: S3 setup for a lakehouse?
  A: Bucket per env, clear prefixes, SSE-KMS, block public access, versioning, lifecycle rules, and bucket-owner enforced.

- Q: IAM for Databricks?
  A: Use instance profiles or role assumption with least-privilege S3 policies. Enable credential passthrough when needed.

- Q: Networking?
  A: VPC with VPC endpoints/PrivateLink for S3 and services, security groups locked down, and egress control.

- Q: Glue Catalog vs Unity Catalog?
  A: Prefer Unity for Databricks governance. Use Glue when sharing with AWS-native tools; avoid dual sources of truth.

- Q: Ingestion options and trade-offs?
  A: DMS/Debezium for CDC, Auto Loader for files, Kinesis/MSK for streams. Choose by latency needs and ops overhead.

- Q: Monitoring and alerts?
  A: Databricks job/audit logs to CloudWatch, alerts for failures/lag/cost. Simple dashboards in Databricks SQL.

- Q: Cost controls and tags?
  A: Tag resources, use budgets/alerts, cluster policies, auto-termination, instance pools, and spot instances.

SQL and data modeling
- Q: Window function example?
  A: Use row_number() over (partition by key order by ts desc) and pick rn = 1 to get the latest record.

- Q: SCD Type 2 in Delta?
  A: MERGE on business key: expire current row (set valid_to) and insert a new row with updated values. Handle late data with timestamp conditions.

- Q: Star schema vs wide tables (and Data Vault)?
  A: Star for BI flexibility and joins; wide for simple serving/ML. Use Data Vault for raw, auditable ingestion; present as star.

- Q: Time-travel, SCD, reproducibility?
  A: Use Delta versioning/time travel, partition by date, keep code/config in git, and use deterministic inputs.

- Q: Optimize Databricks SQL?
  A: Cache hot data, materialize aggregates, prune partitions, and use Z-ORDER or Liquid Clustering plus Photon.

Orchestration, CI/CD, Terraform, and Git
- Q: Manage Databricks with Terraform?
  A: Define catalogs, schemas, grants, clusters, jobs, secret scopes, instance profiles in code with modules.

- Q: CI/CD for PySpark/SQL?
  A: Unit/integration tests, build a wheel, run smoke tests on sample data, deploy with dbx/CLI via GitHub Actions.

- Q: Version notebooks and dependencies?
  A: Store notebooks in repos, package shared code, lock dependencies, and pin runtime versions.

- Q: Secrets management?
  A: Keep secrets in AWS Secrets Manager/KMS and reference via Databricks secret scopes. Never hardcode.

- Q: Deploy across dev/test/prod?
  A: Separate catalogs/workspaces, Terraform workspaces/vars, role assumption, and promote code/data through stages.

- Q: Job deps, retries, SLAs?
  A: Model DAGs in Workflows, set retries/backoff/timeouts, and alert to Slack/Email. Track SLAs with simple metrics.

Data quality, testing, and observability
- Q: How do you test pipelines?
  A: Pytest unit tests, PySpark integration tests on small data, and data validation (Great Expectations/Deequ) in silver.

- Q: Data contract checks?
  A: Enforce schema, nullability, ranges, enums, and referential integrity. Quarantine or fail bad records.

- Q: Verify migrated datasets?
  A: Compare counts and checksums by partition, sample diffs on keys, and parallel-run for a period.

- Q: Lineage and docs?
  A: Use Unity Catalog lineage and table comments, generate lightweight docs, and record ADRs for key decisions.

- Q: Handle PII?
  A: Minimize collection, encrypt everywhere, mask/tokenize in non-prod, and apply column/row-level security and retention.

Performance and cost optimization
- Q: Control Databricks costs?
  A: Right-size and autoscale clusters, use pools and spot, auto-terminate, and monitor for idle/failed runs.

- Q: Avoid small files and optimize Delta?
  A: Batch writes to target size, Auto Optimize/compaction, scheduled OPTIMIZE and VACUUM.

- Q: Cache vs materialize?
  A: Cache within a job for repeated reads; materialize gold tables reused across jobs/users.

- Q: Speed up queries?
  A: Enable AQE, broadcast small joins, dynamic partition pruning, prune partitions, and use Photon.

- Q: Storage vs compute trade-offs in Delta?
  A: Keep reasonable VACUUM retention, enable CDF selectively, and use Z-ORDER or Liquid Clustering based on query patterns.

Working as the sole Data Engineer
- Q: End-to-end platform you built?
  A: I set up ingestion, bronze/silver/gold, orchestration, monitoring, and governance, then delivered BI/ML-ready gold tables.

- Q: Operating as the only DE?
  A: Keep standards simple, prioritize a clear backlog, pair with SWE/DS, and automate repetitive work.

- Q: Decision with incomplete info?
  A: Choose the simplest reversible option, document assumptions, measure impact, and iterate quickly.

- Q: Communicating complex topics?
  A: Use simple diagrams and metrics, focus on outcomes for execs, dive into details for engineers.

- Q: Production incident example?
  A: A job lagged due to skew; I identified hot keys, added salting/broadcast, reprocessed backlog, and added monitoring to prevent repeats.

- Q: Balancing speed, correctness, cost?
  A: Ship the smallest useful slice with basic tests, add rigor as usage grows, and watch cost metrics.

Language and collaboration
- Q: Present migration in English to execs vs engineers?
  A: Execs: business impact, timeline, risks. Engineers: architecture, data flows, SLAs, and testing plan.

- Q: Async work and documentation?
  A: Default to written ADRs, design docs, and clear tickets/PRs. Maintain runbooks and regular status updates.

- Q: Handle cross-team friction?
  A: Clarify goals and constraints, agree on a small experiment or SLA, and communicate openly.

Go and cross-language migration
- Q: Translate Go logic to PySpark/SQL and validate?
  A: Map to DataFrame/SQL first, use UDFs only if needed. Build test cases from Go outputs to confirm parity.

- Q: Pitfalls with Go types/time to Spark/Delta?
  A: Time zones and zero times, numeric precision, and Go zero-values vs Spark nulls.

Practical/whiteboard exercises
- Q: MERGE INTO for CDC with audit columns?
  A: Stage CDC data with op codes; MERGE ON keys with WHEN MATCHED AND op='D' THEN DELETE, WHEN MATCHED THEN UPDATE (set cols, updated_at), WHEN NOT MATCHED THEN INSERT (with created_at/updated_at).

- Q: Join two large tables with skewed key?
  A: Broadcast the smaller table, use salting on the skewed key, enable AQE skew join, and prune columns before join.

- Q: Structured Streaming with watermark and dedup?
  A: Read stream, withWatermark on event time, dropDuplicates on key+event_time, write to Delta with checkpointing.

- Q: Terraform to provision job cluster and job?
  A: Define databricks_cluster (with instance pool/profile) and databricks_job resources; keep configs in variables and modules.

- Q: Optimize a slow query on a partitioned Delta table?
  A: Ensure partition filters are used, prune columns, Z-ORDER/Liquid Cluster on filter columns, reduce shuffles, and consider Photon.

- Q: Cutover plan from Postgres to Delta with rollback?
  A: Backfill, enable CDC, parallel-run and validate, snapshot at T0, cut consumers, monitor, and if issues arise, roll back to the snapshot/time travel.