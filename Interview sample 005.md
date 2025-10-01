## Below is a focused, role‑specific list of likely interview questions based on the Senior Databricks Data Engineer JD you attached. They are grouped by topic to mirror the JD emphasis (Unity Catalog, PySpark/Delta/Spark tuning, CI/CD with Azure DevOps, ETL/ELT, lakehouse design, collaboration).

Screening and experience
- Walk us through a recent Databricks project where you owned design and delivery. What were the outcomes?
- What makes you a strong fit for a senior role on a remote, international (US) project?
- Describe a time you led a technical topic end‑to‑end and influenced stakeholders.

Databricks lakehouse architecture
- Explain the medallion (Bronze/Silver/Gold) architecture. When would you deviate from it?
- How do you choose between batch and streaming for a given requirement?
- When would you use Delta Live Tables vs building your own Structured Streaming pipelines?
- What are common anti‑patterns you’ve seen in lakehouse designs and how do you avoid them?

Unity Catalog (UC) and governance
- Describe the UC object model (metastore, catalogs, schemas, tables, views, volumes). How does it differ from the Hive metastore?
- Steps to migrate from Hive Metastore to Unity Catalog; key pitfalls and how to mitigate them.
- How do you manage access in UC? Which privileges are most commonly granted at catalog/schema/table levels?
- How do access modes (single user, shared, no isolation) affect data access and security?
- How do you set up external locations and storage credentials for ADLS Gen2 in UC?
- Implementing row‑level and column‑level security in UC (dynamic views, masking). Give examples.
- How do you enable and use data lineage in UC? What are its limitations?
- How do you structure catalogs for multi‑tenant or multi‑domain environments?
- How would you implement least‑privilege access and standardized grants at scale?
- How do you handle secrets and service principals in Databricks/Azure Key Vault?

Delta Lake
- Core Delta Lake features (ACID, time travel, schema enforcement/evolution). How have you used each?
- Explain MERGE INTO for CDC. What are performance and correctness considerations?
- When to use OPTIMIZE and Z‑ORDER; what to choose as Z‑ORDER columns?
- How do you manage small files and file size compaction?
- VACUUM: retention settings, data recovery risk, and compliance considerations.
- Explain Delta Change Data Feed and when to use it.
- Schema evolution: when to allow, when to block; how to control drift.

PySpark and Spark optimization
- How do you diagnose and fix performance issues using the Spark UI?
- Explain AQE: what does it optimize and how do you enable/tune it?
- Join strategies: when to broadcast, handle skew, or use salting/hints?
- Partitioning: choosing partition columns, avoiding over/under‑partitioning, coalesce vs repartition.
- UDF vs built‑in functions vs pandas/Arrow UDFs: trade‑offs and performance.
- Caching, checkpointing, and when each is appropriate.
- What are common reasons for out‑of‑memory failures on executors and how do you fix them?
- How do you set and justify cluster sizing (cores, memory, autoscaling, Photon)?

Real‑time/streaming
- Structured Streaming fundamentals: triggers, watermarks, stateful operations, exactly‑once guarantees.
- How do you handle late/duplicate data and state store growth?
- Auto Loader vs file‑based batch ingestion; configuration and recovery semantics.
- Designing idempotent streaming sinks to Delta; handling schema evolution in streams.

ETL/ELT design and best practices
- How do you design reliable, restartable pipelines? Discuss orchestration, lineage, idempotency.
- Explain your approach to data quality (expectations, validations, quarantine patterns).
- Handling slowly changing dimensions (SCD) on Delta: options and trade‑offs.
- How do you standardize conventions (naming, folder structures, table properties, checkpoints)?

Databricks Jobs and orchestration
- Jobs vs Workflows vs DLT pipelines: when to use each?
- Task orchestration (dependencies, parameters, cluster reuse, job clusters vs all‑purpose).
- Handling retries, alerting, and failure diagnostics.

CI/CD and Azure DevOps
- Your preferred approach to CI/CD for Databricks (Repos, Databricks Asset Bundles, dbx, CLI, REST API).
- Outline a DevOps pipeline: build, unit tests, quality checks, package (wheel), deploy to DEV/TEST/PROD, run smoke tests.
- How do you promote UC objects (catalogs, schemas, tables, permissions) across environments?
- Managing notebooks vs python packages; pros/cons in CI/CD.
- Secret management in pipelines (Key Vault, variable groups).
- How do you implement automated permission grants and policy enforcement?
- Have you used Terraform for Databricks/Azure? Describe modules to provision workspace, UC, grants.

Azure platform integration
- Best practices for integrating with ADLS Gen2 (mounts vs ABFS direct, passthrough).
- Using Managed Identities/Service Principals with UC storage credentials.
- Ingesting from Azure sources (Event Hubs, Service Bus, Synapse, SQL DB). What are common patterns?
- When would you consider Azure SQL/Synapse/Fabric instead of Databricks?

Observability, monitoring, and cost optimization
- How do you monitor pipelines, clusters, and jobs (metrics, logs, Spark event logs, audit logs)?
- Cost controls: autoscaling, spot/low‑priority nodes, Photon, caching, pruning, file sizes, Z‑ORDER trade‑offs.
- How do you implement data and platform SLAs/SLOs and alerting?

Testing and quality engineering
- Unit/integration testing strategy for PySpark (pytest, chispa, delta‑rs, local vs cluster tests).
- How do you test Structured Streaming logic deterministically?
- Contract testing and schema enforcement in pipelines.

Security, compliance, and governance
- Designing PII handling: masking, tokenization, RLS/CLS with UC, auditability.
- How do you align with regulatory requirements (e.g., GDPR data deletion with Delta VACUUM/time travel)?
- Cluster policies and workspace controls to enforce governance.

Documentation and collaboration
- What documentation do you produce (runbooks, ADRs, data contracts, lineage)?
- How do you translate ambiguous business requirements into technical designs?
- Example of mentoring engineers and raising the team’s bar.

Behavioral and scenario questions
- You’ve inherited slow, unreliable pipelines. What’s your triage and stabilization plan in 30/60/90 days?
- A business user requests broad access to a sensitive catalog for “speed.” How do you respond?
- An urgent production incident hits during a release window. How do you lead resolution?
- Describe a challenging stakeholder conversation and how you achieved alignment.

Live coding/exercise prompts (typical for this role)
- Write a PySpark job to read raw JSON from ADLS, normalize nested structures, apply quality checks, and write to Delta with partitioning.
- Implement a CDC MERGE on a large table with skewed keys; include performance tactics.
- Build a small Structured Streaming pipeline with watermarking and aggregation to a Delta sink.
- Show how you’d optimize a slow job: identify skew, change join strategy, and explain parameter changes.
- Author a minimal Azure DevOps YAML pipeline to lint, test, build a wheel, and deploy a Databricks bundle to a DEV workspace.

Nice‑to‑have topics (may appear)
- Microsoft Fabric basics: OneLake, lakehouse concept, shortcuts, when to choose Fabric vs Databricks.
- Multi‑cloud experiences (GCP/AWS) and how designs change across clouds.
- Databricks certification learnings and how they influenced your practice.

English communication (end‑client interview)
- Explain your recent project and design decisions to a non‑technical stakeholder.
- Clarify trade‑offs (cost vs latency vs complexity) for a real‑time requirement in simple terms.

## Here are concise, simple answers (a few sentences each) to the key questions most aligned to the role.

Screening and experience
- Walk us through a recent Databricks project you owned.
  - I designed and built a lakehouse using the medallion pattern on Delta Lake and governed it with Unity Catalog. I delivered both batch and streaming pipelines in PySpark, added data quality checks, and set up CI/CD in Azure DevOps. I also created runbooks and dashboards so support was simple. As a result, runtimes dropped by about 40% and access control became consistent across teams.

- Why are you a strong fit for a senior role on a remote US project?
  - I work independently, break down work clearly, and communicate progress in a predictable way. I’m used to overlapping with US hours and handling async updates with good documentation. I lead design reviews, mentor teammates, and resolve production issues calmly. I can talk to both engineers and business users and keep everyone aligned.

- Describe a time you led a technical topic end to end.
  - I led a migration from a legacy warehouse to Delta Lake. I gathered requirements, proposed the lakehouse design, planned the cutover, and set up CI/CD and monitoring. I handled stakeholder demos and change management. We delivered on time, reduced costs, and improved data freshness.

Lakehouse architecture
- Explain the medallion (Bronze/Silver/Gold) architecture. When would you deviate?
  - Bronze stores raw, immutable data as-is. Silver applies cleaning, standardization, and joins to create trusted datasets. Gold is curated and shaped for analytics and reporting. I might deviate for a tiny data product where the extra layers add no value, or when a dimensional model must be strictly enforced for a legacy BI tool.

- How do you choose between batch and streaming?
  - I look at latency needs, data volume and variability, and operational cost. If the business needs sub-minute updates or event-driven reactions, I choose streaming. If daily or hourly updates are enough, batch is simpler and cheaper. Sometimes a small micro-batch pipeline balances speed and cost.

- When to use Delta Live Tables vs custom Structured Streaming?
  - DLT is great when you want quick setup, built-in quality checks, lineage, and simple operations. Custom Structured Streaming is better when you need complex logic, custom sinks, or features not supported by DLT. I often start with DLT to move fast, then switch to custom if requirements outgrow it.

Unity Catalog (UC) and governance
- UC object model vs Hive Metastore
  - UC organizes data as metastore > catalog > schema > table/view/volume and centralizes governance across workspaces. It provides fine-grained permissions, lineage, and support for external locations. Hive Metastore is usually per workspace and lacks unified security and lineage. UC also simplifies collaboration by using three-level names like catalog.schema.table.

- Steps to migrate from Hive Metastore to UC; pitfalls
  - I inventory current tables, create storage credentials and external locations, and register tables in UC. I update all code to three-level names and adjust paths away from legacy mounts. I test permissions, lineage, and jobs in a lower environment before cutover. Common pitfalls are missing grants, DBFS mount dependencies, and breaking time travel if paths change—so I plan for a phased migration.

- How do you manage access in UC?
  - I grant privileges to groups, not individuals (USAGE, SELECT, MODIFY, CREATE) at catalog/schema/table level. I follow least-privilege and separate human users from service principals. I standardize grants using Terraform or SQL scripts so environments stay consistent. I also document data owners and access request paths.

- How do you set up external locations and storage credentials for ADLS Gen2?
  - I create a storage credential backed by a managed identity or service principal with Storage Blob Data rights on the container. Then I define an external location that points to the ADLS path. I grant READ/WRITE on the external location to the right groups and test with a small read/write. This keeps storage access secure and auditable.

- Implementing row-level and column-level security
  - I use dynamic views to filter rows based on current_user() or group membership. For column masking, I use CASE expressions or built-in masking functions in views. I centralize rules and reuse them across tables to avoid drift. I test performance and make sure the business understands the rules.

- How do you enable and use data lineage in UC?
  - Lineage is built-in for most Databricks operations. It shows upstream and downstream dependencies and is useful for impact analysis before changes. I review lineage when planning schema changes or deprecations. For external tools, I complement UC lineage with docs or connectors if needed.

Delta Lake
- Core Delta Lake features and how you use them
  - ACID transactions make writes reliable, even during failures. Time travel lets me query past versions for debugging or audits. Schema enforcement and evolution help control changes and prevent bad data. I also use table properties and expectations to keep data quality high.

- MERGE INTO for CDC: performance and correctness
  - I pre-dedupe the source and filter to only changed keys to reduce work. I partition the target table wisely and use predicates in MERGE to avoid scanning all data. For big tables, I may split updates and inserts into separate steps. I monitor stats, consider Z-ORDER on join/filter columns, and use Change Data Feed when it simplifies incremental logic.

- When to use OPTIMIZE and Z-ORDER
  - I use OPTIMIZE to compact small files and improve read performance, usually on a schedule for high-churn tables. I use Z-ORDER on columns commonly used in filters or joins, like customer_id or event_date. I avoid overusing Z-ORDER because it increases write costs. I verify improvements with query profiles before rolling out widely.

- Managing small files
  - I control write parallelism with repartition/coalesce to target sensible file sizes (e.g., 128–512 MB). I use Auto Loader with file limits and run OPTIMIZE to compact files. I avoid over-partitioning; too many tiny partitions slow performance. I also prefer batch merges over per-record writes.

- VACUUM: retention and risks
  - I set a retention that meets compliance (often 7 days or more). Short retention risks breaking time travel and external readers. Before lowering retention, I confirm every consumer can handle it. For GDPR deletions, I coordinate deletion, retention change if needed, and careful scheduling of VACUUM.

PySpark and Spark optimization
- Diagnosing performance with Spark UI
  - I check the DAG for long stages, skewed tasks, and big shuffles. I look at executor CPU/memory usage and failed tasks. I review SQL explain plans and query profiles for inefficient joins or scans. Then I fix root causes like skew, missing filters, or excessive serialization.

- What is AQE and how to use it?
  - Adaptive Query Execution adjusts plans at runtime based on actual stats. It can change join strategies, coalesce small partitions, and handle skewed partitions. I turn it on by default and tune shuffle/partition settings. It often reduces shuffle size and speeds up joins with uneven data.

- Join strategies: broadcast, skew, salting
  - If one table is small, I broadcast it to avoid a shuffle. If a key is skewed, I salt the key, use skew hints, or rely on AQE skew join to split heavy partitions. I push filters early and select only needed columns to reduce data movement. I also cache small dimensions when reused.

- Partitioning: choosing and tuning
  - I pick partition columns that match frequent filters and have good selectivity. I avoid too many partitions, which create overhead, and too few, which hurt parallelism. I use repartition to increase parallelism and coalesce to reduce small tasks. I validate with read metrics and cost.

Streaming
- Structured Streaming basics and exactly-once
  - I define sources and sinks, use checkpoints for state and progress, and set triggers for latency. With Delta sinks, I get exactly-once semantics through idempotent writes. I add watermarks for late data and design stateful operations carefully. I also include dead-letter paths for bad records.

- Handling late/duplicate data and state growth
  - I use watermarks and windows to bound state size. I deduplicate using keys and sequence numbers or event-time windows. I monitor the state store and tune partitions and memory. If needed, I split the pipeline into smaller stages.

CI/CD and Azure DevOps
- Preferred CI/CD approach for Databricks
  - I keep code in Git, use Databricks Repos for development, and package shared logic as wheels. I deploy with Databricks Asset Bundles or dbx, with environment configs for DEV/TEST/PROD. I include automated tests, quality checks, and approvals. Deployments are repeatable and traceable.

- Outline a DevOps pipeline
  - Stages: lint/format, unit tests, build wheel, security scan, package deployment artifact, deploy to DEV, run smoke tests, then promote to TEST/PROD with approvals. I store workspace URLs, tokens, and secrets in variable groups/Key Vault. I tag builds with git shas for traceability. Rollbacks are just redeploying a previous artifact.

Behavioral and scenarios
- Stabilizing slow, unreliable pipelines (30/60/90 days)
  - First 30 days: add monitoring and alerts, fix top failures, and document the current state. Next 30: optimize hotspots (joins, partitions), standardize patterns, improve CI/CD and retries. Last 30: harden SLAs, create runbooks, and reduce manual toil. I share clear metrics to show progress.

- Leading during a production incident
  - I open a comms channel, assign roles, and freeze risky changes. I focus on mitigation first (fallbacks, reruns, scaling), then find the root cause using logs and metrics. After recovery, I run a blameless postmortem and create follow-up tasks. I also improve monitoring to catch it earlier next time.

Azure integration
- ADLS Gen2: mounts vs ABFS direct; passthrough
  - I prefer ABFS direct paths with Unity Catalog external locations because they are simpler and more secure. Mounts are legacy and can bypass governance. I use managed identity or service principal for access (passthrough when possible). This keeps secrets out of code and permissions centralized.

Security, compliance, and governance
- Handling PII (masking, RLS/CLS, tokenization)
  - I classify sensitive fields early and decide on masking or tokenization at the Silver layer. I enforce row/column security with UC dynamic views and restrict access to only what users need. I log access and review it regularly. I document the controls so audits are straightforward.

Testing and quality engineering
- Unit/integration testing for PySpark
  - I test business logic with pytest and chispa to compare DataFrames. I mock inputs and keep I/O thin so tests are fast and deterministic. I add small integration tests on a cluster for key pipelines. CI runs these tests on every change.

Live coding/exercise approach
- CDC MERGE on a large, skewed table
  - I pre-dedupe and filter the change set to only affected keys. I handle skew with salting or rely on AQE skew join and consider broadcasting small dimensions. I MERGE with tight predicates and then OPTIMIZE the target. I verify correctness with row counts and sample queries, and track performance in the Spark UI.

English communication (end‑client)
- Explain your recent project and design decisions to a non‑technical stakeholder
  - We built a central data platform that brings raw data in, cleans it, and turns it into trusted, ready-to-use tables. This reduced errors and made reporting faster and more self-service. We chose this approach because it’s reliable, cost-effective, and easy to scale as needs grow. It also gives clear data ownership and access control.
