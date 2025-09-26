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
  A: Stand up S3 + Delta Lake + Unity Catalog and define domains, schemas, and governance. Do a full historical backfill into bronze, then keep it in sync via CDC into silver/gold. Run both platforms in parallel for a period, validate outputs, then cut over consumers with a rollback snapshot ready.

- Q: Batch backfill vs CDC—what and why?
  A: Use a one-time batch backfill to move history quickly and cheaply. Then switch to CDC (e.g., DMS/Debezium) to capture ongoing changes with low latency. This avoids reprocessing full tables and minimizes risk during cutover.

- Q: Medallion layout and catalog structure?
  A: Bronze holds raw, append-only data; Silver is cleaned, deduped, and conformed; Gold is business-ready with aggregates and serving views. Use a catalog per environment (dev/test/prod) and schemas per domain (e.g., sales, marketing) with least-privilege access. Keep naming consistent and document table purposes.

- Q: Ensure parity when rewriting Go logic to PySpark/SQL/Java?
  A: Create test fixtures from the current system and compare outputs for the same inputs. Add unit tests for tricky business rules and use checksums/row-count checks by partition. Run both pipelines in parallel until metrics and samples match consistently.

- Q: Schema evolution and data contracts?
  A: Version schemas and communicate changes before deployment. Allow additive changes by default; block breaking changes with constraints and CI checks. Use Delta’s schema enforcement/evolution and document rules in contracts the producers agree to.

- Q: Cutover, rollback, and backfill strategy?
  A: Do parallel runs, then pick a cutover time when both sides are in sync and validated. Keep a point-in-time snapshot and use Delta time travel for quick rollback. Partitioned backfills let you fix specific dates without reprocessing everything.

- Q: Idempotency, dedup, late data?
  A: Use deterministic keys and MERGE for upserts so re-runs don’t create duplicates. For streams, apply withWatermark + dropDuplicates and handle late data with windowing and state TTL. For batch reprocesses, overwrite by partition and verify counts.

- Q: Minimal viable architecture for a startup?
  A: Keep it simple: Databricks Workflows, one or two shared job clusters with autoscaling, S3 with KMS, and Unity Catalog for governance. Ingest with Auto Loader and DMS; basic monitoring via job alerts and CloudWatch logs. Avoid heavy external tooling until there’s a clear need.

Databricks and Spark
- Q: DataFrames vs SQL vs UDFs vs Pandas UDFs?
  A: Prefer SQL or DataFrames because Catalyst can optimize them well. Use UDFs only when built-ins can’t express the logic; Pandas UDFs are good for vectorized custom operations. Keep UDFs pure and avoid unnecessary serialization.

- Q: Handle skewed joins and shuffles?
  A: Broadcast the small side when possible and enable AQE’s skew join handling. Salt hot keys, filter early, and reduce columns before the join. Also ensure partitioning is sensible to avoid massive shuffles.

- Q: Partitioning and small files?
  A: Partition on low-cardinality, frequently filtered columns (often event_date). Use Auto Optimize/Auto Compaction, OPTIMIZE with target file sizes, and batch writes to reduce tiny files. Review table stats periodically and adjust strategy if query patterns change.

- Q: Delta features you use?
  A: MERGE INTO for upserts and SCDs, and time travel for debugging or rollback. Change Data Feed for downstream incremental processing and constraints for quality gates. Maintain tables with OPTIMIZE/Z-ORDER (or Liquid Clustering) and VACUUM.

- Q: Structured Streaming design (checkpointing, watermarks, exactly-once)?
  A: Use Delta sink with checkpoints to achieve exactly-once semantics. Set watermarks so state doesn’t grow unbounded and handle late data gracefully. Make output idempotent and include monitoring for lag and failures.

- Q: Cluster choices?
  A: Job clusters for production jobs (clean, ephemeral), all-purpose for development and exploration. Use autoscaling with instance pools and Photon for ETL/SQL workloads; consider spot for cost savings with on-demand fallback. Keep runtimes consistent across environments.

- Q: Workflows vs Jobs vs external orchestrators?
  A: Start with Databricks Workflows/Jobs for simplicity and tight integration. Move to an external orchestrator only when you have many cross-system dependencies or complex SLAs. Keep DAGs small and observable either way.

- Q: Unity Catalog secure setup?
  A: Use managed/external locations backed by KMS, and grant permissions via groups, not users. Enable lineage and set up logical domains with clear ownership. Keep PII in separate schemas with stricter controls.

- Q: Profiling/debugging slow Spark jobs?
  A: Check the physical plan and stage metrics for skew, spill, and large shuffles. Reduce data early, broadcast when safe, and tune partitions. Use Adaptive Query Execution and optimize file layout to help the optimizer.

- Q: Notebooks vs repos/packages?
  A: Prototype in notebooks for speed, then move core logic into versioned packages. Use Repos and CI to test code, and keep configuration separate from code. Notebooks become thin orchestration or documentation layers.

AWS (data platform on AWS)
- Q: S3 setup for a lakehouse?
  A: Separate buckets (or prefixes) per environment and data layer, with clear naming. Enforce SSE-KMS, block public access, enable versioning, and lifecycle rules for logs and old files. Use bucket-owner enforced and tight bucket policies.

- Q: IAM for Databricks?
  A: Use instance profiles or role assumption for access to S3 and KMS with least-privilege policies. Prefer role-based access and group mapping over user-level permissions. Rotate credentials and avoid embedding keys anywhere.

- Q: Networking?
  A: Run in a VPC with VPC endpoints/PrivateLink for S3 and control-plane services to keep traffic private. Lock down security groups and egress; consider firewall rules for outbound control. Monitor with VPC Flow Logs for anomalies.

- Q: Glue Catalog vs Unity Catalog?
  A: Unity Catalog is best for Databricks-native governance, lineage, and cross-workspace sharing. Use Glue when integrating with AWS-native tools (Athena, EMR) or mixed engines. Avoid dual catalog sources for the same datasets to prevent drift.

- Q: Ingestion options and trade-offs?
  A: DMS or Debezium/MSK for CDC (lower latency, more ops), Auto Loader for file-based batch (simple and scalable), Kinesis/MSK for streaming events. Choose based on latency, reliability, and maintenance cost. Start simple and evolve.

- Q: Monitoring and alerts?
  A: Send Databricks job and audit logs to CloudWatch; alert on job failures, lag, and cost anomalies. Add table-level data quality checks and publish simple dashboards. Keep runbooks and on-call notifications in place.

- Q: Cost controls and tags?
  A: Tag clusters, jobs, and S3 paths by team/environment and set budgets/alerts. Enforce cluster policies, autoscaling, auto-termination, and instance pools. Use spot instances where safe and track per-job cost trends.

SQL and data modeling
- Q: Window function example?
  A: For latest record per entity, use row_number() over (partition by id order by timestamp desc) and filter rn = 1. It’s efficient and easy to reason about. Add tie-breakers to guarantee deterministic results.

- Q: SCD Type 2 in Delta?
  A: Use MERGE on the business key: when matched and changed, expire the current row (set valid_to) and insert a new row with valid_from and current flag. Handle late-arriving updates by comparing event timestamps. Keep indexes like Z-ORDER/Liquid Clustering on business keys for faster merges.

- Q: Star schema vs wide tables (and Data Vault)?
  A: Stars are great for BI and ad-hoc queries, with conformed dimensions and clear metrics. Wide tables are simpler for specific dashboards or ML features but can duplicate logic. Use Data Vault for auditable raw ingestion, then publish star/gold models.

- Q: Time-travel, SCD, reproducibility?
  A: Delta’s versioning lets you reproduce past states for audits or bug fixes. Partition by natural time and store parameters in code/config so runs are deterministic. Keep seeds and feature definitions versioned.

- Q: Optimize Databricks SQL?
  A: Prune partitions and columns, and materialize heavy aggregates used often. Use caching for short-lived reuse and Z-ORDER or Liquid Clustering to improve locality. Photon generally speeds up SQL workloads.

Orchestration, CI/CD, Terraform, and Git
- Q: Manage Databricks with Terraform?
  A: Define catalogs, schemas, permissions, clusters, jobs, secret scopes, and instance profiles as code. Use modules and workspaces for environments, and run plans in CI with approvals. Keep state secure and version every change.

- Q: CI/CD for PySpark/SQL?
  A: Run unit and integration tests on sample data, package code as wheels, and deploy via dbx/CLI. Add smoke tests post-deploy and roll back quickly if checks fail. Pin runtimes and libraries to avoid drift.

- Q: Version notebooks and dependencies?
  A: Store notebooks in Git with Repos; keep core logic in packages and only light orchestration in notebooks. Lock dependencies (requirements.txt/poetry.lock) and standardize runtimes. Use feature branches and code reviews.

- Q: Secrets management?
  A: Store secrets in AWS Secrets Manager and reference via Databricks secret scopes. Limit access by role and rotate regularly. Never print secrets in logs or notebooks.

- Q: Deploy across dev/test/prod?
  A: Separate workspaces or catalogs per environment and promote via CI using Terraform variables/workspaces. Use role assumption for cross-account access. Keep data isolation strict and promote data alongside code when needed.

- Q: Job deps, retries, SLAs?
  A: Model DAGs with clear inputs/outputs, set retries with backoff and timeouts, and alert to Slack/Email. Track SLAs (e.g., data freshness) with simple metrics and dashboards. Add circuit breakers to prevent cascading failures.

Data quality, testing, and observability
- Q: How do you test pipelines?
  A: Unit-test transformations and UDFs, then run PySpark integration tests on small representative data. Add data validation checks (Great Expectations/Deequ) at bronze→silver and silver→gold. Automate these in CI and block deploys on critical failures.

- Q: Data contract checks?
  A: Enforce schema, nullability, ranges, enums, and referential integrity where applicable. Fail fast or quarantine bad records with clear error paths. Track contract violations and notify producers.

- Q: Verify migrated datasets?
  A: Compare row counts and checksums by partition and do key-based spot diffs. Run both systems in parallel for a period and reconcile discrepancies. Document known differences and sign off with stakeholders.

- Q: Lineage and docs?
  A: Use Unity Catalog lineage and table comments to auto-capture flows and context. Maintain lightweight design docs and ADRs for key decisions. Keep a data dictionary for gold tables.

- Q: Handle PII?
  A: Minimize collection, encrypt at rest/in transit, and segregate PII in restricted schemas. Mask or tokenize in non-prod and apply column/row-level security. Enforce retention policies and audit access.

Performance and cost optimization
- Q: Control Databricks costs?
  A: Right-size clusters, enable autoscaling, and use instance pools and spot where tolerant. Auto-terminate idle clusters and clean up unused jobs/assets. Monitor spend by tag and review heavy queries.

- Q: Avoid small files and optimize Delta?
  A: Write larger batch files, enable Auto Optimize/compaction, and run scheduled OPTIMIZE with target sizes. Use VACUUM to clear old files while respecting retention. Monitor number of files per partition.

- Q: Cache vs materialize?
  A: Cache within a job when data is reused multiple times in the same run. Materialize gold tables when many jobs/users share the results or for BI serving. Rebuild materializations on a schedule and track staleness.

- Q: Speed up queries?
  A: Enable AQE, broadcast small dims, and filter early to reduce shuffles. Use dynamic partition pruning and Photon. Optimize file layout with Z-ORDER/Liquid Clustering based on common filters.

- Q: Storage vs compute trade-offs in Delta?
  A: Longer retention and CDF increase storage but help debugging and incremental processing—enable selectively. Optimize to reduce compute on reads; vacuum and compaction balance cost and performance. Measure impact and adjust per table.

Working as the sole Data Engineer
- Q: End-to-end platform you built?
  A: I set up ingestion, the medallion layers, orchestration, governance, and monitoring, then delivered gold datasets for BI/ML. I owned standards, CI/CD, and cost control. I partnered with DS/SWE to align models to business needs.

- Q: Operating as the only DE?
  A: Keep conventions simple and documented, and prioritize a clear roadmap with quick wins. Pair with SWE/DS for domain knowledge and automate repetitive tasks to buy time. Review metrics weekly to guide improvements.

- Q: Decision with incomplete info?
  A: Choose the simplest reversible approach and document assumptions and risks. Release in small steps, measure, and iterate. Escalate when trade-offs affect business SLAs or cost significantly.

- Q: Communicating complex topics?
  A: Use simple diagrams and examples, and tailor depth to the audience. Execs get outcomes, cost, and timeline; engineers get architecture, edge cases, and testing. Summarize decisions and next steps in writing.

- Q: Production incident example?
  A: A streaming job fell behind due to skew; I identified hot keys in the Spark UI and added salting and broadcasts. I reprocessed the backlog safely, added alerts, and documented a runbook. Postmortem led to better partitioning and tests.

- Q: Balancing speed, correctness, cost?
  A: Ship the smallest valuable slice with guardrails, then harden as adoption grows. Prefer designs that are cheap to run and easy to roll back. Track cost and freshness SLAs to guide priorities.

Language and collaboration
- Q: Present migration in English to execs vs engineers?
  A: Execs: why we’re moving, cost/time benefits, risks, timeline, and checkpoints. Engineers: source-to-target mapping, CDC approach, data contracts, SLAs, and validation plan. Both get a clear cutover and rollback plan.

- Q: Async work and documentation?
  A: Default to written decisions (ADRs), short design docs, and clear tickets/PRs. Keep runbooks and dashboards so anyone can self-serve status. Use regular updates and office hours for alignment.

- Q: Handle cross-team friction?
  A: Clarify goals, constraints, and definitions early. Propose a small experiment with clear success criteria and timelines. Keep communication open and assume good intent.

Go and cross-language migration
- Q: Translate Go logic to PySpark/SQL and validate?
  A: Re-express logic with DataFrame/SQL functions first; use UDFs only when needed. Build tests from known Go inputs/outputs and compare results at partition and record levels. Watch for differences in null handling and float precision.

- Q: Pitfalls with Go types/time to Spark/Delta?
  A: Time zones, zero time (0001-01-01), and leap seconds can cause surprises—normalize to UTC and handle nulls. Decimal precision and integer overflows need explicit types. Map enums/booleans carefully and document conversions.

Practical/whiteboard exercises
- Q: MERGE INTO for CDC with audit columns?
  A: Stage CDC with op codes and timestamps. MERGE ON keys with WHEN MATCHED AND op='D' THEN DELETE; WHEN MATCHED THEN UPDATE set cols and updated_at; WHEN NOT MATCHED THEN INSERT with created_at/updated_at. Add conditions to avoid overwriting newer records by comparing event timestamps.

- Q: Join two large tables with skewed key?
  A: Broadcast the smaller table, prune columns, and filter early. Salt the skewed key and enable AQE skew join. Consider bloom filters or pre-aggregation to reduce data before the join.

- Q: Structured Streaming with watermark and dedup?
  A: Read the stream, set withWatermark on event time, and use dropDuplicates on key + event time. Write to Delta with checkpoints and transactional writes for exactly-once. Monitor input rate, lag, and state size.

- Q: Terraform to provision job cluster and job?
  A: Define databricks_instance_pool or cluster with instance profile, runtime, and policies. Create a databricks_job referencing a notebook or wheel, parameters, and schedules. Manage secrets/scopes and tie to CI for automated deploys.

- Q: Optimize a slow query on a partitioned Delta table?
  A: Ensure queries filter on partition columns and prune columns early. Use Z-ORDER/Liquid Clustering on common filters and enable Photon. Fix small files with OPTIMIZE and check for skew/shuffle in the plan.

- Q: Cutover plan from Postgres to Delta with rollback?
  A: Backfill history, turn on CDC, and run in parallel while validating counts/checksums and sample diffs. Freeze at a known good snapshot, cut consumers to Delta, and monitor closely. If issues arise, roll back using time travel/snapshot and fix by partition.