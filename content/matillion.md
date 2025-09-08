# Matillion
Matillion

* [What is Matillion and how does it differ from ETL/ELT tools like Fivetran, dbt, Airflow, Informatica, and Databricks for data engineering use cases?](#What-is-Matillion-and-how-does-it-differ-from-ETL-ELT-tools-like-Fivetran-dbt-Airflow-Informatica-and-Databricks-for-data-engineering-use-cases)
* [How do Matillion ETL (VM-based) and Matillion Data Productivity Cloud (Designer, Data Loader, CDC) compare in architecture and capabilities?](#How-do-Matillion-ETL-VM-based-and-Matillion-Data-Productivity-Cloud-Designer-Data-Loader-CDC-compare-in-architecture-and-capabilities)
* [When would you choose Matillion ETL on a VM versus Matillion’s SaaS (DPC) and why?](#When-would-you-choose-Matillion-ETL-on-a-VM-versus-Matillion-s-SaaS-DPC-and-why)
* [How does Matillion implement ELT pushdown and which components execute in-warehouse versus on the Matillion host?](#How-does-Matillion-implement-ELT-pushdown-and-which-components-execute-in-warehouse-versus-on-the-Matillion-host)
* [Which components or patterns break pushdown and how do you minimize non-pushdown operations?](#Which-components-or-patterns-break-pushdown-and-how-do-you-minimize-non-pushdown-operations)
* [How do orchestration jobs differ from transformation jobs and how do you decide where logic belongs?](#How-do-orchestration-jobs-differ-from-transformation-jobs-and-how-do-you-decide-where-logic-belongs)
* [How do you organize projects, folders, shared jobs, and naming conventions for maintainability and reuse?](#How-do-you-organize-projects-folders-shared-jobs-and-naming-conventions-for-maintainability-and-reuse)
* [How do environments work in Matillion and how do you parameterize connections per dev/stage/prod?](#How-do-environments-work-in-Matillion-and-how-do-you-parameterize-connections-per-dev-stage-prod)
* [What are the different variable types (environment, job, grid, fixed) and how do you scope and secure them?](#What-are-the-different-variable-types-environment-job-grid-fixed-and-how-do-you-scope-and-secure-them)
* [How do you use grid variables to build metadata‑driven pipelines that iterate over tables and sources?](#How-do-you-use-grid-variables-to-build-metadata-driven-pipelines-that-iterate-over-tables-and-sources)
* [How do you pass variables between jobs and manage defaults, overrides, and secrets?](#How-do-you-pass-variables-between-jobs-and-manage-defaults-overrides-and-secrets)
* [How do you manage credentials securely (Matillion credential manager, cloud secret stores, KMS/Key Vault/Secret Manager)?](#How-do-you-manage-credentials-securely-Matillion-credential-manager-cloud-secret-stores-KMS-Key-Vault-Secret-Manager)
* [How do you configure SSO (SAML/OIDC) and RBAC in Matillion and enforce least privilege by environment?](#How-do-you-configure-SSO-SAML-OIDC-and-RBAC-in-Matillion-and-enforce-least-privilege-by-environment)
* [How do you isolate teams and tenants using projects, environments, IAM roles, and network segmentation?](#How-do-you-isolate-teams-and-tenants-using-projects-environments-IAM-roles-and-network-segmentation)
* [What cloud permissions are required for Matillion ETL (instance profile/service principal) to access S3/ADLS/GCS and warehouses?](#What-cloud-permissions-are-required-for-Matillion-ETL-instance-profile-service-principal-to-access-S3-ADLS-GCS-and-warehouses)
* [How do you use private endpoints/VPC endpoints to keep data plane traffic private for storage and warehouses?](#How-do-you-use-private-endpoints-VPC-endpoints-to-keep-data-plane-traffic-private-for-storage-and-warehouses)
* [How do you backup and recover Matillion ETL projects, metadata, and configurations across regions or accounts/subscriptions?](#How-do-you-backup-and-recover-Matillion-ETL-projects-metadata-and-configurations-across-regions-or-accounts-subscriptions)
* [How do you handle high availability and disaster recovery for Matillion ETL instances and job state?](#How-do-you-handle-high-availability-and-disaster-recovery-for-Matillion-ETL-instances-and-job-state)
* [How do you upgrade Matillion versions safely, validate compatibility, and roll back if needed?](#How-do-you-upgrade-Matillion-versions-safely-validate-compatibility-and-roll-back-if-needed)
* [How do you export/import or promote projects across environments, and what pitfalls occur with environment bindings?](#How-do-you-export-import-or-promote-projects-across-environments-and-what-pitfalls-occur-with-environment-bindings)
* [How do you integrate Git-based version control with Matillion and manage branches, PRs, and releases?](#How-do-you-integrate-Git-based-version-control-with-Matillion-and-manage-branches-PRs-and-releases)
* [How do you implement CI/CD for Matillion (APIs/CLI, GitHub Actions/Azure DevOps/CodeBuild) to deploy jobs automatically?](#How-do-you-implement-CI-CD-for-Matillion-APIs-CLI-GitHub-Actions-Azure-DevOps-CodeBuild-to-deploy-jobs-automatically)
* [How do you tag, document, and annotate jobs/components to support discovery and governance?](#How-do-you-tag-document-and-annotate-jobs-components-to-support-discovery-and-governance)
* [How do you schedule jobs with Matillion’s scheduler versus external orchestrators (Airflow, ADF, Step Functions, Cloud Composer)?](#How-do-you-schedule-jobs-with-Matillion-s-scheduler-versus-external-orchestrators-Airflow-ADF-Step-Functions-Cloud-Composer)
* [How do you design event-driven pipelines (webhooks, SNS/SQS, EventBridge, Logic Apps) that trigger Matillion jobs?](#How-do-you-design-event-driven-pipelines-webhooks-SNS-SQS-EventBridge-Logic-Apps-that-trigger-Matillion-jobs)
* [How do you tune job concurrency, parallel components, and queueing to maximize throughput without overloading the warehouse?](#How-do-you-tune-job-concurrency-parallel-components-and-queueing-to-maximize-throughput-without-overloading-the-warehouse)
* [How do you instrument and limit concurrency per environment or per warehouse to avoid contention and runaway spend?](#How-do-you-instrument-and-limit-concurrency-per-environment-or-per-warehouse-to-avoid-contention-and-runaway-spend)
* [How do you design idempotent pipelines and ensure safe retries at the component and job level?](#How-do-you-design-idempotent-pipelines-and-ensure-safe-retries-at-the-component-and-job-level)
* [How do you implement error handling with Try/Catch, conditional execution, Raise Data Exception, and rollback patterns?](#How-do-you-implement-error-handling-with-Try-Catch-conditional-execution-Raise-Data-Exception-and-rollback-patterns)
* [How do you implement alarms and notifications (email, Slack, Teams, PagerDuty) from job status and error conditions?](#How-do-you-implement-alarms-and-notifications-email-Slack-Teams-PagerDuty-from-job-status-and-error-conditions)
* [How do you centralize logs and metrics to CloudWatch/Stackdriver/Log Analytics and build dashboards for SLAs?](#How-do-you-centralize-logs-and-metrics-to-CloudWatch-Stackdriver-Log-Analytics-and-build-dashboards-for-SLAs)
* [How do you use Matillion’s REST API to run jobs, set variables, retrieve task history, and automate deployments?](#How-do-you-use-Matillion-s-REST-API-to-run-jobs-set-variables-retrieve-task-history-and-automate-deployments)
* [How do you secure the Matillion API with tokens/IP allowlists and enforce rate limits and audit trails?](#How-do-you-secure-the-Matillion-API-with-tokens-IP-allowlists-and-enforce-rate-limits-and-audit-trails)
* [How do you monitor job duration trends, failures, and row counts to detect regressions and data anomalies?](#How-do-you-monitor-job-duration-trends-failures-and-row-counts-to-detect-regressions-and-data-anomalies)
* [How do you implement data quality checks (row counts, constraints, duplicates) natively and with frameworks like Great Expectations/Deequ?](#How-do-you-implement-data-quality-checks-row-counts-constraints-duplicates-natively-and-with-frameworks-like-Great-Expectations-Deequ)
* [How do you manage lineage from raw sources to curated tables and expose it to catalogs (Glue, Purview, Data Catalog)?](#How-do-you-manage-lineage-from-raw-sources-to-curated-tables-and-expose-it-to-catalogs-Glue-Purview-Data-Catalog)
* [How do you design cost-aware pipelines that minimize warehouse time, leverage auto-suspend, and push heavy work in-warehouse?](#How-do-you-design-cost-aware-pipelines-that-minimize-warehouse-time-leverage-auto-suspend-and-push-heavy-work-in-warehouse)
* [How do you estimate and attribute cost per pipeline/team using tags, warehouse usage, and Matillion task history?](#How-do-you-estimate-and-attribute-cost-per-pipeline-team-using-tags-warehouse-usage-and-Matillion-task-history)
* [How do you implement blue/green or canary releases for complex pipelines and roll back safely?](#How-do-you-implement-blue-green-or-canary-releases-for-complex-pipelines-and-roll-back-safely)
* [How do you build reusable job templates and shared jobs for common patterns (file loads, SCD merges, CDC merges)?](#How-do-you-build-reusable-job-templates-and-shared-jobs-for-common-patterns-file-loads-SCD-merges-CDC-merges)
* [How do you implement metadata-driven ingestion frameworks using grids, dictionaries, and dynamic SQL generation?](#How-do-you-implement-metadata-driven-ingestion-frameworks-using-grids-dictionaries-and-dynamic-SQL-generation)
* [How do you handle schema drift and column evolution for relational and semi-structured sources?](#How-do-you-handle-schema-drift-and-column-evolution-for-relational-and-semi-structured-sources)
* [How do you implement SCD Type 1 and Type 2 patterns in Matillion efficiently across Snowflake/BigQuery/Redshift/Synapse?](#How-do-you-implement-SCD-Type-1-and-Type-2-patterns-in-Matillion-efficiently-across-Snowflake-BigQuery-Redshift-Synapse)
* [How do you implement deduplication and late-arriving data handling without double counting?](#How-do-you-implement-deduplication-and-late-arriving-data-handling-without-double-counting)
* [How do you choose between append, merge/upsert, and full refresh patterns per table and workload?](#How-do-you-choose-between-append-merge-upsert-and-full-refresh-patterns-per-table-and-workload)
* [How do you maintain surrogate keys, natural keys, and referential integrity in an ELT approach?](#How-do-you-maintain-surrogate-keys-natural-keys-and-referential-integrity-in-an-ELT-approach)
* [How do you reconcile source-to-target row counts and checksums and generate exception reports?](#How-do-you-reconcile-source-to-target-row-counts-and-checksums-and-generate-exception-reports)
* [How do you manage time zones, daylight savings, and timestamp normalization across sources and warehouses?](#How-do-you-manage-time-zones-daylight-savings-and-timestamp-normalization-across-sources-and-warehouses)
* [How do you handle large text/binary fields, encoding, and newline/quote handling in CSV/JSON loads?](#How-do-you-handle-large-text-binary-fields-encoding-and-newline-quote-handling-in-CSV-JSON-loads)
* [How do you ingest from APIs using the API Query/REST connector and handle pagination, rate limits, and retries?](#How-do-you-ingest-from-APIs-using-the-API-Query-REST-connector-and-handle-pagination-rate-limits-and-retries)
* [How do you design incremental API extraction with bookmarks/watermarks and recover from failures idempotently?](#How-do-you-design-incremental-API-extraction-with-bookmarks-watermarks-and-recover-from-failures-idempotently)
* [How do you parse nested JSON and flatten arrays/objects into relational tables efficiently?](#How-do-you-parse-nested-JSON-and-flatten-arrays-objects-into-relational-tables-efficiently)
* [How do you create custom connectors using Matillion’s Connector SDK and manage OAuth/token refresh securely?](#How-do-you-create-custom-connectors-using-Matillion-s-Connector-SDK-and-manage-OAuth-token-refresh-securely)
* [How do you validate and mock external APIs for CI tests and protect credentials in test runs?](#How-do-you-validate-and-mock-external-APIs-for-CI-tests-and-protect-credentials-in-test-runs)
* [How do you ingest files from S3/ADLS/GCS and choose file formats, compression, and partitioning strategies?](#How-do-you-ingest-files-from-S3-ADLS-GCS-and-choose-file-formats-compression-and-partitioning-strategies)
* [How do you size and batch files to avoid the small-files problem and maximize parallel load performance?](#How-do-you-size-and-batch-files-to-avoid-the-small-files-problem-and-maximize-parallel-load-performance)
* [How do you design landing zones and lifecycle policies on cloud storage for raw, staged, and curated layers?](#How-do-you-design-landing-zones-and-lifecycle-policies-on-cloud-storage-for-raw-staged-and-curated-layers)
* [How do you control file deletion, archiving, and quarantine of bad files with clear operational runbooks?](#How-do-you-control-file-deletion-archiving-and-quarantine-of-bad-files-with-clear-operational-runbooks)
* [How do you bulk load to Snowflake using external/internal stages, file formats, copy options, and error handling?](#How-do-you-bulk-load-to-Snowflake-using-external-internal-stages-file-formats-copy-options-and-error-handling)
* [How do you tune Snowflake COPY options (ON_ERROR, VALIDATION_MODE, TRUNCATECOLUMNS, FORCE) and stage credentials?](#How-do-you-tune-Snowflake-COPY-options-ON-ERROR-VALIDATION-MODE-TRUNCATECOLUMNS-FORCE-and-stage-credentials)
* [How do you implement Snowflake MERGE at scale and manage clustering/ordering and micro-partitions?](#How-do-you-implement-Snowflake-MERGE-at-scale-and-manage-clustering-ordering-and-micro-partitions)
* [How do you use Snowflake Streams and Tasks with Matillion to build incremental pipelines and orchestrate dependencies?](#How-do-you-use-Snowflake-Streams-and-Tasks-with-Matillion-to-build-incremental-pipelines-and-orchestrate-dependencies)
* [How do you load into BigQuery with load jobs vs query jobs and manage write dispositions and partitioned/clustered tables?](#How-do-you-load-into-BigQuery-with-load-jobs-vs-query-jobs-and-manage-write-dispositions-and-partitioned-clustered-tables)
* [How do you optimize BigQuery costs using partition pruning, clustering, and slot reservations vs on-demand?](#How-do-you-optimize-BigQuery-costs-using-partition-pruning-clustering-and-slot-reservations-vs-on-demand)
* [How do you load into Redshift using COPY from S3, choose dist/sort keys, and schedule VACUUM/ANALYZE?](#How-do-you-load-into-Redshift-using-COPY-from-S3-choose-dist-sort-keys-and-schedule-VACUUM-ANALYZE)
* [How do you leverage Redshift Spectrum external tables from Matillion and manage Glue Catalog metadata?](#How-do-you-leverage-Redshift-Spectrum-external-tables-from-Matillion-and-manage-Glue-Catalog-metadata)
* [How do you load into Synapse using COPY INTO/PolyBase, manage external data sources, and tune parallelism?](#How-do-you-load-into-Synapse-using-COPY-INTO-PolyBase-manage-external-data-sources-and-tune-parallelism)
* [How do you compare Matillion’s performance patterns across Snowflake, BigQuery, Redshift, and Synapse?](#How-do-you-compare-Matillion-s-performance-patterns-across-Snowflake-BigQuery-Redshift-and-Synapse)
* [How do you orchestrate Databricks or Delta Lake targets from Matillion and implement Delta MERGE?](#How-do-you-orchestrate-Databricks-or-Delta-Lake-targets-from-Matillion-and-implement-Delta-MERGE)
* [How do you integrate Matillion with dbt for modeling while keeping orchestration and ingestion in Matillion?](#How-do-you-integrate-Matillion-with-dbt-for-modeling-while-keeping-orchestration-and-ingestion-in-Matillion)
* [How do you balance business logic between SQL components, Python/Batch components, and warehouse-native SQL?](#How-do-you-balance-business-logic-between-SQL-components-Python-Batch-components-and-warehouse-native-SQL)
* [How do you prevent anti-patterns like row-by-row Python loops and replace them with set-based SQL?](#How-do-you-prevent-anti-patterns-like-row-by-row-Python-loops-and-replace-them-with-set-based-SQL)
* [How do you cache and broadcast small reference datasets efficiently for joins in transformation jobs?](#How-do-you-cache-and-broadcast-small-reference-datasets-efficiently-for-joins-in-transformation-jobs)
* [How do you handle skewed joins and repartitioning strategies in warehousing engines from Matillion SQL?](#How-do-you-handle-skewed-joins-and-repartitioning-strategies-in-warehousing-engines-from-Matillion-SQL)
* [How do you manage temporary and transient tables, schemas, and cleanup to control storage costs?](#How-do-you-manage-temporary-and-transient-tables-schemas-and-cleanup-to-control-storage-costs)
* [How do you structure medallion (bronze/silver/gold) layers and enforce contracts between layers?](#How-do-you-structure-medallion-bronze-silver-gold-layers-and-enforce-contracts-between-layers)
* [How do you manage CDC with Matillion Data Loader/CDC Agent for sources like MySQL, Postgres, and SQL Server?](#How-do-you-manage-CDC-with-Matillion-Data-Loader-CDC-Agent-for-sources-like-MySQL-Postgres-and-SQL-Server)
* [How do you configure CDC agents, secure network access, and handle initial snapshots vs ongoing replication?](#How-do-you-configure-CDC-agents-secure-network-access-and-handle-initial-snapshots-vs-ongoing-replication)
* [How do you apply CDC changes to targets with MERGE, resolve out-of-order events, and handle schema changes?](#How-do-you-apply-CDC-changes-to-targets-with-MERGE-resolve-out-of-order-events-and-handle-schema-changes)
* [How do you detect CDC lag, backpressure, and recover from agent restarts or network partitions?](#How-do-you-detect-CDC-lag-backpressure-and-recover-from-agent-restarts-or-network-partitions)
* [How do you compare Matillion CDC to vendor tools (Fivetran, Debezium, StreamSets) for your requirements?](#How-do-you-compare-Matillion-CDC-to-vendor-tools-Fivetran-Debezium-StreamSets-for-your-requirements)
* [How do you design near-real-time pipelines with CDC feeding warehouse tasks and downstream transformations?](#How-do-you-design-near-real-time-pipelines-with-CDC-feeding-warehouse-tasks-and-downstream-transformations)
* [How do you design replay and backfill strategies that do not double-apply CDC changes?](#How-do-you-design-replay-and-backfill-strategies-that-do-not-double-apply-CDC-changes)
* [How do you stage and validate fine-grained deletes and GDPR erasures across downstream tables?](#How-do-you-stage-and-validate-fine-grained-deletes-and-GDPR-erasures-across-downstream-tables)
* [How do you incorporate data masking/tokenization for PII during ingestion and transformation?](#How-do-you-incorporate-data-masking-tokenization-for-PII-during-ingestion-and-transformation)
* [How do you enforce row-level/column-level security downstream and ensure Matillion jobs respect access policies?](#How-do-you-enforce-row-level-column-level-security-downstream-and-ensure-Matillion-jobs-respect-access-policies)
* [How do you publish curated datasets to BI platforms and keep schema contracts and documentation in sync?](#How-do-you-publish-curated-datasets-to-BI-platforms-and-keep-schema-contracts-and-documentation-in-sync)
* [How do you handle object dependencies in Matillion (Run Orchestration/Run Transformation) to avoid cycles and deadlocks?](#How-do-you-handle-object-dependencies-in-Matillion-Run-Orchestration-Run-Transformation-to-avoid-cycles-and-deadlocks)
* [How do you build conditional flows based on data checks or metadata lookups (e.g., run downstream only if new data)?](#How-do-you-build-conditional-flows-based-on-data-checks-or-metadata-lookups-e-g-run-downstream-only-if-new-data)
* [How do you construct dynamic SQL safely and prevent SQL injection when using variables and metadata tables?](#How-do-you-construct-dynamic-SQL-safely-and-prevent-SQL-injection-when-using-variables-and-metadata-tables)
* [How do you test jobs locally or in a sandbox with sample data and seedable randomness for deterministic results?](#How-do-you-test-jobs-locally-or-in-a-sandbox-with-sample-data-and-seedable-randomness-for-deterministic-results)
* [How do you separate configuration from code and use environment-driven settings without code changes?](#How-do-you-separate-configuration-from-code-and-use-environment-driven-settings-without-code-changes)
* [How do you parameterize warehouse sizes, role names, and storage locations for different environments?](#How-do-you-parameterize-warehouse-sizes-role-names-and-storage-locations-for-different-environments)
* [How do you warm up warehouses or pre-stage data to bound pipeline latency during scheduled runs?](#How-do-you-warm-up-warehouses-or-pre-stage-data-to-bound-pipeline-latency-during-scheduled-runs)
* [How do you implement SLA tracking per pipeline and enforce deadlines or timeout policies for long steps?](#How-do-you-implement-SLA-tracking-per-pipeline-and-enforce-deadlines-or-timeout-policies-for-long-steps)
* [How do you implement retry with exponential backoff and jitter for transient warehouse/storage/API errors?](#How-do-you-implement-retry-with-exponential-backoff-and-jitter-for-transient-warehouse-storage-API-errors)
* [How do you validate schema before load and reject or quarantine records that fail constraints?](#How-do-you-validate-schema-before-load-and-reject-or-quarantine-records-that-fail-constraints)
* [How do you remediate malformed files and partial loads using copy error tables and retry logic?](#How-do-you-remediate-malformed-files-and-partial-loads-using-copy-error-tables-and-retry-logic)
* [How do you manage time-partitioned data and retention policies and automate partition pruning/cleanup?](#How-do-you-manage-time-partitioned-data-and-retention-policies-and-automate-partition-pruning-cleanup)
* [How do you compress and encode data optimally for the target warehouse (ZSTD, Snappy, GZIP, column encodings)?](#How-do-you-compress-and-encode-data-optimally-for-the-target-warehouse-ZSTD-Snappy-GZIP-column-encodings)
* [How do you write quality-of-service tests to guard against performance regressions after job changes?](#How-do-you-write-quality-of-service-tests-to-guard-against-performance-regressions-after-job-changes)
* [How do you simulate scale and concurrency in pre-prod to validate warehouse sizing and autosuspend policies?](#How-do-you-simulate-scale-and-concurrency-in-pre-prod-to-validate-warehouse-sizing-and-autosuspend-policies)
* [How do you tune Snowflake warehouse size, auto-suspend/auto-resume, and statement concurrency for Matillion workloads?](#How-do-you-tune-Snowflake-warehouse-size-auto-suspend-auto-resume-and-statement-concurrency-for-Matillion-workloads)
* [How do you tune BigQuery reservation slots and concurrency for Matillion-driven transformations?](#How-do-you-tune-BigQuery-reservation-slots-and-concurrency-for-Matillion-driven-transformations)
* [How do you tune Redshift WLM/Workload Manager and queue priorities for Matillion ETL jobs?](#How-do-you-tune-Redshift-WLM-Workload-Manager-and-queue-priorities-for-Matillion-ETL-jobs)
* [How do you tune Synapse DWU/compute pools and concurrency for Matillion pipelines?](#How-do-you-tune-Synapse-DWU-compute-pools-and-concurrency-for-Matillion-pipelines)
* [How do you instrument end-to-end latency from source arrival to publish and identify bottlenecks at each step?](#How-do-you-instrument-end-to-end-latency-from-source-arrival-to-publish-and-identify-bottlenecks-at-each-step)
* [How do you expose operational metrics and KPIs for platform health to stakeholders and on-call engineers?](#How-do-you-expose-operational-metrics-and-KPIs-for-platform-health-to-stakeholders-and-on-call-engineers)
* [How do you encrypt data at rest and in transit across storage, warehouses, and Matillion components?](#How-do-you-encrypt-data-at-rest-and-in-transit-across-storage-warehouses-and-Matillion-components)
* [How do you rotate secrets, keys, and tokens used by Matillion and test rotations without downtime?](#How-do-you-rotate-secrets-keys-and-tokens-used-by-Matillion-and-test-rotations-without-downtime)
* [How do you validate compliance requirements (HIPAA/PCI/GDPR) and configure logging, masking, and retention accordingly?](#How-do-you-validate-compliance-requirements-HIPAA-PCI-GDPR-and-configure-logging-masking-and-retention-accordingly)
* [How do you set up guardrails and budgets to cap spend per environment and prevent runaway jobs?](#How-do-you-set-up-guardrails-and-budgets-to-cap-spend-per-environment-and-prevent-runaway-jobs)
* [How do you control who can create/edit/run jobs and who can modify environments and credentials?](#How-do-you-control-who-can-create-edit-run-jobs-and-who-can-modify-environments-and-credentials)
* [How do you audit changes to jobs, variables, and credentials and integrate with SIEM solutions?](#How-do-you-audit-changes-to-jobs-variables-and-credentials-and-integrate-with-SIEM-solutions)
* [How do you integrate Matillion with ticketing/ITSM for change approvals and incident tracking?](#How-do-you-integrate-Matillion-with-ticketing-ITSM-for-change-approvals-and-incident-tracking)
* [How do you design multi-region or multi-account deployments and promote artifacts programmatically?](#How-do-you-design-multi-region-or-multi-account-deployments-and-promote-artifacts-programmatically)
* [How do you share common connectors and credentials across projects while isolating secrets?](#How-do-you-share-common-connectors-and-credentials-across-projects-while-isolating-secrets)
* [How do you manage library dependencies for Python components and ensure reproducibility across environments?](#How-do-you-manage-library-dependencies-for-Python-components-and-ensure-reproducibility-across-environments)
* [How do you integrate Matillion with message queues (SQS, Pub/Sub, Service Bus) and exactly-once downstream effects?](#How-do-you-integrate-Matillion-with-message-queues-SQS-Pub-Sub-Service-Bus-and-exactly-once-downstream-effects)
* [How do you build a central parameter store or configuration database that Matillion jobs consult at runtime?](#How-do-you-build-a-central-parameter-store-or-configuration-database-that-Matillion-jobs-consult-at-runtime)
* [How do you export job definitions as JSON and analyze them to build lineage and impact analysis tools?](#How-do-you-export-job-definitions-as-JSON-and-analyze-them-to-build-lineage-and-impact-analysis-tools)
* [How do you compare Matillion’s Designer pipelines (DPC) with classic ETL jobs for team onboarding and governance?](#How-do-you-compare-Matillion-s-Designer-pipelines-DPC-with-classic-ETL-jobs-for-team-onboarding-and-governance)
* [How do you migrate from Matillion ETL (VM) to the Data Productivity Cloud and preserve pipelines and schedules?](#How-do-you-migrate-from-Matillion-ETL-VM-to-the-Data-Productivity-Cloud-and-preserve-pipelines-and-schedules)
* [How do you compare Matillion Data Loader (batch) and Matillion CDC for ongoing ingestion needs?](#How-do-you-compare-Matillion-Data-Loader-batch-and-Matillion-CDC-for-ongoing-ingestion-needs)
* [How do you validate Data Loader pipelines, monitor run status, and integrate failure alerts into your NOC processes?](#How-do-you-validate-Data-Loader-pipelines-monitor-run-status-and-integrate-failure-alerts-into-your-NOC-processes)
* [How do you implement cross-cutting concerns like PII scanning, schema validation, and DQ in reusable shared jobs?](#How-do-you-implement-cross-cutting-concerns-like-PII-scanning-schema-validation-and-DQ-in-reusable-shared-jobs)
* [How do you structure a medallion architecture in Matillion and enforce contract tests between layers?](#How-do-you-structure-a-medallion-architecture-in-Matillion-and-enforce-contract-tests-between-layers)
* [How do you surface dataset readiness signals (success flags, watermarks) to downstream consumers reliably?](#How-do-you-surface-dataset-readiness-signals-success-flags-watermarks-to-downstream-consumers-reliably)
* [How do you design table-by-table SLAs and prioritize pipelines accordingly in scheduling and resource allocation?](#How-do-you-design-table-by-table-SLAs-and-prioritize-pipelines-accordingly-in-scheduling-and-resource-allocation)
* [How do you ensure reproducibility of transformations by pinning Matillion release, warehouse versions, and SQL patterns?](#How-do-you-ensure-reproducibility-of-transformations-by-pinning-Matillion-release-warehouse-versions-and-SQL-patterns)
* [How do you manage long-running or heavy merges and minimize lock contention in the warehouse?](#How-do-you-manage-long-running-or-heavy-merges-and-minimize-lock-contention-in-the-warehouse)
* [How do you handle partition swaps or zero-downtime publish patterns for serving tables?](#How-do-you-handle-partition-swaps-or-zero-downtime-publish-patterns-for-serving-tables)
* [How do you implement snapshotting strategies and slowly-changing snapshots for audit and reproducibility?](#How-do-you-implement-snapshotting-strategies-and-slowly-changing-snapshots-for-audit-and-reproducibility)
* [How do you coordinate Matillion with warehouse-native features like Snowflake Tasks, BigQuery Scheduled Queries, or Redshift MVs?](#How-do-you-coordinate-Matillion-with-warehouse-native-features-like-Snowflake-Tasks-BigQuery-Scheduled-Queries-or-Redshift-MVs)
* [How do you expose pipeline health and data freshness to product/BI teams in a self-serve dashboard?](#How-do-you-expose-pipeline-health-and-data-freshness-to-product-BI-teams-in-a-self-serve-dashboard)
* [How do you archive unused jobs/artifacts and clean up obsolete variables, connections, and tables?](#How-do-you-archive-unused-jobs-artifacts-and-clean-up-obsolete-variables-connections-and-tables)
* [How do you prevent accidental runs in production during testing by using run permissions and safe defaults?](#How-do-you-prevent-accidental-runs-in-production-during-testing-by-using-run-permissions-and-safe-defaults)
* [How do you manage API quotas and backoffs for high-volume third-party connectors without breaching SLAs?](#How-do-you-manage-API-quotas-and-backoffs-for-high-volume-third-party-connectors-without-breaching-SLAs)
* [How do you safely process personally identifiable data and prove minimization and masking across the pipeline?](#How-do-you-safely-process-personally-identifiable-data-and-prove-minimization-and-masking-across-the-pipeline)
* [How do you design for tenant isolation so that one tenant’s pipelines cannot read or impact another’s data?](#How-do-you-design-for-tenant-isolation-so-that-one-tenant-s-pipelines-cannot-read-or-impact-another-s-data)
* [How do you compare Matillion to building ingestion with Airflow + dbt + custom code for your organization’s skill set and roadmap?](#How-do-you-compare-Matillion-to-building-ingestion-with-Airflow-dbt-custom-code-for-your-organization-s-skill-set-and-roadmap)
* [How do you present TCO and ROI for Matillion, including licenses, cloud compute, storage, and operational overhead?](#How-do-you-present-TCO-and-ROI-for-Matillion-including-licenses-cloud-compute-storage-and-operational-overhead)
* [How do you train new engineers on Matillion best practices and enforce code reviews and standards?](#How-do-you-train-new-engineers-on-Matillion-best-practices-and-enforce-code-reviews-and-standards)
* [How do you build a center-of-excellence library of shared components, connectors, and job templates?](#How-do-you-build-a-center-of-excellence-library-of-shared-components-connectors-and-job-templates)
* [How do you validate and document operational SLOs and define escalation paths for pipeline breaches?](#How-do-you-validate-and-document-operational-SLOs-and-define-escalation-paths-for-pipeline-breaches)
* [How do you plan and execute a large-scale migration of legacy ETL (Informatica/Talend/SSIS) into Matillion with minimal downtime?](#How-do-you-plan-and-execute-a-large-scale-migration-of-legacy-ETL-Informatica-Talend-SSIS-into-Matillion-with-minimal-downtime)

## What is Matillion and how does it differ from ETL/ELT tools like Fivetran, dbt, Airflow, Informatica, and Databricks for data engineering use cases?
What Matillion is (core summary)
- A cloud-native ELT/data integration platform purpose-built to load and transform data inside cloud data warehouses (Snowflake, Redshift, BigQuery, Azure Synapse).
- Runs as an instance you deploy in your cloud account and provides a GUI-driven job designer, pre-built connectors, orchestration primitives, and transformation components that typically generate and push SQL to run in the target warehouse (“pushdown” ELT). It also supports scripting (Python/SQL/Bash) and orchestration of external services.

How Matillion differs from other popular tools (feature-by-feature comparison)

1) Fivetran
- Role focus: Fivetran = fully managed, connector-first Extract+Load (EL); minimal configuration, automated schema maintenance for many SaaS sources.
- Matillion difference: Matillion provides connectors too but is a broader ELT/orchestration tool with a GUI for building transformation pipelines. Fivetran is stronger for low-touch, maintenance-free ingestion; Matillion is stronger when you need integrated transformation + orchestration and want to author transforms in a visual tool (but both can land into the same warehouse).
- Typical pattern: Fivetran (ingest) + dbt (transform) vs Matillion (ingest + transform + orchestrate) in one product.

2) dbt
- Role focus: dbt = code-first SQL transformation framework with model dependency graphs, testing, docs, and best-in-class engineering workflows (modular SQL, CI/CD).
- Matillion difference: Matillion is GUI/component-driven and generates SQL for the warehouse; it includes orchestration, connectors and some job-management features. dbt is superior for software engineering practices, testing, modularity and maintainable SQL; Matillion is preferable for teams wanting a GUI, rapid drag-and-drop builds, or integrated ingestion/orchestration without adopting a code-first workflow.
- Interop: Many teams use Matillion for ingestion/orchestration and dbt for the transformation layer when they want dbt’s governance and testing.

3) Airflow
- Role focus: Airflow = general-purpose, code-defined workflow orchestrator (DAGs) used to schedule and orchestrate arbitrary tasks across systems.
- Matillion difference: Matillion includes orchestration primitives but is specialized for ELT/data pipelines with built-in connectors and transformation components. Airflow offers more flexibility for complex, non-warehouse workflows and custom operators but requires more engineering and maintenance. Use Airflow when you need programmatic DAGs and wide ecosystem operators; use Matillion when you want turnkey ELT/warehouse-centric pipelines with less custom code.

4) Informatica (PowerCenter / Cloud)
- Role focus: Informatica = enterprise-grade ETL/metadata management platform with deep connector coverage, complex transformations, data governance and legacy/on-prem support.
- Matillion difference: Matillion is cloud-native and optimized for pushing transformations into modern cloud warehouses; it’s generally simpler and faster to deploy for cloud ELT. Informatica is more appropriate for very large, heterogeneous enterprise requirements, heavy on-prem systems, or where advanced metadata/governance/complex transformation engines are mandatory.

5) Databricks
- Role focus: Databricks = unified analytics platform (Spark-based) for large-scale distributed processing, machine learning, streaming, and Delta Lake. It’s compute-first and code-driven (not just SQL).
- Matillion difference: Matillion is not a general-purpose distributed compute engine. It relies on the target warehouse to execute heavy SQL and is optimized for SQL-based ELT. Databricks is preferable for large-scale Spark jobs, advanced ML/stream processing, complex transformations that don’t fit well into SQL pushdown, or when you need Delta Lake-style lakehouse capabilities.

Key architectural/operational contrasts
- Execution model: Matillion orchestrates and typically generates SQL executed in the warehouse (pushdown). Fivetran loads data; dbt compiles SQL run in the warehouse; Airflow orchestrates anywhere; Databricks executes distributed Spark jobs; Informatica can execute off-node ETL engines.
- UX: Matillion = GUI + low-code components; dbt/Airflow/Databricks = code-first (SQL/Python/Notebook/DAGs); Fivetran = mostly config/no-code for connectors.
- Maintenance: Fivetran is the most hands-off for connectors. Matillion requires a running instance (customer-managed VM/container) to operate. Airflow and Databricks require more operational overhead.
- Scalability & workload fit: Matillion scales by leveraging warehouse compute; it’s excellent for SQL-centric transformations. Databricks is for large-scale, non-SQL compute. Informatica targets complex enterprise data flows. Airflow is for orchestrating complex dependency graphs across systems.

When Matillion is a good fit
- You use a cloud data warehouse (Snowflake/Redshift/BigQuery/Synapse) and want integrated ingestion, ELT transformations, and orchestration in one product.
- You prefer a GUI/low-code environment for building transforms and pipelines.
- You want transformations to leverage the warehouse compute (pushdown SQL) rather than managing separate cluster infrastructure.
- You need built-in connectors and basic orchestration without building a lot of custom code.

When to choose something else
- Need fully managed, zero-maintenance ingestion at scale with minimal engineering — Fivetran.
- Need production-grade SQL engineering, testing, modularity and CI/CD — dbt.
- Need flexible, code-driven orchestration for arbitrary workloads — Airflow.
- Enterprise on-prem / heavy governance / deep connector and metadata needs — Informatica.
- Need large-scale distributed compute, streaming, or ML-focused pipelines — Databricks.

Limitations of Matillion to be aware of
- Requires hosting an instance in your cloud (not purely serverless).
- Not designed for heavy Spark-style distributed processing; best when transformations can be pushed to the warehouse.
- GUI approach can be less suited to teams that require full programmatic control and code-centric workflows (though Matillion supports Git integration and scripting).

Summary
Matillion is a specialist ELT/orchestration platform optimized for cloud data warehouses and rapid pipeline construction via a GUI, whereas the other tools either specialize in connectors (Fivetran), code-first transformations and testing (dbt), general orchestration (Airflow), enterprise ETL/governance (Informatica), or distributed compute/lakehouse workloads (Databricks). Choice depends on your architecture, scale, team skillset, and whether you prefer low-code GUI pipelines or code-driven engineering practices.

[Top](#top)

## How do Matillion ETL (VM-based) and Matillion Data Productivity Cloud (Designer, Data Loader, CDC) compare in architecture and capabilities?
Short answer
- Matillion ETL (VM-based) is a full-featured, customer‑hosted ELT orchestration and transformation engine installed in your cloud account (EC2/VM). It’s aimed at enterprise-grade, complex pipelines, CI/CD, and deep operational control.
- Matillion Data Productivity Cloud (the SaaS suite: Designer, Data Loader, CDC) is a Matillion‑hosted, self‑service SaaS stack focused on rapid ingestion, simple visual transformations and change-data-capture. It’s optimized for quick onboarding, SaaS-source loading, and point-to-point CDC/ELT flows.

Detailed comparison (by area)

1) Architecture & deployment
- Matillion ETL (VM)
  - Deployed into your cloud account (AWS/Azure/GCP) as a VM/instance in your VPC/subnet.
  - You control VM sizing, networking, IAM, backups, and patching. Single‑tenant runtime.
  - Jobs run in the VM orchestrator but generate SQL/commands that execute in the target data warehouse (ELT pushdown).
- Data Productivity Cloud (Designer, Data Loader, CDC)
  - SaaS, Matillion‑hosted multi‑tenant service. No VM to manage.
  - Runs in Matillion infrastructure; connectors reach into your sources/targets over secure connections (VPC peering, private link or public endpoints as applicable).
  - Each app is optimized for its purpose (ingest, mapping, CDC) and integrates with cloud warehouses.

2) Primary capability focus
- Matillion ETL (VM)
  - Orchestration + transformation (complex ELT workflows).
  - Rich component library (orchestration tasks, transformation components, scripting: Python, Bash), advanced branching, loops, error handling.
  - Designed for complex multi-step pipelines, cross‑service orchestration, and heavy transformations that leverage warehouse SQL.
- Data Productivity Cloud
  - Data Loader: self‑service ingestion for SaaS/DB sources into warehouses with templates and scheduling.
  - Designer: low‑code, visual transformation/mapping for analysts and data engineers.
  - CDC: continuous replication/change capture for near‑real‑time loading into a warehouse or staging layer.
  - Emphasis on rapid setup, simplicity, and standardized patterns rather than deep orchestration complexity.

3) Data movement & transformation model
- Both follow ELT principles (use target warehouse compute for heavy transformations), but:
  - ETL (VM) is broader in orchestration capabilities and complex SQL generation/pushdown controls.
  - Data Loader/Designer provide simpler mapping UIs, auto-generated SQL, and curated patterns for common data flows.

4) Real‑time / CDC
- Matillion ETL (VM)
  - Can perform frequent batch jobs and orchestrate CDC processes but is not a dedicated SaaS CDC product.
- Matillion CDC (part of Data Productivity Cloud)
  - Purpose‑built for continuous replication/low-latency streaming of changes from transactional sources into warehouses/staging.
  - Easier setup and management for ongoing replication; SaaS‑managed capture/replication pipelines.

5) Connectors & sources
- ETL (VM): very broad connector set exposed via components and custom connectors; good for APIs, cloud services, and on‑prem/SSH sources (depending on networking).
- Data Loader/CDC: focused connectors for common SaaS apps, databases and transactional systems with prebuilt templates; CDC targets transactional DBs.

6) Scalability & performance
- ETL (VM): scale by sizing the VM and relying on warehouse compute for heavy SQL; for very large orchestration needs you may manage multiple instances or design job partitioning.
- Data Productivity Cloud: Matillion manages scaling of the SaaS components; performance for transformations still relies on the target warehouse.

7) Security & compliance
- ETL (VM): you manage security posture — VPC, NSGs, IAM roles, cloud-level encryption, key management. Credentials stored in instance; network isolation is under your control.
- Data Productivity Cloud: Matillion manages infrastructure security and compliance (Matillion provides compliance/attestation info like SOC2); you still control where connectors go and credentials are stored securely by Matillion. Options often exist for private connectivity (VPC peering/Private Link) depending on platform.

8) DevOps, versioning & collaboration
- ETL (VM): mature features — Git integration, branches, promotions across environments, parameterized environments, staging/production separation. Better suited to CI/CD workflows.
- Data Productivity Cloud: Designer/Data Loader are built for speed and self-service; collaboration features exist but the enterprise DevOps toolset is less extensive than the VM product.

9) Extensibility & custom logic
- ETL (VM): supports Python, Bash, custom SQL, user‑defined components, job chaining—more extensible for bespoke logic.
- Designer: low‑code mapping with transformation nodes and some scripting, but designed to hide complexity. Data Loader is even more template-driven.

10) Monitoring, logging & operations
- ETL (VM): detailed job logs, history, audit trails, notifications, retry logic; you host log retention and integration with your monitoring stack.
- Data Productivity Cloud: SaaS dashboards, run history, alerts; Matillion provides operational console and Matillion-managed retention. Less host-level log control.

11) Typical use cases
- Matillion ETL (VM)
  - Complex, enterprise-grade pipelines that require advanced orchestration, CI/CD, custom scripting, and deep integration into your cloud environment.
  - Teams that need full control over networking/security and versioned deployments.
- Data Productivity Cloud (Designer, Data Loader, CDC)
  - Fast onboarding of SaaS data sources, self‑service ingestion, simple visual transformations, and continuous replication from transactional DBs.
  - Analytic teams that want minimal ops overhead and quick time-to-value.

12) Licensing & cost model (high level)
- ETL (VM): instance license + cloud VM/infra costs. You pay for the VM size and storage you provision.
- Data Productivity Cloud: subscription (SaaS) pricing, often per-seat or per‑usage/connector tiers. Matillion handles infra costs. Check Matillion for exact commercial models.

How they work together
- Common pattern: use Data Loader/CDC for fast, managed ingestion and ongoing replication into the warehouse, then use Matillion ETL (VM) for downstream complex orchestration, transformations, enrichment, and production workflows. Designer can be a middle ground for teams wanting visual transformations without full VM management.

Caveats & decision pointers
- Choose VM-based ETL when you need enterprise controls, advanced orchestration, and custom extensibility.
- Choose Data Productivity Cloud when you want SaaS simplicity for ingestion, rapid developer/analyst enablement, or managed CDC with minimal ops.
- Evaluate connector coverage, networking options (private connectivity), governance/DevOps needs, and SLA/compliance requirements before selecting.

No further text.

[Top](#top)

## When would you choose Matillion ETL on a VM versus Matillion’s SaaS (DPC) and why?
Short answer
- Choose Matillion SaaS (DPC) when you want Matillion to manage the control plane, reduce operational overhead, get automatic upgrades and centralized multi-team governance, and you can allow outbound connectivity to Matillion’s managed service.
- Choose Matillion ETL on a VM when you need complete control of the runtime/control plane location (data residency), strict network isolation or compliance (air‑gapped/GovCloud/HIPAA/PCI), custom networking to private sources, or you must manage instance sizing and OS patching yourself.

Why — key tradeoffs

1) Operational responsibility
- SaaS (DPC): Matillion manages the control plane, upgrades, availability, and many administrative tasks. Less internal ops work.
- VM: You manage the instance(s), OS patching, Matillion upgrades (unless you use auto‑update patterns), backups and scaling.

2) Security, compliance & connectivity
- SaaS (DPC): Requires outbound connectivity to Matillion’s managed control plane. Good for cloud-first environments with standard internet access and enterprise SSO.
- VM: Keeps full control in your VPC/tenant—preferred when policy forbids external control planes, when using private endpoints, or for strict compliance/regulatory requirements.

3) Data locality and network topology
- SaaS (DPC): Best when workloads can use cloud-native connectors and don’t require fully private-only access.
- VM: Necessary when you must run in the same private network as data sources (on‑prem databases, private S3, private Snowflake endpoints) or use VPN/peering with non‑internet accessible systems.

4) Multi-account / multi-team management
- SaaS (DPC): Easier centralized administration, cross-environment governance, license management, and collaboration for many teams/accounts.
- VM: You’ll typically deploy and manage instances per account/region and handle cross-account governance yourself.

5) Feature cadence and support
- SaaS (DPC): Faster access to new features and fixes; Matillion controls releases and support.
- VM: You may lag on features until you apply upgrades; gives you control over timing of changes.

6) Cost and procurement
- SaaS (DPC): Subscription model; lower infra/ops overhead but recurring SaaS fees.
- VM: VM compute costs + Matillion license (marketplace/bring-your-own-license); might be cheaper for predictable heavy workloads but requires ops resources.

When to pick each (concise scenarios)
- Pick SaaS (DPC) if you want rapid onboarding, centralized management across multiple clouds/accounts, minimal internal ops, and your security policy allows a managed control plane.
- Pick VM if you require strict data residency, private network-only access, air‑gapped or government deployments, or you must control exact instance configuration and maintenance windows.

Quick decision checklist
- Is outbound connectivity to Matillion permitted? No → VM.
- Do you need on‑prem or private‑only data access? Yes → VM.
- Do you want Matillion to handle upgrades, uptime, and central governance? Yes → SaaS (DPC).
- Do you have strict regulatory/GovCloud requirements? Likely VM (validate with compliance teams).
- Are you managing many teams/accounts and want centralized control? SaaS (DPC) generally wins.

Final note
Both options run Matillion functionality; the choice is primarily about where you want the control plane and operational responsibility to live, and whether your network/compliance posture allows a managed SaaS control plane.

[Top](#top)

## How does Matillion implement ELT pushdown and which components execute in-warehouse versus on the Matillion host?
Matillion implements ELT pushdown by generating and submitting SQL (or native warehouse commands) to the target cloud data warehouse, and running almost all set-based transformation logic inside that warehouse. The Matillion instance (host) acts as the orchestration/control plane — it builds the SQL, stages files when needed, triggers warehouse load and query jobs, and runs any components that cannot be expressed as pushdown SQL.

High-level mechanics
- Transformation components build a directed graph of operations and compile that graph into SQL (or into the warehouse’s native DDL/DML/load commands). That SQL is sent to the warehouse and executed there (pushdown).
- Loading usually uses cloud-native bulk-load mechanics: stage files to S3/GCS/Azure Blob (or use PUT/COPY for Snowflake), then issue COPY/LOAD/COPY INTO/BigQuery load jobs in the warehouse.
- Matillion does not stream large volumes of data through the instance; the heavy lifting (compute and I/O) occurs in the data warehouse.

What runs in-warehouse (executed by the target database)
- All generated transformation SQL: SELECTs, JOINs, GROUP BY/Aggregations, Window functions, CTAS/CREATE TABLE AS, INSERT/UPDATE/MERGE statements produced by transformation components.
- Bulk load/unload commands (COPY, COPY INTO, BigQuery load jobs, Snowflake PUT/COPY workflows, Redshift COPY).
- Warehouse-native functions and UDFs invoked in the generated SQL.
- Where applicable, warehouse-managed compute (e.g., Spark on Databricks when Matillion triggers jobs/notebooks) — Matillion will invoke the remote execution but the heavy compute runs inside that platform.

What runs on the Matillion host (control plane / non-pushdown components)
- The Matillion application, web UI, job engine, job metadata and scheduler.
- Orchestration components and control-flow logic (If, Wait, Run Task, Trigger, Job orchestration, notifications).
- Components that cannot be converted to pushdown SQL: Python script components, Bash/OS-level scripts, custom scripts and local transformations, file manipulation (zip/unzip, file system operations), encryption/decryption, REST API calls that fetch external data, SFTP/FTP transfers, some connectors that stage data through the instance.
- Uploading/staging to cloud storage when orchestration components are used to put files into S3/GCS/Blob; these use the Matillion instance to perform the API calls, but the subsequent bulk load is executed by the warehouse.
- Small metadata queries or control queries issued by Matillion to manage jobs or check object existence — these are light-weight control SQL but initiated by the host.

Common patterns / examples
- Typical ELT: Orchestration job downloads or receives a file (SFTP/API) -> uploads it to S3/GCS/Blob (host does API call) -> Matillion issues a COPY/LOAD command to the warehouse -> transformation job compiles SQL and runs transformations in-warehouse.
- When you need custom Python logic that cannot be expressed in SQL, the Python component runs on the Matillion host and that processing happens outside the warehouse.

Exceptions/notes
- Some connectors or components may stage data via cloud storage rather than pulling everything through the instance; the exact staging behavior can vary by connector and target warehouse.
- For platforms with their own compute (Databricks), Matillion may invoke remote jobs/notebooks so execution occurs in that remote compute environment rather than the Matillion host.

Summary
- Pushdown principle: Matillion pushes set-based work as SQL to the warehouse and leverages the warehouse’s compute/storage.
- Matillion host: orchestration, GUI, control logic, file/API connectors, and any components that cannot be expressed as pushdown SQL.

[Top](#top)

## Which components or patterns break pushdown and how do you minimize non-pushdown operations?
Short answer: anything that forces Matillion to process rows outside the target database breaks pushdown. Common culprits are scripts, iterators, API/file downloads, and components that materialize or generate data in the Matillion engine. Minimize them by pushing logic into SQL (CTE/CTAS/MERGE), using bulk loads, staging everything in the target, and replacing row-by-row patterns with set-based SQL.

Which components/patterns typically break pushdown (with why)
- Python Script, Bash Script, R Script components — execute on the Matillion instance, so data must be pulled out of the warehouse into Matillion memory for processing.
- Iterators / For Each / While loops — often perform many small queries or row-by-row operations rather than a single set-based SQL statement.
- Grid / Row Generator / Inline values — generate data in Matillion, forcing downstream components to materialize that data locally.
- API Query / HTTP/REST connectors (when they fetch data into Matillion) — data comes from outside the warehouse and needs loading before DB operations.
- Components that explicitly extract data to files or local staging (S3 download local, file transforms performed in Matillion) — these create a break in the ELT chain.
- Any transformation that uses a function or algorithm not supported natively by the target DB (complex Python-only logic, custom libraries) — Matillion cannot translate it to SQL.
- Per-row lookup/update patterns (e.g., lookups implemented as repeated DB calls) — they result in many round-trips instead of a single SQL join/update.
- Preview/sample operations during development (data preview that pulls rows locally) — not a runtime problem, but can give the impression of non-pushdown.

How to minimize non-pushdown operations (tactical rules and examples)
- Prefer ELT (SQL) components: use Table Input, DB Query, Select, SQL Script, CTAS/INSERT AS SELECT, MERGE/UPSERT. Convert multi-step transforms into one SQL statement or CTE chain.
  - Example: replace a Matillion iterator that updates 100 tables one-by-one with a single MERGE or set-based UPDATE that handles all rows.
- Stage everything in the target warehouse first: load API/file data into staging tables (COPY/LOAD), then run SQL transforms against staging inside the DB.
  - Example: use the target’s bulk COPY command to load S3/Blob data, then run a SQL job to parse/transform using JSON functions.
- Replace per-row operations with joins and window functions: use SQL JOINs, windowed aggregates, array/JSON functions rather than lookups that iterate row-by-row.
  - Example: instead of a Lookup component that queries per row, create a mapping table in the DB and join it in a single query.
- Avoid Matillion-side scripts for logic that the DB supports: leverage native SQL functions (JSON, regex, date math, UDFs) instead of Python parsing.
  - Example: use Snowflake’s PARSE_JSON and FLATTEN rather than downloading JSON and using Python to parse.
- Consolidate smaller components into a single SQL Script component when possible: many small transformations can often be fused into one CTAS/SELECT. This reduces intermediate materialization.
- Use temporary tables in the database, not Matillion memory: if you need intermediate results, create transient/temp tables in the warehouse to keep all processing server-side.
- Use bulk operations for loads/updates: use COPY, bulk insert, or vendor-specific bulk utilities rather than row-by-row inserts.
- Validate pushdown capability per component and target dialect: consult component docs and test SQL preview/validation to ensure Matillion generates SQL for the component and that the target supports the functions used.
- If you must use scripts, limit data size and scope: run them only for small control tasks or metadata operations; push heavy lifting back into SQL.
- Replace iterators with set-based SQL or stored procedures in the target where a loop is unavoidable but can be implemented server-side.

Detecting and verifying pushdown
- Check component documentation for “pushdown” support and whether it generates native SQL for your target.
- Use SQL preview / generated SQL in Matillion to verify work is translated into a single SQL statement or CTAS.
- Monitor network/DB metrics: many small queries or high data egress indicates non-pushdown behavior.

When non-pushdown is unavoidable
- Keep the non-pushdown work small and isolated (small datasets, metadata tasks).
- Run it on a suitably sized Matillion instance (enough memory/CPU).
- Consider moving complex logic into database-side user-defined functions or stored procedures so execution remains inside the warehouse.

Concise rule of thumb: if Matillion needs to iterate rows, call external APIs, or run custom code on its own instance, pushdown is broken. Design transforms as set-based SQL executed in the warehouse to retain pushdown.

[Top](#top)

## How do orchestration jobs differ from transformation jobs and how do you decide where logic belongs?
Short answer
- Orchestration jobs manage control flow and external operations: extract, move, stage, load, call APIs, handle files, invoke cloud services, schedule and chain jobs, and perform notifications/monitoring.
- Transformation jobs contain the data logic that runs inside the target warehouse: set-based SQL operations (joins, aggregates, CTEs, MERGE/UPSERT), data modeling, cleansing and enrichment. Matillion transformation components compile into SQL that is executed by the target database.

Detailed differences
- Execution target:
  - Orchestration: runs on the Matillion runtime and orchestrates external systems (S3, APIs, cloud storage, file system, Snowflake/Redshift/BigQuery bulk load commands, Python scripts, etc.).
  - Transformation: compiles to SQL and runs in the data warehouse engine (push-down processing).
- Purpose:
  - Orchestration: move and stage data, manage workflow, handle file formats and transfer, perform bulk loads, maintain job state, handle retries/notifications.
  - Transformation: implement the business logic and data model—transform staged data into cleansed, conformed tables and marts.
- Components:
  - Orchestration components include S3 Put/Get, API Query, Download File, Run Orchestration Job, Run Transformation Job, Python Script, Create/Delete File, Snowflake/Redshift Load components.
  - Transformation components are things like Table Input, Filter, Join, Calculator, Aggregate, Merge — all creating SQL.
- State & idempotency:
  - Orchestration typically handles stateful concerns (staging table lifecycle, checkpoints).
  - Transformation should be idempotent, set-based, and re-runnable since it’s executing SQL in the warehouse.

How to decide where logic belongs (rules of thumb)
- Put in orchestration when:
  - It involves external systems: API calls, file transfers, decompress/encrypt, cloud storage management.
  - You need to orchestrate job flow, retries, notifications, or environment-specific operations.
  - You’re performing bulk load operations (COPY/PUT) and file staging before SQL processing.
  - Logic is procedural or script-like (looping over files, polling).
  - You need centralized job control, conditional branching or runtime orchestration across many jobs.
- Put in transformation when:
  - It’s set-based data processing: joins, aggregations, window functions, dedupe, merges (UPDATE/MERGE/UPSERT).
  - Performance is best achieved by pushing work into the warehouse engine.
  - You’re implementing data model logic (staging → core → marts), business rules, derived fields.
  - You need easier lineage/traceability for SQL-based transformations.
- Mixed/edge cases:
  - Incremental loads: orchestration can extract and stage deltas; transformation performs the MERGE/UPSERT and dedupe in-warehouse.
  - Data validation: orchestration can run quick checks and route failures; transformation can produce detailed validation queries and exception tables.
  - Lightweight transformations (simple column renames or casts) can be done during load in orchestration if it simplifies flow, but prefer transformation for maintainability.

Design best practices
- Separation of concerns: use orchestration for movement & control, transformation for modeling and business logic.
- Keep orchestration jobs lean — don’t implement heavy set-based SQL inside orchestration; call transformation jobs to run SQL in the warehouse.
- Make transformation jobs modular, idempotent, and parameterized. Expose reusable components and templates.
- Use staging tables: orchestration lands raw data to staging; transformations clean and conform.
- Optimize for push-down: leverage the warehouse engine’s strengths; avoid row-by-row processing in Matillion where SQL will perform better.
- Error handling & observability: use orchestration for retries, notifications, and operational logging; have transformation write audit/version info into tables if needed.
- Cost/performance trade-offs: pushing more work into the warehouse increases compute usage — balance cost with performance.

Concrete example
- API → S3 → Warehouse:
  - Orchestration job calls API, writes JSON/CSV to S3, triggers a Snowflake COPY command (or uses Matillion S3 Load), then calls a transformation job.
  - Transformation job reads staged table(s), performs joins/aggregations/dedup, and writes to final tables using SQL MERGE.

Summary checklist
- External systems, file ops, bulk load, orchestration logic → Orchestration job.
- SQL-based set operations, modeling, merges, performance-sensitive processing → Transformation job.

[Top](#top)

## How do you organize projects, folders, shared jobs, and naming conventions for maintainability and reuse?
Project organization and naming in Matillion should make intent obvious, minimize duplication, and enable safe promotion between environments. Key principles: keep jobs small and single-purpose, parameterize behavior, centralize shared logic, enforce consistent naming, and version-control everything. Concrete guidelines:

Project strategy
- One project per deployment lifecycle strategy:
  - Recommended: Git-backed project per environment (dev/test/prod) OR single Git-backed project with branches mapped to environments. Choose one and stick to it.
  - Use Matillion Environments for credentials/connection details so the same job code moves cleanly between environments.
- Use a dedicated "Shared Library" project (or a top-level Shared folder) for cross-project reusable jobs/components if multiple projects need exactly the same routines.

Folder structure (example)
- /Orchestration
  - /Ingest
    - /<SourceSystem> (API, S3, DB)
  - /Load (landing → staging)
  - /Publish (move to warehouse)
- /Transformation
  - /Staging
  - /EDW (subject-area folders: Sales, Finance, HR)
  - /Marts (dependent business marts)
- /Common (shared utilities)
  - /Checks (data quality)
  - /Helpers (generic orchestration sub-jobs)
  - /Templates (reusable parameterized jobs)
- /Deprecated or /Archive (for retired jobs)
- /Tests (unit / integration jobs)

Shared jobs and reuse
- Use Matillion Shared Jobs or a Shared Library project to publish reusable orchestration/transformation routines.
- Build small, parameterized shared jobs (ingest chunk, load partition, retry logic, send alert) rather than monolithic multi-purpose jobs.
- Use Project Variables and Environment Variables to keep shared jobs generic: the job takes variables for table names, schema, file patterns, etc.
- Expose a small, well-documented parameter surface on shared jobs (name, type, required/optional).
- Maintain a versioning policy for shared jobs: include a version parameter or use Git tags/releases of the Shared Library project.
- Wrap shared behavior in idempotent jobs with clear error handling and logging so they can be safely reused.

Naming conventions (principles)
- Prefix by job type: ORC_, TRF_, CHK_, UT_, LIB_, API_, ING_, LND_, STG_, MAT_ (or other consistent tokens).
- Include system/domain and purpose: <TYPE>_<DOMAIN>_<OBJECT>_<ACTION>_<VERSION?>. Examples:
  - ORC_INGEST_SALES_API_v1
  - TRF_STG_SALES_ORDER_TO_FACT
  - CHK_STG_NULLS_CUSTOMER
  - LIB_RETRY_WRITE_S3
- Use Pascal or snake case consistently; avoid spaces and special characters.
- For variables: PROJECT_<name> for project variables, ENV_<name> for environment variables. Example: PROJECT_SALES_SCHEMA, ENV_DB_HOST.
- For components: COMP_<purpose> or keep them in the /Common folder and name by function: COMP_SEND_EMAIL.

Parameterization and variables
- Keep environment-specific values in Matillion Environments (connection strings, buckets, credentials).
- Use Project Variables for project-wide constants (schemas, owner emails, default batch sizes).
- Use Job Variables for run-specific values.
- Always document variable purpose and allowed values in the job description or a README in the folder.

Version control and deployments
- Use Git integration for every project. Commit frequently and use feature branches for changes.
- Map branches to lifecycle (develop, qa, release, main) or have per-environment branches depending on chosen strategy.
- Use automated promotion (CI/CD) to deploy released branches or tagged commits to higher environments.
- Store shared library in Git too, and require change reviews for shared jobs.

Operational practices for maintainability
- Keep jobs single-responsibility and short; break complex flows into orchestration that calls small transformation jobs.
- Add descriptive job descriptions and document input/output contracts at the top of jobs (variables, expected tables).
- Include logging, audit rows, and metrics in orchestration jobs (start/end timestamps, row counts).
- Implement standard error handling patterns (centralized retry, alert job).
- Create a lightweight test job per subject area to validate transforms after deployment.
- Use folder-level naming/versioning when deprecating (move to /Deprecated and add a deprecation date in the job description).

Access control and governance
- Restrict edit rights on Shared Library and /Common folders; allow read-only for consumers.
- Use Git reviews for changes to shared logic.
- Maintain a CHANGELOG and ownership metadata for critical shared jobs.

Examples (compact)
- ORC_ING_SALES_CRM_LOAD — orchestration: ingest CRM data
- TRF_STG_SALES_CRM_TO_ORDER_FACT — transformation: stage → EDW fact
- CHK_DATA_QUALITY_STG_CUSTOMER — data quality check job
- LIB_SEND_ALERT_EMAIL_v2 — shared utility job

Follow these conventions consistently and enforce via templates, onboarding docs, and code reviews so maintainability and reuse become predictable.

[Top](#top)

## How do environments work in Matillion and how do you parameterize connections per dev/stage/prod?
Short answer
- A Matillion Environment is the container for all environment-specific settings: connection definitions (DW, cloud storage, etc.), environment variables, and cloud credentials. You create one Environment per dev/stage/prod and switch the active Environment in the UI; jobs/components reference names/variables and therefore resolve differently per Environment.
- Parameterize connections either by (A) creating same-named connections in each Environment (simple and common) or (B) by using Environment Variables inside a single connection definition (more explicit and flexible). Mark secrets as encrypted and keep naming consistent.

How it works (details)
- Environment object: holds connection definitions, Environment Variables, credentials (IAM/keys), and other environment-scoped settings. Switching the active Environment in Matillion causes jobs to use that Environment’s connections/variables.
- Scope of variables: define variables at Environment or Project level (use Environment variables for env-specific values like endpoints and passwords). Use encrypted variables for secrets.
- Connection resolution: components/jobs reference a connection by name. That name is resolved to the connection object defined in the currently active Environment; if the connection fields themselves use variables, those variables are resolved from the current Environment.

Two practical approaches

1) Same-named connections per environment (recommended for simplicity)
- In each Environment (Dev, QA, Prod) create a connection with the same logical name (for example "SNOW_DW").
- Fill in environment-specific host/user/password/warehouse/etc. in that Environment.
- Jobs reference "SNOW_DW" and will automatically connect to the appropriate resource when you switch Environments.

Pros: simple, minimal change to jobs.
Cons: connection definition duplication.

2) Variable-driven connections (recommended for fine-grained control)
- In the connection properties use placeholders referencing Environment Variables, e.g.:
  - Account: ${SNOW_ACCOUNT}
  - User: ${SNOW_USER}
  - Password: ${SNOW_PWD} (mark this variable encrypted)
  - Database: ${SNOW_DB}
- In each Environment, define SNOW_ACCOUNT, SNOW_USER, SNOW_PWD, SNOW_DB with the environment-specific values.
- Jobs reference the connection name; the connection resolves using the Environment Variables from the active Environment.

Pros: single connection definition in project, easy to audit and manage differences.
Cons: slightly more setup; make sure all variables exist in each Environment.

Concrete example (Snowflake)
- Create Environment variables in Dev:
  - SNOW_ACCOUNT=dev-account
  - SNOW_USER=dev_user
  - SNOW_PWD (encrypted)=dev_password
  - SNOW_DB=dev_db
- Create similar variables in Prod with prod values.
- Create a Snowflake connection whose fields are ${SNOW_ACCOUNT}, ${SNOW_USER}, ${SNOW_PWD}, ${SNOW_DB}.
- Switch Environment to Prod and jobs will use prod credentials.

Operational tips / best practices
- Keep connection names consistent across Environments so jobs don’t need conditional logic.
- Use Environment Variables for endpoints and Project variables for values shared across Environments.
- Mark sensitive variables as encrypted (secure) in Matillion.
- Use the Matillion REST API or export/import to automate propagating variable definitions across Environments for CI/CD.
- Test by switching the Environment in the UI to validate jobs pick up the right connections.
- Keep secrets out of Git by storing them as Environment-level encrypted variables rather than hard-coding in jobs.

Answer format like this maps cleanly to dev/stage/prod workflows: create one Environment per stage, externalize credentials/endpoints via Environment Variables, and reference connection names consistently in jobs.

[Top](#top)

## What are the different variable types (environment, job, grid, fixed) and how do you scope and secure them?
Short, interview-style breakdown of the four Matillion variable types, scoping/precedence, and how to secure them.

1) Environment variables
- Purpose: environment-specific configuration (DB host/port, environment credentials, S3 bucket names, endpoints).
- Scope/lifecycle: defined per Environment (Manage Environments). Available to every job that runs in that Environment. Persistent until changed.
- Use cases: values that change between dev/test/prod but must be consistent across many jobs.
- Security: mark the variable as Secure (checkbox) so Matillion masks and encrypts the stored value. Control who can edit environments via Matillion roles/permissions (only give Manage Environments to admins). For secrets prefer external secret stores (AWS Secrets Manager/Azure Key Vault/GCP Secret Manager) and fetch at runtime rather than embedding long-lived credentials.

2) Job variables
- Purpose: job-local values such as runtime parameters, iteration counters, dynamic dates, batch IDs.
- Scope/lifecycle: defined at the Job level (Job properties or Manage Variables within the job). Available only inside that job and the components it runs. Not automatically exposed to other jobs unless explicitly mapped/passed.
- Use cases: values that vary run-to-run or are specific to that orchestration/transformation.
- Security: can also be marked Secure for masking/encryption. Limit who can edit jobs via role permissions. When calling sub-jobs, map variables deliberately instead of relying on global state.

3) Grid variables
- Purpose: row/column style data used by Grid Iterator / Iterator-like components (used to iterate across lists of values).
- Scope/lifecycle: created/used by iterator components and exist only within the iterator’s scope during that run/iteration; not global or persistent after the iteration completes.
- Use cases: table/list of items to loop over (e.g., list of tables, schema/table pairs, partition values).
- Security: avoid putting secrets into grid data. If you must, treat values as sensitive and, where possible, retrieve secrets from a secure store inside the iteration. Grid variables are ephemeral so they’re less of a risk at rest, but they can still be visible in job logs or component configs — secure the job and component-level access.

4) Fixed variables
- Purpose: design-time constants that should not change between environments or runs (true constants).
- Scope/lifecycle: defined with Fixed scope and intended as immutable/config constants at design time.
- Use cases: fixed strings or IDs that are part of the job design (e.g., application-level constants).
- Security: if they contain sensitive info you can mark them Secure, but best practice is to keep secrets in Environment variables or (preferably) external secret stores.

Variable resolution/precedence (practical rules)
- Typical precedence: Job variables override Environment variables; Environment variables override Fixed variables. Grid variables are scoped to the iterator and will shadow other variables inside that iterator’s scope.
- When invoking a sub-job, variables are not automatically inherited unless you explicitly map/pass them (use the Run Orchestration / Run Transformation component’s variable mapping).

How to secure variables in Matillion (practical checklist)
- Use the Secure checkbox when creating variables to mask values in the UI and have Matillion encrypt the metadata entry.
- Restrict who can edit variables/environments/jobs via Matillion user roles and permissions (Admin → Manage Roles / Environment permissions).
- Avoid storing long-lived secrets in Matillion when possible. Use cloud secret stores (AWS Secrets Manager, Azure Key Vault, GCP Secret Manager) and fetch at runtime using built-in connectors or API calls.
- Minimize exposure: keep secrets in Environment or a secure external store, not in grid data or logs; avoid printing variable values in logging components.
- Audit and rotate: enable logging/auditing of changes and rotate credentials regularly.
- Rely on cloud provider encryption: ensure the Matillion metadata DB and the underlying cloud resources use encryption-at-rest and secure network access.

Quick examples of good practice
- Put DB host, non-sensitive config in Environment variables.
- Put per-run parameters (execution date, batch id) in Job variables.
- Put iteration lists in Grid variables (Grid Iterator) and don’t put secrets there.
- Keep true constants as Fixed only if they truly won’t change; otherwise use Environment variables for environment-specific constants.

End.

[Top](#top)

## How do you use grid variables to build metadata‑driven pipelines that iterate over tables and sources?
High-level pattern
- Create a Grid project variable that holds the metadata rows you want to iterate (columns like source, schema, table, query, target_table, incremental_flag, etc.).
- Populate that grid from whatever metadata source you have (manual entry, a CSV/JSON file, a metadata table, an API call, or a DB query).
- In an orchestration job use a Grid Iterator to loop over the grid rows.
- Inside each iteration call a Transformation (or run components directly) and reference the current row’s columns as variables to build SQL, table names and component properties.
- Add audit/error handling logic (success/fail grid, retry, logging) so you can track each row.

Concrete steps

1) Define the grid variable
- Project → Variables → New Variable
- Type = Grid
- Define columns (example): source, src_schema, src_table, incremental_sql, target_table, pk_column

2) Populate the grid
Options:
- Store metadata in a database table and fetch it at runtime. Have an orchestration job run a DB Query that returns the metadata rows and write those rows into the grid variable (common pattern: use a Database Query component that supports storing its result into a grid variable or use a small Python Script component to set the grid variable from query results).
- Load a CSV/JSON file containing metadata and transform it into the grid (use file-read + a small script or component to convert the file resultset to the grid).
- Manually populate for simple cases via the variables UI.

3) Iterate with Grid Iterator
- Add a Grid Iterator (Orchestration). Point it at the grid variable.
- Within the iterator every column becomes readable for the current row. Use those columns to parameterize downstream components and job calls.

4) Reference grid columns inside components
- Use the grid column tokens in SQL, component fields and job parameters to make everything dynamic.
- Example (pseudo-SQL inside a Transformation job invoked from the iterator):
  SELECT * FROM ${src_schema}.${src_table} WHERE ${incremental_sql}
- Or pass ${src_schema}, ${src_table} as Job Parameters when calling a Transformation job from the iterator and use those params inside that job.

5) Call a Transformation job (typical pattern)
- Inside the Grid Iterator, use Run Transformation or Run Orchestration to execute a child job that does the actual extract/load/transform.
- Map grid columns to job parameters (source/schema/table etc.). The child job uses those parameters to build dynamic components (Table Input SQL, Target table name, staging paths, etc.).

6) Logging and error handling
- Wrap the per-row processing in try/catch logic (or use a conditional to trap errors from the child job).
- Capture row-level success/failure into an audit grid (append row with status, start/end time, error text).
- Optionally continue on error or stop the entire job depending on your SLA.

Example metadata-driven flow (summary)
- Orchestration job:
  1. Database Query: SELECT schema, table_name, pk, incremental_sql FROM metadata.my_tables WHERE enabled = true
  2. Put query result into grid variable TablesGrid
  3. Grid Iterator (TablesGrid)
     - Run Transformation Job “load_table” with parameters: schema=${TablesGrid.schema}, table=${TablesGrid.table_name}, pk=${TablesGrid.pk}, incr_where=${TablesGrid.incremental_sql}
     - On success append to AuditGrid with status=OK
     - On failure append to AuditGrid with status=ERROR and error message
  4. At end, write AuditGrid to a table or file.

Notes on referencing and quoting
- Use the grid column tokens in component fields and SQL. Ensure you handle quoting/escaping for schema/table names and NULLs.
- If you build SQL strings, use Set Variable components to assemble the SQL and then reference that variable in a Database Query or Table Input.

Advanced patterns and tips
- Parallelism: Matillion’s Grid Iterator is sequential by default. If you need parallel loads, spawn multiple child jobs in parallel (careful with DB/concurrency limits). One pattern: split the grid into N chunks and start N concurrent orchestration jobs, each processing its chunk.
- Small metadata footprint: store only pointers/identifiers in the grid (names, queries), not big payloads.
- Incremental logic: keep incremental_sql or last_run columns in the grid; update metadata table after successful load and refresh grid next run.
- Dynamic component properties: most Matillion component fields accept variables — you can dynamically change queries, table names, S3 paths, file names, etc.
- Use audit and retry policies for idempotency: capture row-level state and allow retry of failed rows.

Common pitfalls
- Forgetting to escape identifiers when constructing fully-qualified names.
- Large grids: grids are in-memory — if you have millions of rows don’t use a grid for row-level iteration; instead break into batches or process in-database.
- Passing complex JSON in grid cells: prefer IDs and fetch heavy metadata inside the child job to avoid bloating the grid.

This pattern keeps the orchestration generic and lets you onboard new tables/sources by changing metadata only, not job code.

[Top](#top)

## How do you pass variables between jobs and manage defaults, overrides, and secrets?
Key concepts
- Variables are defined in Project → Manage Variables. Types: Text, Integer, Boolean, Password (secure). Each variable has a default value and is referenced in jobs as ${variable_name}.
- Runtime values can override defaults via the Run Job dialog, the API/scheduler, or via orchestration components. You can change variables during execution with the Set Variable component.
- Secrets: use the Password type (encrypted and masked in the UI) or pull secrets from your cloud secrets manager (AWS Secrets Manager, Azure Key Vault, GCP Secret Manager) using Matillion components/integration.

How to pass variables between jobs
- Parent → Child
  - Run Orchestration (or Run Transformation) component: open the component’s Properties and provide mappings for the child job’s variables. You can set mappings to literal values or expressions using the parent’s variables (e.g. child_var = ${parent_var}).
  - Alternatively, use project-scoped variables: parent sets a project variable (Set Variable) and the child reads ${that_variable}. This is simpler but uses a global variable rather than explicit parameter passing.
- Child → Parent (returning values)
  - Have the child Set Variable on a project-scoped variable before finishing. The parent reads that project variable after the Run Orchestration completes.
  - Or expose explicit “output” variable mapping by having both jobs use a named project variable and mapping it via Run Orchestration, rather than relying on ephemeral local state.
- Local (job-only) variables
  - Variables created/used only inside a job via Set Variable are effective for that runtime; to hand values out you must write them to a project variable or pass them explicitly into the caller.

Managing defaults and overrides
- Default values: set in Manage Variables when you create the variable. That value is used unless overridden.
- Per-run overrides:
  - Manual: Run Job dialog → Variables tab to supply runtime values.
  - API/Scheduler: supply a JSON payload with variable overrides when invoking a job.
  - Within a parent job: map variables in Run Orchestration to override values passed into the child.
- Set Variable component: change a variable mid-run (overrides the current value for the rest of that run).
- Precedence: runtime overrides (API/Run dialog/parent mapping) and Set Variable during execution take precedence over the stored default.

Handling secrets
- Use Password variable type for secrets. These are stored encrypted, masked in the UI, and not displayed in clear text.
- Better: store secrets in a secrets manager (AWS Secrets Manager / Azure Key Vault / GCP Secret Manager) and fetch them at runtime with Matillion’s secrets integration or a REST/Cloud component. This centralizes rotation and auditing.
- Do not log secrets or return them as output variables. When passing secrets between jobs, pass references or use project Password variables, and avoid printing them in any component that emits logs.
- When passing secrets via Run Orchestration, map the child’s secure variable to a secure project variable or to the secret fetched at runtime; do not inline literal secrets in component properties.

Example patterns (pseudo)
- Define in Manage Variables:
  - api_url (Text, default = https://api.example)
  - environment (Text, default = dev)
  - db_password (Password, default = <empty>)
- Parent job:
  - Set Variable api_token = result_of_auth_call
  - Run Orchestration → ChildJob: map child_input_token = ${api_token}
- Child job:
  - Use ${child_input_token} in calls
  - Set Variable return_count = <calculated_count>
- Parent reads ${return_count} after the Run Orchestration completes.

Best practices
- Use clear naming to indicate scope and intent (parent_input_, child_output_, secret_).
- Prefer secrets manager + transient retrieval rather than hard-coding secrets into project variables where possible.
- Keep variables project-scoped only when you need cross-job access; otherwise keep values local to the job run using Set Variable.
- Never write secrets to logs or return them in job outputs. Use Password type and secrets manager for production credentials.

[Top](#top)

## How do you manage credentials securely (Matillion credential manager, cloud secret stores, KMS/Key Vault/Secret Manager)?
Core principles
- Never embed plaintext secrets in jobs, scripts or Git. Use a managed secret store and reference secrets at runtime.
- Apply least-privilege IAM: Matillion should have just the permissions needed to retrieve secrets and access downstream systems.
- Prefer short-lived credentials, federated identities or key-pairs over long-lived username/passwords when supported (e.g., cloud DB IAM auth, Snowflake key-pairs).
- Use customer-managed encryption keys (CMKs) for high‑sensitivity secrets and enable rotation/auditing.
- Keep secret access auditable and automated: centralized secret stores, rotation policies, and cloud audit logs.

Matillion options and recommended pattern
- Matillion Credential Manager (built‑in):
  - Purpose: convenient place in the Matillion UI to store connection credentials and connection strings that jobs reference.
  - Security model: values are stored encrypted at rest and masked in the UI. Use it for non-sensitive metadata or when external secret stores are not available.
  - Limitations: credentials live in the Matillion instance. For stronger operational controls and centralized rotation/audit, prefer cloud secret stores.
  - Best practice when used: restrict Matillion user roles (only admins should create/view credentials) and do not check credential-containing XML/JSON into Git.

- External cloud secret stores (recommended):
  - AWS Secrets Manager / SSM Parameter Store, Azure Key Vault, GCP Secret Manager:
    - Store all secrets there; configure Matillion to fetch at runtime instead of storing them locally.
    - Use instance/service identities (EC2 instance role, Azure Managed Identity, GCP service account/workload identity) so Matillion can access secrets without embedded keys.
    - Grant minimal permissions (secretsmanager:GetSecretValue or secretmanager.versions.access; plus kms:Decrypt if using CMKs).
    - Enable automatic rotation where available, and rotate secrets used by Matillion on a schedule or with trigger-based rotation.

How to implement per cloud (concise steps)
- AWS (Secrets Manager + KMS)
  1. Put DB/service credentials into AWS Secrets Manager. Use a CMK for encryption if required.
  2. Give the Matillion EC2 instance role permission secretsmanager:GetSecretValue and kms:Decrypt for that secret/CMK.
  3. In Matillion, configure the connection to use Secrets Manager reference (or use an environment variable that holds the secret ARN and call AWS CLI/SDK from a Secure Script if needed).
  4. Prefer IAM-based DB connections (Redshift IAM auth) where possible to avoid static DB passwords.

- Azure (Key Vault + Managed Identity)
  1. Store secrets in Azure Key Vault.
  2. Enable a System or User Assigned Managed Identity on the Matillion VM.
  3. Grant that identity Key Vault access policy/role for get/list secrets.
  4. In Matillion, reference Key Vault secrets (via built‑in connector support or script using MSI/Tokens).

- GCP (Secret Manager + Workload Identity)
  1. Store secrets in Secret Manager.
  2. Attach a service account to the Matillion GCE instance or use Workload Identity; grant secretmanager.versions.access.
  3. Configure Matillion connections to read secrets via Secret Manager API.

KMS / Key Vault / CMK usage
- Use customer-managed keys (AWS KMS, Azure Key Vault keys, Cloud KMS) to control and audit encryption of secrets.
- Use CMKs to:
  - Protect secrets in Secrets Manager/Key Vault.
  - Enable key rotation policies and separate key admins from secret admins.
- Ensure Matillion has decrypt rights only — store keys and audit usage centrally.

Operational controls and hardening
- RBAC: restrict who can create, edit, or view credentials in Matillion. Ensure only approved admins can unmask secrets.
- Audit/Logging: enable cloud audit logs for secret access and KMS usage; funnel into SIEM.
- Rotation: automate credential rotation and test job workflows to handle rotated credentials. Prefer short TTL tokens.
- Secrets in pipelines/CI: store pipeline/service account credentials only in the cloud secret store or CI secret vault; do not store in Matillion project repositories.
- Network: restrict Matillion and downstream systems with VPC, private networking, and firewall rules; prevent secrets retrieval from unauthorized networks.
- Least privilege: use dedicated service accounts/roles per environment (dev/stage/prod) and per system.

Matillion job-level patterns
- Use Credential Manager entries that reference external secrets (where Matillion supports direct integration) rather than plaintext variables.
- Use environment variables (secure/hidden) only for non-shared, instance-specific references (e.g., secret ARN or Key Vault URL), but keep actual secrets in the cloud vault.
- For components that require API keys, pass secrets at runtime via Get Variable / Get Credentials functionality without writing them to logs.
- Avoid printing secrets in logs. Scrub or mask log output and disable verbose logging for components handling secrets.

Example secure flow (AWS)
- Secrets in Secrets Manager encrypted with a CMK.
- Matillion EC2 role has secretsmanager:GetSecretValue + kms:Decrypt.
- Jobs reference a Credential Manager entry that points to the Secrets Manager ARN.
- Secrets rotate automatically; rotation lambda updates secrets; Matillion reads new value on next job run.

Summary (concise)
- Prefer cloud secret stores with managed identity access and CMKs over Matillion-local storage.
- If using Matillion Credential Manager, lock it down with strict RBAC and do not store long-lived secrets in code or repos.
- Enforce least privilege, rotation, and audit logging; prefer short-lived/federated credentials when available.

[Top](#top)

## How do you configure SSO (SAML/OIDC) and RBAC in Matillion and enforce least privilege by environment?
High-level approach
- Use your IdP for authentication and group claims; Matillion enforces authorization via its Groups/Permissions model.
- Configure SAML 2.0 or OIDC in Matillion Admin to accept the IdP, map IdP groups/claims to Matillion Groups, and then assign least-privilege permissions to those Matillion Groups on a per-environment basis.
- Keep an emergency local admin account and audit logs enabled.

SAML (SAML 2.0) — configuration steps (typical)
1. Prepare in IdP:
   - Create a new SAML app/enterprise application (Okta, ADFS, Azure AD SAML, etc.).
   - Set Assertion Consumer Service (ACS) / Single Sign-On URL to the Matillion SAML endpoint shown in Matillion Admin (instance-specific).
   - Set Audience / Entity ID to the Matillion value from Admin.
   - Configure NameID to Email (or preferred unique identifier).
   - Pass group membership as an attribute (e.g., "groups" or "memberOf") containing the IdP group names you will map.
   - Export IdP metadata (certificate, SSO URL, entity ID).

2. Configure Matillion:
   - Admin → Authentication / Identity Provider → choose SAML.
   - Upload IdP metadata (or paste SSO URL and certificate).
   - Configure Matillion entity ID / ACS if required.
   - Map SAML attributes to Matillion fields (NameID to username/email; groups attribute to Matillion groups).
   - Optionally enable Just-In-Time (JIT) user creation and set default group(s) for new users.

3. Group mapping:
   - Create Matillion Groups (Platform Admin, Project Admin, Environment-Dev-User, Environment-Prod-Viewer, etc.).
   - Map IdP group names (from SAML attribute) to Matillion Groups in the mapping UI or via automatic group import if supported.

4. Test:
   - Use a test user in the IdP that is a member of specific groups and verify Matillion login and correct privileges.

OIDC — configuration steps (typical)
1. Prepare in IdP (OIDC provider like Azure AD, Okta, Google):
   - Register a client application.
   - Set Redirect/Callback URI to the Matillion OIDC callback URL (Matillion Admin shows it).
   - Request scopes: openid, profile, email and groups (if supported).
   - Record Client ID and Client Secret.
   - Configure group claims in token/claims (group names or role claims).

2. Configure Matillion:
   - Admin → Authentication / Identity Provider → choose OIDC/OpenID Connect.
   - Enter Provider metadata / issuer URL, Client ID and Client Secret, and required scopes.
   - Map claims: sub/email to username, groups claim to Matillion groups.
   - Optionally enable JIT provisioning and default groups.

3. Group mapping and testing:
   - Same as SAML — map IdP groups to Matillion Groups and test login.

Matillion RBAC concepts and steps
- Matillion objects: System (instance), Projects, Environments, Jobs, Components.
- Matillion Groups: core unit of authorization. Assign users to groups (via IdP mapping or manual).
- Permissions are granted at different scopes: instance-level (admin/system), project-level, environment-level.
- Typical group role design:
  - Platform/System Admin: full access to Matillion instance (use sparingly).
  - Project Admins: manage projects, jobs, and deployments for a specific project.
  - Environment Admins: can edit environment configuration, credentials, and run jobs in that environment.
  - Developers: create and edit jobs in dev/staging environments, limited or no prod access.
  - Operators/Run-only: allowed to execute jobs in a specific environment but not edit.
  - Viewers/Auditors: read-only access to projects and job run history.

Enforcing least privilege by environment — practical patterns
- Environment-specific groups:
  - Create groups per environment-team pair: e.g., data-dev-engineers, data-staging-operators, data-prod-ops.
  - Map IdP groups (or create mapping rules) so users only receive memberships for environments they should access.

- Grant minimal effective permissions:
  - Developers: give Edit/Create on dev environments and Projects, no execute or credential-edit on prod.
  - Staging: allow run + test privileges, restrict credential edits.
  - Production: allow only a small set of Operator and Environment Admins to run production; no editing of job definitions or environment credentials except by dedicated release engineers.
  - Use "execute only" where available for run-only operators.

- Protect credentials and environment configuration:
  - Restrict Environment Admin permission tightly — only people who must manage connections get it.
  - Use dedicated service accounts for automated runs; map those to a minimal group with only run permissions for the target environment.

- Use separate projects or branches for dev vs prod:
  - Keep dev work in separate projects and only promote tested artifacts to prod (via deployment jobs or CI/CD).

- Require MFA and enforce session controls at the IdP for prod access:
  - Use IdP policies to require stronger auth for groups mapped to production Matillion Groups.
  - Use conditional access (Okta/AD) to restrict which endpoints/users can access production.

- Audit and logging:
  - Enable Matillion audit logs and send them to central logging (CloudWatch/Stackdriver/Azure Monitor) for monitoring.
  - Periodically review group membership mappings and Matillion group permissions.

Operational details and gotchas
- Always retain at least one local Matillion admin account for emergency lockout recovery.
- IdP group names must match Matillion mapping exactly (case sensitivity can matter). Normalize or use claims transformation if necessary.
- JIT provisioning is convenient but review default groups assigned to new users to avoid over-privilege.
- When changing SSO config, test with a non-production instance or a small pilot group.
- For automated tooling (CI/CD), use service accounts with client credentials (OIDC client or a dedicated Matillion user with very limited scope).
- If you need automated group sync beyond SAML/OIDC claims, consider whether your IdP supports SCIM (Matillion may not natively support SCIM; use IdP-side management or scripts).

Example mapping scenario (concise)
- IdP groups: data-team-dev, data-team-staging, data-team-prod.
- Matillion Groups: data-dev-developers (Edit+Run on Dev env), data-staging-operators (Run on Staging env), data-prod-operators (Execute-only on Prod env).
- Map IdP group -> Matillion Group via SAML/OIDC group claim mapping.
- Assign environment permissions per Matillion Group accordingly; deny project edit in prod groups.

Testing and validation
- Create test users per group, verify SSO login and that only the intended environments and actions are available.
- Validate credential edit restrictions by attempting to modify environment credentials with different role users.
- Review audit trail after tests to confirm actions are logged.

This yields an SSO-authenticated Matillion where authorization is driven by IdP group claims mapped into Matillion Groups and then scoped to environments with least-privilege assignments.

[Top](#top)

## How do you isolate teams and tenants using projects, environments, IAM roles, and network segmentation?
Goal-first summary
- Use Projects and Environments for logical separation and credential scoping.
- Enforce access control with Matillion roles (mapped from SSO groups) + cloud IAM (instance roles / service accounts / assume-role).
- Enforce network-level isolation with VPC/subnets, security groups, private endpoints, and per-tenant network boundaries.
- Choose a deployment pattern (single instance multi-tenant, multi-project with strict role mapping, or one-instance-per-tenant) based on security requirements and operational cost.

How the Matillion constructs map to isolation controls
- Projects: logical containers for Jobs/Orchestration/Transforms. Use Projects to separate team or tenant assets, limit who can open/modify those Jobs via Matillion roles.
- Environments: contain connection definitions (credentials, connection endpoints) and environment-specific variables. Use separate Environments per tenant and per lifecycle (dev/test/prod) so credentials and endpoints are scoped and not shared.
- Matillion roles & SSO group mapping: use Matillion’s role model (Administrator/Developer/Operator/Viewer or custom roles) and map external SAML/IdP groups (Azure AD/G Suite/Okta) to those roles. That enforces UI access and Project visibility.
- Cloud IAM / service accounts: use cloud-native identities (AWS IAM roles, GCP service accounts, Azure Managed Identity/service principal) to control access to data sources and cloud storage. Give Matillion instances or specific runtime components minimal privileges, and use assume-role patterns for per-Environment credential separation.
- Network segmentation: place Matillion and target data stores in controlled VPC/subnets and use security groups, private endpoints (VPC endpoints, PrivateLink, Private Endpoint), peering or Transit Gateway, and firewall rules to limit access to only the Matillion subnet(s).

Recommended patterns (trade-offs)
1) Logical multi-tenant (cost-effective, medium isolation)
- Single Matillion instance.
- Projects per team/tenant.
- Environments per tenant+stage (e.g., TenantA-prod, TenantA-dev).
- Use SSO group -> Matillion role mappings so users only see their Projects and Environments.
- Use IAM role assumption (or service account impersonation) per Environment so credentials used for S3/warehouse access are tenant-scoped.
- Network: place Matillion in a subnet that can reach all tenant data stores via fine-grained security groups and endpoint policies.
- Pros: low infra overhead, centralized management. Cons: risk of privilege misconfiguration, weaker blast radius.

2) Network-isolated multi-tenant (stronger network isolation)
- Single Matillion instance but with multiple network interfaces or NAT/peering selectively allowing different Environments to reach only their tenant resources.
- Use PrivateLink/VPC endpoints and per-tenant security group rules on target data stores.
- Use IAM roles per Environment and encrypted secrets; restrict which Environments can assume which roles.
- Pros: good network control, lower cost than full instance-per-tenant. Cons: more complex network setup.

3) Full isolation per tenant (highest security)
- Deploy one Matillion instance per tenant (can be in separate cloud account/VPC).
- Each instance has its own Projects/Environments, instance IAM role, KMS key, and network boundary.
- Authentication via tenant IdP mapped to that instance or centrally federated.
- Pros: maximal isolation and compliance-friendly. Cons: higher cost and operational overhead.

Concrete controls and best practices
- Project & Environment assignment
  - Make Projects team/tenant-specific. Use naming conventions (tenant-team-project).
  - Create separate Environments per tenant and per lifecycle. Never share production credentials across Environments.
- Credentials & secret management
  - Do not hard-code credentials in Jobs. Store credentials in Environment definitions or in cloud secrets manager.
  - If using cloud secrets manager, grant Matillion instance/service account only decrypt/get secrets permissions for the appropriate secrets.
  - Use KMS-managed encryption keys per tenant where compliance requires separation.
- IAM least privilege
  - Use least-privilege IAM roles/service accounts. Prefer role assumption per Environment so runtime access is tenant-scoped.
  - Use temporary credentials/STS where supported.
  - Limit Matillion EC2/GCE/VM instance role to only what it needs; do not give blanket S3 or DB privileges.
- SSO & role mapping
  - Integrate with SAML/IdP and map IdP groups to Matillion roles to enforce project and environment visibility.
  - Use IdP group membership to control who can create or deploy changes (restrict create/deploy to a smaller admin/devops group).
- Network-level controls
  - Host Matillion in private subnet or limit UI access via security groups + IP allowlists or use a bastion or VPN.
  - Use VPC endpoints (S3, Secrets Manager) and endpoint policies to restrict data-plane access.
  - Place target warehouses/databases in private subnets and lock access to Matillion subnets via security groups or private link endpoints.
  - For cross-account access, use VPC peering, Transit Gateway, or cross-account IAM roles with tight trust policies.
- Audit, logging and monitoring
  - Enable Matillion audit logs and push job/activity logs to centralized logging (CloudWatch, Stackdriver, Azure Monitor).
  - Enable cloud audit trails (CloudTrail, equivalent) to track IAM role assumptions and secret access.
  - Tag resources for tenant and environment for cost and security reporting.
- CI/CD and promotion
  - Use distinct Environments for CI/CD promotion; avoid sharing production connections in lower environments.
  - Store infrastructure and project artifacts in version control and enforce role-based deployment approvals.
- Emergency access & backups
  - Have break-glass admin accounts stored securely and audited.
  - Back up Projects and configuration regularly and encrypt backups per tenant.

Example mapping
- Team A (TenantA)
  - Projects: tenantA_sales, tenantA_ops
  - Environments: tenantA_dev, tenantA_prod
  - Environment credentials: use tenantA-prod IAM role (assume-role) that only allows S3 bucket tenantA-* and Redshift/warehouse access for TenantA.
  - Matillion access: IdP group TenantA-Developers -> Matillion Developer role with visibility of TenantA Projects only.
  - Network: TenantA_prod Environment uses a subnet that has security group allowing outbound to TenantA DB endpoint only.
- Team B (TenantB) same pattern, with different roles and different subnet or different IAM role trust.

When to pick which pattern
- Regulated / high-risk tenants: use instance-per-tenant or separate accounts with unique keys and VPCs.
- Medium risk with cost sensitivity: logical multi-tenant + strict IAM + network endpoint policies.
- Low-risk / internal teams: Projects + Environments + SSO role mapping + shared instance.

Trade-offs summary
- Logical separation (Projects + Environments + roles) is quick and low-cost but relies on flawless IAM/SAML mapping and secrets handling.
- Network segmentation hardens attack surface and reduces lateral movement risk but increases networking complexity.
- Full-instance isolation gives the best blast-radius guarantee at the cost of provisioning and management overhead.

Implementation checklist
- Define tenancy model (logical vs full isolation).
- Create Projects and Environments per tenant+stage.
- Integrate IdP and map groups to Matillion roles.
- Implement per-Environment IAM role/service-account and secret scoping.
- Harden network: private subnets, security groups, private endpoints, restrict UI access.
- Enable logging/auditing and apply resource tagging.
- Document runbooks for deployments, cross-account role assumptions, and incident response.

[Top](#top)

## What cloud permissions are required for Matillion ETL (instance profile/service principal) to access S3/ADLS/GCS and warehouses?
Short, role-focused lists you can use for Matillion ETL instance profiles / service principals / service accounts. Assume least-privilege: scope permissions to the specific bucket/container/bucket prefix, key, dataset, cluster, secret, etc.

AWS (Matillion running on EC2 / IAM Instance Profile)
- S3 (read/write): s3:ListBucket (on bucket), s3:GetObject (on bucket/*), s3:PutObject (on bucket/*), s3:DeleteObject (if deletes required), s3:GetBucketLocation. If you use versioned buckets and need versions: s3:GetObjectVersion.
- KMS (if bucket encrypted with CMK): kms:Decrypt, kms:Encrypt, kms:GenerateDataKey, kms:DescribeKey (scope to the key ARN).
- Redshift / COPY & UNLOAD:
  - If Matillion pushes data to S3 and Redshift pulls via COPY: either attach an IAM role to the Redshift cluster with S3 permissions OR allow Matillion to pass an IAM role to Redshift: iam:PassRole (on the role ARN) plus the S3 perms above (if Matillion itself writes to S3).
  - Matillion connects to Redshift over JDBC with DB credentials — no special AWS API actions required for the JDBC connection.
- Athena / Glue / Spectrum:
  - Athena: athena:StartQueryExecution, athena:GetQueryExecution, athena:GetQueryResults, athena:GetWorkGroup; result location requires S3 access as above.
  - Glue (for Data Catalog/Spectrum): glue:GetDatabase, glue:GetTable, glue:GetPartition, glue:GetTableVersion, glue:GetDatabases; glue:CreateTable only if you create tables.
- Secrets Manager (if storing DB credentials there): secretsmanager:GetSecretValue (scope to the secret ARN).
- Additional: ec2:DescribeInstances or sts:GetCallerIdentity rarely needed — Matillion rarely requires it except for diagnostics.

Azure (Matillion running on Azure VM / Managed Identity / Service Principal)
- ADLS Gen2 (read/write): grant RBAC at container or storage-account level:
  - Storage Blob Data Reader (read/list): Microsoft.Storage/storageAccounts/blobServices/containers/blobs/read equivalents (roles/storage.blobDataReader).
  - Storage Blob Data Contributor (write/delete): roles/storage.blobDataContributor (storage.objects/create, storage.objects/delete).
  - Minimal actions: Microsoft.Storage/storageAccounts/blobServices/containers/blobs/read, write, delete, list, and Microsoft.Storage/storageAccounts/listKeys only if using account key auth (avoid account keys and prefer SPN/managed identity).
- Key Vault (if keys used for encryption or storing secrets): key vault permissions - get/list for secrets (Microsoft.KeyVault/vaults/secrets/get) and unwrapKey/decrypt for keys (if CMEK).
- Synapse / Azure SQL / Synapse Serverless:
  - JDBC connectivity uses DB credentials. If Synapse must access ADLS directly (COPY/EXPORT), give Synapse managed identity or the service principal Storage Blob Data Contributor on the target container.
- Azure Active Directory (for service principal): Application permissions limited to sign-in/usage for the SPN; do not grant broad directory permissions.
- Azure Key Vault for DB credentials: vault/secrets/get scoped to secret.
- If Matillion needs to create role assignments or manage resources: Microsoft.Authorization/roleAssignments/write (avoid unless required).

GCP (Matillion running on GCE / Service Account)
- GCS (read/write):
  - Read: storage.objects.get, storage.objects.list (or roles/storage.objectViewer).
  - Write: storage.objects.create (or roles/storage.objectCreator).
  - Delete: storage.objects.delete (or roles/storage.objectAdmin if you need full control).
  - Bucket metadata: storage.buckets.get for bucket-level operations.
- KMS (if using CMEK): cloudkms.cryptoKeyDecrypt, cloudkms.cryptoKeyEncrypt, cloudkms.cryptoKeys.get (scope to the key resource).
- BigQuery:
  - Submit jobs: bigquery.jobs.create (or roles/bigquery.jobUser).
  - Dataset/table access: bigquery.dataViewer, bigquery.dataEditor, or bigquery.dataOwner depending on read/write needs; for load jobs you need bigquery.tables.updateData or bigquery.tables.create as appropriate.
  - If staging to GCS, ensure the service account also has the necessary GCS rights on the staging bucket.
- Secret Manager (if used): secretmanager.access (secret manager access version e.g., secretmanager.versions.access).
- Snowflake on GCP: Snowflake uses its own credentials or storage integration; if using a GCS stage for Snowflake, give the Snowflake integration SA storage.objects.get and storage.objects.create as needed (this is Snowflake-side setup; Matillion only needs Snowflake DB credentials).

Snowflake specifics (all clouds)
- Matillion connects over JDBC using a Snowflake user; Matillion needs DB privileges to run loads/queries (CREATE STAGE/USAGE/WRITE depending on workflow).
- If using external stages on S3/ADLS/GCS: the cloud-side role/identity used by Snowflake must have the object storage permissions described above (S3 perms, Storage Blob Data Reader/Contributor, or GCS object viewer/creator). Matillion itself does not need extra cloud API perms for Snowflake stages beyond whatever credentials it stores to connect to Snowflake.

General recommendations / notes (brief)
- Scope to resource ARNs/IDs and prefer managed identities/service accounts over long-lived keys.
- Include KMS/KeyVault/CMEK decrypt/encrypt permissions if encryption-at-rest with customer keys is used.
- Provide secrets access permission only to the exact secret resource (secretsmanager:GetSecretValue, keyvault/secrets/get, secretmanager.versions.access).
- For JDBC warehouse connections (Redshift, Snowflake, Synapse, BigQuery) Matillion typically needs only network access and DB credentials; cloud API permissions are only required when Matillion or the warehouse must read/write cloud object storage on your behalf.

[Top](#top)

## How do you use private endpoints/VPC endpoints to keep data plane traffic private for storage and warehouses?
Goal: keep Matillion data-plane traffic between the Matillion instance and cloud storage / warehouses on the cloud provider’s private network (no public internet egress).

High-level approach
- Deploy Matillion as a data-plane instance inside your VPC / VNet / VPC network (private subnets, no public IPs if possible).
- Create provider-native private endpoints for each target service (S3 gateway endpoints or PrivateLink/interface endpoints on AWS; Private Endpoints / Private Link for Azure; Private Service Connect / VPC Service Controls / Private Google Access on GCP).
- Configure DNS so service hostnames resolve to the private endpoint IP(s).
- Configure Matillion connections to use the private hostnames (or the standard hostnames if private DNS rewrites them).
- Harden security: security groups, endpoint policies, IAM role/policies, Key Management access.

AWS — practical details
- S3: create a Gateway VPC Endpoint for com.amazonaws.<region>.s3 and attach to the route tables used by Matillion subnets. With the gateway endpoint, standard s3:// paths will use the private endpoint automatically.
- Other AWS APIs Matillion uses: create Interface Endpoints (AWS PrivateLink) for services used by Matillion: sts, kms, secretsmanager, glue, ec2 (if needed). Enable “Private DNS” on these endpoints so standard hostnames resolve to the endpoint IPs.
- Warehouses:
  - Redshift: launch the Redshift cluster in the same VPC (or a VPC peered with Matillion VPC). Use the cluster’s internal endpoint; secure with SGs.
  - Snowflake on AWS: use Snowflake PrivateLink (account-specific PrivateLink endpoints). Configure DNS to point to PrivateLink hostname and use that endpoint in Matillion Snowflake connection.
  - Databricks: use VPC peering or PrivateLink (depending on offering) so Matillion connects via private IP to the workspace JDBC endpoint.
- IAM / Roles: prefer instance profile/EC2 role for S3 access so credentials need not traverse public internet. Lock down endpoint policies to restrict principals and prefixes.

Azure — practical details
- Deploy Matillion VM inside your VNet (Matillion AMI in Azure or Azure VM).
- Storage: create Private Endpoints for Blob/ADLS Gen2 and link Private DNS Zones (blob.core.windows.net, dfs.core.windows.net) to your VNet so default storage account hostnames resolve privately.
- Warehouses:
  - Azure Synapse / SQL Data Warehouse: create Private Endpoints and associated private DNS zones so the SQL endpoints resolve inside your VNet.
  - Azure Databricks: use VNet injection / Private Link depending on workspace config.
- Key Vault & Managed Identity: use Private Endpoint for Key Vault and use managed identity for authentication from the Matillion VM.
- Ensure subnet NSG rules permit outbound to the private endpoint IP ranges; no NAT required if all service access is via private endpoints.

GCP — practical details
- Deploy Matillion VM (or Google Marketplace instance) into a VPC subnet.
- Cloud Storage: enable Private Google Access and configure Private Service Connect for Cloud Storage APIs (or use VPC Service Controls to restrict access).
- BigQuery: use Private Service Connect for BigQuery APIs (or VPC Service Controls + Private Google Access). For connectors that require public endpoints, use Cloud NAT only if absolutely required and restrict via firewall rules.
- Snowflake on GCP: use Snowflake Private Connectivity options (Provider-specific Private Service Connect or PrivateLink equivalent).
- IAM: use service accounts attached to the instance and restricted IAM roles for Cloud Storage / BigQuery.

Matillion-specific configuration notes
- Matillion instance itself does not require special “private endpoint” settings for S3 once the VPC endpoint and DNS are in place — S3 requests resolve to the gateway endpoint automatically.
- For JDBC connectors (Snowflake, Redshift, Synapse, Databricks), specify the private hostname/endpoint returned by the private connectivity configuration or rely on private DNS to resolve the normal hostnames to private IPs.
- For secrets and credentials, use Secrets Manager / Key Vault / Secret Manager via their private endpoints; configure Matillion to retrieve credentials from those services using private access.
- If using instance profiles / managed identities, ensure Matillion is running with the correct instance profile/service account and that endpoint policies allow the instance principal.

Security and hardening
- Use security groups / NSGs to restrict inbound/outbound to only required warehouse and storage endpoint IPs and ports.
- Use endpoint policies (AWS) or equivalent to restrict which S3 buckets or APIs the endpoint can access.
- Encrypt traffic with TLS (private endpoints still use TLS). Validate certificates if you pin certs or use custom hostnames.
- Use KMS/Key Vault integration over private endpoints for encryption key access.
- Audit with VPC Flow Logs, CloudTrail/Azure Monitor/Cloud Logging to ensure no unexpected public egress.

Testing and troubleshooting checklist
- From Matillion instance, verify DNS resolution: hostname should resolve to endpoint private IP(s).
- Test TCP connectivity: telnet/ssldump/nc to the endpoint port.
- Confirm requests hit endpoint: check endpoint metrics and flow logs.
- If access fails: check route tables, endpoint subnet association, SG/NSG rules, endpoint policy, private DNS zone linkage.
- For fully-private setups, ensure Matillion’s control-plane interactions (if SaaS control plane used) are either permitted by whitelisting control-plane IPs or use an architecture Matillion recommends for “air-gapped/isolated” deployments.

Limitations & operational notes
- Some managed SaaS warehouses require provider-specific Private Link configurations that may involve account-level setup and DNS changes.
- Matillion control-plane (SaaS) interactions may still require outbound connectivity for license/management; verify Matillion’s documentation for control/data plane split and whitelist control-plane IPs if needed.
- Cross-VPC access requires VPC peering, Transit Gateway, PrivateLink, or VPN/Direct Connect/ExpressRoute; plan routing and DNS accordingly.

Summary
Deploy Matillion into your private network, attach the appropriate provider private endpoints (gateway/interface/PrivateLink/Private Service Connect), configure DNS and connection hostnames, use instance IAM/service accounts for auth, and lock down security groups and endpoint policies so all storage and warehouse traffic stays on the provider’s private network.

[Top](#top)

## How do you backup and recover Matillion ETL projects, metadata, and configurations across regions or accounts/subscriptions?
Short answer
- Use Matillion project export or Git integration for job definitions; take VM/image snapshots for full instance state; back up Matillion metadata DB (or dump project JSONs) and any instance encryption/keystore; externalize secrets to cloud secret stores. Combine these so you can rebuild or copy to another region/account and re-import projects and secrets.

What you must back up
- Project definitions (jobs, shared components, environment variables, schedules) — the primary logical artifacts.
- Matillion metadata/encryption material — anything that encrypts stored credentials or ties projects to an instance.
- Instance-level configuration (OS-level changes, installed drivers, custom packages, scheduler state).
- External resources referenced by jobs (connection endpoints, JDBC drivers, S3 buckets, VPC configs, IAM roles).
- Credentials/secrets — either exported securely or stored in an external secret manager.

Methods and details

1) Project export / import
- Use Matillion’s Project → Export to create project JSON archive(s). Store these in S3/Azure Blob/GCS or in your artifact repository.
- Import into another Matillion instance via Project → Import.
- Exports are the simplest way to move projects across accounts/regions.

2) Git integration (recommended for CI/CD and cross-account moves)
- Link Matillion projects to an external Git repo (Bitbucket/GitHub/Azure Repos).
- Push job definitions to Git; clone/pull from the target Matillion instance to recreate projects.
- This provides versioning and controlled promotion between environments and regions.

3) Instance images / snapshots (for full instance recovery)
- Create AMIs (AWS), VM images (Azure), or machine images/snapshots (GCP) regularly to capture the running Matillion instance, configuration files, drivers, local files, and the embedded metadata store.
- Copy AMI/images to other regions or account (share AMI or copy image).
- Use images to recover identical instances quickly.

4) Metadata DB backup
- If Matillion uses an embedded PostgreSQL (or a separate metadata DB), schedule regular DB dumps (pg_dump) or snapshot the DB filesystem. This preserves state that might not be captured by project exports (instance-specific metadata).
- Restore the DB dump on the target instance or rehydrate from the image snapshot.

5) Encryption keys and credentials handling
- Matillion encrypts stored credentials using an instance-specific key/keystore. Exports or images may not yield usable decrypted passwords on a new instance unless you restore the encryption key or re-enter credentials.
- Two options:
  - Externalize secrets into AWS Secrets Manager / Azure Key Vault / GCP Secret Manager and reference them from Matillion (preferred).
  - Back up and restore the Matillion keystore/encryption key along with instance images and import it on the target instance (follow Matillion docs for exact keystore file locations and secure handling).

6) Automation: REST API and scripting
- Use Matillion REST API or CLI to script project export/import, list projects, and automate backups to object storage.
- Combine with cloud automation (Lambda, Functions, Cloud Scheduler) to regularly push exports/snapshots off-instance.

Recovery/migration steps (across region or account)
1. Provision target Matillion instance (same Matillion version).
2. Restore instance image or install Matillion and apply any OS-level/configuration changes.
3. Restore metadata DB or import project JSONs / clone from Git.
4. Restore or import keystore/encryption material if needed to recover encrypted credentials, or rewire credentials to a secret manager and reconfigure connections.
5. Recreate or attach IAM roles, VPC/subnet and security group settings, service endpoints, and any external dependencies (databases, S3/Blob containers).
6. Validate jobs, schedules, and run smoke tests.

Caveats and best practices
- Credentials encryption: passwords may not be recoverable on new instance unless keystore is restored or secrets externalized. Treat this as a core design consideration.
- Version compatibility: restore to the same Matillion version to avoid incompatibilities.
- Test restores regularly — don’t rely solely on backups without recovery drills.
- Use Git for lightweight, auditable cross-account/region promotion; use images for quick full-instance recovery.
- Minimize sensitive data in project exports; keep secrets in secure, central secret stores.
- Maintain access controls and encryption for exported artifacts (object storage, images).

Quick checklist to implement now
- Enable project Git integration and push all projects to repo.
- Schedule automated project exports to secure object storage.
- Take and replicate VM images/AMI snapshots to target regions/accounts.
- Back up metadata DB (pg_dump/snapshots).
- Move secrets into cloud secret manager and configure Matillion to reference them.
- Document and test the restore/migration steps.



[Top](#top)

## How do you handle high availability and disaster recovery for Matillion ETL instances and job state?
Short answer: treat the Matillion instance as replaceable infrastructure and treat the project repository and credentials as the state that must be highly available/backed up. Use cloud HA tools (Multi‑AZ DB, images/snapshots, automation) + Git/project exports + idempotent job design so you can failover or rebuild quickly and resume work safely.

Details

1) Instance availability (Matillion application)
- Don’t attempt active‑active Matillion on a single project. Assume a single primary application instance and make recovery fast.
- Build the instance from an immutable image/template (AMI, Azure VM image, GCP image) and store launch templates/CloudFormation/ARM/Terraform definitions so you can recreate an instance quickly.
- Use provider features for availability of the VM (EBS-backed snapshots, automatic backup, placement in AZ as appropriate). Use an Elastic IP / DNS CNAME so a new instance can assume the service endpoint quickly.
- Automate provisioning and configuration (CloudFormation/Terraform/Ansible) so a replacement instance has the exact configuration, environment variables, SSH keys, and monitoring.

2) Project repository and job state (where Matillion stores definitions/history)
- Externalize Matillion’s internal PostgreSQL repository whenever possible (supported configuration) and host it in a managed database service (AWS RDS/Azure Database for PostgreSQL/GCP Cloud SQL).
  - Configure the DB for Multi‑AZ (or equivalent) and automated backups/snapshots.
  - Enable point‑in‑time recovery and retention policy that matches your RTO/RPO.
  - For cross‑region DR, use read replicas or cross‑region snapshots/replication and a documented failover process.
- Use Git integration (GitHub/Bitbucket/GitLab) for Matillion projects. Keep all jobs/version history in Git and enforce pushes — this gives an off‑instance copy you can clone to a new Matillion instance instantly.
- Regularly export Matillion projects (project export or API) and store exports in durable object storage (S3/Blob Storage/GCS).

3) Credentials and secrets
- Matillion stores credentials in the project DB; ensure encryption keys/backups are managed and stored securely.
- Keep a separate secrets vault (AWS Secrets Manager/Azure Key Vault/GCP Secret Manager) for any credentials outside Matillion so they can be reconfigured quickly.
- Document and back up any instance‑level keys or certificates.

4) Running jobs and job history (in‑flight jobs)
- In‑flight jobs are interrupted by instance failure. Design jobs to be idempotent and resumable:
  - Use staging tables and upsert/merge strategies in the target warehouse.
  - Record checkpoints or high‑water marks (last loaded timestamp, CDC offsets).
  - Use small, restartable atomic tasks rather than one monolithic long transaction.
- Log job progress externally where feasible:
  - Send logs/audit entries to S3/Blob Storage, CloudWatch/Log Analytics, or into the data warehouse so run history is preserved outside the Matillion DB.
  - Use Matillion’s APIs to capture job status and history into external monitoring if required.

5) Failover / Recovery process
- Recovery components:
  - Instance: spin up new instance from image or IaC template, attach Elastic IP/DNS.
  - Project DB: use RDS failover or restore DB from snapshot if DB was local to instance.
  - Git/project exports: if DB is lost, import projects from Git or export files.
  - Secrets: restore from vault and reconfigure connections.
- Typical steps:
  1. Promote standby DB or restore DB snapshot to a new DB instance (if DB was lost).
  2. Launch Matillion instance from template and point it at restored/external DB or import projects from Git.
  3. Reattach IP/DNS and reconfigure any environment integrations.
  4. Reconcile any in‑flight work using checkpoint tables, resume or re-run idempotent orchestration jobs.
- Define RTO/RPO and validate this runbook with regular DR drills.

6) Automation, monitoring, and testing
- Automate builds and test DR periodically. Validate:
  - Instance build completes with correct configuration.
  - Projects restore properly from DB or Git.
  - Jobs can be resumed or restarted and produce correct results.
- Monitor instance health, DB replication lag, backup success, and job failure alerts. Maintain runbooks and contact lists.

7) Cloud‑specific notes (high level)
- AWS: use RDS Multi‑AZ for the project DB, EBS snapshots/AMI, Elastic IP, CloudFormation for redeploy.
- Azure: use Azure Database for PostgreSQL (zone‑redundant), VM images, Azure Resource Manager templates.
- GCP: use Cloud SQL with high availability, custom images, Deployment Manager / Terraform.

Summary
- Separate concerns: make the Matillion VM replaceable and protect the project repository/DB and credentials.
- Externalize state (managed DB + Git + exports), automate instance rebuilds (images + IaC), design jobs to be idempotent and checkpointable, and practice the DR runbook regularly to meet your RTO/RPO.

[Top](#top)

## How do you upgrade Matillion versions safely, validate compatibility, and roll back if needed?
Goal-oriented, repeatable approach:

1) Pre-upgrade planning
- Read Matillion release notes and breaking-change / compatibility sections for the target version. Identify required intermediate upgrades if the release notes state a forced upgrade path.
- Inventory: Matillion instance type (AWS/Azure/GCP), Matillion version, projects, custom components, Python scripts, external connectors, Git integration, credentials, third-party drivers, and scheduled jobs.
- Create a test plan with critical jobs/end-to-end pipelines to run post-upgrade and acceptance criteria (run-time, row counts, success/failure status).
- Schedule a maintenance window and notify stakeholders. Disable automated triggers and scheduled jobs during the upgrade.

2) Backups and snapshots (must-have before upgrade)
- Export projects: use Matillion’s project Export for all active projects (Project → Export). Store artifacts in version-controlled storage.
- Export custom components and any external code (Component Library, Python files).
- Backup Matillion metadata DB (Postgres): pg_dump or native DB snapshot. Example: pg_dump -U <user> -h localhost -Fc matillion_db > matillion_db.dump
- Take infrastructure snapshot:
  - AWS: create AMI and EBS snapshots of the EC2 instance.
  - Azure: create VM image/snapshot.
  - GCP: create a machine image or disk snapshot.
- If using Git integration, ensure latest pushes/branches/tags are committed.

3) Upgrade execution (staging first)
- Perform upgrade in a non-production environment first; run the test plan.
- Upgrade options:
  - Marketplace/AMI-based instances: launch new instance from the Matillion AMI image for the target version or apply vendor-provided update. Attach or restore configuration as per Matillion docs.
  - Cloud console/VM: follow Matillion-specific upgrade procedure for that cloud (often involves launching the new AMI/image and migrating/pointing to the DB or importing projects).
  - In-place upgrades: only if Matillion supports it for that release — follow official steps precisely.
- Validate connectivity to target data warehouses (Snowflake/Redshift/BigQuery/Synapse) and ensure drivers/Credentials are unchanged and compatible.

4) Validation checklist after upgrade
- Basic health checks: UI login, version number, service processes running, Matillion logs for errors.
- Project validation: import/export complete, all projects visible.
- Run critical orchestration jobs and transformation jobs from your test plan; verify row counts, success statuses, and downstream systems have expected data.
- Validate Git operations: commit, push, pull, branch switching.
- Validate custom components and Python scripting (library versions can change).
- Validate scheduler and triggers; confirm they are re-enabled as expected.
- Monitor for errors over a defined observation window.

5) Rollback strategy and steps
- Principle: fastest rollback is restore of snapshot/image or spin up pre-upgrade instance.
- Rollback options:
  - Restore VM snapshot / AMI / machine image to the pre-upgrade instance.
  - Restore Postgres DB backup and import projects if you restored a clean VM.
  - Re-launch previous Matillion AMI/VM and attach prior DB snapshot or import exported projects.
  - If using Git as source of truth, you can launch any compliant Matillion instance and import projects from Git branch/tag.
- Typical rollback sequence:
  1. Stop the upgraded instance (to prevent data drift).
  2. Launch a new instance from the pre-upgrade AMI/image or restore disk snapshot.
  3. Restore Matillion DB snapshot or import project exports.
  4. Reconfigure network/elastic IP/endpoint so clients point to the restored instance.
  5. Run smoke tests and critical pipelines to confirm pre-upgrade state is restored.
- Validate that downstream systems are consistent; if the upgrade completed jobs that changed downstream state, additional reconciliation may be required.

6) Post-upgrade operational steps
- Re-enable schedules and triggers after successful validation.
- Monitor performance and logs for several production cycles.
- Record findings, update runbook with any platform-specific gotchas and documented rollback steps and snapshots used.

7) Additional considerations
- Compatibility: confirm Matillion components (connectors, Python libs, custom components) are supported in the target version. Check third-party driver versions for data warehouses.
- Breaking changes: follow release notes about removed/renamed components, changed job behaviors, or new required configuration.
- Use automation: script backups, AMI creation, and smoke tests to reduce human error.
- When in doubt or for major version upgrades, plan a staged rollback window and test restores ahead of the production upgrade.

[Top](#top)

## How do you export/import or promote projects across environments, and what pitfalls occur with environment bindings?
Ways to move projects between Matillion environments (Dev → Test → Prod)

1) Git integration (recommended for CI/CD)
- Connect your Matillion projects to a shared Git repo (Bitbucket, GitHub, GitLab).
- Develop and commit changes in the Dev instance, push to a branch (feature → develop → release).
- On the Test/Prod Matillion instances, pull the appropriate branch to get the updated jobs.
- What Git does not move: environment definitions, credentials, instance-specific configuration, or encrypted secure values.

2) Project Export / Project Import (UI or REST API)
- Use Project → Export Project (or right‑click a job → Export Job for single jobs) to create an export file.
- In the target instance use Project → Import Project (or Import Job) to load the file.
- You can automate this with Matillion’s REST API endpoints for export/import.

3) Individual job export/import
- Export individual jobs if you only need a subset (remember to export dependent jobs/components too).
- Import them into the target project and re-link dependencies.

Common pitfalls with environment bindings and how they manifest

- Missing or differently named Environments
  - Jobs/components reference an Environment by name/ID. If the target Matillion instance does not have the same Environment name (or ID mapping differs) bindings break and components show “missing environment” or similar errors.
  - Mitigation: create the same Environment name in target before import, or use a consistent naming convention across instances.

- Credentials and secrets not exported or masked
  - Passwords, API keys, or some secure values are not exported or are stripped/masked for security.
  - Mitigation: re-enter credentials in the target environment or use a secrets manager and reference those in the job using environment variables.

- Environment variables and scope confusion
  - Project vs environment variables: values meant to change per environment must be stored as environment-scoped variables. If you hard-code values in components, they will not change on promotion.
  - Some exported variable definitions may not include secure/value content; secure values must be re-populated.
  - Mitigation: parameterize all environment-specific configuration with variables, and only commit variable names to Git/export; populate secure values in each instance.

- Component-level references / resource IDs
  - Some components store references (IDs) that do not map across Matillion instances, causing unbound components after import.
  - Mitigation: rebuild or re-bind those components in the target, or avoid relying on instance-specific references where possible.

- Missing dependent jobs or shared resources
  - Exporting a job without its dependencies (sub-jobs, shared components, helper jobs, scripts) leads to broken flows.
  - Mitigation: map dependencies and export/import the full set, or use Git to capture the whole project.

- Differences in target platform configuration
  - Schema names, databases, buckets, IAM roles, or Snowflake/Redshift/BigQuery connection details often differ between environments and must be recreated.
  - Mitigation: create target connections/environments and verify object availability before running jobs.

- Version incompatibilities
  - Matillion version differences can cause unexpected behavior or import warnings.
  - Mitigation: align Matillion versions across environments or test imports before full promotion.

Operational recommendations (practical rules to avoid pitfalls)
- Standardize environment names across Matillion instances so imports map correctly.
- Put all environment-specific config into environment variables, not hard-coded component fields.
- Use Git for version control of jobs and to perform controlled promotions (branches/tags).
- Script or document environment provisioning (connections, roles, secrets) so target setup is repeatable.
- Always re-populate secure values in the target manually or via a secure secret store.
- After import/pull, perform a smoke test of key jobs and validate bindings before allowing production runs.

Summary: Use Git for structured promotion and Project Export/Import or API for ad-hoc moves. The usual failures come from missing/different environments, absent credentials, hard‑coded environment values, and instance-specific IDs — mitigate by consistent environment names, parameterization (variables), scripted environment setup, and post-import verification.

[Top](#top)

## How do you integrate Git-based version control with Matillion and manage branches, PRs, and releases?
Overview
- Matillion integrates directly with Git providers (GitHub, GitLab, Bitbucket, Azure DevOps) so Matillion jobs and metadata are stored as JSON in a Git repository and can be committed, branched, pushed and pulled from the Matillion UI or via Git tooling.
- Typical artifacts stored: orchestrations, transformations, variables, environment metadata — files live in repository folders (e.g., /orchestrations, /transformations).

Setup
- Create a repo in your Git provider and generate credentials (Personal Access Token or username/password per your provider).
- In Matillion: open the Project settings → Version control / Git configuration and set the remote repository URL, auth token, and initial branch.
- After connecting, Matillion exposes Git actions: Commit, Push, Pull (Fetch), Create Branch, Switch Branch, Delete Branch, etc.

Day-to-day workflow (developer)
- Create a feature branch (in Git provider or Matillion UI).
- Make changes in Matillion (jobs/edit). Commit locally from Matillion with a descriptive message, then Push to the remote branch.
- Open a Pull Request / Merge Request in your Git provider to merge the feature branch into the target branch (e.g., develop or main).
- Reviewers inspect JSON diffs in the PR; include human-readable explanations in the PR body and small focused commits to make reviewable diffs.
- After PR approval, merge to the target branch; teammates pull or Matillion project(s) switch to that branch to pick up changes.

Branching strategies and environment mapping
- Common pattern:
  - One Matillion project per environment (recommended): Dev project -> linked to dev branch, QA project -> linked to release/staging branch, Prod project -> linked to main/master branch.
  - Alternative: Single Matillion project switching branches, but this risks unintended overwrites and complicates concurrent environment testing.
- Branch naming: feature/<ticket>, release/<version>, hotfix/<ticket>, main/master for production.
- Protect main/master with branch protection and required PR reviews and CI checks.

Handling PRs and code review
- PRs operate like any Git workflow. Because JSON diffs can be noisy:
  - Keep commits small and focused (one job/one logical change per commit).
  - In PR descriptions include a summary of job changes and screenshots or exported job XML/JSON snippets of key logic.
  - Use reviewer checklists: variable/env changes, credentials not in repo, SQL/queries reviewed, runbook for deployment steps.

Conflict management
- Avoid conflicts by assigning jobs per developer or feature, committing frequently, and communicating.
- If conflicts occur, resolve them using standard Git merge tools (git mergetool, CLI). After resolving and pushing the merge, Pull in Matillion to align the project working tree.
- When switching branches in Matillion you must commit or discard local changes; Matillion will prompt — do not switch with uncommitted changes unless you intend to discard them.

Releases and promotion to production
- Typical release flow:
  1. Develop features in feature branches -> PR -> merge into develop.
  2. Create a release branch from develop for stabilization and QA.
  3. QA Matillion project pulls the release branch for testing.
  4. After sign-off, merge release branch into main/master and tag the commit with a release tag.
  5. Production Matillion project pulls the main/master branch (or CI/CD pushes it) and you run validation jobs.
- Automate promotion using CI/CD:
  - On merge to main, CI pipeline can call Matillion’s REST API (or use scripts) to import or sync the repo into the production Matillion instance and/or trigger validation jobs.
  - Alternatively, use Git-based promotion where the Prod Matillion project is configured to the main branch and an operator runs Pull on that project after merge.

Automation and APIs
- Use your Git provider CI to run validation steps (linting of SQL, unit tests, static checks of JSON), then automate deployment with Matillion REST API or a command-line approach to import/export job bundles.
- Tagging releases in Git gives clear audit points; CI pipelines can deploy specific tags to production.

Security and environment separation
- Never store secrets/credentials in Git. Use Matillion Environment variables, project variables, or a secrets manager that’s not committed.
- Parameterize connections so the same jobs run across dev/stage/prod without code changes.

Best practices summary
- Use one Matillion project per environment where possible and map branches to those projects for clear separation.
- Commit early and often, keep commits small and meaningful.
- Protect main/master, require PRs with reviews, and use CI validation.
- Keep credentials out of Git and use environment-level variables.
- Resolve JSON conflicts through Git merge tooling and verify in Matillion after merges.
- Tag releases and automate promotion with CI and Matillion APIs for repeatable, auditable deployments.

[Top](#top)

## How do you implement CI/CD for Matillion (APIs/CLI, GitHub Actions/Azure DevOps/CodeBuild) to deploy jobs automatically?
High-level approach
- Two common patterns:
  1. Git-based promotion: use Matillion’s built-in Git integration. Developers commit/branch in a remote Git repo; target Matillion instances pull the relevant branch (via the UI or API) to promote changes.
  2. Project export/import: export a project artifact from the source instance (REST/CLI), store it as a pipeline artifact, then import it into the target instance (REST/CLI). Useful when moving between different Matillion deployments or for full-project promotion.
- Both patterns pair with automated validation: run smoke/unit jobs via the Matillion REST API after deploy, assert job status, and optionally roll back by re-importing a saved artifact.
- Security/network: pipeline runners must reach Matillion endpoints (private VPC => use self-hosted runners/CodeBuild in VPC). Store Matillion credentials/keys in secure secrets.

Key Matillion integration points
- REST API: export/import project, run job, list jobs, update environment/variables. Authenticate with Matillion credentials (store in pipeline secrets).
- Built-in Git: Matillion supports connecting to remote Git (GitHub/GitLab/Bitbucket). Use branch strategy (dev/test/prod) and call Matillion API or use a Matillion job/component to pull a branch.
- CLI wrappers: You can wrap REST API calls in scripts or use a community/enterprise CLI if available — the CI/CD flow is the same underneath (HTTP calls).

Recommended promotion flow (Git-based)
1. Developer work in dev Matillion; commit to remote Git (feature branches).
2. Merge to environment branch (e.g., release/main).
3. CI pipeline triggers on branch merge:
   - Call Matillion target instance’s Git pull API (or call an orchestration job that executes “Git Pull”) to sync the project to that environment.
   - Run validation jobs via the job-run API.
   - Record results and notify.
4. If validation fails, either revert the Git merge or re-run a previous branch.

Recommended promotion flow (Export/Import)
1. Source Matillion: export project via REST API to create artifact (zip/tgz).
2. CI pipeline stores artifact as build artifact.
3. Target Matillion: import artifact via REST API with overwrite option.
4. Update environment variables/credentials (via API or set in target environment).
5. Run validation jobs and mark deployment success/failure.

Practical implementation details and pitfalls
- Credentials & secrets: use pipeline secret stores (GitHub Actions secrets, Azure DevOps variable groups, AWS Secrets Manager). Never hard-code Matillion credentials in repo.
- Overwrite/backups: before import, back up the target project (export) so you can roll back quickly.
- Environment differences: externalize connection configuration (use Matillion Environments/variables) and don’t store environment-specific secrets in project artifacts. Use API to set environment variable values after import.
- Idempotency: builds should be repeatable. Prefer Git promotion for incremental changes; use export/import for full-state deployment when necessary.
- Permissions: Matillion user used by CI must have permissions to export/import projects and run jobs.
- Networking: runners must reach Matillion endpoint; use VPN/VPC or self-hosted runners in same network.

Example cURL templates (replace placeholders; check your Matillion API docs for exact endpoint names)
- Export project (source instance)
  curl -u "${MAT_USER}:${MAT_PASS}" -X POST "https://${MAT_HOST}/rest/v1/project/export" \
    -d "projectName=MyProject" --output ./project.zip
- Import project (target instance)
  curl -u "${MAT_USER}:${MAT_PASS}" -X POST "https://${TARGET_HOST}/rest/v1/project/import?overwrite=true" \
    -F "file=@./project.zip"
- Run a job (start job and get runId)
  curl -u "${MAT_USER}:${MAT_PASS}" -X POST "https://${TARGET_HOST}/rest/v1/job/run" \
    -H "Content-Type: application/json" \
    -d '{"projectName":"MyProject","jobName":"Orchestration/MySmokeTestJob"}'
- Update environment variable (example)
  curl -u "${MAT_USER}:${MAT_PASS}" -X POST "https://${TARGET_HOST}/rest/v1/environment/updateVariable" \
    -H "Content-Type: application/json" \
    -d '{"projectName":"MyProject","environmentName":"prod","variableName":"s3_bucket","variableValue":"prod-bucket"}'

GitHub Actions example (simplified)
- Workflow triggers on push to main, exports from dev, imports to prod:
  - name: Export Matillion project
    run: |
      curl -u "${{ secrets.MAT_USER }}:${{ secrets.MAT_PASS }}" -X POST "https://${{ secrets.MAT_DEV_HOST }}/rest/v1/project/export" \
        -d "projectName=MyProject" --output project.zip
  - uses: actions/upload-artifact@v3
    with: name: project-zip path: project.zip
  - name: Download artifact and import to prod
    uses: actions/download-artifact@v3
    with: name: project-zip
  - name: Import to Prod Matillion
    run: |
      curl -u "${{ secrets.MAT_USER }}:${{ secrets.MAT_PASS }}" -X POST "https://${{ secrets.MAT_PROD_HOST }}/rest/v1/project/import?overwrite=true" \
      -F "file=@project.zip"
  - name: Run smoke test
    run: |
      curl -u "${{ secrets.MAT_USER }}:${{ secrets.MAT_PASS }}" -X POST "https://${{ secrets.MAT_PROD_HOST }}/rest/v1/job/run" \
      -H "Content-Type: application/json" \
      -d '{"projectName":"MyProject","jobName":"Orchestration/Smoke"}'

Azure DevOps example (YAML or classic pipeline)
- Inline script task that performs the same curl export/import/run steps. Use pipeline variables for MAT_USER/MAT_PASS/MAT_HOST and mark them secret in variable groups.

AWS CodeBuild example (buildspec.yml)
- phases:
    pre_build:
      commands:
        - export MAT_USER=${MAT_USER} # from env or Secrets Manager
    build:
      commands:
        - curl -u "${MAT_USER}:${MAT_PASS}" -X POST "https://${MAT_DEV_HOST}/rest/v1/project/export" -d "projectName=MyProject" --output project.zip
        - aws s3 cp project.zip s3://my-artifacts-bucket/project.zip
- Deploy step (another CodeBuild project or step) pulls the artifact and imports to target Matillion.

Validation and rollback
- Validation: after import/pull, call job-run API on lightweight smoke tests and assert their completion status via job status endpoints. Fail pipeline on non-success.
- Rollback: keep the previous project export artifact and re-import it if needed. Alternatively revert the Git merge and trigger a pull.

Branching strategy recommendations
- Use branches to represent promotion gates: feature -> develop -> release/main -> prod.
- Use pull requests and CI checks on commits (linting, job validation) before merging to promotion branches.
- For teams managing connections or secrets, keep those out of Git and apply per-environment post-deploy.

Summary checklist for automated Matillion CI/CD
- Connect Matillion to remote Git or rely on REST export/import.
- Build pipeline steps: export or git-pull, artifact storage, import/pull to target, update environment variables, run smoke tests, report status.
- Secure credentials in secret stores and ensure network connectivity.
- Back up target project before import and keep artifacts for rollback.
- Prefer Git-based promotion for incremental, traceable changes; use export/import for full-project moves or cross-instance promotions.

End.

[Top](#top)

## How do you tag, document, and annotate jobs/components to support discovery and governance?
Matillion supports multiple in‑product ways to tag, document and annotate jobs/components, and you can extend that with conventions, automation and integration for enterprise governance. Below is a practical approach — what to use in Matillion, how to apply it, and recommended governance practices.

What to use in Matillion
- Job-level metadata
  - Job Description: every job has a Description field — use it for purpose, owner, SLA, inputs/outputs and important notes.
  - Tags (job labels): use job tags (or a tagging field in your environment) to classify by domain, sensitivity, app, team, environment, etc.
  - Naming conventions: use standardized name patterns (domain_pipeline_type_frequency) so jobs are self-describing.
- Component-level documentation
  - Component Comments/Notes: most components expose a free-text comment/notes property in the properties pane — use it to explain non-obvious transforms, business rules and assumptions.
  - Annotations/Notes on canvas: use the canvas annotation or note objects (visual sticky-notes) to group logic, call out caveats, or provide high-level flow explanations.
- Reusable constructs & organization
  - Shared library jobs: encapsulate common logic in shared orchestration/transformation jobs and call them (Run Job component). Document the shared job’s description and tag it as “shared” or “library.”
  - Variables: name variables clearly and add comments where available so parameter semantics are discoverable.
- Version control & audit
  - Git integration: store projects in Git (commit messages and branches provide context and change history).
  - Job run history & audit logs: Matillion records job runs and execution metadata for operational governance and troubleshooting.

Operational/governance practices
- Mandatory metadata fields: require job description, owner (email/Team), SLA, data sensitivity/classification, and downstream consumers as part of a naming/tagging checklist before promotion.
- Tag taxonomy: define and publish a controlled set of tags (e.g., domain:finance, sens:PII, critical:true, owner:team-dataeng). Enforce as part of code review or CI checks.
- Standardized comment format: agree on templates for job descriptions and component comments (purpose, inputs, outputs, assumptions, business rules, last updated).
- Shared library & ownership: place reusable jobs in a documented “library” folder with a clear owner and change process.
- Lineage capture: capture source and target table names in job descriptions/variables and/or write execution metadata to a governance schema/table in the warehouse so lineage and provenance can be queried.

Automation and integration
- Metadata extraction via API: use Matillion’s REST API (or export tools) to extract job and component metadata (names, descriptions, tags, variables, run history) on a schedule and push into your metadata catalog (Collibra, Alation, Data Catalog, internal CMDB).
- CI checks: incorporate metadata checks into CI pipelines (validate presence of owner, sensitivity tag, description length, naming pattern) before merge/deploy.
- Catalog and lineage sync: map Matillion metadata to your enterprise catalog by exporting job-level and component-level metadata and populating catalog fields (owner, SLA, data domains, dependencies).
- Automated documentation: generate markdown or wiki pages from extracted metadata and commit them to the project repo (or push to central docs) so documentation stays in sync with code.

Example minimum metadata to capture
- Job name (standardized), Description, Owner (email/team), Tags (domain, sensitivity, criticality), Input sources, Output targets, Schedule/SLA, Version/Git commit id, Last modified date.

Concrete checklist for adoption
1. Define naming and tag taxonomy + description template.
2. Add required fields to job/component templates and train teams to populate them.
3. Enforce via Git/CI: validation script that calls Matillion metadata API to assert required metadata before deploy.
4. Extract metadata regularly and feed into enterprise catalog for discovery, lineage and policy enforcement.
5. Use shared library jobs, annotations and component comments to document implementation details that are not appropriate for higher‑level catalog entries.

This combination of Matillion’s built‑in descriptions, tags, annotations and component comments plus Git/version control, API-driven metadata export and CI validation delivers discoverability and governance without blocking developer productivity.

[Top](#top)

## How do you schedule jobs with Matillion’s scheduler versus external orchestrators (Airflow, ADF, Step Functions, Cloud Composer)?
Short answer
- Matillion scheduler: built-in, UI-driven cron/calendar schedules, handles Matillion job dependencies, variables and basic notifications; best for simple, self-contained Matillion workflows.
- External orchestrators: trigger Matillion jobs via Matillion’s REST API (or a light wrapper), poll for job status (or use callbacks), and manage cross-system dependencies, retries, and enterprise scheduling policies. Typical patterns differ slightly by orchestrator (Airflow/Cloud Composer, ADF, Step Functions).

How Matillion’s scheduler works (what you get and how you use it)
- Where: Scheduler UI inside the Matillion instance (per-environment).
- Scheduling types: cron-style schedules, calendar/daily/weekly, one-off, and recurring.
- Job scoping: schedule Orchestration jobs (which in turn run Transformation jobs or components).
- Dependencies: chain jobs inside Matillion using “Run Orchestration Job” components and job-level dependency controls.
- Parameters: native support for job and environment variables; scheduled runs can use different environments.
- Visibility: run history, success/failure states, logs accessible in the Matillion UI.
- Notifications: email and webhooks (simple alerting).
- Best suited for: simple to moderate ELT flows wholly owned in Matillion, low-latency local schedules, teams that prefer UI-only control.

How external orchestrators trigger Matillion (general pattern)
- Trigger: external orchestrator sends authenticated HTTP request to Matillion’s REST API to start a job and can pass job variables.
- Monitor: orchestrator polls Matillion job execution endpoints to follow run status or uses a callback/webhook pattern if implemented.
- Authenticate & secure: keep Matillion credentials in the orchestrator’s secret store (Airflow Connections/Secrets, ADF Key Vault, AWS Secrets Manager). Ensure network connectivity (open firewall, VPC peering, NAT, VPN) between orchestrator and Matillion instance.
- Idempotency/concurrency: orchestration should guard against duplicate triggers; Matillion can also be configured to prevent concurrent runs of the same job.
- Logging/observability: capture Matillion run ID and propagate into orchestrator logs for troubleshooting.

Patterns and examples by orchestrator

Airflow / Cloud Composer
- How to call: use HttpOperator/SimpleHttpOperator, BashOperator with curl, or a custom operator that wraps Matillion REST calls.
- Typical flow: Airflow task posts to Matillion run-job API → returns execution id → Airflow Sensor (HttpSensor or custom) polls Matillion for completion → branch on success/failure.
- Auth: store Matillion credentials in Airflow Connections or Secret Manager.
- Why use Airflow: full DAG orchestration across systems, retries, SLA handling, XComs to pass Matillion execution IDs.

Azure Data Factory (ADF)
- How to call: Web Activity to POST to Matillion REST API for a run. For more complex logic or auth, use an Azure Function or Logic App invoked by ADF.
- Typical flow: ADF pipeline Web Activity triggers Matillion job → subsequent Web Activity or Azure Function polls for status → pipeline branching based on result.
- Auth & secrets: store credentials in Key Vault and reference them from the Web Activity or Function.
- Why use ADF: integrate Matillion runs into broader Azure-centric pipelines and data movement tasks.

AWS Step Functions
- How to call: Step Functions typically call a Lambda which invokes the Matillion REST API (simpler to manage auth and polling inside Lambda).
- Patterns: 
  - Synchronous: Lambda starts job and loops/polls Matillion until completion (within Lambda timeout constraints).
  - Callback pattern: Lambda starts job and Step Functions uses a wait/poll state or a callback using a task token; Matillion could notify via webhook to an API Gateway/Lambda to resume the Step Function.
- Why use Step Functions: orchestrate serverless workflows that include Matillion alongside other AWS services with robust state management.

General Cloud Composer note
- Cloud Composer is managed Airflow; use the same Airflow patterns (HttpOperator, sensors, connections, IAM/secret integration).

Practical considerations and best practices
- Single source of truth: choose one scheduler to avoid double schedules (disable Matillion scheduler for jobs controlled externally).
- Network posture: Matillion often runs in your VPC — ensure orchestrator has network access (VPC peering, NAT, security groups).
- Secrets management: never hard-code Matillion credentials; use orchestrator secret stores.
- Polling vs callbacks: polling is simplest (poll job-status endpoint) but increases load/delay; implement webhook/callbacks if you need immediate notification.
- Error handling: propagate Matillion run IDs to the orchestrator, implement retries/backoff and handle partial failures explicitly.
- Variables and environment mapping: pass job variables when triggering from outside; map Matillion environments appropriately.
- Monitoring: use both Matillion logs and orchestrator logs; include run IDs and timestamps to correlate runs.
- Scale & governance: use external orchestrators when you need enterprise scheduling, cross-system DAGs, role-based access, audit trails, and complex retry policies; use Matillion scheduler for smaller, contained ELT schedules.

Summary
- Use Matillion scheduler for simplicity and fully Matillion-contained jobs. Use external orchestrators to integrate Matillion runs into broader, cross-platform workflows by calling Matillion’s REST API, polling for status (or implementing callbacks), and handling secrets, network access, and error/retry behavior from the orchestrator side.

[Top](#top)

## How do you design event-driven pipelines (webhooks, SNS/SQS, EventBridge, Logic Apps) that trigger Matillion jobs?
Short answer: don’t call Matillion directly from every event — front the Matillion REST “run job” API with a lightweight, authenticated middleware (API Gateway / Logic App / Lambda / Step Function) that validates, deduplicates and queues events, injects event metadata as job variables, starts the job, monitors or records the run-id, and handles retries/errors/visibility. Below are concrete patterns, requirements and best practices for webhooks, SNS/SQS, EventBridge and Azure Logic Apps.

Key building blocks
- Trigger source: webhook / SNS / SQS / EventBridge / Logic App.
- Middleware/orchestrator: API Gateway, Lambda, Step Functions, Logic App, Azure Function, or an EventBridge API Destination.
- Matillion invocation: Matillion REST API to start an orchestration job and optionally set job variables. Capture returned run-id for monitoring.
- Persistence / queueing: SQS, SNS -> SQS, EventBridge, Service Bus, or blob landing area for large payloads.
- Monitoring & DLQ: CloudWatch/Cloud Monitor + Dead-letter queue + alerting.
- Secrets & network: Secrets Manager / Key Vault + VPC/private endpoints or IP allowlist + TLS.

Detailed design considerations

1) How to call Matillion
- Use Matillion’s REST API “run job” endpoint to start an orchestration job. Supply project/group/job identifiers plus variables in request body.
- Authenticate using a least-privilege API/service account; store credentials in Secrets Manager/Key Vault and inject at runtime.
- Capture the response run-id (or run object) so you can poll status or correlate completion with the originating event.

2) Recommended event flow patterns
- Direct webhook -> API Gateway -> Lambda -> Matillion
  - Use API Gateway to authenticate and throttle.
  - Lambda validates payload, de-duplicates (if required), writes event to SQS or DB for persistence, then calls Matillion REST (async). Return 202 quickly for webhooks if upstream needs immediate ack.
- EventBridge -> API Destination or Lambda/Step Function -> Matillion
  - EventBridge API Destination can call Matillion directly and handle throttling, auth, and retries.
  - For controlling job lifecycle or chaining downstream actions, use Step Functions: Start Matillion job, poll for completion via Matillion status endpoint, handle success/fail transitions.
- SNS/SQS -> Consumer Lambda/ECS -> Matillion
  - Use SQS (FIFO if order/deduplication required) as buffer for burst traffic. Lambda or ECS worker pulls messages, invokes Matillion jobs, writes success/failure. Use DLQ for permanent failures.
- Azure Logic Apps -> HTTP action -> Matillion
  - Logic Apps validate/transform events, fetch API credentials from Key Vault and call Matillion REST. If Matillion is in private VNet, use Integration Service Environment or hybrid connectors.

3) Idempotency and deduplication
- Prefer queueing with SQS FIFO for guaranteed dedupe/order or use de-dupe keys.
- Pass a unique event_id / correlation_id as a Matillion job variable. Have the Matillion orchestration job do a lookup (control table / metadata store) at start and exit early if already processed.
- Persist event metadata on receipt (DB / object store). Use this storage to enforce idempotency across retries.

4) Error handling, retries, and DLQ
- Implement exponential backoff and limited retries in the middleware. Let queues hold messages for retry instead of retrying a webhook synchronously.
- Use DLQ for messages that exceed retries; attach context and original payload to improve debugging.
- For synchronous webhook patterns, return HTTP 202 and process asynchronously. Do not block the upstream caller during long Matillion runs.
- For job-level failures, use Matillion job notifications or have the orchestration job call a callback endpoint (or post status to a status table / SNS topic).

5) Orchestration and monitoring
- If downstream steps depend on Matillion job completion, orchestrate with Step Functions / Durable Functions / Logic Apps that:
  - Call Matillion REST start
  - Poll run status (or have Matillion call a callback webhook) until terminal state
  - Branch on success/failure
- Log run-id and correlation-id at every step. Emit metrics (job_start, job_end, duration, success/fail) to CloudWatch or Azure Monitor.
- Capture Matillion job logs for troubleshooting; store key metadata (event_id, run_id, timestamps) in a central audit table.

6) Security and networking
- Don’t expose Matillion admin console publicly without protection. Prefer private endpoints, IP whitelisting, or API Gateway with WAF.
- Use TLS. Use API keys / service account credentials stored in Secrets Manager / Key Vault. Rotate keys regularly.
- If Matillion lives in a VPC/VNet, ensure the middleware (Lambda in VPC, integration runtime in Azure) has network access (NAT, VPC endpoints, peering).
- Use a dedicated service account for API calls with minimum permissions.

7) Performance and scaling
- Matillion runs orchestration jobs but heavy lifting is done on the target warehouse. Consider:
  - Batching events in the queue and invoking Matillion with a batch pointer rather than one job per event for high event rates.
  - Throttling job launches to avoid overwhelming Matillion or the warehouse (use queue consumers or Step Functions with concurrency limits).
  - Horizontal scaling of middleware (Lambda concurrency, ECS tasks) while controlling Matillion concurrency.
- Observe Matillion’s concurrency limits and the downstream warehouse resource usage; tune sizing accordingly.

8) Passing event data to Matillion
- For small payloads: pass payload fields or the event_id as job variables in the REST call.
- For large payloads: store payload in S3/Blob and pass the object URL or pointer as a variable; Matillion job reads it from storage.
- Always pass a correlation_id and original timestamp for traceability.

9) Example AWS architecture (concise)
- Event -> API Gateway (auth) -> Lambda (validate, persist to DynamoDB, push to SQS) -> SQS -> Lambda worker -> POST to Matillion /rest API with variables (event_id, payload URL) -> capture run-id -> Lambda writes run status to DynamoDB and triggers Step Function for follow-up/polling if needed -> CloudWatch metrics & DLQ for failed messages.

10) Example EventBridge shortcut
- EventBridge rule -> API Destination to Matillion API (auth via OAuth/API key). Good for simple routes (EventBridge manages auth and retries). Use Step Function if you need to wait for job completion.

11) Example Azure architecture
- Event (HTTP webhook / Event Grid) -> Logic App (validate, store payload in Blob, get secrets from Key Vault) -> HTTP action to Matillion REST. For private Matillion, use Integration Service Environment or Hybrid Connection. Capture run-id in storage and use a Durable Function or Logic App polling loop to wait for completion.

Operational checklist before production
- Secrets stored and rotated.
- Network access tested and secured.
- Idempotency checks implemented.
- Retry policy and DLQ configured.
- Monitoring, alerts and audit logs in place.
- Rate limits and concurrency caps defined.

Concrete operational notes for interviews
- Prefer queue-based patterns (SQS/Service Bus) to absorb bursts and allow retries/DLQ.
- Use Step Functions/Durable Functions when you need reliable “start job + wait for completion” logic.
- Use EventBridge API Destinations for simple, serverless calls directly to Matillion if you don’t need complex orchestration.
- Always pass a correlation_id into the Matillion job and persist run-id to tie events to job runs.

No generic one-size-fits-all — choose between immediate synchronous starts vs queued asynchronous starts based on event volume, desired latency, Idempotency, and downstream dependencies.

[Top](#top)

## How do you tune job concurrency, parallel components, and queueing to maximize throughput without overloading the warehouse?
Short answer
- Treat Matillion as a coordinator that spins up SQL work in the warehouse. Concurrency must be sized against warehouse capacity (CPU/slots/credits) and the average resource cost of your queries. Measure first, set a safe concurrency cap in Matillion, isolate heavy workloads to separate warehouses, and use job-level throttles/queueing patterns to avoid bursts that saturate the warehouse.

How I approach it (step‑by‑step)

1) Measure the warehouse capacity and workload
- Use your warehouse monitoring (Snowflake Query History / Warehouses view, Redshift STV_RECENTS / WLM, BigQuery slot utilization) to capture:
  - average and p95 query CPU / memory / temp usage
  - average query runtime
  - concurrency at various times and any queue/wait times
  - credit or slot consumption and peaks
- Use Matillion’s Query History, Audit logs and job timings to map which jobs/components produce which SQL and their cost.

2) Define safe utilization and a concurrency target
- Pick a target utilization (typical: 60–80%) to leave headroom for spikes and concurrency overhead.
- Estimate average resource cost per job (e.g., an “average heavy transform” uses ~0.2 of a warehouse’s compute). Concurrency_limit ≈ floor(target_capacity / average_job_cost).
- Example: if the warehouse handles ~8 heavy transforms at <80% before contention, set Matillion concurrency ≈ 5–6 for heavy jobs.

3) Configure Matillion concurrency controls
- Environment-level: set a global “max concurrent jobs” cap (this prevents Matillion from launching unlimited jobs).
- Job-level: control whether a job allows concurrent runs and use job properties or variables to limit parallel invocations.
- Run Job components: choose synchronous vs asynchronous execution. Use synchronous when you need to enforce sequential execution; asynchronous when you can run safe parallel children but combine with rate limits.
- Parallel branches on the canvas: Matillion will run independent branches concurrently; treat each branch as a separate SQL workload and include this when calculating concurrency.
- Use a simple token/semaphore pattern (DB table, S3 lock file, SQS) or Matillion job variables to gate how many instances of a job run in parallel.

4) Queueing and throttling patterns inside Matillion
- Stagger and batch work: implement batched loops (Iterator) with sleeps/Wait when needed to throttle downstream concurrency.
- Use a semaphore table or an external queue: before starting heavy queries increment a counter; if counter > limit then sleep/retry. Decrement on completion. This works well for controlling concurrency for dynamically started jobs.
- Prefer running multiple small batches sequentially if concurrency causes contention.
- Use "wait for job" / synchronous Run Job to serialize dependent workloads.

5) Separate workloads by purpose
- Ingest (COPY/LOAD) vs heavy ELT transforms: run ingestion on a small, dedicated warehouse sized for high concurrency but low per-query cost, and run heavy transforms on a larger compute warehouse.
- Use role-based warehouses or separate Snowflake virtual warehouses / Redshift concurrency queues to isolate spikes (prevents an ELT spike from throttling BI queries).

6) Use warehouse autoscaling and features smartly
- For Snowflake: multi-cluster or auto-scale can absorb short bursts — but watch cost. Autoscaling gives more concurrency but you still need to limit Matillion so scaling events don’t cascade costs.
- For Redshift: use WLM queues and concurrency scaling; configure WLM priorities for ETL vs BI.
- Configure auto-suspend to save credits, but don’t autosuspend too aggressively if warm caches/CTEs are helpful.

7) Tune component-level behavior
- Prefer native bulk loads (COPY, COPY INTO) and staging to cloud storage rather than row-by-row inserts.
- Use CTAS/CREATE TABLE AS SELECT for heavy transforms instead of many small UPDATEs.
- Chunk large loads and read splits in parallel only if the warehouse can handle additional concurrent COPY/SELECTs.
- Reduce returned row counts where Matillion fetches data back to the instance (avoid unnecessary extract-to-client).

8) Monitoring and feedback loop
- Monitor query queue time, average runtime, failures, and credit burn after any concurrency change.
- Increase concurrency slowly (one step at a time) and test during representative peak windows.
- Add alerts for query queue growth, large spikes in credits, or slowdowns in SLA queries.

Concrete examples
- Example A (heavy transforms): Warehouse handles ~8 heavy queries. Target utilization 75% -> safe concurrency = floor(8 * 0.75) = 6. Set Matillion environment max concurrent jobs = 6. Use synchronous Run Job to chain sub-steps inside heavy jobs.
- Example B (many small loads): Use a smaller dedicated loading warehouse sized for many small COPY operations. Allow higher Matillion concurrency for ingest jobs but limit concurrent transforms to avoid competition.

Quick checklist to implement immediately
- Profile current queries and Matillion job timings.
- Set a conservative environment-level max concurrent jobs in Matillion.
- Mark heavyweight jobs as non-concurrent or gate them with a semaphore.
- Separate ingest vs transform into different warehouses.
- Replace row-by-row operations with bulk COPY/CTAS.
- Implement simple token table or rate-limit loops for fine-grained throttling.
- Monitor and iterate, increasing concurrency only after verifying no resource contention.

Pitfalls to avoid
- Turning Matillion loose with unlimited concurrent job starts on a single warehouse.
- Relying solely on warehouse autoscale as a correctness control (it mitigates, but increases cost).
- Treating number of Matillion threads as the only metric—must combine with warehouse telemetry (CPU/slots/temp/queue).

This approach balances Matillion’s ability to run parallel components with the reality of finite warehouse capacity: measure, cap, isolate, throttle, and iterate.

[Top](#top)

## How do you instrument and limit concurrency per environment or per warehouse to avoid contention and runaway spend?
High-level approach: control concurrency both in Matillion (so jobs don’t launch uncontrolled) and in the data warehouse (so queries can’t spin up unlimited compute or consume unlimited credits). Instrument everything so you can detect hot spots and enforce limits automatically.

How to instrument (what to capture and where)
- Matillion job metadata and audit:
  - Capture job run history (start/end, job name, environment, status, duration, run id). Use Matillion’s job-run history and REST API to pull this into a monitoring system (CloudWatch, Datadog, Grafana, etc.).
  - Tag jobs with environment and logical workload (e.g., prod/etl/high-priority) via naming conventions or environment variables.
- Warehouse usage and cost telemetry:
  - Snowflake: WAREHOUSE_METERING_HISTORY, QUERY_HISTORY, and ACCOUNT_USAGE views; enable RESOURCE_MONITOR to track credit usage.
  - Redshift: STL and system tables (stl_query, stl_wlm_query) and WLM metrics.
  - BigQuery: slot/reservation metrics, billing exports to BigQuery.
- Correlate Matillion runs with warehouse usage in dashboards and alerts (job X started at T produced Y credits over Z minutes).
- Alerts and reporting: set thresholds for concurrent jobs, credit burn rate, or unexpected warehouse scaling and trigger alerts/auto-actions.

How to limit concurrency (Matillion-side)
- Disable concurrent runs for critical jobs: set job property Allow Concurrent Runs = false for any job that cannot run in parallel.
- Orchestrate sequential execution: build parent orchestration jobs that call child jobs sequentially rather than scheduling many independent jobs that overlap.
- Use controlled scheduling windows: schedule heavy jobs in non-overlapping windows and use calendar-based scheduler rules.
- Use Matillion REST API to implement your own semaphore: before starting a workload, call Matillion API to query active runs and only proceed if below a threshold.
- Implement an internal job-queue/semaphore pattern:
  - Simple DB-based semaphore: have a “concurrency_locks” table in the warehouse. A job tries to insert a row under a transaction; a stored procedure returns success only if count(active_rows) < limit. On completion, job deletes its row. The orchestration job loops/waits until it can acquire the slot.
  - Cloud queue-based approach: use SQS/Cloud Tasks with a fixed concurrency worker pool; Matillion jobs pop tasks only when capacity is available.
- Use environment variables to represent concurrency limits (per environment or workload); read them at job start to decide behavior.

How to limit concurrency (warehouse-side)
- Snowflake:
  - Use a dedicated warehouse per environment or workload to isolate costs.
  - Configure MIN_CLUSTER/MAX_CLUSTER (for multi-cluster warehouses) to limit auto-scaling. Set max_cluster_count = 1 if you want no auto-scale.
  - Use auto-suspend and a short auto-suspend timeout to avoid idle costs.
  - Use RESOURCE_MONITORs to cap credits or suspend operations when a quota is hit.
- Redshift:
  - Configure WLM (workload management) queues with concurrency slots and memory allocations.
  - Disable or control Concurrency Scaling if it would blow cost.
- BigQuery:
  - Use slot reservations and limit slots per project/workload.
  - Use separate projects for environments with per-project quotas and billing.

Automatic controls
- Use warehouse resource monitors to cut queries when a spend threshold is hit (Snowflake resource monitor actions: NOTIFY, SUSPEND, etc.).
- Use orchestration jobs that check warehouse load (from warehouse usage views) before launching heavy queries; if load is high, delay/retry.
- Use Matillion API + external scheduler to globally cap the number of simultaneously running jobs across environments.

Concrete control pattern (example using Snowflake table semaphore)
- Create table:
  - CREATE TABLE matillion_semaphore (env VARCHAR, job_run_id VARCHAR, acquired_at TIMESTAMP);
- Try-acquire stored proc (pseudo):
  - If (SELECT COUNT(*) FROM matillion_semaphore WHERE env = :ENV) < :LIMIT then INSERT row and return TRUE else return FALSE.
- Matillion orchestration:
  - Loop: call stored proc; if TRUE proceed; if FALSE WAIT N seconds and retry up to M times; if timeout, fail or reschedule.
- On job completion or failure: delete its row to free slot.

Operational best practices (short checklist)
- Isolate environments with separate warehouses or reservations.
- Use job-level Allow Concurrent Runs = false for non-parallelizable jobs.
- Implement semaphores (DB-based or API-based) for groups of jobs that share compute.
- Enforce warehouse limits (max clusters, resource monitors, WLM, slot reservations).
- Instrument end-to-end (Matillion run history + warehouse metering + billing) and create alerts for unusual concurrency or spend.

This combination gives you three layers of protection: prevent matillion from launching excessive jobs, prevent the warehouse from automatically scaling beyond policy, and detect/cut spend with monitoring and resource monitors.

[Top](#top)

## How do you design idempotent pipelines and ensure safe retries at the component and job level?
Design for idempotency and safe retries in Matillion by applying database-native idempotent patterns, explicit checkpoints/state, and defensive orchestration logic. Describe goals, then practical component- and job-level patterns you can implement in Matillion.

Core principles
- Make every write repeatable without changing the final state (idempotent). Use MERGE/UPSERT or INSERT ... ON CONFLICT semantics instead of blind appends.
- Isolate transient state (staging/temp tables) from target tables and only “publish” to the target in an atomic, repeatable step.
- Record progress in a control/audit table (job_run_id, step, status, watermark, processed_files, checksum) so retries can resume or be safely skipped.
- Use deterministic keys/hashes for dedupe so the same source data re-applied doesn’t create duplicates.
- Prefer set-based SQL that the warehouse can execute atomically instead of row-by-row logic.

Component-level patterns (how to build idempotent components in Matillion)
- Use SQL components (Execute Query / Table Output) to perform idempotent database operations:
  - MERGE into target using natural/business/ surrogate keys so re-running MERGE is safe.
  - INSERT ... ON CONFLICT DO NOTHING / UPDATE (Postgres/Redshift/BQ equivalents) when available.
- Staging + atomic swap:
  - Load incoming data into a job-specific temp table (include job_run_id or timestamp in name or column).
  - Validate/transform/dedupe there.
  - Atomically swap into production (e.g., MERGE, INSERT INTO target SELECT FROM temp, or RENAME temp -> final when supported).
  - Drop temp after successful publish. If a retry occurs, the temp can be recreated deterministically.
- Use a stable load identifier:
  - Add a load_id or file_name column to staged rows. MERGE on load_id ensures the same load applied multiple times is idempotent.
- File ingestion (S3/GCS):
  - Track processed file names or object version IDs in a control table before deleting/moving files.
  - Only delete/move S3 objects after the corresponding ID is recorded as COMPLETE.
  - Use consistent manifest approach (process files listed in a manifest and mark manifest processed).
- Avoid destructive in-place deletes without guards:
  - If you must DELETE before INSERT, trap the job_run_id or snapshot so that re-run can detect already-processed deletes.
- Component retries and transient failures:
  - Make components re-runnable by ensuring they either are purely read-only, or their writes are idempotent (as above).
  - For non-idempotent external steps (e.g., calling an API that triggers side-effects), implement a dedupe/ack mechanism on that external system or record a unique request id so replays are no-ops.

Job-level patterns (orchestration, checkpoints, locks)
- Job_run control table:
  - At job start, create a job_run record with job_run_id, parameters, status=IN_PROGRESS, start_time.
  - After each major step, update the job_run row with step and status (or insert step-level rows).
  - On success mark status=COMPLETED with end_time and checksum; on failure mark FAILED with error details.
  - On job start, check if a COMPLETED job_run already exists for the same parameters and skip if appropriate.
- Checkpointing / resume:
  - Break jobs into explicit steps. After each step successfully completes, write a checkpoint record. A retry resumes from the last checkpoint.
  - Use Matillion variables to hold job_run_id and last_completed_step and branch logic to skip already-completed steps.
- Advisory locks / run-once semantics:
  - Use a lock table or DB advisory locks so only one instance of a job can process a given dataset concurrently.
  - Acquire the lock at start; if lock held, either fail or wait depending on policy. Ensure lock release on termination (use finally/cleanup logic).
- Watermarking for incremental loads:
  - Read the stored watermark (last_ts) from control table and query source for new rows.
  - Do not advance watermark until the new rows are safely merged/published. Only update watermark at the end of a successful publish step to make retries safe.
- File / message source coordination:
  - Record the set of message IDs or file names processed in the control table so retries don’t reprocess already-applied files.
- Roll-forward vs rollback:
  - Prefer roll-forward idempotent merges rather than complex rollbacks. If rollback is required, implement reversible operations with explicit compensating transactions recorded in control table.
- Error handling patterns:
  - Use Try/Catch logic implemented with branching and status updates: on exception write FAILED status, keep state for manual/automated retry.
  - Keep destructive finalization steps (like deleting source files) as the last step and gated by job_run status=COMPLETED.

How to implement these patterns in Matillion (concrete tactics)
- Use Execute Query components to:
  - Create/update job_run control rows, obtain job_run_id into a Matillion variable.
  - Acquire/release locks (using SQL or advisory lock calls).
  - Run MERGE/UPSERT SQL statements for the publish step.
- Use Transformation Jobs for set-based SQL work (staging, dedupe, merge).
- Use Orchestration Jobs to:
  - Sequence steps, set/check Matillion variables, branch on control table state, call transformation jobs.
  - Use the Run Orchestration / Run Transformation components to modularize steps and capture return codes.
- Use Python Script components when you need custom logic (e.g., build and record file lists from S3, call external APIs with idempotent request ids).
- Variables: store job_run_id, watermark, processed_file_list, last_step, and use them to make conditional branching decisions.
- File processing: use S3 components and Execute SQL to insert file records into processed_files table before deletion, or only delete after marking COMPLETE.

Example patterns (short)
- Snowflake/S3 incremental load:
  - Orchestration: create job_run row, list S3 files, insert file names into staging_files table with job_run_id, load files into temp table named temp_mytable_{job_run_id}, transformation: dedupe and MERGE temp -> target on business_key, update job_run status to COMPLETED, then delete S3 files only after COMPLETED.
- Checkpoint/resume:
  - After step1 (load), write checkpoint step=LOAD_DONE. On retry check job_run.last_step and skip load if LOAD_DONE. Repeat for TRANSFORM and PUBLISH steps.
- Watermark + merge:
  - Read watermark from control table, fetch source rows where ts > watermark, load and MERGE, on success update watermark = max(ts) from processed batch.

Testing and validation
- Re-run full pipeline from scratch multiple times and confirm stable final state and no duplicates.
- Simulate partial failure (kill job mid-flow) and confirm resume from checkpoint works and no double-application occurs.
- Test concurrent kicks to validate lock behavior.
- Add assertion queries (row counts, checksums) as automatic post-checks before marking COMPLETED.

Quick checklist before enabling retries
- Are write operations idempotent (MERGE/UPSERT or guarded INSERT)?
- Is there a control table with job_run_id and checkpoints?
- Are source artifacts (files/messages) recorded so they are not double-consumed?
- Is the watermark advanced only after successful publish?
- Are locks in place to avoid concurrent conflicting runs?
- Are finalization/destructive steps gated on job_run COMPLETED?

These patterns let you build Matillion pipelines that can be safely retried at the component and job levels with predictable, repeatable outcomes.

[Top](#top)

## How do you implement error handling with Try/Catch, conditional execution, Raise Data Exception, and rollback patterns?
Short, technical how-to for Matillion error-handling patterns (Try/Catch, conditional execution, Raise Data Exception, rollback).

1) Try / Catch (Orchestration jobs)
- Use the Try component to wrap the risky sequence of components.
- Wire a Catch component to the Try. Any failure inside the Try triggers the Catch path.
- Inside Catch perform recovery: log error, run rollback SQL, send notifications, set variables, or call compensating jobs.
- Capture context: use the built-in Job/Task failure output (Catch receives the failure, you can use Set Variable or SQL to record details) and use Send Email / Post to Slack to surface the exception.
- Example flow:
  - Try -> Run SQL (DML/Load) -> End
  - Try -> failure -> Catch -> Run SQL (ROLLBACK) -> Send Email -> Fail Job/End

2) Conditional execution (If / Boolean branching)
- Use an If component (or variable-driven boolean) to branch on validation checks or counts produced by a preceding SQL Script or Transformation.
- Typical pattern:
  - SQL Script: SELECT COUNT(*) INTO :invalid_count FROM staging WHERE <bad condition>;
  - If (invalid_count > 0) -> Raise Data Exception / Send notification / Abort; Else -> continue with commit/load.
- Use Set Variable to capture the result of a SQL or python component and reference it in the If component condition.
- Use this to avoid failing on unexpected data silently and to make failure decisions explicit.

3) Raise Data Exception (row-level / transformation validation)
- In Transformation jobs use the Raise Data Exception component to explicitly throw a job error for problematic rows.
- Typical placement: after a Filter/Calculator that identifies invalid rows (e.g., missing keys, bad types).
- Behavior: the Raise Data Exception will mark the job as failed and stop processing; include a custom message to aid triage.
- Use when you want deterministic failure when business rules are violated (e.g., duplicate PKs, NULL in required column).
- Pattern:
  - Source -> Filter invalid rows -> If any rows -> Raise Data Exception (message includes row/column info) -> upstream Catch handles notifications/rollback.

4) Rollback patterns (transaction control and compensating actions)
- For DB transactions:
  - Use a SQL Script component (or multiple Run SQL components) to execute BEGIN; do DML; then COMMIT or ROLLBACK.
  - Wire transaction COMMIT on the normal (Try success) path; wire ROLLBACK from the Catch path.
  - Example (Snowflake/Redshift generic):
    - Try -> SQL Script: BEGIN;
    - Try -> Run SQL inserts/updates
    - Try -> SQL Script: COMMIT;
    - Catch -> SQL Script: ROLLBACK;
- Important: verify the target DB supports the DDL/DML within transactions you need (some DDL auto-commits).
- For non-transactional operations (S3 file copies, API calls) implement compensating actions in the Catch path: delete files, reverse API calls, remove partial loads, or run cleanup SQL that undoes partial state.
- Keep transactional scope small and explicit. Prefer single-transaction subjobs invoked by Run Orchestration Job so you can start/commit/rollback at subjob boundaries.

5) End-to-end patterns and best practices
- Combine patterns:
  - Use validation SQL -> If invalid -> Raise Data Exception (or set variable) -> Try/Catch higher-level job does rollback and notify.
  - Wrap a Run Orchestration Job (that performs all DML within a DB transaction) with Try/Catch at the parent job to centralize rollback and alerts.
- Logging and diagnostics: write failure details (error text, failing SQL, row keys) to a table or send as a message in Catch.
- Idempotency: ensure retryable jobs clean up partial artifacts before re-running (either via rollback SQL or compensating steps).
- Test failure paths explicitly (force errors, invalid data) to ensure Catch/rollback/notifications behave as expected.
- Be aware of Matillion specifics: Try/Catch is an orchestration construct; Raise Data Exception is a transformation construct. Use variables and SQL Script to pass state between them.

Concise example (conceptual wiring)
- Parent Orchestration:
  - Start -> Try -> Run Orchestration Job (subjob: BEGIN; DML; COMMIT) -> End
  - Try -> failure -> Catch -> Run SQL (ROLLBACK) -> Send Email -> Fail Job

- Validation prior to commit:
  - SQL Script -> Set Variable invalid_count
  - If invalid_count > 0 -> Raise Data Exception (or Call Catch workflow)
  - Else -> proceed to commit

This delivers deterministic fail/notify/rollback behavior while keeping transactional control explicit.

[Top](#top)

## How do you implement alarms and notifications (email, Slack, Teams, PagerDuty) from job status and error conditions?
Short answer: use Matillion job-level failure hooks (On Failure / On Success) to call a small notification orchestration job that sends messages via Matillion components (Send Email) or HTTP calls (Slack/Teams/PagerDuty webhooks/APIs). Keep secrets in Matillion Credentials, include job context (name, run id, error text) in the message, and use PagerDuty for paging vs Slack/Teams/email for alerts.

How to implement (practical steps)

1) Design pattern
- For every production orchestration job set the “On Failure” (and optionally “On Success”) job property to run a dedicated notification orchestration job.
- The notification job gathers context (job name, run id, error), formats a message, and sends notifications via the appropriate channel(s).
- Store tokens/credentials in Matillion’s Credentials manager and reference them from components.

2) Collecting context and error details
- Pass the calling job name and any error message into the notification job as job-level variables (set when you call it), or
- Inside the notification job call the Matillion REST API to fetch the job execution details/logs and include them in the message.
- Include useful fields: job name, environment, run id/timestamp, step that failed, error message, link to the Matillion instance or job.

3) Sending email
- Use Matillion’s Send Email component (Orchestration). Configure SMTP using credentials.
- Compose subject/body with variables: e.g., Subject: “[ALERT] Matillion job failed: ${JOB_NAME}”
- Attach log snippets if useful (fetch via API or pass text variable).

4) Sending Slack
- Preferred: use a Slack Incoming Webhook or Slack API.
- Use Matillion’s Slack component if available, or use an HTTP Query component to POST the webhook URL.
- Example payload: {"text":"[ALERT] Job failed: MyJob — Error: ... — RunId: ..."}
- Store webhook URL in Credentials (do not hard-code).

5) Sending Microsoft Teams
- Use an Incoming Webhook for the Teams channel and POST JSON from an HTTP Query component.
- Example minimal payload: {"text":"[ALERT] Job failed: MyJob — Error: ..."}
- Optionally send a MessageCard for richer output (title, facts, themeColor).

6) Sending PagerDuty pages
- Use PagerDuty Events API v2 (POST to https://events.pagerduty.com/v2/enqueue) via HTTP Query.
- Payload example (simplified):
  {
    "routing_key":"<INTEGRATION_KEY>",
    "event_action":"trigger",
    "payload": {
      "summary":"Matillion job failed: MyJob",
      "severity":"critical",
      "source":"matillion",
      "custom_details": { "run_id":"...", "error":"..." }
    }
  }
- Store routing_key in Credentials. Use severity to control escalation.

7) Using Matillion REST API to enrich notifications
- If you need stack traces or log lines, call Matillion’s REST API from the notification job to fetch execution/log info and include it.
- This lets you send short summaries in Slack and full logs via email or attach to ticketing systems.

8) Aggregation / throttling / escalation
- For noisy failures, implement a digest job that collects failures over a time window and sends a single summary.
- For critical failures, immediately call PagerDuty; for informational failures send email/Slack.
- Protect against notification storms by checking recent alerts (store state in a lightweight table or use a variable) or rate-limit in the notification job.

9) Best practices
- Keep secrets in Credentials, not hard-coded.
- Include a direct link to the Matillion job run in messages for quick troubleshooting.
- Test webhooks/credentials in a dev environment first.
- Use structured JSON payloads for programmatic consumption.
- Use On Success to send completion notices when needed, and use an “always run” notification path for post-mortem summaries.

Example minimal implementation flow
- Orchestration Job A fails → Matillion runs the job configured in A’s On Failure.
- That notification job receives A’s name and error variable (or queries REST API).
- Notification job executes:
  - HTTP Query to Slack webhook with summary,
  - HTTP Query to PagerDuty (if severity=critical),
  - Send Email component with full log excerpt.

This covers the common channels (email, Slack, Teams, PagerDuty) and keeps notification logic centralized, secure, and easy to change.

[Top](#top)

## How do you centralize logs and metrics to CloudWatch/Stackdriver/Log Analytics and build dashboards for SLAs?
Short answer: collect Matillion logs (instance/application/job/task/audit) and structured job metrics (status, duration, row counts, last success timestamp) from the Matillion instance and push them into the native cloud logging/monitoring stack (CloudWatch, Cloud Logging/Monitoring, Log Analytics) using a log agent or metric API. Create log-based metrics or push custom metrics at job-completion and build dashboards/alerts from those metrics to measure SLAs.

Detailed, interview-style breakdown

1) What to centralize
- Logs: Matillion application logs, job/task logs, orchestration/transform execution logs, audit logs, system logs.
- Metrics: job duration, success/failure (count), rows processed, last_success_timestamp, SLA_miss_flag, queue/backpressure metrics, host resource metrics (CPU/mem/disk).
- Events/notifications: job start/finish/fail, retries, manual interventions.

2) Instrumentation pattern (recommended)
- Standardize a small JSON payload emitted at the end of every job (or on failure) with fields: environment, job_name, job_id, run_id, status, duration_seconds, rows_processed, start_ts, end_ts.
- Emit that payload either to:
  - stdout (if containerized) or to a local file that the log agent tails; or
  - call cloud metric API (PutMetricData / custom metric) from a Python Script or Run Command step inside the job; or
  - send to an intermediate (S3/GCS/Azure Blob) and run ingestion (Lambda/Cloud Function/Logic App) to push to monitoring.

3) How to forward logs/metrics to each cloud

AWS — CloudWatch Logs / CloudWatch Metrics
- Logs:
  - Install/enable the CloudWatch Logs agent or unified CloudWatch agent on the Matillion EC2 instance; configure it to tail Matillion log files (where Matillion writes app/task logs) and /var/log/syslog.
  - Configure log group names and stream patterns (e.g., /matillion/{env}/{job}).
  - Optionally configure Matillion to write job JSON payloads to a known file that the agent tails.
- Metrics:
  - Two options:
    1) Create log-based metrics in CloudWatch Logs (metric filters) by searching for your structured JSON/status lines and creating metric filters (e.g., count of "status=FAIL" per minute).
    2) Push custom metrics at job completion using aws cloudwatch put-metric-data from a Python Script or OS Command component:
       aws cloudwatch put-metric-data --namespace "Matillion" --metric-name JobDuration --dimensions Job=LoadCustomer,Env=prod --value 123 --unit Seconds
- Dashboards/Alerts:
  - Build CloudWatch Dashboard widgets for JobDuration (avg/p95), FailureCount, LastSuccessTimestamp (use metric math to compute staleness), SLA_miss_count.
  - Create CloudWatch Alarms on SLA_miss_count > 0 or LastSuccessTimestamp older than threshold (use metric math or create a binary custom metric).

GCP — Cloud Logging / Cloud Monitoring (Stackdriver)
- Logs:
  - Install the Ops agent (recommended) on the VM or configure GKE logging if Matillion runs in a container. Configure it to tail Matillion log files or pick up stdout.
  - Use structured JSON logs so Cloud Logging can parse fields.
  - Create logs-based metrics (counter or distribution) from search filters (e.g., severity=ERROR or jsonPayload.status=FAIL).
- Metrics:
  - Use logs-based metrics OR push custom metrics to Cloud Monitoring via the Monitoring API from a Python Script in Matillion (google-cloud-monitoring client).
  - Example Python snippet (conceptual): create TimeSeries with metric type custom.googleapis.com/matillion/job_duration and attach labels job_name/env.
- Dashboards/Alerts:
  - Build a Monitoring dashboard combining custom metrics and logs-based metrics.
  - Create alerting policies (e.g., last_success_timestamp < now - SLA_window or metric job_failure_count > 0) and notification channels (email, PagerDuty).

Azure — Log Analytics / Azure Monitor
- Logs:
  - Install the Azure Monitor agent or enable the Diagnostics extension on the VM; configure file collection for Matillion logs and system logs, pointing them to a Log Analytics workspace.
  - If Matillion runs on AKS or containers, use container insights / stdout capture to collect logs.
  - Prefer JSON structured logs to make Kusto parsing simple.
- Metrics:
  - Create log-based metrics in Log Analytics (Kusto query to count failures, etc.) or push custom metrics using the Azure Monitor metrics API from an OS command or script inside Matillion.
  - Example to push metric: use Azure Monitor REST API or the Azure CLI extension to send custom metrics from job finish script.
- Dashboards/Alerts:
  - Use Log Analytics queries to compute SLA compliance and build Azure Monitor Workbooks or Dashboards.
  - Configure alert rules (Log Search alerts or Metric alerts) and action groups for escalations.

4) Concrete implementation pattern (repeatable)
- Build a Job Wrapper template in Matillion:
  - Start: record start timestamp.
  - Core job steps.
  - End/On-Fail handler: compute duration, status, rows; emit structured JSON log line and call a small script that pushes the metric to the cloud monitoring API (or writes to a file the agent tails).
  - On-Failure: same payload with status=FAIL plus error details.
- Use one central S3/GCS/Blob bucket only if you want asynchronous ingestion pipelines (Lambda/Cloud Function) which then transform and push into the monitoring system; useful for unified multi-cloud.

5) Example commands/snippets (practical)
- AWS PutMetricData:
  aws cloudwatch put-metric-data --namespace "Matillion" --metric-name SLA_Miss --dimensions Job=LoadCustomer,Environment=prod --value 1 --unit Count
- GCP Python (conceptual):
  from google.cloud import monitoring_v3
  series = monitoring_v3.TimeSeries()
  # create series with custom.googleapis.com/matillion/sla_miss etc. then client.create_time_series
- Azure: use HTTP POST to Azure Monitor Metrics ingestion endpoint or az monitor metrics (refer to Azure docs for exact CLI).

6) Dashboard / SLA design ideas (what to surface)
- SLA metrics:
  - % on-time = 1 - (SLA_miss_count / total_runs) over window.
  - Time since last successful run (staleness).
  - Job success rate (1h/24h/7d).
  - Job duration percentiles (p50/p95/p99).
  - Failure trend and top failing jobs (heatmap).
- Visuals:
  - SLA compliance gauge, trend lines for duration and failure count, table of jobs with last run time/status and SLA status, alert count timeline.
- Alerts:
  - Immediate alert on any SLA_miss_count > 0 for critical pipelines.
  - Thresholds for failure rate and latency percentiles.
  - Escalation via SNS/PubSub/Action Groups to on-call.

7) Operational concerns and best practices
- Use structured JSON logs for reliable parsing.
- Use consistent metric namespaces/dimensions (env, team, job_group, job_name).
- Grant minimal IAM permissions to the agent or scripts.
- Be mindful of cost: log volume, ingestion, custom metric cardinality. Limit label cardinality (don’t use highly dynamic IDs as dimensions).
- Retention: set retention policies for logs and metrics.
- Test end-to-end with a synthetic job to validate dashboards and alerts.
- Keep a single standardized wrapper/job template so all jobs emit the same schema.

8) Matillion-specific notes
- Matillion UI shows job logs and history; export/automate by using the wrapper pattern or Matillion API if you need programmatic pulls.
- Use Matillion’s Python Script or Run Command components to call cloud CLI/SDKs or post webhooks.
- Use Matillion Notifications/Webhooks to stream failures to a function that converts them to monitoring metrics or logs.

Checklist to implement
- Decide SLA definitions and metric schema.
- Add standardized emit step (JSON + push) to all jobs (templated wrapper).
- Install/configure cloud logging agent on Matillion host to tail logs (or use push to metric API).
- Create log-based metrics / custom metrics from emitted fields.
- Build dashboards and alerting rules.
- Secure and tune (retention, cardinality, costs).

This approach centralizes both raw logs and structured SLA metrics in the native cloud monitoring service, gives you reliable dashboards (percentiles, staleness, on-time percentage), and generates alerts for SLA breaches.

[Top](#top)

## How do you use Matillion’s REST API to run jobs, set variables, retrieve task history, and automate deployments?
Quick overview
- Matillion REST API is authenticated with HTTPS using HTTP Basic Auth (username:password) or service account credentials. Endpoints and exact JSON shapes can vary by Matillion version, so confirm the API path on your instance (the API docs are available on the Matillion instance).
- Typical workflow: authenticate → call run/export/import/variable endpoints → poll status via returned run/task id → read history endpoints for logs/results.
- Below are the common operations and example calls (replace placeholders with your host/project/job names).

1) Run a job
- Call the run-job endpoint (POST). The response usually returns a runId or taskId you can poll for status.
- Example curl (generic):
  curl -u 'USERNAME:PASSWORD' \
    -H 'Content-Type: application/json' \
    -X POST "https://MATILLION_HOST/rest/v1/job/run" \
    -d '{
      "projectName":"MyProject",
      "jobName":"Orchestration/MyJob",
      "variables": { "ENV_VAR":"value", "DATE":"2025-08-29" }
    }'
- Typical flow:
  1. POST to run → receive runId/taskId.
  2. Poll the job status endpoint (GET /rest/v1/job/status or /rest/v1/task/{id}/status) until Completed/Failed.
- Minimal Python example (requests):
  import requests, time
  auth = ('USER','PASS')
  base = 'https://MATILLION_HOST/rest/v1'
  r = requests.post(f'{base}/job/run', auth=auth, json={'projectName':'MyProject','jobName':'Orchestration/MyJob','variables':{'x':'1'}})
  run = r.json()
  run_id = run.get('runId') or run.get('taskId')
  while True:
      s = requests.get(f'{base}/job/{run_id}/status', auth=auth).json()
      if s.get('status') in ('FINISHED','FAILED','STOPPED'): break
      time.sleep(5)

2) Set variables (project / environment / job scopes)
- Matillion exposes endpoints to create/update variables at project or environment scope. Use POST/PUT to set a variable value.
- Example curl (generic):
  curl -u 'USERNAME:PASSWORD' \
    -H 'Content-Type: application/json' \
    -X POST "https://MATILLION_HOST/rest/v1/variable" \
    -d '{
      "projectName":"MyProject",
      "scope":"environment",
      "variables":[ {"name":"API_ENDPOINT","value":"https://api.prod"} ]
    }'
- Notes:
  - Scopes: project-level, environment-level, or job-level (different endpoints/params).
  - After changing variables, you can trigger a job run that uses them.

3) Retrieve task / job history and logs
- Use the history endpoints to list past runs and inspect logs for a runId/taskId.
- Example curl to list history (generic):
  curl -u 'USERNAME:PASSWORD' "https://MATILLION_HOST/rest/v1/job/history?projectName=MyProject&jobName=Orchestration/MyJob&limit=10"
- Example to fetch logs/details for a run:
  curl -u 'USERNAME:PASSWORD' "https://MATILLION_HOST/rest/v1/job/{runId}/log"
- Tips:
  - Filter by date range, job name, status — query parameters vary by version.
  - Use the log endpoint to capture console output and task-level timings for auditing and alerting.

4) Automate deployments (export/import, CI/CD)
- Export project (produce a ZIP/JSON project file)
  - Endpoint typically: POST/GET /rest/v1/project/export or /rest/v1/export/project
  - Example:
    curl -u 'USER:PASS' -X GET "https://MATILLION_HOST/rest/v1/project/export?projectName=MyProject" -o MyProject.zip
- Import project on target instance
  - Endpoint: POST /rest/v1/project/import (multipart/form-data upload)
  - Example:
    curl -u 'USER:PASS' -F "project=@MyProject.zip" "https://TARGET_MATILLION/rest/v1/project/import"
- Typical CI/CD flow
  1. In CI (Jenkins/GitHub Actions/GitLab): export project from source Matillion (or pull from VCS if using Matillion Git integration).
  2. Store artifact in CI artifacts or file server.
  3. Upload artifact to target Matillion using import endpoint (optionally pass flags to overwrite).
  4. Update environment-specific variables and connection credentials via variable/config endpoints.
  5. Run smoke jobs via job-run endpoint and verify job history/logs for success.
  6. Record deployment result and artifact id in CI logs.
- Notes:
  - When automating, handle idempotency: check for existing jobs/projects, use overwrite flags as required by your Matillion version.
  - Secure credentials: use CI secrets for Matillion username/password and avoid exposing them in logs.

5) Error handling and best practices
- Always use HTTPS and a service account with least privileges necessary.
- Polling strategy: exponential backoff for status checks to avoid hammering the API.
- Parse returned run/task id and use the dedicated status/log endpoints rather than relying on UI polling.
- Confirm exact endpoint names and payloads on your Matillion instance’s API docs — Matillion versions add/rename endpoints.

Summary of practical steps to combine these operations in automation
- Authenticate (Basic Auth).
- Optionally set variables via variable endpoint for the target environment.
- Trigger job run with variables in the request body.
- Capture runId and poll the status endpoint; on completion fetch logs and store them.
- For deployments: export project from source → transfer artifact → import to target → set variables → run verification jobs → check history/logs.



[Top](#top)

## How do you secure the Matillion API with tokens/IP allowlists and enforce rate limits and audit trails?
Goal: enforce strong auth for Matillion’s REST/API surface, restrict allowed callers by network, throttle abuse, and retain immutable audit trails. Practical controls are a combination of Matillion features (tokens, RBAC, job history) plus cloud/network gateways, WAF/ALB, and centralized logging/SIEM.

1) Authentication / tokens
- Use Matillion API Tokens tied to specific Matillion users (Admin → API Tokens). Treat them as bearer tokens and assign tokens only to least-privilege users/roles (create a limited-role user for automation).
- Token policies: short lifetimes, per-application tokens (no shared tokens), name/annotate tokens with owner and purpose, store secrets in a vault (AWS Secrets Manager / Azure Key Vault / GCP Secret Manager), rotate regularly, and revoke on compromise.
- Enforce strong user auth for token issuance: require SSO (SAML/Okta) or LDAP for human users that create tokens. Apply MFA on the admin/SSO side.
- Transport security: force TLS (HTTPS) — terminate TLS at ALB/API Gateway with trusted certs (ACM). Prefer mTLS at the gateway if you need stronger client authentication.

2) Network / IP allowlist
- Defense in depth: enforce at the network perimeter (preferred) and at Matillion if you have an allowlist option.
- Cloud-network controls:
  - AWS: place Matillion in a private VPC, expose only through an Application Load Balancer or API Gateway. Security Group inbound: allow TCP 443 only from your gateway/bastion or corporate CIDRs. Use NACLs for extra filtering.
  - Azure: use NSGs, Application Gateway / WAF, and Service Endpoints or Private Link.
  - GCP: use VPC firewall rules and Cloud Armor.
- If Matillion instance has an "allowed IPs" or “Access Control” UI, populate it with corporate IP ranges and the gateway IPs. If not, enforce at the cloud layer.
- For developer access use a VPN or jump/bastion host so Matillion UI/API is not publicly open.

3) Rate limiting / throttling
- Matillion does not provide advanced per-token throttling; implement rate limits at the gateway or edge:
  - AWS API Gateway: use Usage Plans and API Keys (or Lambda authorizer reading Matillion tokens) and configure throttle settings (e.g., rate = 10 rps, burst = 20) and per-key quotas.
  - AWS ALB + WAF: use WAF rate-based rules (e.g., block IPs exceeding X requests/5 minutes).
  - Nginx example:
      limit_req_zone $binary_remote_addr zone=matillion:10m rate=10r/s;
      server { ...
        location / {
          limit_req zone=matillion burst=20 nodelay;
        }
      }
  - Cloudflare / Cloud Armor / Application Gateway WAF provide similar facilities and can rate-limit by IP, path, or header (token).
- Implement per-token or per-user quotas at the gateway/authorizer so a stray token can be throttled/revoked without impacting others.

4) Audit trails and logging
- Capture and centralize:
  - Matillion application logs and audit logs (user logins, project changes, token creation/revocation).
  - Orchestration and transformation job run history (start/end, user/trigger, success/failure, job steps and logs).
  - Edge/access logs: ALB/API Gateway access logs, WAF logs, CloudFront/Cloudflare logs.
  - Infrastructure logs: CloudTrail (AWS) / Activity Logs (Azure) / Audit Logs (GCP) for VM/API changes.
- Log content to record: timestamp, principal (user or token id), client IP, endpoint/method, request id/trace id, response code, latency, and any error messages.
- Centralize to CloudWatch Logs/Log Analytics/Cloud Logging or SIEM (Splunk, Elastic, SumoLogic). Enable log forwarding and set immutable storage (S3 with Object Lock or equivalent) for compliance.
- Retention & monitoring: define retention policies per compliance, enable indexes and saved searches (failed auth spikes, unusual IPs, sudden rate increases). Alert on anomalies (many 401/403, token reuse from multiple IPs, big bursts).
- Correlate job-run history with API calls (use request IDs or custom headers) so you can map API-driven orchestration runs to the caller.

5) Operational controls / RBAC
- Apply Matillion roles (Admin/Developer/Operator) and create automation-specific roles with minimal privileges.
- Use Git integration for project changes (auditable commits).
- Use SSO + SCIM provisioning to control who can create tokens; disable local admin accounts where possible.
- Have runbooks for token compromise: immediate revocation, search logs for use, rotate secrets, and notify stakeholders.

6) Example deployment pattern (recommended)
- Private Matillion instance in VPC.
- Fronted by API Gateway or ALB + WAF with TLS termination and rate-limiting rules.
- API Gateway or a Lambda authorizer validates Matillion API token or maps it to an API key/quota.
- Security Group: only gateway IPs allowed inbound to Matillion.
- Logs: API Gateway/ALB/WAF -> CloudWatch/S3; Matillion logs -> CloudWatch/S3; CloudTrail -> SIEM. Alerts wired to PagerDuty/Teams.

Checklist to implement immediately
- Create per-app API tokens, set expirations, store in vault, and rotate.
- Put Matillion behind gateway/WAF and restrict inbound SG/NSG to known IPs/VPN.
- Configure gateway rate limits (per-token/per-IP).
- Centralize logs (Matillion + ALB/API GW + WAF + CloudTrail) into SIEM, enable retention and alerting.
- Use SSO and least-privilege roles; document incident response for token compromise.

Result: tokens enforce identity, network controls enforce origin, gateway/WAF enforce throttling & IP rules, and centralized immutable logs provide auditability and detection.

[Top](#top)

## How do you monitor job duration trends, failures, and row counts to detect regressions and data anomalies?
Short answer: capture job-run metadata and row counts (either from Matillion or from the warehouse), centralize them as time-series metrics, and create dashboards + alert rules that detect statistically significant deviations (thresholds, percent-change, or anomaly models). Implementation options in Matillion:

What to capture
- Job run metadata: job_name, job_id/run_id, start_ts, end_ts, duration, status, error_message.
- Row/volume metrics: rows_read, rows_written, rows_loaded per table/step (or final table counts).
- Optional: component-level durations, connector latencies, resource usage.

Where to get the data
- Matillion UI and Job History: quick visibility of recent runs and durations.
- Matillion REST API: extract job-run history (start/end, status, logs) programmatically on a schedule and push to your monitoring/storage.
- Instrument jobs to emit metrics: use an HTTP/API Query or Python component at job end to post metrics to Datadog/Prometheus/CloudWatch/your metrics endpoint.
- Write to a warehouse logging table: at the end of each job insert a row into a central job_log table (job_name, run_id, start_ts, end_ts, duration, status, expected_rows, actual_rows, err). For row counts, run count(*) on the target/staging tables as part of the job and capture results into that table.

How to implement row counts inside Matillion
- After main load, run a SQL component per target to SELECT COUNT(*) (and optionally key-based freshness checks or per-partition counts) and insert those values into the job_log table using an SQL Insert component.
- Or capture component-level row counts by assigning them to variables (Matillion allows job variables and you can set them from SQL results) and persist those variables to the logging table.

Centralization and toolchain
- Store metrics in a time-series system (Prometheus/CloudWatch/Datadog) or in the warehouse (table with timestamps).
- Build dashboards (Grafana, Datadog, Looker, QuickSight) showing duration trends, failure rates, and row-count history per job/table.
- Forward Matillion system logs to cloud logging (CloudWatch/Cloud Logging) where available for deeper diagnostics.

Alerting and anomaly detection
- Simple threshold alerts: duration > X minutes, row count = 0, or status != SUCCESS.
- Relative-change alerts: row_count deviates > N% from 7-day median or duration > 2x median.
- Statistical alerts: z-score (current − mu)/sigma > 3, or seasonal decomposition / rolling-percentile anomaly detectors.
- Failure-rate alerts: failures in last 1 hour > X or failure rate over 24h > baseline + delta.
- Use automated anomaly detection in Datadog/Grafana/CloudWatch Anomaly Detection for noisy metrics.

Example implementation pattern (practical)
1) In Matillion job start: set a run_id and start_ts into job variables.
2) Run pipeline. For each target table, after load run a SQL component:
   - SELECT COUNT(*) AS rows INTO temp; then INSERT INTO job_log(job_name, run_id, start_ts, end_ts, duration, table_name, rows, status) VALUES(...).
3) At job end: set status variable and insert final summary row; also POST metrics to your monitoring API (HTTP Query component) with duration and rows.
4) Periodic collector: a small service (lambda/Cloud Function) that calls Matillion REST API for job history and reconciles/repairs any missing metrics into your metric store.
5) Create dashboards and alerts: define baseline windows (7–30 days), alert on % change or statistical anomalies.

Practical alert rules to start with
- Critical: job status != SUCCESS → immediate alert.
- High: duration > median(7d) * 3 OR duration > absolute threshold.
- Medium: row_count < 50% of 7d median OR row_count = 0.
- Trend: sustained increase in average duration or failure rate over a rolling 24–72h window.

Notes on reliability
- Persist metrics in the warehouse for historical forensic queries (easier to join with data domain metadata).
- Use both Matillion run history and independent checks (counts from warehouse) to detect silent data regressions where Matillion reports success but data is wrong.
- Include partition/key-level checks for large tables to detect partition-specific anomalies.

Example minimal schema for job_log
- job_name (text), run_id (text), start_ts (timestamp), end_ts (timestamp), duration_s (int), status (text), table_name (text), rows (bigint), error_text (text)

This approach gives stable dashboards for trends, robust alerts for regressions, and the ability to investigate failures and data anomalies from both Matillion-side and warehouse-side telemetry.

[Top](#top)

## How do you implement data quality checks (row counts, constraints, duplicates) natively and with frameworks like Great Expectations/Deequ?
High-level pattern
- Use Matillion to run the checks close to the data (SQL in the target warehouse) or to orchestrate an external validator (Great Expectations/Deequ).  
- Fail/branch the job based on check results using Matillion variables + If/Branch components (or by capturing exit codes from external jobs).  
- Persist validation results and metrics to a metadata table or S3 for audit and alerting, and quarantine bad data if needed.

Native Matillion (SQL-first) — row counts, constraints, duplicates
1) Row counts / expected vs actual
- After load, run a SQL query to get the count:
  SELECT COUNT(*) AS cnt FROM schema.table;
- Compare against an expected value (a Matillion variable or a historical value stored in a metadata table):
  - Use an “Execute Query” / “Database Query” component to set a Matillion variable to the count.
  - Use an “If Condition” component to compare variable to threshold; branch to success or failure.
- Example:
  - Query returns cnt. Use Matillion SQL like:
    SELECT CASE WHEN COUNT(*) BETWEEN :min_expected AND :max_expected THEN 1 ELSE 0 END AS ok FROM schema.table;
  - Read ok into a variable and branch.

2) Constraints (NOT NULL, ranges, enumerations, referential integrity)
- Run targeted SQL checks that return offending counts:
  - Not null violation:
    SELECT COUNT(*) FROM schema.table WHERE critical_col IS NULL;
  - Range violation:
    SELECT COUNT(*) FROM schema.table WHERE amount < 0 OR amount > 100000;
  - Enumeration:
    SELECT COUNT(*) FROM schema.table WHERE status NOT IN ('NEW','OPEN','CLOSED');
  - Referential integrity:
    SELECT COUNT(*) FROM child c LEFT JOIN parent p ON c.parent_id = p.id WHERE p.id IS NULL;
- If any check returns > 0 treat as failure: set variable, use If Component to abort, send alert, move data to quarantine table.

3) Duplicates
- Detect duplicates:
  SELECT key_col, COUNT(*) cnt FROM schema.table GROUP BY key_col HAVING COUNT(*) > 1;
- Get the count of duplicate keys: SELECT SUM(cnt) FROM (previous) sub;
- Deduplicate in a transform using window functions:
  SELECT * FROM (
    SELECT *,
           ROW_NUMBER() OVER (PARTITION BY key_col ORDER BY load_ts DESC) rn
    FROM schema.table
  ) t WHERE rn = 1;
- Or use Matillion Transform components to run the query and write de-duplicated output.

How to fail/branch the Matillion job
- Use Database Query to write check result into a variable (or a small result table/file).
- Use If Component (or Branch) to inspect that variable: route to success or route that performs remediation (quarantine, rollback, notify).
- Use the “Run Command” / “Run Python” component to explicitly exit with non-zero on failure if you need to fail the job run.

Integrating Great Expectations
1) Execution options
- Run GE inside a Python environment you control that Matillion can invoke:
  - Use Matillion’s Run Command / Run Python script component on the Matillion instance (if GE/venv is installed), OR
  - Package GE into a Docker container and call it from Matillion (Run Command), OR
  - Run GE as part of a Databricks notebook / EMR / Glue job and trigger from Matillion (Databricks/EMR components).
2) Typical flow
- Create Expectations suites (in a repo) for each table/column: expect_table_row_count_to_be_between, expect_column_values_to_not_be_null, expect_column_values_to_be_unique, expect_column_values_to_be_in_set, etc.
- Trigger GE validation (great_expectations.validation_operators or CLI validate) and write the validation result JSON to S3 or return it on stdout.
- Matillion reads the result (S3 File Read or capture stdout) and parses success boolean or "statistics.success" in the JSON.
- Use If/Branch to decide: continue / quarantine / re-run / notify.
3) Example Python snippet
  import great_expectations as ge
  batch = context.get_batch(batch_kwargs)
  result = context.run_validation_operator("action_list_operator", assets_to_validate=[batch], run_name="matillion-run")
  if not result["success"]:
      exit(2)   # Matillion sees non-zero exit code -> treat as failure
- Advantages: expressive expectations, human-readable suites, built-in docs, historical validation storage.
- Operational notes: store GE expectations in repo; store validation artifacts to S3; make sure the environment has access to the warehouse (JDBC or via exported data).

Integrating Deequ (Spark-based)
1) Execution options
- Deequ runs on Spark (Scala/Java). Options to run via Matillion:
  - Trigger an EMR step (Spark job with Deequ) or a Databricks notebook/job that runs Deequ, or run on Glue/EMR via pydeequ.
  - Matillion components exist to trigger EMR or Databricks and fetch job results.
2) Typical flow
- Attach Deequ checks: completeness, uniqueness, distinctness, min/max, anomaly detection, custom constraints.
- Run VerificationSuite (Scala) or pydeequ VerificationSuite (Python) against the loaded DataFrame.
- Write Deequ’s verification result (JSON) to S3 or return status.
- Matillion reads result and branches similarly to GE.
3) Example Scala-style Deequ snippet
  val verificationResult = VerificationSuite()
    .onData(dataFrame)
    .addCheck(
      Check(CheckLevel.Error, "Data quality checks")
        .isComplete("critical_col")
        .isUnique("business_key")
        .isContainedIn("status", Array("NEW","OPEN","CLOSED"))
        .hasSize(_ >= 1000 && _ <= 200000)
    )
    .run()
  // write verificationResult.json -> S3
- You can also use Deequ for metrics backfill and anomaly detection on time-series counts.

Where to run GE/Deequ from Matillion
- Preferred: run them in the compute that best scales to your data:
  - Small/medium data: run GE on Matillion instance (Python) or via a container.
  - Large datasets: run Deequ/pydeequ on Spark cluster (EMR/Databricks) triggered by Matillion.
- Always ensure network access from the execution environment to the target warehouse or that you extract a batch to S3 for validation.

Capturing and surfacing results
- Persist validation outcomes to a metadata table with columns: job, table, check_type, status, offending_count, run_ts, payload_link.
- Use Matillion’s notification components (email, webhook/Slack via HTTP) to notify on failure.
- Maintain historical metrics for trend analysis and alert on anomalies.

Example Matillion orchestration pattern
1) Load data into target table.
2) Run SQL-based quick checks (counts, nulls, duplicates) — write results into variables.
3) If any SQL-check fails: run remediation branch (quarantine, rollback), notify, stop.
4) If SQL-checks pass and you require deeper checks, trigger GE or Deequ job.
5) Parse validation result JSON, write to audit table, branch on pass/fail.

Tradeoffs and when to pick each approach
- Native SQL checks in Matillion: simplest, lowest latency, best for straightforward constraints and counts; easiest to fail job quickly.
- Great Expectations: best for rich expectations, documentation, team collaboration, and local Python environments; easier suite management and reporting.
- Deequ: best for very large datasets on Spark and for metric/anomaly capabilities at scale.

Summary
Use Matillion SQL checks and variables/If components for fast, native gating (counts, not-null, duplicates), and orchestrate Great Expectations or Deequ for richer or large-scale validations. Persist results and branch the pipeline on pass/fail to enforce data quality.

[Top](#top)

## How do you manage lineage from raw sources to curated tables and expose it to catalogs (Glue, Purview, Data Catalog)?
Short summary
- Treat Matillion as the source of design-time and runtime metadata (job JSON, component properties, run logs). 
- Construct a lineage graph by extracting: source datasets, transformation components (with SQL), target tables, plus runtime load metrics. 
- Push that graph into your catalog(s) via their ingestion APIs (AWS Glue API, Microsoft Purview/Atlas API, Google Data Catalog/lineage APIs) or via an OpenLineage-compatible layer if you standardize on that.

How I implement it (step‑by‑step, production pattern)

1) Enforce design standards in Matillion
- Use consistent job/component naming conventions and required annotations (job description, component "Table" properties, custom variables or tags that capture source system, dataset name, environment).
- Use explicit components for reads/writes (e.g., Table Input/Output, Load components) rather than ad‑hoc scripts where possible so you can reliably detect inputs/outputs.

2) Extract design-time metadata from Matillion
- Export job definitions (Matillion job JSON) or use the Matillion REST/metadata API to get job/component schemas and component properties (SQL text, target table names, file paths).
- For each component, parse properties to identify source datasets (S3 paths, external DB tables, APIs) and target datasets.

3) Capture runtime metadata
- Collect Matillion run history / component logs (rows processed, timestamps, run id). Matillion exposes run metadata in job history and logs that you can query via API or export to a metadata database / logging sink.
- Augment with target DB/system metadata (COPY/CMD logs, warehouse query history, information_schema) to verify actual reads/writes and row counts. This is essential when components generate dynamic SQL or use intermediate temp tables.

4) Build the lineage graph
- Represent entities as nodes (datasets/tables/files) and processes as edges (job/component runs). Include attributes: schema, partitioning, last update, record counts, owner, Git commit id.
- For field-level lineage, parse component SQL to map input columns to output columns. If SQL is generated dynamically, resolve it at runtime or instrument the generation step to emit mappings.

5) Normalize and store metadata
- Store extracted metadata and lineage in a central metadata store (graph DB or relational metadata DB) so you can deduplicate, version, and generate different views for catalogs.

6) Export to catalogs (Glue, Purview, Google Data Catalog)
- AWS Glue: use Glue APIs (boto3) to register/update table definitions and add key/value metadata in table Parameters or create custom Glue table properties. Glue currently doesn’t store complex process lineage natively, so either:
  - store process/lineage as custom metadata on tables, or
  - integrate with AWS Lake Formation or a separate lineage visualization that references Glue tables.
- Microsoft Purview: use the Purview (Atlas-compatible) REST APIs to create entities (DataSet, Process) and relationships (process -> inputs, process -> outputs). Purview is designed to store process lineage, so create "Process" entities for Matillion jobs/components and link to dataset entities.
- Google Data Catalog: create/patch entries via the Data Catalog API and use tags to attach metadata. For explicit lineage you can push to Google Data Lineage (if using BigQuery lineage tools) or use events to populate GCP lineage tooling. Where direct lineage is limited, store process info in tags or an external lineage service and link back to Data Catalog entries.

7) Automate and schedule
- Create a Matillion orchestration job or an external scheduler that:
  - runs after deployments/runs,
  - calls a metadata extractor (script or lambda/container) that reads Matillion job JSON + run logs,
  - updates your metadata store and pushes changes to Glue/Purview/Data Catalog.
- Keep this idempotent and incremental (update changed objects only).

8) Use standards where possible
- If you want multi-vendor interoperability, implement an OpenLineage (or Marquez) emitter for Matillion metadata: translate Matillion job/component/run to the OpenLineage schema and push to a centralized lineage/observability system. Then write small connectors from OpenLineage to each catalog.

Practical notes, gotchas, and best practices
- SQL parsing complexity: automatic field-level lineage can be brittle. Prefer explicit mappings in components, or capture lineage at both design and runtime to reconcile differences.
- Dynamic SQL & temp tables: resolve them at runtime or instrument the code to emit actual final target table names/columns.
- Versioning: capture Matillion job Git commit id and deployment timestamps to correlate lineage to code versions.
- Access & security: you need catalog write APIs with appropriate IAM/service principals. For Purview use service principal + appropriate RBAC; for Glue use IAM roles.
- Reconciliation: reconcile Matillion-declared lineage with observed activity (query history, COPY logs) to catch drift or undocumented processes.

Example minimal implementation overview
- Step A: Build a small metadata extractor that calls Matillion API to get job JSON and recent run logs.
- Step B: Parse components for "table" and "SQL" fields to produce triples (job/component) -> inputs -> outputs.
- Step C: Push dataset entries to the target catalog (Glue create_table / Purview entity / Data Catalog entry) and push lineage relationships (Purview/Atlas for full lineage; for Glue/Data Catalog add metadata/tags linking to a lineage process).
- Step D: Schedule extractor to run after Matillion deployments and periodically after runs.

Outcome
- You end up with a near-real‑time lineage graph that ties raw sources to curated tables, enriched with runtime metrics, available in your chosen catalog(s) for users and governance workflows.

[Top](#top)

## How do you design cost-aware pipelines that minimize warehouse time, leverage auto-suspend, and push heavy work in-warehouse?
High-level principles
- Push compute into the warehouse (ELT) — run SQL to transform data in-place instead of pulling rows into Matillion or Python.
- Minimize warehouse-on time by batching work, coalescing steps into single queries, and using auto-suspend/auto-resume appropriately.
- Avoid per-row or iterative operations that cause many short warehouse resumes; prefer set-based operations (CTAS, INSERT...SELECT, MERGE).
- Stage raw files (S3/GCS/Blob) and use the database-native bulk COPY/LOAD to land data quickly without prolonged compute.
- Use incremental/CDC patterns and partitioning/clustering to reduce data scanned per job.

Matillion patterns and components to use
- Orchestration job controls:
  - Use lightweight checks (Database Query components) to detect new/changed data before starting warehouse work.
  - Use Start Warehouse / Stop Warehouse (or the cloud provider equivalent) around heavy Transformation jobs so compute is on only when needed.
  - Use the “Run Transformation” component to call a Transformation job that executes SQL in-warehouse.
- Transformation job design:
  - Prefer SQL Script, Create Table, Merge, and Table Input components that generate single in-warehouse SQL statements rather than many small component translations.
  - Use Temporary/Transient tables and CTAS to perform multi-step work inside the warehouse in a single SQL pipeline.
  - Use Merge (upsert) components to do in-warehouse upserts instead of extract/compare/load loops.
- Loading:
  - Use bulk APIs (Salesforce Bulk, S3 stage + COPY INTO for Snowflake/Redshift, GCS load for BigQuery) and land raw files in storage first.
  - Use Matillion’s “S3 Load” / “GCS Load” / “Stage Load” components to stage then run a single COPY/LOAD statement.
- Avoid Matillion-hosted processing for heavy work:
  - Don’t use Python, Bash, or Grid components to process large datasets — they run on the Matillion instance and move data out of the warehouse, increasing runtime and network cost.
  - Use them only for orchestration logic, metadata checks, API control, or small object manipulation.

Auto-suspend/auto-resume considerations
- Set auto-suspend low enough to avoid paying for idle time, but not so low that you incur excessive resume overhead for many short jobs.
- If you have many short jobs, consolidate into fewer, slightly longer runs (batch windows) to amortize resume time.
- For unpredictable workloads, rely on explicit Start/Stop around the jobs you control to precisely manage compute; use auto-resume for ad-hoc queries.
- Measure resume latency and include it in job timing; sometimes choosing a larger warehouse reduces wall-clock time and total credits consumed.

Cost-aware SQL techniques
- Push logic into a single set-based SQL statement (use CTEs, single CTAS or INSERT...SELECT with all joins/aggregations).
- Minimize scanned data: filter by partition/date, use clustering or partition pruning where supported.
- Use materialized views / result cache for expensive repeated queries.
- Use compression and columnar formats for staged files to reduce I/O and load cost.
- Choose warehouse size based on compute-time tradeoff: higher concurrency/size can finish faster and reduce billable seconds.

Incremental / CDC patterns
- High-watermark columns (last_modified, updated_at) or CDC streams to only process changed rows.
- Use staging tables + MERGE into final tables.
- Use change tables or Snowflake Streams and Tasks where available to push only deltas through transformation.

Scheduling and concurrency
- Group related small tasks to run sequentially inside a single started warehouse where possible.
- Limit parallel jobs that share the same warehouse if concurrency causes scaling that increases cost.
- Use separate warehouses for low-priority/background jobs vs interactive or time-sensitive pipelines.

Monitoring and feedback loop
- Track warehouse credits and job durations (cloud billing + Matillion job logs).
- Alert on unexpected increases in run-time or credits.
- Keep a cost-per-pipeline dashboard and revisit cluster sizing and patterns periodically.

Concrete example orchestration flow (Snowflake/S3 example)
1. Orchestration job -> Database Query: check max(last_modified) in source/metadata; exit early if no new data.
2. Orchestration job -> Start Warehouse component (if not using auto-resume).
3. Orchestration job -> S3 load: copy new files to S3 staging.
4. Orchestration job -> Run Transformation job that executes a single SQL Script:
   - CREATE TEMP TABLE staged AS COPY INTO...;
   - INSERT INTO target_table SELECT ... FROM staged JOIN dim...;
   - MERGE to apply updates.
5. Orchestration job -> Stop Warehouse component.
6. Orchestration job -> metadata update and logging.

Quick checklist before deployment
- Are heavy ops done in-warehouse (single SQL where possible)? Y/N
- Do you use bulk load into stages instead of row APIs? Y/N
- Are you avoiding Python/Bash for large data transformations? Y/N
- Do you run a lightweight pre-check to avoid unnecessary runs? Y/N
- Do you control Start/Stop or have a sane auto-suspend value? Y/N
- Are delta/CDC patterns in place to limit data scanned? Y/N
- Are you monitoring credits and run times? Y/N

End.

[Top](#top)

## How do you estimate and attribute cost per pipeline/team using tags, warehouse usage, and Matillion task history?
High-level approach: ensure queries and jobs are tagged, collect two data sources (Matillion task/job history + warehouse query/usage/billing), then join and allocate costs either directly (per-query cost from the warehouse) or proportionally (time/CPU share) when direct attribution isn’t available.

1) Instrumentation / tagging
- Define a tagging taxonomy: team, cost_center, project, job_id. Make tags mandatory for new jobs.
- In Matillion:
  - Put a team/cost tag in project variables or job-level variables.
  - Ensure every orchestration/transformation job sets a tag that gets passed to the warehouse session (job_id, team, environment). For Snowflake use QUERY_TAG or a SET SESSION variable; for BigQuery add labels to jobs; for Redshift use WLM query_group or add comments/labels if supported.
  - For components that run SQL, prepend or inject a short session tag (e.g., ALTER SESSION SET QUERY_TAG = 'team=etl_team;job=my_job;run=12345') or use the connector feature if Matillion supports query-tagging for that platform.
- Tag Matillion instance usage (EC2/Azure VM) by job or by user where possible; enable Matillion audit logs.

2) Data sources to pull
- Matillion task/job history: use Matillion REST API or scheduled export. Fields to capture: job_name, job_id/run_id, project, team tag variable, start_time, end_time, status, component breakdown if available, instance_hostname.
- Warehouse query & billing data:
  - Snowflake: QUERY_HISTORY / ACCESS_HISTORY / METERING_VIEW from ACCOUNT_USAGE includes QUERY_TAG, EXECUTION_TIME, WAREHOUSE_NAME, CREDITS_USED. Use these to compute direct cost per query.
  - BigQuery: INFORMATION_SCHEMA.JOBS or audit logs include labels and bytes billed/slot time. Use labels to map to jobs.
  - Redshift: STL/ system tables for query runtime and CPU time; if WLM groups used, map query_group to job/team.
  - Cloud billing: use AWS/Azure/GCP cost allocation data for instance/warehouse hourly costs, storage, egress.

3) Matching Matillion runs to warehouse queries
- Primary (preferred): match on query tag/session variable that Matillion injects. For each Matillion run_id, collect all queries with that run_id tag.
- Fallback: match by time-window (queries executed between job start and job end) + user/schema + SQL pattern heuristics.
- Where multiple jobs overlap, use query-level tags if possible. Otherwise prorate by query execution time or CPU.

4) Attribution models / formulas
- Direct per-query cost (best): sum the cost metric from warehouse per query grouped by tag/team.
  - Example (Snowflake): cost(team) = SUM(CREDITS_USED) for QUERY_HISTORY where QUERY_TAG contains team=...
- Proportional allocation (when only warehouse-level costs available):
  - Get total warehouse compute cost for the period (C_total).
  - From query history, compute total execution_time (T_total) and per-team execution_time (T_team).
  - cost(team) = C_total * (T_team / T_total)
  - Optionally weight by bytes scanned or CPU, not just wall time.
- Matillion instance (EC2) cost allocation:
  - If single shared instance: decide charge model:
    - Time-based: allocate EC2 cost by sum(job_runtime) per team divided by monitored time window.
    - Active-usage: allocate only active job runtime (sum durations) relative to total active runtime.
  - If Matillion uses auto-scaling workers: use worker-hour metrics and attribute by job runtime on workers if available.
- Include other costs:
  - Storage and long-term resources: allocate by proportion of data size per team/project.
  - External API or 3rd-party cost: attach to job via Matillion metadata and add to team cost.

5) Implementation steps / ETL to compute costs
- Ingest Matillion job history daily via API into a cost schema (job_run table).
- Ingest warehouse query history and billing tables into the same schema.
- Normalize tags and parse query_tag into structured fields (team, job_id, run_id).
- Join:
  - If run_id present: join job_run.run_id = query_history.run_id
  - Else join by job_name/team and query start_time BETWEEN job_start and job_end
- Compute:
  - Per-query cost = query.billing_credits or compute_cost_estimate
  - Per-job cost = SUM(per-query cost) + allocated Matillion instance cost * (job_runtime / total_job_runtime)
  - Per-team cost = SUM(per-job cost)
- Save aggregates daily and expose via dashboard (BI): team, pipeline, job, date, runs, runtime, credits, $cost.

6) Example SQL/pseudocode (Snowflake)
- Get per-job credits (assuming QUERY_TAG contains run_id):
  SELECT j.team,
         j.job_name,
         j.run_id,
         SUM(q.credits_used) AS credits_used
  FROM job_runs j
  JOIN SNOWFLAKE.ACCOUNT_USAGE.QUERY_HISTORY q
    ON q.query_tag LIKE '%' || j.run_id || '%'
  WHERE q.start_time BETWEEN j.start_time - interval '1 minute' AND j.end_time + interval '1 minute'
  GROUP BY 1,2,3;
- If credits_used is not available, prorate warehouse cost:
  per_team_cost = warehouse_cost_period * (SUM(q.total_elapsed_time for team) / SUM(q.total_elapsed_time for warehouse))

7) Quality controls and edge cases
- Untagged queries: collect into "unknown" bucket. Run a periodic audit to identify untagged jobs and enforce tag policy.
- Retries and multi-run queries: use run_id to deduplicate and track retries separately.
- Auto-scaling / pause/resume warehouses: use the raw credits or cloud billing to capture real cost. Avoid using wall-clock time for paused warehouses.
- Caching: cached results may not incur compute; query history will show ZERO credits—handle accordingly.
- Mixed workloads on the same warehouse: encourage using separate warehouses per environment or workload class to simplify accounting, or leverage query_tag to separate.

8) Metrics to report
- Total cost by team, pipeline, job
- Credits or $ per run and per hour
- Runs, successful vs failed runs
- Average runtime and resource intensity (credits/run, bytes scanned/run)
- Percent of untagged or unassigned cost

9) Practical tips
- Make tagging automatic: template jobs, pre-fill variables, gating PRs that add jobs without tags.
- Use the warehouse/platform’s native query tagging features for highest fidelity (Snowflake QUERY_TAG, BigQuery labels, Redshift WLM).
- Schedule a daily batch that ingests job history + query history and produces the cost rollups.

This yields a defensible cost allocation: direct per-query attribution when tagging is in place, and proportional allocation when not, combined with Matillion host-cost allocation based on job runtime.

[Top](#top)

## How do you implement blue/green or canary releases for complex pipelines and roll back safely?
Short answer: use Matillion’s Git/Environment features plus safe data deployment patterns (staging + swap, idempotent jobs, backups) and automate promotion + monitoring so you can run the new pipeline in parallel, validate on production-like data or a sample, and switch traffic (or the target tables) atomically — with a clear, tested rollback plan to revert job configuration and/or table swaps quickly.

Pattern 1 — Blue/Green (parallel full pipelines)
- Concept: run two complete pipeline versions in parallel (blue = current prod, green = new). Green writes to separate targets (schema/table suffix, separate database, or separate cloud dataset). After verification, switch consumers to green or atomically swap tables; keep blue as fallback.
- How to implement in Matillion:
  - Version control: put changes into a Git branch (green). Use Matillion Project Git integration so the green pipeline is fully reproducible.
  - Separate targets: use Environment variables / Credentials to point green to a different schema or database. Name tables with suffixes or use per-environment schemas (prod_blue, prod_green).
  - Run green in parallel: trigger Matillion jobs via the REST API or scheduler and monitor status. Use the same orchestration logic but different environment variables.
  - Validation: run automated data quality (QA) jobs inside Matillion to compare row counts, checksums, key distributions, and business rules between blue and green results.
  - Cutover:
    - Best: atomically swap table names or views (Snowflake: CREATE OR REPLACE VIEW or zero-downtime table rename patterns; BigQuery: use table aliases or swap with partition/table copy; Redshift: swap via views or rename with minimal downtime).
    - Alternative: change a single environment variable (or credentials) that all downstream jobs and consumers use to point from blue schema to green schema, then re-run short orchestrations to reconcile state.
  - Post-cutover: keep blue intact (don’t drop) until a retention window passes. Record exact Git commit/deployment metadata for traceability.
- Rollback:
  - If problems occur, either:
    - switch consumers back to blue (reverse the environment variable or view rename), or
    - rename tables back to the original names if you used swap renames.
  - Revert Matillion project Git branch (or check out previous commit) and redeploy/import if you changed the Matillion project itself.
  - Reconcile incremental data produced during the failed green period using staging and incremental logic or replay from source CDC.

Pattern 2 — Canary (incremental traffic/sample)
- Concept: run the new pipeline on a small fraction of data or time windows; gradually increase traffic if metrics are good.
- How to implement in Matillion:
  - Parameterize sampling: add a job variable (sample_pct, sample_id_mod) to route a subset of source records to green processing. Examples: hash(id) % 100 < sample_pct or use source keys/time windows.
  - Use environment variables to select canary mode vs full mode.
  - Create a canary orchestration that runs green pipeline only for sample keys or selected partitions.
  - Automate promotion: CI/CD or orchestrator increases sample_pct over time as metrics pass.
  - Validation: run automated comparisons on the sampled outputs (data correctness checks, latency, resource usage).
- Rollback:
  - Stop increasing sample_pct and immediately set it to 0 (via environment variable), or disable the green jobs via API.
  - Revert pipeline code in Git if needed and re-run impacted jobs to reprocess sampled records via the stable pipeline.

Automation & CI/CD
- Use Git branches for dev/green, merge to main for production, and use Matillion REST API or the project export/import CLI to deploy branches to the Matillion instance used for production.
- Use an external CI runner (Jenkins/GitHub Actions/GitLab CI) to:
  - Validate pipeline JSON (lint), run unit tests, and export a release artifact (Matillion project ZIP).
  - Deploy artifact to Matillion (project import via API) then trigger job runs for smoke tests.
  - Orchestrate blue/green promotion steps (change environment variable, swap views, promote DNS/consumers).
- Trigger and monitor jobs via Matillion REST API to implement automated cutover and rollback steps.

Safe data practices to enable safe rollbacks
- Idempotency: design jobs so re-running them is safe (upsert with natural keys, merge patterns).
- Staging + atomic swap: always load into staging/new tables, validate, then swap or replace the production pointer.
- Backups & snapshots: take table snapshots or cloud-native backups before destructive schema changes; keep historical data for quick restore.
- Backwards-compatible schema changes: prefer additive changes; use views to hide schema differences from consumers.
- Checkpointing/state: persist last-processed offsets/timestamps so you can resume or replay reliably.
- Validation gates: automated data quality checks with thresholds that automatically block promotion or trigger rollbacks.
- Observability: collect and monitor key metrics (row counts, latencies, error rates, downstream consumer errors); automate alerts and rollbacks on breaches.

Rollback playbook (concrete sequence)
1. Detect failure via metrics or QA checks.
2. Immediately stop/disable the green pipeline jobs (REST API + job state).
3. If using blue/green table swap: atomically switch the pointer back to blue (rename tables or revert view/env variable).
4. If using canary: set sample_pct to 0 and reprocess the affected keys via blue pipeline.
5. Revert Matillion project code: git checkout <previous-commit> and redeploy/import, or merge a rollback branch.
6. Reconcile data: run reconciliation jobs to fix any partial writes, using idempotent upserts or replay from source/CDC.
7. Keep logs/artifacts and take snapshots for postmortem.

Examples of practical implementations
- Snowflake: load into schema prod_green, run QA, then perform an atomic swap by renaming tables or using CREATE OR REPLACE VIEW to point consumers to the new objects. Keep prod_blue as backup.
- BigQuery: write to prod_green tables, validate, then use table copy/rename or change dataset-level aliases where possible; or have consumers use a view that you update to point to new tables.
- Redshift: write to new schema and flip a view that consumers query; if you need physical rename, ensure you handle cluster locks/down time.

Operational tips
- Keep the blue copy running and readable for a retention window; don’t drop it immediately.
- Keep deployments small and reversible — break complex changes into multiple deployable, backward-compatible steps.
- Test the rollback procedure in a staging environment and automate as much as possible.
- Maintain an “Immutable deployment record” (Git commit id, deployed artifact, environment variables) for each release.
- Use feature flags or environment variables to make cutover a single configuration change rather than code edits.

Summary checklist before a release
- Jobs are idempotent and use staging.
- Environment variables allow target switching.
- Git branch for the release exists and is deployable.
- Automated QA/data-quality jobs ready to validate green.
- Monitoring and alerting for key metrics.
- Backup/snapshot of production targets.
- Tested rollback script that can be run automatically or manually.

This approach uses Matillion’s Git, environment variables/credentials, job parameterization, staging + swap patterns, the REST API for orchestration, and strong data safety practices to implement blue/green or canary releases with fast, safe rollback paths.

[Top](#top)

## How do you build reusable job templates and shared jobs for common patterns (file loads, SCD merges, CDC merges)?
Approach summary
- Build small, focused reusable jobs (child jobs) for single responsibilities (file discovery/load, staging, merge logic, audit) and call them from parent orchestration jobs.  
- Parameterize everything via Job/Project/Environment variables so jobs are configuration-driven.  
- Expose templates in your repo (Matillion job templates / exported job JSON) and keep reusable jobs in a shared “common” folder or project branch.  
- Standardize logging, error handling, and test harness (dry-run flag, sample inputs).  
- Use Run Orchestration / Run Transformation to invoke shared jobs and pass arguments.

Common reusable building blocks and how to implement them
1) Shared utilities (always present)
- Variables: source_bucket, file_pattern, file_mask, file_format, staging_schema, staging_table, target_schema, target_table, key_columns, surrogate_key_column, effective_from_col, effective_to_col, current_flag_col, change_type_col, lsn_col, dry_run, notify_emails. Keep sensitive values in Environment variables.  
- Components: Get file list (S3/GCS/Azure List objects), conditional branch, notification (SMTP/Slack), failure handler, audit insert/update component.  
- Location: single “Common” folder or separate project so multiple teams can call the same jobs.

2) File-load template
- Purpose: discover files, stage raw file into a staging table (parquet/CSV/JSON), validate schema, produce a canonical staging table.
- Key variables: source_path, file_pattern, file_format, staging_schema, staging_table, file_header_rows, delimiter, columns_map (JSON or mapping table).
- Components to use: List objects, Download/Copy/Cloud-specific Load component (e.g., S3 Load / COPY INTO / Azure Blob Load), Orchestration SQL to create/drop staging table, Transformation job if flattening/normalizing needed.
- Behavior: checkpoint file names, move processed files to archive folder or tag them, write audit record with row counts and file metadata.
- Reuse: parent orchestration calls this job with variables specifying file and target staging table.

3) SCD merge template (supporting Type 1 and Type 2)
- Purpose: apply changes from staging to slowly changing target with configurable SCD type.
- Key variables: target_schema, target_table, staging_schema, staging_table, business_key_cols (comma-separated), surrogate_key_col, scd_type (1|2), effective_from_col, effective_to_col, current_flag_col, history_retention_days, hashing flag.
- Components/technique:
  - Deduplicate staging by business key (ROW_NUMBER over ordering column if present).  
  - Use a Merge (database MERGE) or SQL Upsert pattern: 
    - For Type 1: update target set columns = staging where business keys match and data changed, insert for non-matches.  
    - For Type 2: detect changed rows -> update existing records to set effective_to = now and current_flag = false; insert new row with new surrogate key/effective_from/current_flag true. Use database MERGE where possible for performance.
  - Use audit table to log counts of inserts/updates/no-changes.
  - Provide dry_run: generate and validate SQL but don’t commit (or write changes to a shadow table).
- Reuse: encapsulate SCD logic in a Transformation or SQL job and call with variables. Keep SQL templates in job variables or script components for portability.

4) CDC merge template
- Purpose: consume CDC stream (change_type + key + payload + LSN/timestamp), collapse to latest per key, apply deletions/inserts/updates deterministically.
- Key variables: cdc_schema, cdc_table, target_schema, target_table, business_key_cols, change_type_col, lsn_col/timestamp_col, ordering_col, apply_delete_flag.
- Components/technique:
  - Stage CDC events; dedupe/resolve by business key selecting latest LSN/timestamp (ROW_NUMBER partition by key order by lsn desc).  
  - Split by change_type: DELETE -> delete from target where key matches; INSERT/UPDATE -> upsert via MERGE. Prefer a single MERGE that handles delete via WHEN MATCHED AND change_type='D' THEN DELETE, WHEN MATCHED THEN UPDATE, WHEN NOT MATCHED THEN INSERT (if DB supports).  
  - For out-of-order events use LSN or tombstone logic; include conflict resolution rules (last-write-wins or LSN-based).
  - Support transactional boundaries: batch CDC into transaction windows and commit once per batch.
- Reuse: CDC job is called with flags indicating source format (Debezium, DB native), and mappings of columns.

How to wire reusable jobs together (pattern)
- Parent orchestration:
  1. Discover files/CDC messages (call File-list/CDC-list job).  
  2. For each file or batch, call File-load job to stage raw data (Run Orchestration).  
  3. Validate staging (call validation job).  
  4. Call SCD or CDC merge job (Run Transformation or Run Orchestration) passing schema/table and key mappings.  
  5. Run audit/notification and move/archive files on success; on failure call error handler that logs and notifies.
- Pass variables when invoking child jobs. Use job “Arguments” to pass values or set Project variables before calling.

Deployment, governance and best practices
- Git-based templates: keep canonical child jobs in a single repo branch (common library). Use branching and pull requests for changes. Use exported job JSON as template artifacts for onboarding.
- Environments: use Environment variables for credentials and environment-specific prefixes (dev/test/prod). Keep only config difference across environments.  
- Idempotency: design merges to be idempotent (use staging + MERGE patterns, dedupe CDC). Include dry-run and backout logic.  
- Observability: standard audit table with: job_name, run_id, start_ts, end_ts, source_count, inserted, updated, deleted, errors, file_name, LSN_range. Expose failure codes and line-level error retention for reprocessing.  
- Security: least-privileged IAM roles for reading source storage and writing to target. Secrets in Environment variables.  
- Performance: use bulk loads (COPY, parquet) to staging then set-based MERGE; avoid row-by-row operations.

Example variable list for an SCD job (concise)
- TARGET_SCHEMA, TARGET_TABLE, STAGING_SCHEMA, STAGING_TABLE, BUSINESS_KEYS (comma-separated), SURROGATE_KEY, SCD_TYPE, EFF_FROM_COL, EFF_TO_COL, CURR_FLAG_COL, DRY_RUN.

Example variable list for a CDC job (concise)
- CDC_SCHEMA, CDC_TABLE, TARGET_SCHEMA, TARGET_TABLE, BUSINESS_KEYS, CHANGE_COL, LSN_COL, APPLY_DELETE ('Y'/'N'), DRY_RUN.

Common pitfalls to avoid
- Hardcoding schema/table names — prevents reuse.  
- Not deduplicating CDC input — leads to data corruption.  
- Trying to do heavy row-by-row processing in orchestration; push set operations into database MERGE.  
- No audit or idempotency — reprocessing becomes risky.  
- Using credentials or environment-specific settings inside job logic rather than Environment variables.

Performance and testing
- Unit-test each reusable job in a dev environment with representative sample files/CDC snaps.  
- Load-test merge logic with high cardinality keys and large batches; tune commit batch sizes.  
- Add assertion steps to fail early (e.g., rowcounts mismatch) and support rerun with savepoints.

Result
You get a library of small, parameterized, tested jobs (file-load, validations, SCD-merge, CDC-merge, audit) called by orchestrations. This minimizes duplication, speeds onboarding, enforces standards, and simplifies maintenance.

[Top](#top)

## How do you implement metadata-driven ingestion frameworks using grids, dictionaries, and dynamic SQL generation?
High-level approach
- Treat metadata as the single source of truth: source definitions, target definitions, incremental keys, column mappings, load type (full/incremental/upsert), file locations, control flags, and watermark/CDC settings.
- Store that metadata where it’s easy to iterate from Matillion: an in-job Grid for small static sets, or a control table / JSON file / S3 manifest for production-scale metadata.
- Use an Iterator to loop the metadata rows, bind row values to Matillion variables, generate the SQL needed for that row dynamically, execute it, and update audit/watermark info.

Canonical Matillion implementation pattern (components + flow)
1) Metadata store
   - Small project/test: use a Grid component with columns like connection, src_schema, src_table, tgt_schema, tgt_table, load_type, incr_col, cols_list, transform_json.
   - Prod: store metadata in a control table (metadata_catalog) in your warehouse or an external JSON manifest in S3. Query it at job start.

2) Driver job
   - SQL Query component (if metadata in DB) or Grid (built-in) feeds a Row/ Grid Iterator.
   - Use Grid Iterator / Row Iterator to drive per-source iterations.
   - For each iteration set job variables (Set Variable component) for: src_conn, src_table, tgt_table, load_type, incr_col, cols, transform_rules, batch_size.

3) Dictionary/Mapping usage
   - Implement dictionaries for:
     - Column mappings (source_col -> target_col)
     - Transformation rules (cast, default, concat)
     - Primary key definitions and upsert rules
     - Connection-specific settings (file format, delimiter, parallelism)
   - Dictionary can be:
     - A separate Grid / table joined to the main metadata row
     - A JSON blob stored in a metadata column (then parsed in Python)
     - A project/environment variable for global mappings

4) Dynamic SQL generation
   - Keep SQL templates with placeholders, e.g.:
     INSERT INTO {tgt_schema}.{tgt_table} ({tgt_cols})
     SELECT {src_cols} FROM {src_schema}.{src_table} {where_clause};
   - Generate the concrete SQL string per iteration by substituting placeholders with values from the grid/dictionary.
   - Methods for substitution:
     - Use Matillion variable substitution (${variable_name}) for simple concatenation.
     - Use a Python Script component for complex templating (JSON parsing, dynamic column lists, conditional WHERE clauses). Python makes it easy to build strings safely and set Matillion variables for downstream components.

5) Execution
   - Execute generated SQL in a Run SQL command / DB Query component.
   - For bulk loads (files), use Bulk Load components (S3 Load for Redshift, Snowflake Load for Snowflake) parameterized by the metadata variables.
   - For upserts, generate MERGE/INSERT ... ON CONFLICT statements based on the PK dictionary.

6) Audit, watermark and error handling
   - After successful run, update a control/audit table with status, row counts, runtime, and new watermark (max(incr_col)).
   - On failure, log error text, set status, optionally retry or mark source as failed depending on a metadata flag.
   - Use try/except blocks in Python components and check exit codes from DB components to capture errors.

Concrete example (conceptual)
- Metadata Grid row:
  source_conn = "src_db"
  src_schema = "raw"
  src_table = "orders"
  tgt_schema = "dw"
  tgt_table = "dim_orders"
  load_type = "incremental"
  incr_col = "modified_ts"
  cols_list = "order_id, cust_id, amount, modified_ts"
  transform_json = '{"amount":"CAST(amount AS numeric(18,2))","cust_id":"COALESCE(cust_id,-1)"}'

- Python component (pseudo)
  1) Read job variables set by Grid Iterator: src_schema, src_table, tgt_schema, tgt_table, incr_col, cols_list, transform_json
  2) Parse transform_json into a dict
  3) Build select_list by applying transforms to each src column:
     select_list = [transform.get(col, col) + " AS " + col for col in cols]
  4) Build where_clause = f"WHERE {incr_col} > (SELECT last_watermark FROM meta_watermark WHERE table = '{src_table}')"
  5) sql = f"INSERT INTO {tgt_schema}.{tgt_table} ({cols_list}) SELECT {', '.join(select_list)} FROM {src_schema}.{src_table} {where_clause};"
  6) Set a Matillion variable SQL_STATEMENT = sql

- Execute
  - Run the SQL_STATEMENT with a Run SQL Query component.

Best practices and considerations
- Prefer metadata/control table for production so metadata changes are auditable and can be edited without editing jobs.
- Keep SQL templates modular and version-controlled. Use Python for conditional logic; use simple ${vars} substitution for trivial cases.
- Pushdown and performance: build SQL that leverages the target DB’s set-based operations. Avoid row-by-row operations in Matillion where possible.
- Concurrency: design the iterator to run either sequentially or parallel depending on resource limits. Use concurrency metadata flags for per-source parallelism.
- Security: store connection names in Matillion and never hard-code credentials in metadata. Validate and sanitize metadata values before constructing SQL.
- Testing: include a dry-run flag in metadata to build SQL and log it without execution. Use separate dev/prod metadata environments.
- Audit & Idempotency: update watermark and audit rows atomically after successful commits; include unique run_id in audit logs.

When to use Grid vs external metadata
- Grid: quick prototypes, small fixed lists, parameterized demo jobs.
- External metadata table / JSON: production scale, multi-team management, dynamic changes, easier history and governance.

This combination (Grid/dictionary => iterator => dynamic SQL template => execute => audit/watermark) is the standard metadata-driven ingestion pattern in Matillion.

[Top](#top)

## How do you handle schema drift and column evolution for relational and semi-structured sources?
Short answer: treat schema drift as a metadata problem and build a small metadata-driven control loop inside Matillion that (1) ingests raw data without schema assumptions, (2) detects differences vs. stored metadata, (3) applies safe structural changes (ADD columns, preserve old columns, store raw payloads), and (4) adapts downstream transformations dynamically. Below are concrete patterns, Matillion components to use, and example SQL for relational and semi-structured sources.

High-level pattern
- Raw landing: load the source payload as-is into a landing/staging area (full table copy for relational, a single raw column for semi-structured e.g. VARIANT/JSON).
- Detect: compare current source schema (INFORMATION_SCHEMA or by parsing JSON) to a pipeline metadata table containing expected columns/types.
- Reconcile/Apply: generate and run DDL/DDL-like operations to bring staging in sync (e.g., ALTER TABLE ADD COLUMN, create new staging columns as VARIANT/STRING).
- Normalize downstream: use metadata-driven mappings to update transformation logic (automatically add mapping/flatten steps or handle new fields as "extra" columns).
- Versioning/backfill: optionally backfill historical rows for new columns or keep null/defaults and maintain a column history table.

Matillion components to implement this
- Orchestration jobs for control flow and scheduling.
- Table Iterator (or custom iterator) to loop through tables/sources.
- Execute Query / Database Query components to run metadata queries and DDL (ALTER/CREATE).
- Python Script (or Bash/Run Command) to compute diffs and build dynamic SQL statements if required.
- Create Table / S3 Load / Bulk Load components to stage data.
- Variables (Environment/Job variables) to pass table/column lists and assembled SQL.
- Transformation jobs to do downstream flattening, parsing, and normalization; these can be metadata-driven.

Relational sources — pragmatic approach
1) Landing: load the full source table into a staging schema in the target EDW (COPY, INSERT ... SELECT *, etc.) so you capture all columns automatically.
2) Detect new/missing columns:
   - Snowflake example:
     SELECT column_name, data_type
     FROM information_schema.columns
     WHERE table_schema='SRC_SCHEMA' AND table_name='SRC_TABLE';
   - BigQuery:
     SELECT column_name, data_type FROM `project.dataset.INFORMATION_SCHEMA.COLUMNS` WHERE table_name='SRC_TABLE';
   - Redshift:
     SELECT "column", type FROM pg_table_def WHERE schemaname='schema' AND tablename='table';
   Compare that list to your pipeline metadata table (e.g., pipeline_metadata.columns).
3) Apply changes:
   - Generate ALTER TABLE ADD COLUMN statements for newly discovered columns. Default to a safe type (VARCHAR/STRING) and then later cast/normalize.
   - Use Matillion Execute Query or Python Script to run DDL. Example pseudo SQL:
     ALTER TABLE stg.SRC_TABLE ADD COLUMN new_col VARCHAR;
4) Downstream transform:
   - Update metadata mapping table to include new columns so transformation jobs can automatically create output columns.
   - For automated pipelines, have transformation jobs read the metadata table and add columns via dynamic SQL or generate a SELECT that includes COALESCE(raw_col::type, NULL) for new columns.
5) Type changes and renames:
   - Detect type changes by comparing data_type values. Treat type changes conservatively: create a new column with the wider type, stage data there, then run a controlled migration.
   - Renames: these are ambiguous — require business mapping table or heuristics (similar name, same distinct value set). Prefer explicit mapping.

Semi-structured sources (JSON, XML) — recommended approach
1) Landing: load raw payload into a single JSON/VARIANT column (Snowflake VARIANT, BigQuery JSON/STRING, Redshift SUPER if available). This preserves all fields regardless of schema drift.
   - Snowflake COPY INTO stg.table(raw_variant) FROM @s3/... FILE_FORMAT=(type=json)
2) Discover keys:
   - Snowflake keys example:
     SELECT DISTINCT f.key
     FROM stg.table, LATERAL FLATTEN(input=>raw_variant) f;
   - BigQuery: UNNEST + JSON functions or query a set of sample rows and extract keys with JSON functions.
3) Reconcile:
   - For each discovered key not present in metadata, add a column to the normalized table (string/variant), or keep it accessible from the raw VARIANT until someone requests normalization.
   - Option: store a JSON blob of "unknown keys" into a single column to avoid frequent DDL.
4) Flattening and mapping:
   - Use SQL (LATERAL FLATTEN, JSON_EXTRACT, JSON_VALUE) to extract nested structures to normalized columns. Drive the list of extracted keys from your metadata table so the transformation is self-updating.
5) Nested arrays/complex objects:
   - Persist complex nested structures as separate normalized tables generated by iterating over keys and using LATERAL FLATTEN; capture schema changes per nested object similarly.

Example implementation flow in Matillion
- Orchestration job:
  - Table Iterator over source tables/files.
  - For each table:
    - Run Execute Query to get current column list from information_schema (or run a Python Script that calls the DB).
    - Compare to pipeline metadata table (Python or Execute Query returning diff).
    - If new columns found: build ALTER TABLE statements (via Python Script or SQL Generator) and execute them with Execute Query.
    - Kick off a Transformation job to normalize data using the updated metadata.
- Transformation job:
  - Read metadata table, generate SELECT that includes all known columns and a catch-all for raw/unknown fields.
  - Write normalized rows to final schema.

Handling tricky cases
- Frequent small changes: keep raw payload and only normalize fields that are mature (less churn). Avoid DDL thrash by batching schema updates (daily/weekly).
- Renames: require human confirmation or a mapping service to avoid data loss.
- Type collisions: prefer widening types and validating downstream conversions in a controlled job.
- Backfill: optionally run backfill SQL to populate new columns for historical rows using expressions on the raw payload.

Monitoring, governance, and testing
- Log schema diffs to a metadata/version table (who, when, detected columns/types).
- Add automated tests that run after DDL: nullability checks, type checks, sample rows validation.
- Fail the job or send alerts when unexpected destructive changes are detected (column drops, incompatible type changes, etc.).
- Keep lineage: record which transformation version introduced a structural change.

Summary checklist for Matillion
- Always land raw (full table or raw JSON/VARIANT).
- Use information_schema or flattening functions to detect schema differences.
- Use Matillion Execute Query + Python Script + Variables to compute and apply DDL dynamically.
- Drive transformations from a metadata table so downstream jobs adapt automatically.
- Prefer additive DDL (ADD columns, add variant columns) and defer destructive changes to controlled releases.

[Top](#top)

## How do you implement SCD Type 1 and Type 2 patterns in Matillion efficiently across Snowflake/BigQuery/Redshift/Synapse?
Short answer: implement SCD logic as ELT (push as much work as possible to the target DB), stage incoming rows, compute a change-hash on the business attributes, then use set-based SQL (MERGE where supported, or staged UPDATE + INSERT) to apply Type 1 or Type 2. In Matillion do this inside Transformation jobs (orchestration for orchestration tasks), using DB-native components (Table Input, Table Output, DB Query / Merge / Update) so the heavy work runs in Snowflake/BigQuery/Redshift/Synapse.

Below are concise, production-ready patterns, Matillion components to use, and platform-specific notes.

1) Common pre-work (applies to Type 1 and Type 2)
- Stage source delta into a staging table (fast bulk load / Table Output / Bulk Load components). Use micro-batch or full-batch depending on volume.
- Deduplicate staging by business key (keep last per source timestamp).
- Compute a checksum/hash of the business attributes used to detect change (MD5/sha256 of concatenated attribute values). This reduces column comparisons and minimizes data movement.
- Ensure a surrogate key strategy for Type 2 (DB sequence / identity / Matillion component that generates keys). Prefer DB-generated keys for concurrency.

Matillion components: Orchestration job to land data → Transformation job to dedupe/compute hash → push staging to target with Table Output or Bulk Load.

2) SCD Type 1 (overwrite attributes, no history)
Pattern: For each business key, update attributes to current values; insert new business keys.

Recommended steps (set-based):
- Use MERGE INTO target USING staging ON business_key
  - WHEN MATCHED AND target.hash <> staging.hash THEN UPDATE SET <attr columns>, hash=staging.hash, last_updated = current_timestamp
  - WHEN NOT MATCHED THEN INSERT (...)

If MERGE not available/desired:
- UPDATE target t SET ... FROM staging s WHERE t.business_key = s.business_key AND t.hash <> s.hash
- INSERT INTO target SELECT s.* FROM staging s LEFT JOIN target t ON s.business_key = t.business_key WHERE t.business_key IS NULL

Matillion components: Use the DB-native Merge component or DB Query for custom MERGE. For update/insert split, use Table Input to select changed rows and Table Update / Table Output.

Platform notes:
- Snowflake: Use MERGE. Use transient staging tables. Push hash calculation down to Snowflake for best performance.
- BigQuery: MERGE is supported; prefer partitioned+clustered tables. For very high-volume updates, consider CTAS (create new partition/table then swap).
- Redshift: If MERGE supported in your cluster version, use it. Otherwise prefer CTAS pattern (build new table from existing + staging, then swap) to avoid large row-by-row updates. Remember VACUUM/ANALYZE after major changes.
- Synapse (Dedicated SQL pool): MERGE supported. For large workloads, use CTAS + swap for partition-level replacements and use PolyBase for bulk ingestion.

3) SCD Type 2 (keep history, active flag, start/end dates)
Goal: preserve history; new versions inserted, previous active version expired.

Portable, efficient two-step pattern (works on all targets):
Step A — expire existing active records that changed:
  UPDATE target t
  SET active_flag = 0, end_date = current_timestamp
  FROM staging s
  WHERE t.business_key = s.business_key
    AND t.active_flag = 1
    AND t.hash <> s.hash;

Step B — insert new rows for changed and new keys:
  INSERT INTO target (surrogate_key, business_key, <attrs>, hash, start_date, end_date, active_flag)
  SELECT nextval(...)/GENERATE_ID(), s.business_key, s.<attrs>, s.hash, current_timestamp, NULL, 1
  FROM staging s
  LEFT JOIN target t ON t.business_key = s.business_key AND t.active_flag = 1
  WHERE t.business_key IS NULL -- new keys
     OR t.hash <> s.hash     -- changed keys

Notes:
- Do Step A and Step B in a transaction where supported to ensure consistency.
- You can sometimes collapse into MERGE in DBs that have flexible MERGE semantics, but portability and clarity often favor the two-step approach.
- Maintain start_date, end_date, active_flag, and the surrogate key.

Matillion components: Use DB Query or Merge if your DB supports multi-action MERGE and you want the simplest flow. Otherwise use a Transformation job that executes Update (DB Query), then Insert (Table Output). Use an Orchestration job for sequencing and transaction control.

Platform-specific optimizations
- Snowflake
  - Best: Snowflake Streams + Tasks + MERGE. Create a Stream on staging or source table to produce change rows; run a Task that MERGEs those changes into the SCD dimension. Streams reduce need for your own hashing/diff logic.
  - Use transient tables and clustering keys on business_key for large dimensions.
  - Use zero-copy clones for development/testing.
- BigQuery
  - Use MERGE for incremental SCD. Use partitioning (date-based) and clustering (business_key, hash) to speed up scans.
  - For very large dims, prefer CTAS (write a new partition or table using SELECT that merges staging & current) and swap table names to avoid expensive DML.
- Redshift
  - If MERGE is available, use MERGE. For older clusters or large updates, use CTAS to rebuild the affected slices and swap tables. Carefully design distkey/sortkey on business_key to minimize data movement.
  - Run ANALYZE and VACUUM after large inserts/updates.
- Synapse (Dedicated SQL pool)
  - Use MERGE or CTAS + swap. Use distribution column that aligns with business_key and use partitioning where helpful. Use PolyBase for bulk loads into staging.

Performance and reliability best practices
- Push comparisons into the DB (ELT). Avoid row-by-row transformations in Matillion.
- Use checksums/hashes to reduce column comparisons and eliminate unnecessary updates.
- Load staging in micro-batches sized to avoid long lock contention; tune batch size per platform.
- Use DB sequences/IDENTITY for surrogate keys; avoid Matillion-side key generation for concurrency.
- Use indexes/clustering/distribution tuned on business_key and active_flag.
- Wrap update + insert in a transaction on DBs that support it; for systems where DDL swap is cheaper, build new table and atomically swap.
- Monitor vacuum/analyze and table bloat (Redshift); reclaim / reorganize as needed.
- Test and validate with zero-downtime deploy: use clones or staging schemas, validate row counts and checksum differences before production swap.
- For near real-time CDC, prefer vendor-specific streaming primitives where available (Snowflake Streams, Debezium into BigQuery/Streaming + MERGE, etc.)

Matillion-specific component guidance
- Use Orchestration jobs to control ingestion, staging table creation, and sequencing.
- Use Transformation jobs to run pushdown SQL; most heavy logic should be in Table Input/DB Query or the Merge component that generates native SQL.
- Use the Table Merge component when supported; otherwise use DB Query for custom SQL.
- Keep SQL templates in variables or reusable snippets in shared jobs; use environment variables for schema/table names.
- Use Matillion's "Wait For" and "Run Orchestration Job" components to coordinate multi-step SCD flows (expire → insert → post-processing).

Example pseudo-SQL templates

Type 1 MERGE (generic)
MERGE INTO target t
USING staging s
  ON t.business_key = s.business_key
WHEN MATCHED AND t.hash <> s.hash
  THEN UPDATE SET t.attr1 = s.attr1, t.attr2 = s.attr2, t.hash = s.hash, t.last_updated = CURRENT_TIMESTAMP
WHEN NOT MATCHED
  THEN INSERT (business_key, attr1, attr2, hash, created_at) VALUES (s.business_key, s.attr1, s.attr2, s.hash, CURRENT_TIMESTAMP);

Type 2 two-step (portable)
-- expire
UPDATE target t
SET active_flag = 0, end_date = CURRENT_TIMESTAMP
FROM staging s
WHERE t.business_key = s.business_key
  AND t.active_flag = 1
  AND t.hash <> s.hash;

-- insert new versions (new or changed)
INSERT INTO target (surrogate_key, business_key, attr1, attr2, hash, start_date, end_date, active_flag)
SELECT NEXTVAL('seq_dim'), s.business_key, s.attr1, s.attr2, s.hash, CURRENT_TIMESTAMP, NULL, 1
FROM staging s
LEFT JOIN target t ON t.business_key = s.business_key AND t.active_flag = 1
WHERE t.business_key IS NULL OR t.hash <> s.hash;

Keep the logic set-based, stage aggressively, compute hashes in the DB, and prefer native MERGE/streaming features per platform for best throughput and simplicity.

[Top](#top)

## How do you implement deduplication and late-arriving data handling without double counting?
Short answer: use idempotent, set-based upserts from a staging area with deterministic dedupe logic (business/event keys + event_time + checksums), maintain processed-event state or use merge semantics in the warehouse, and run a bounded reconciliation window for late arrivals so corrections update previous rows rather than inserting new ones.

Concrete patterns and how you implement them in Matillion

1) Landing → Staging with batch metadata
- Always land raw payloads to a staging table (raw_records) with ingestion metadata: batch_id, ingestion_ts, source_file, and raw payload.
- Use Matillion Orchestration job(s) to move files into raw staging (S3/GCS → stage table) and capture batch_id per run.

2) Detect duplicates and compute deterministic keys/checksums
- In a transformation component (SQL/script), compute:
  - business_key or event_id (the natural unique key)
  - event_ts (source event time)
  - payload_hash = md5(concat(col1, col2, ...))
- This makes dedup decisions deterministic across retries and late arrivals.

3) Use a staging-dedup step (row_number over partition)
- Select latest record per business_key using SQL windowing:
  SELECT * FROM (
    SELECT *, ROW_NUMBER() OVER (PARTITION BY business_key ORDER BY event_ts DESC, batch_id DESC) rn
    FROM staging
  ) WHERE rn = 1
- This returns the canonical record per key for that load window.

4) Idempotent writes to target using MERGE/UPSERT
- Always write to target using MERGE (or ON CONFLICT/UPSERT) keyed on business_key/event_id.
- Compare payload_hash and/or event_ts to decide INSERT / UPDATE / NO-OP.
- Example (Snowflake-style):
  MERGE INTO target t
  USING (SELECT business_key, payload_hash, event_ts, ... FROM deduped_staging) s
    ON t.business_key = s.business_key
  WHEN MATCHED AND t.payload_hash <> s.payload_hash
    THEN UPDATE SET t.col1 = s.col1, t.payload_hash = s.payload_hash, t.event_ts = s.event_ts
  WHEN NOT MATCHED THEN
    INSERT (...);

- In Matillion use the DB-specific "Merge" or "SQL Script" components to run that statement.

5) Facts / event dedupe and avoiding double count
- Treat events as immutable if possible: use event_id as primary key and MERGE on event_id; insert only when not exists.
- If events can be corrected/duplicated, store a processed_events table with event_id, payload_hash, ingestion_ts and use MERGE/UPDATE when payload_hash changes. Aggregations are computed from this deduped events table.
- For aggregate tables, never incrementally ADD without knowing the delta. Either:
  - Recompute aggregates from deduped base for the affected period (correct but heavier), or
  - Maintain current aggregate and apply delta = new_value - old_value (requires reading prior row for each event_id). Use MERGE to apply the delta so late-arriving change updates aggregate only by the difference.

6) Late-arriving data handling
- Watermark + reconciliation window:
  - Maintain a processed watermark (max event_ts processed).
  - For each regular load handle events > watermark.
  - Periodically reprocess a reconciliation window (e.g., last 7 days) to catch late arrivals and corrections. Use the MERGE approach so updates replace prior rows rather than creating duplicates.
- TTL for reconciliation: choose window size based on SLA and source behavior.
- If real-time accuracy is required, use source CDC (or transaction id) and apply changes continuously via the same MERGE/upsert logic.

7) SCD for Dimensions
- Implement SCD2 for slowly changing dims so late-arriving corrections create new version rows with effective_from/effective_to and current_flag.
- Matillion has built-in SCD components or you can implement via MERGE + timestamps.

8) Checksums and idempotency for retries
- Store payload_hash and last_ingested_batch_id in target rows.
- On re-run of a batch, compare batch_id/payload_hash to detect already-applied rows and skip updates.
- Use unique constraints on business_key/event_id in the warehouse to protect against duplicate inserts; handle conflicts via MERGE/ON CONFLICT.

9) Matillion-specific implementation notes
- Use Orchestration jobs for file ingestion, watermark management, and scheduling reconciliation runs.
- Use Transformation jobs for dedup logic (SQL components or Table Input → Transformations → Table Output).
- Use the warehouse-specific Merge/Upsert components or run a SQL Script component for complex MERGE logic (Snowflake/BigQuery/Redshift).
- Use Environment variables for watermark, reconciliation window, and batch_id so jobs remain parameterized and idempotent.

10) Example flow (summary)
- Orchestration: increment batch_id → load raw files to staging.
- Transformation: compute event_id, event_ts, payload_hash; dedupe with ROW_NUMBER → produce deduped_batch.
- Transformation: MERGE deduped_batch into target_events using event_id and payload_hash.
- Aggregation: recompute/adjust aggregates from target_events for affected partitions/dates.
- Reconciliation: scheduled job that reprocesses last N days using same path and MERGE logic.

Short checklist to avoid double counting
- Use a unique natural/event key for deduping.
- Compute and store payload hash to detect true changes.
- Use MERGE/upsert semantics (idempotent writes).
- Keep raw data and ingestion metadata for reprocessing/audit.
- Reconcile a bounded window for late-arriving changes rather than naive append-only aggregation.
- Enforce unique constraints and use merge conflict handling in the warehouse.

Code snippet (generic Snowflake-style dedupe + merge)
WITH staged AS (
  SELECT business_key, event_ts, payload_hash, col1, col2, batch_id,
         ROW_NUMBER() OVER (PARTITION BY business_key ORDER BY event_ts DESC, batch_id DESC) rn
  FROM raw_staging
)
, deduped AS (
  SELECT * FROM staged WHERE rn = 1
)
MERGE INTO target t
USING deduped s
  ON t.business_key = s.business_key
WHEN MATCHED AND t.payload_hash <> s.payload_hash
  THEN UPDATE SET col1 = s.col1, col2 = s.col2, payload_hash = s.payload_hash, event_ts = s.event_ts
WHEN NOT MATCHED THEN
  INSERT (business_key, col1, col2, payload_hash, event_ts) VALUES (s.business_key, s.col1, s.col2, s.payload_hash, s.event_ts);

This enforces deterministic dedup and ensures late/corrected records update existing rows instead of creating duplicates.

[Top](#top)

## How do you choose between append, merge/upsert, and full refresh patterns per table and workload?
Short answer
- Append when rows are purely new (append-only facts), when you can partition by ingestion/window and when updates/deletes are rare or handled separately.
- Merge/upsert when rows can be updated or deleted and you have a reliable business/primary key (or CDC) so changes can be applied idempotently.
- Full refresh when the table is small, the change ratio is high (replacing is cheaper than diffs), there’s no reliable key, or when you need a guaranteed consistent rebuild.

Decision checklist (apply per table/workload)
1. Does the source produce updates/deletes?
   - No → consider append.
   - Yes → need merge/upsert or full refresh.
2. Is there a stable unique key or CDC stream?
   - Yes → merge/upsert (best for incremental diffing).
   - No → full refresh (or build surrogate keys and stage carefully).
3. How big is the data and how many rows change?
   - Small (fits cheaply in warehouse) or high-change% → full refresh.
   - Large and low-change% → merge/upsert or partitioned append + targeted reprocess.
4. SLA/latency and cost constraints:
   - Low latency, high volume → append with partitioning and later reprocessing for late-arriving records.
   - Cost-sensitive on warehouses with expensive DML (BigQuery/Redshift) → favor bulk loads and CTAS/partition swaps over row-by-row merge.
5. Need for history (SCD):
   - SCD Type 1 → merge/upsert.
   - SCD Type 2 → insert new rows + update flags/close old rows (usually done via merge/upsert against current keys or using staging + set-based SQL).
6. Operational safety:
   - If truncation would cause outages, use transactional swap (load new table and rename) or use merge/upsert.

Heuristics / rules of thumb
- If <~100k rows or dataset size is tiny and update rate is high → full refresh nightly.
- If >GBs and only a small % change → merge/upsert or incremental partition loads.
- If the table is a fact that is append-only by design → append (COPY/BULK load) and keep dedupe logic for late-arriving rows by reprocessing affected partitions only.
- If deletes occur frequently → merge/upsert or partition-based deletes (avoid unbounded append-only).

Implementation patterns in Matillion (practical)
- Append pattern:
  - Use a bulk load component (COPY/Load) or Table Output to insert new rows into the partition for the day/hour.
  - Use partitioning/clustering on the warehouse to limit future reprocessing.
  - For late-arriving updates, run targeted reprocess jobs on affected partitions or run a dedupe job (staging → deduped into target).
- Merge/upsert pattern:
  - Load change set into a staging table (fast bulk load).
  - Use a single MERGE SQL statement (execute via Matillion SQL/Script component) to match on key(s) and insert/update/delete as needed. This is idempotent and handles updates/deletes cleanly.
  - If warehouse DML is expensive, consider CTAS: create new versioned table by joining target & staging, then swap tables (rename) in an orchestration for atomic replace.
- Full refresh pattern:
  - Truncate or create a new table via CTAS, bulk load the complete dataset, then swap/rename to replace production table. Use orchestration to ensure atomic swap (avoid in-place truncate on critical tables).
  - Best for small reference/lookup tables or when build is cheap compared to maintaining complex diffs.

Warehouse-specific considerations
- Snowflake: MERGE is efficient for moderate merges; COPY + CTAS + atomic swap is good for very large churn. Micro-partitioning reduces the cost of selective operations.
- Redshift: DML can be expensive and fragmentation occurs; prefer staging + CTAS + swap + VACUUM/ANALYZE workflows.
- BigQuery: DML is metered and can be costly; prefer write-to-new-table + atomic table replace (or partition-level rewrite) over massive MERGE operations.

Operational patterns
- Staging-first: always land incoming data into a staging table; use set-based SQL to reconcile into production (applies to all patterns).
- Versioned/atomic swaps: for full refresh or large updates, build new table and swap names to avoid downtime or partial states.
- Idempotency: ensure every job is idempotent — include watermarks, hashes, or versioning so reruns don’t double-count.
- Monitoring and cost control: track row counts, change ratios, and query/DML cost to re-evaluate pattern choice regularly.

Examples
- High-volume web events (append-only): Append daily partitioned loads. Reprocess partitions where late events arrive.
- Customer dimension with frequent attribute changes and a primary key: Use merge/upsert from staging to apply updates and upserts.
- Small country/currency lookup updated nightly: Full refresh (truncate/load or swap).
- Large table where 50%+ rows change every load: Full refresh or CTAS/replace is preferable to repeated MERGE.

Concise decision flow
1. Append-only? → Append.
2. Updates/deletes + stable key/CDC? → Merge/upsert via staging + MERGE.
3. No key or high churn/small table? → Full refresh (build & swap).

Summary
Choose append when data is truly additive and partitionable; choose merge/upsert when you must apply updates/deletes reliably and have keys/CDC; choose full refresh when datasets are small, change heavily, or when rebuilding is cheaper and operationally simpler. In Matillion implement via staging + bulk load + set-based SQL (MERGE or CTAS + swap) and pick the physical strategy that balances performance, cost, and operational safety for your warehouse.

[Top](#top)

## How do you maintain surrogate keys, natural keys, and referential integrity in an ELT approach?
Short answer: In ELT (and with Matillion specifically) you keep natural keys as the business identifier in staging, generate and persist surrogate keys in the target dimension (using the database or a mapping table), and enforce referential integrity by resolving lookups (or inserting “unknown” rows) before loading facts. Push the heavy work down to the warehouse (MERGE/UPSERT/SEQUENCE) and use Matillion lookups and merge/upsert components to perform idempotent, set-based operations.

Detailed approach and practical patterns

1) Staging and preserve natural keys
- Bring raw source rows into a staging schema/table unchanged, including the natural/business keys (single or composite).
- Keep a deterministic composite key representation (concatenate + delimiter or hash) if you need a single lookup key.

2) Surrogate key generation strategies
- Use the warehouse’s native mechanism when possible:
  - Snowflake: CREATE SEQUENCE and sequence_name.nextval or IDENTITY column; use MERGE to assign nextval on inserts.
  - Redshift: IDENTITY or CREATE SEQUENCE + nextval('seq').
  - BigQuery: GENERATE_UUID() for string PKs, or FARM_FINGERPRINT(natural_key) for deterministic 64-bit int if acceptable.
- Or maintain an explicit mapping table (dim_key_map) with (natural_key, surrogate_key, hash, last_seen). Upsert into that table to generate new surrogates (using sequence/ROW_NUMBER) and then use it to map facts.
- Avoid generating surrogate keys in the orchestration layer; prefer set-based SQL generation in the warehouse for performance and concurrency.

Example (Snowflake MERGE pattern)
- Upsert dimension:
  MERGE INTO dim d
  USING (SELECT :nat_key AS nat_key, :attr1 AS a1, :attr2 AS a2 FROM src) s
  ON d.nat_key = s.nat_key
  WHEN MATCHED THEN UPDATE SET a1 = s.a1, a2 = s.a2
  WHEN NOT MATCHED THEN INSERT (surrogate_id, nat_key, a1, a2)
    VALUES (my_seq.nextval, s.nat_key, s.a1, s.a2);

3) Handling slowly changing dimensions (SCD)
- SCD Type 1: simple MERGE/UPSERT to keep latest attributes.
- SCD Type 2: on change, close current row (effective_to, is_current=0), insert new row with new surrogate key, effective_from. Use MERGE pattern that compares hashes of changing attributes to detect changes.
- Maintain columns: surrogate_key, natural_key, effective_from, effective_to (or current_flag), version. The surrogate key is immutable once issued.

4) Lookups from facts to dimension surrogate keys
- In Matillion use a Lookup component or a pushdown SQL join to map natural keys in facts to surrogate keys in dimension tables before inserting facts.
- Perform the lookup in the warehouse (SQL pushdown) for performance: join staging_facts to dim (on natural_key OR on business date range for SCD2) to produce fact rows with dim_surrogate_id.
- For SCD2: join on natural_key and the fact date between effective_from and effective_to (or use current_flag for current snapshot).

5) Early-arriving facts (late dimensions)
Options:
- Insert facts with a special surrogate_id for “UNKNOWN” dimension row (create a dummy dim row with surrogate_id = 0 or -1). Backfill later and reconcile.
- Hold/queue those facts in a staging table and replay after the dimension load.
- Auto-insert a minimal dimension row during fact load (insert into dim with surrogate from sequence and minimal attributes), then update later with full attributes.

6) Referential integrity enforcement
- Many cloud warehouses do not enforce FKs (Snowflake doesn’t enforce, Redshift can but often not enforced, BigQuery lacks FKs). Therefore enforce RI in ELT:
  - Resolve all dimension lookups prior to fact load. If lookup fails, handle according to policy (reject, route to error table, create unknown/placeholder).
  - Use MERGE/UPSERTs atomically where supported so dim upserts and mapping are consistent.
  - Use unique constraints or unique indexes on natural_key (or materialized unique mapping) if the warehouse supports enforcement to prevent duplicates at the source of truth.
- Implement validation jobs that check for orphaned facts and report/fix.

7) Idempotency, concurrency and performance
- Use set-based MERGE/INSERT ... ON CONFLICT/UPDATE patterns to make jobs idempotent.
- Use sequences or atomic database functions to avoid race conditions when generating surrogates.
- For high-volume loads, do dimension upserts first in bulk, then join to map surrogate keys for bulk fact insert.
- Maintain a mapping table or caching layer if you must do many single-row lookups to avoid repeated small queries.

8) Matillion-specific implementation notes
- Use Table Input, Transform components (Filter/Join/Calculator) to shape staging data before pushing SQL.
- Use the Merge or Insert/Update components to perform upserts on dimension tables — Matillion will push that SQL to the target DB.
- Use the Lookup component to enrich fact staging with the surrogate key; configure fallback behavior to catch misses.
- Use variables and orchestration orchestration jobs to sequence dimension upserts before fact loads; use dependencies to ensure ordering.
- For change-detection, compute attribute hashes (MD5/SHA) in SQL via Matillion and compare to dim hash to detect SCD2 changes.

9) Monitoring and reconciliation
- Maintain row counts and key-change metrics per job.
- Keep audit columns (loaded_by_job, loaded_at, src_batch_id) and a change log for dim inserts/updates so you can trace surrogate assignments.
- Reconciliation queries to find orphaned facts, duplicate natural keys, or missing mappings.

Summary checklist
- Keep natural keys in staging and persist them in the dim for traceability.
- Generate surrogate keys in the warehouse (sequences, identity, UUID) or via a mapping table; use set-based MERGE/upsert.
- Resolve lookups before loading facts; handle early-arriving facts via unknown rows or holding logic.
- Implement SCD patterns (Type1/Type2) as required; use effective dates/flags for SCD2.
- Enforce referential integrity at ELT layer (pre-join, validations), because many cloud warehouses won’t enforce FKs.
- Use Matillion components to orchestrate these steps while relying on pushdown SQL for performance and concurrency control.

[Top](#top)

## How do you reconcile source-to-target row counts and checksums and generate exception reports?
Goal: produce deterministic row-count and data checksums for source and target, compare them, and generate exception reports listing missing, extra and changed rows — implemented with Matillion orchestration + transformation jobs and pushdown SQL.

High-level approach
- Compute a row-level hash on source and target (deterministic, normalized).
- Compute lightweight aggregates (row count, aggregate checksum) from those row-hashes.
- Compare aggregates; if they differ, do a PK-level join to produce exception sets: inserts (source-only), deletes (target-only), changed rows (PK match but different hash).
- Persist/write exception reports (tables or files) and optionally raise alerts.

Detailed steps (Matillion pattern)

1) Normalize and compute row-level hash (push down to DB)
- Use a Transformation job that runs SQL in-database (via Table Input / SQL Query components) to produce a small table/view with: PK columns, row_hash.
- row_hash = md5(concat_ws('|', normalized_col1, normalized_col2, ...))
  - Normalize: COALESCE(...,''), TRIM, consistent case, round floats, convert timestamps to a canonical string.
  - Use concat_ws or equivalent to avoid NULL concatenation problems.
- Create two hashed datasets: source_hashes and target_hashes (either ephemeral CTEs or persisted staging tables).

Example (generic SQL):
  SELECT
    pk,
    md5(concat_ws('|',
         coalesce(trim(col1), ''),
         coalesce(trim(col2), ''),
         to_char(col3, 'YYYY-MM-DD HH24:MI:SS')
    )) AS row_hash
  FROM source_table
  WHERE partition_key = :load_date;

Run equivalent for target_table.

Note: push the hashing into the source/target databases to avoid moving full row data into Matillion.

2) Compute aggregates (count + aggregate checksum)
- For each side compute:
  - row_count: COUNT(*)
  - checksum: a deterministic aggregate of row_hash values. Options:
    - SUM of a numeric conversion of a portion of the hash (CRC32(row_hash) SUM) — order independent and efficient.
    - MD5 of LISTAGG(row_hash ORDER BY pk) — deterministic but potentially heavy for large datasets.
- Implement the chosen aggregate in SQL and capture results into Matillion variables or small result tables.

Example (CRC32 approach shown generically):
  SELECT COUNT(*) AS cnt, SUM(cast(crc32(row_hash) AS bigint)) AS checksum FROM source_hashes;

3) Compare counts & checksums in Matillion (Orchestration or Transformation)
- Use a single SQL join between the two aggregate results to detect mismatch.
- In an Orchestration job, use the DB Query component to run comparison SQL and set Matillion variables (or use the "If Condition" component to branch).
- If counts + checksums match, job can mark success. If not, proceed to detailed reconciliation.

4) Generate exception reports (PK-level comparison)
- In a Transformation job, join source_hashes and target_hashes on PK (full outer join or three anti-joins) and produce:
  - Inserts: rows present in source_hashes and missing in target_hashes (target pk IS NULL).
  - Deletes: rows present in target_hashes and missing in source_hashes (source pk IS NULL).
  - Changed rows: rows where both exist but row_hash_source <> row_hash_target.
- Include in the exception output: PK, source_values (or source row_hash), target_values (or row_hash), status flag, and any changed column diffs if needed.

Matillion component mapping:
- Orchestration job:
  - Run the load job (if applicable).
  - DB Query / Run SQL to create or refresh hashed staging tables.
  - Run a Transformation job for aggregation and comparison.
  - Use "If Condition" or variable checks to branch to exception-generation Transformation job.
  - Use "Send Email" or "Create Ticket" components for alerts (optional).
- Transformation job:
  - Table Input components to read source_hashes and target_hashes (or DB Query).
  - Join component (Full Outer Join) on PK to classify rows.
  - Calculator components to compute status column (INSERT/DELETE/CHANGE/OK).
  - Filter components to split exception sets into separate streams (inserts, deletes, changes).
  - Table Output or Write File / S3 Put components to persist exception reports (as tables or CSV/Parquet to S3/GCS/Blob).
  - Optionally use "Create/Drop Table" DB Query components to maintain audit tables storing counts and checksums.

Exception report contents
- Minimal: load_date, pk, status (INSERT/DELETE/CHANGE), row_hash_source, row_hash_target.
- Recommended: include source & target column snapshots for changed rows (or include a link to source/target staging) and a reason field if you compute column-level differences.
- Include metadata: reconciliation run timestamp, expected vs actual counts/checksums.

Performance and reliability considerations
- Always compute hashes in the source/target database (pushdown) to avoid network cost.
- Hash only the columns you care about; exclude volatile metadata columns.
- For very large tables, do reconciliation incrementally by partition (date, batch id) rather than full table.
- Use CRC32 or integer-based aggregations where possible for order independence and lower memory; LISTAGG+MD5 is deterministic but can be memory intensive.
- Handle floating precision, timezones, and NULLs explicitly in normalization logic.
- Store historical hashes in an audit table so you can do delta-based reconciliation (compare current hashes to previous run) rather than full-row compares every time.

Simple SQL flow example (conceptual)
1) source_hashes as (SELECT pk, md5(...) row_hash FROM source WHERE partition = X)
2) target_hashes as (SELECT pk, md5(...) row_hash FROM target WHERE partition = X)
3) aggregates:
   SELECT 'source' side, COUNT(*) cnt, SUM(crc32(row_hash)) chk FROM source_hashes
   UNION ALL
   SELECT 'target' side, COUNT(*) cnt, SUM(crc32(row_hash)) chk FROM target_hashes;
4) if mismatch then:
   SELECT coalesce(s.pk,t.pk) pk, s.row_hash row_hash_src, t.row_hash row_hash_tgt,
     CASE WHEN s.pk IS NULL THEN 'DELETE'
          WHEN t.pk IS NULL THEN 'INSERT'
          WHEN s.row_hash<>t.row_hash THEN 'CHANGE' END AS status
   FROM source_hashes s FULL OUTER JOIN target_hashes t USING (pk)
   WHERE s.pk IS NULL OR t.pk IS NULL OR s.row_hash<>t.row_hash;

Audit & notification
- Persist aggregate results and reconciliation status into a reconciliation_audit table for historical tracking.
- Use Matillion Orchestration to send an alert (email or webhook) on failure and attach or link the exception report.

Wrap-up
- Key points: deterministic normalization, compute row-level hashes in-database, compute order-independent aggregate checksums, compare aggregates then escalate to PK-level joins to produce exception reports, and write reports to tables/files. Use Matillion components for orchestration, pushdown SQL, joins/filters and output to storage/DB for reporting and alerting.

[Top](#top)

## How do you manage time zones, daylight savings, and timestamp normalization across sources and warehouses?
High-level principle: normalize to a single canonical timeline (usually UTC) as early as possible in the pipeline, keep original values and metadata for audit/reporting, and use timezone databases (IANA tz names) so DST and historical offset rules are applied correctly.

Typical pattern (applies to Matillion pipelines):
1. Ingest raw timestamp(s) as-is into a staging table/stream, including:
   - original timestamp string
   - any timezone/offset field provided by source (e.g., "America/New_York" or "+02:00")
   - source system id / event metadata
2. Parse to a timezone-aware timestamp (using source offset or tz name). If source provides only a naive timestamp, use source-level metadata or a mapping table to assign a timezone; if unknown, mark as unknown and treat as UTC only after business decision.
3. Convert the timezone-aware timestamp to canonical timezone (UTC) and store a canonical column (ts_utc).
4. Persist helpful derived columns (local_date, local_hour, business_date in a business tz) computed using the appropriate tz name.
5. Keep original inputs and mapping metadata for auditability and reprocessing.
6. Use database-native/time-zone-aware functions where practical for scale; otherwise use Matillion Python components for complex parsing.

Matillion-specific ways to implement this
- Pushdown to database (preferred when processing large volumes):
  - Snowflake: use CONVERT_TIMEZONE or TO_TIMESTAMP_TZ. Example:
    SELECT CONVERT_TIMEZONE('America/Los_Angeles','UTC', TO_TIMESTAMP_TZ(source_ts_str)) AS ts_utc
  - BigQuery: use TIMESTAMP(datetime_string, "America/Los_Angeles") or PARSE_TIMESTAMP with a timezone argument:
    SELECT TIMESTAMP(source_datetime_string, "America/Los_Angeles") AS ts_utc
  - Redshift/Postgres: use AT TIME ZONE where supported:
    SELECT (source_ts AT TIME ZONE 'America/Los_Angeles') AT TIME ZONE 'UTC' AS ts_utc
  Implement these SQLs in Matillion Transformation jobs (Table Input/DBQuery, Filter, Calculator pushdown) so the heavy lifting runs in the warehouse.

- Use Matillion transformation components for row-level or custom parsing:
  - Python Script component (or Orchestration > Run Python) for complex parsing and DST-aware logic. Example Python pattern:
    from dateutil import parser, tz
    dt = parser.isoparse(source_ts_str)         # handles ISO8601 offsets
    if dt.tzinfo is None:
        tzinfo = tz.gettz(source_tz_name)      # use IANA tz name mapping
        dt = dt.replace(tzinfo=tzinfo)
    dt_utc = dt.astimezone(tz.UTC)
    out_ts_utc = dt_utc.isoformat()
  - Use pytz or zoneinfo (Python 3.9+) so DST and historical rules are respected.
  - Matillion Calculator component for simple derived columns once you have canonical timestamps.

- Use Matillion job variables / environment variables:
  - Store default source timezone mappings, target canonical tz (usually UTC), and business time zones as variables so jobs are configurable per environment and source.
  - Create reusable transformation jobs that take source_tz and target_tz as inputs.

DST, historical offsets, and ambiguous times
- Always use IANA tz names (e.g., America/New_York) instead of fixed offsets. That lets libraries/databases apply DST and historical offset changes correctly.
- If source provides only an offset (e.g., +01:00) you can parse it correctly for that specific timestamp, but you lose DST/historical semantics — prefer tz name when available.
- Handle ambiguous or nonexistent local times (DST backward/forward transitions) by:
  - Requiring source to provide offset or tz-aware string, or
  - Applying a deterministic rule (e.g., prefer the DST interpretation or choose earlier/later), and log/flag ambiguous rows for review.
- For historical data, use tz-aware conversions (pytz/zoneinfo or DB functions) — they know past offset changes.

Edge cases & handling unknowns
- If timezone is missing/unknown: store the original, tag row as unknown_tz, and treat as UTC only after an explicit business decision.
- For inconsistent sources (some send offsets, some tz names) keep both fields and use precedence logic: explicit offset in string → use that; else tz name field → use that; else mapping table → use mapped zone; else mark unknown.
- Persist original raw value for replayability.

Performance & scale
- Prefer pushdown (native SQL) in Matillion for high-volume conversions — database engines optimize these conversions and avoid moving data out of the warehouse.
- Use Python only for complex parsing or when database lacks a needed function or tz database; run Python components on staged subsets or as batch jobs if volumes are very large.
- Cache timezone mapping tables and reuse transformation jobs to avoid duplicated logic.

Testing, validation & monitoring
- Create unit tests that exercise DST transitions (spring forward and fall back) and historical dates.
- Build validation checks in Matillion (e.g., compare parsed timestamp against regex/date parsing, count nulls/unknown_tz, check extreme timestamps) and surface metrics to monitoring.
- Keep audit columns (ingest_time, parsed_by_job, parse_status, original_string, original_tz) for debugging/reprocessing.

Implementation checklist for Matillion delivery
- Add staging columns for original timestamp and tz metadata.
- Implement parsing + convert-to-UTC step (SQL pushdown where possible).
- Persist canonical ts_utc and derived columns (local_date, business_date).
- Store original values and a tz-mapping table.
- Use job variables and shared reusable transformation jobs.
- Test with DST edge cases + historical dates and instrument parsing failures.

This ensures consistent canonical time representation, correct DST/historical handling via tz databases, and traceability back to source values while enabling efficient large-scale processing by pushing conversions into the warehouse.

[Top](#top)

## How do you handle large text/binary fields, encoding, and newline/quote handling in CSV/JSON loads?
Key principles
- Avoid pulling huge text/binary payloads through Matillion ETL nodes when possible — push files directly to the cloud storage -> warehouse native load (COPY/LOAD). Matillion should orchestrate the transfer and call the native loader rather than stream huge blobs through the job engine.
- Choose formats that naturally handle embedded newlines and binary: JSON (newline-delimited JSON for streaming), Parquet/Avro/ORC for binary-efficient storage, or base64-encoded payloads for arbitrary binary in text formats.
- Configure file-format/load options (encoding, quote, escape, allow-quoted-newlines) on the native load step in Matillion — these are the right place to control parsing behavior.

CSV handling (encoding, newline, quotes, large text)
- Encoding: set the file encoding explicitly on the load component (UTF-8 is preferred). Remove BOMs or use the loader option to handle BOM. If source uses legacy encodings, set that encoding in the load component or re-encode prior to load.
- Embedded newlines: require the field to be enclosed in quotes and the loader to allow quoted newlines (often called allow_quoted_newlines or similar). If the loader doesn’t support quoted newlines reliably, convert to JSON or use a different format.
- Quotes inside fields: choose the correct quote character and escape mechanism:
  - Doubling quotes ("" inside a quoted field) is common — set FIELD_OPTIONALLY_ENCLOSED_BY/QUOTE="\"" and ESCAPE handling according to target DB.
  - Backslash escaping requires ESCAPE='\\' or equivalent.
- Nulls and empty strings: configure NULL_IF, empty string handling and trimming as required.
- Large text columns: ensure target column is sized to hold content (VARCHAR(max), TEXT, CLOB). For very large values prefer storing in native binary/blob column or external storage, or load as VARIANT/JSONB if semi-structured.
- Practical Matillion pattern: upload CSV to S3/Azure/GCS, use the cloud-specific Load component (S3 Load / Azure Blob Load / GCS Load or the target-specific component) and set the file-format parameters (encoding, quote character, escape, skip header, allow quoted newlines) exposed in Matillion’s component GUI.

JSON handling
- Prefer newline-delimited JSON (NDJSON/JSONL) for streaming loads (one object per line). Many warehouses support this natively and it avoids ambiguity with embedded newlines.
- For nested JSON, load into a semi-structured column (VARIANT/JSONB) when supported (Snowflake VARIANT, BigQuery JSON, Redshift Spectrum with JSONPath or COPY with JSON).
- Use Matillion’s JSON-transform components (Convert JSON to Table / Flatten JSON or Extract JSON) to parse or flatten after load if you need tabular columns.
- If the JSON file is a single huge array, pre-process to NDJSON (one object per line) — Matillion can run a Python or Bash component to split arrays into lines before load.
- Encoding: set encoding to UTF-8; handle BOMs or non-UTF encodings by re-encoding before load.

Binary fields
- Do not put raw binary into CSV. Encode binary as Base64 (or hex) and store in a VARCHAR/BLOB column; decode in-database or in a downstream step if needed.
- Alternative: keep binary artifacts in object storage and store only references/paths in the table.
- Use compression (gzip) for large binary/text payloads. Native loaders support compressed files and process them server-side, avoiding Matillion memory pressure.

Matillion-specific techniques
- Use the cloud-storage -> target DB native load components (S3 Load / Put and then COPY, BigQuery Load component, Snowflake Load, Redshift Load). Configure advanced file-format parameters exposed in the component UI (encoding, quote char, escape char, allow quoted newlines, skip header, compression).
- Pre-process problematic files with Python Script / Bash Script components or the File Iterator: re-encode files, strip BOM, convert JSON array -> NDJSON, base64-encode binaries, or split huge files into chunks.
- For streaming/transform workloads where Matillion must touch the data, paginate or chunk files with File Iterator to keep memory usage manageable.
- Validate with small sample loads and set the target loader’s error-tolerance options (MAXERROR, ON_ERROR, etc.) for controlled testing.

Testing and validation
- Test with representative sample files that include embedded newlines, quotes, BOMs, non-UTF characters, and the largest expected payloads.
- Check target DB error tables/logs from COPY/LOAD to locate bad rows and adjust escape/quote/null handling.
- Monitor Matillion task memory/CPU when pre-processing; prefer server-side native loads for throughput and reliability.

Example common settings you’ll use in Matillion load components
- Encoding: UTF-8
- Quote character: "
- Escape: \ or doubled quote behavior depending on source
- Allow quoted newlines: true (or equivalent)
- Compression: gzip (if applicable)
- For JSON: use JSONL / TYPE=JSON / LOAD into VARIANT/JSONB when supported

Conclude actions
- Use native LOAD/COPY with correct file-format options for CSV and JSON.
- Prefer NDJSON for JSON, base64 or external storage for binary.
- Pre-process only when necessary using Matillion scripts and chunking to protect memory.

[Top](#top)

## How do you ingest from APIs using the API Query/REST connector and handle pagination, rate limits, and retries?
High-level approach
- Use the API Query / REST Query component to call the API, parse the JSON (or XML) payload into rows, and push into your target table or temporary stage.
- Handle pagination with the component’s built-in pagination modes when possible (page, offset, token/continuation, next‑URL). If the built-in modes don’t match the API, implement an orchestration loop to iterate using variables.
- Handle rate limits by either using the component’s request delay/retry settings or by implementing a controlled sleep/backoff in an orchestration loop based on response headers (X-RateLimit-*, Retry-After) or fixed throttling.
- Handle retries via the component’s retry settings where available, or with orchestration-level retry + exponential backoff logic.

Step-by-step configuration (typical)
1) Basic REST/API Query setup
- Endpoint URL, HTTP method (usually GET).
- Authentication: Basic, API key (header/query), OAuth2 if supported.
- Headers and query parameters: set static values or bind Matillion variables.
- Response path / JSONPath: point to the array/object containing items you want to convert to rows.

2) Pagination: pick the right mode
- Page-number pagination
  - Pagination type: Page Number
  - Configure page parameter name (e.g., page), start page and page size param if required (limit/size).
- Offset/limit pagination
  - Pagination type: Offset
  - Configure offset param (e.g., offset), limit param (e.g., limit) and starting offset (usually 0).
- Token/continuation pagination
  - Pagination type: Token or Continuation
  - Configure JSONPath where the API returns the next token (e.g., $.next_cursor) and the query param/header name to send on next call.
- Next-page URL
  - Pagination type: Next URL (or provide a JSONPath to the next link, e.g., $.links.next or $.next)
  - The component will call the returned URL directly for the next page.
- When built-in pagination is insufficient
  - Use an orchestration job: call API, parse and extract a next-token/next-URL into a variable, loop until empty, use Job Iteration/While/Loop components to control iteration.

3) Capturing and parsing results
- Set the results JSONPath to the array of items so Matillion maps fields.
- If you need raw responses for debugging, write response body to cloud stage (S3/Blob) or to a table column.

Handling rate limits
- Prefer to respect API headers: X-RateLimit-Remaining, X-RateLimit-Reset, Retry-After.
  - If the connector exposes response headers, read these and compute wait time: sleep = reset_timestamp - now + small buffer.
- Use static throttling when headers aren’t available:
  - Many connectors include a “Delay between requests” or a “Pause between pages” setting — use it to throttle requests to under the API limit.
  - Alternatively implement a sleep in an orchestration loop between calls (Sleep component).
- Conservative default: set a delay that keeps requests well within documented limits, then optimize once you know exact limits.

Retries and backoff
- Use the component’s built-in retry configuration if present (Retry count, Retry interval).
- For 429 or 5xx responses:
  - If API returns Retry-After, use its value for the delay before retrying.
  - Implement exponential backoff if built-in support is missing:
    - Orchestration pattern: try call → on failure increment attempt variable → Sleep for base_delay * 2^(attempt-1) → retry until max attempts.
- Recommended values: small number of retries (3–5), initial delay 1–5s, exponential backoff multiplier 2, but adjust per API SLA.

Error handling and logging
- Failures: surface non-retriable errors to stop the job; capture error payloads in a table/stage for diagnostics.
- For partial failures (some pages ok, later pages fail), design to be idempotent or resumable (store last successful offset/token).
- Log headers and status codes so you can detect rate-limit responses and tune throttling accordingly.

Practical examples
- Offset example:
  - Pagination type = Offset
  - Offset param = offset, Limit param = limit, Start offset = 0, Page size = 1000
  - Component auto-iterates until empty result.
- Next-link example:
  - Pagination type = Next URL
  - Next link JSONPath = $.links.next
  - Results JSONPath = $.data.items
- Token example:
  - Pagination type = Token
  - Token JSONPath = $.meta.next_token
  - Token param name = cursor

When built-in pagination or retry settings are insufficient
- Implement orchestration loop:
  - Use REST/API Query to call initial URL.
  - Use Calculate Variable / Get XML/JSON Property to extract next token/URL or headers.
  - Use a While or Loop component that repeats until next token/URL is empty or a max-iteration variable is reached.
  - Between iterations use Sleep to throttle and implement retry/backoff logic by checking status codes and Retry-After header.

Testing and operational tips
- Start with a low page size and a conservative delay to avoid hitting live limits.
- Capture raw responses and response headers during development for tuning.
- Make jobs idempotent: persist last offset/token so you can resume after failures.
- Monitor for 429s and 5xx errors and adjust delay or backoff accordingly.

Summary checklist
- Choose appropriate pagination mode (built-in where possible).
- Configure auth, headers, JSONPath for items.
- Use built-in retry/delay settings; otherwise implement orchestration-level backoff and retries.
- Respect rate-limit headers where available; otherwise apply conservative throttling.
- Log responses and make ingestion resumable.

[Top](#top)

## How do you design incremental API extraction with bookmarks/watermarks and recover from failures idempotently?
High-level design pattern (Matillion-oriented)
- Maintain a persistent control table in the target warehouse (not Matillion variables) that records per-source bookmarks/cursors and run state. Variables are runtime-only; use them only to pass values inside a run.
- Extract pages/changes from the API into a staging area (S3/GCS/warehouse staging table) and commit staging results atomically into the target using MERGE/upsert.
- Never advance the persistent bookmark until the staging -> target merge completes successfully.
- Make every load idempotent: use deterministic upsert/merge or dedupe logic keyed by a source unique key (or source_id + last_modified).
- For long paginated extractions, track both “last_committed_bookmark” and a transient “last_processed_page_token” so you can resume efficiently but still be safe.

Control-table schema (recommended)
- source_name (pk)
- last_committed_bookmark (timestamp or cursor)
- last_requested_bookmark (optional; for in-flight runs)
- last_committed_page_token (optional)
- in_progress (boolean) or run_id
- last_success_ts
- error_count/message

Matillion orchestration flow (step-by-step)
1) Read control row: Table Input reads last_committed_bookmark and in_progress.
2) Acquire lock: set in_progress = true AND run_id = UUID (update control table) or use advisory locking so concurrent runs don’t collide.
3) Compute extraction window: start_bookmark = last_committed_bookmark, end_bookmark = now() - safety_lag (safety_lag handles late-arriving updates).
4) Start page loop:
   - Use a While/Until loop (Orchestration job) controlled by a Matillion variable page_token or done_flag.
   - In each iteration call API Query (or Python component) with parameters (start_bookmark, end_bookmark, page_token).
   - Push API response to staging:
     - Option A: write raw JSON to S3 and use a Transformation job or JSON-to-table to load into a transient staging table.
     - Option B: parse JSON in Matillion and load rows directly into a staging table.
   - On successful page load, either update a checkpoint table/column with the page_token (optional), or just continue.
   - Follow API error handling (retry with exponential backoff; honor rate limits). If repeated failures: fail job without updating last_committed_bookmark.
5) After loop completes (all pages for the window loaded), run a Transformation job:
   - Load staging into target with an atomic MERGE/UPSERT statement (SQL Script component). Include dedupe logic if multiple pages could overlap.
6) On successful MERGE:
   - Update control table last_committed_bookmark = end_bookmark, clear in_progress, record last_success_ts and run_id.
7) On failure anywhere:
   - Do not advance last_committed_bookmark.
   - Optionally persist last_requested_bookmark/page_token so you can diagnose and resume manually.
   - Clear in_progress only if you implement safe checkpoint semantics; otherwise require manual intervention or automated recovery logic.

Idempotency strategies
- Use MERGE (preferred) or INSERT ... ON CONFLICT upsert keyed by source natural key or source_id:
  - Example (Snowflake-style):
    MERGE INTO target t
    USING staging s
      ON t.source_id = s.source_id
    WHEN MATCHED AND s.last_modified > t.last_modified THEN
      UPDATE SET ... 
    WHEN NOT MATCHED THEN
      INSERT (...);
- Keep a unique constraint/index on the natural key to prevent duplicates if MERGE isn’t used.
- Include a source_run_id or extract_window_id column in staging; use it for diagnostics and to ensure repeated page writes can be deduped.
- Prefer deterministic dedupe (row_number partition by source_id order by last_modified desc) and insert the top row per key.

Checkpointing / partial progress and safe resume
- Two safe approaches:
  1) Coarse-grained safe: only update last_committed_bookmark after the whole extraction window merged. On failure, re-run the whole window. Simpler, fully safe, less efficient for very large windows.
  2) Fine-grained checkpoint: after each page is loaded + merged into staging, persist last_committed_page_token (or set last_requested_bookmark). But treat page-token persistence carefully:
     - Keep both last_committed_bookmark and last_committed_page_token.
     - If a run stops after writing page_token but before merge, resume from last_committed_bookmark (not last_requested) to avoid partial-commit issues; reprocess some pages but MERGE ensures idempotency.
- Recommended compromise: process in reasonably small windows (hourly/daily) so reprocessing cost is acceptable, and rely on MERGE for idempotency.

Failure recovery patterns
- Never advance the bookmark before target merge completes.
- Use atomic MERGE so either the batch is fully reflected or not.
- To resume:
  - If last_committed_bookmark unchanged -> re-run from that bookmark.
  - If you have a page-level checkpoint scheme, check last_committed_page_token; if mismatch with last run, reprocess last page(s) (idempotently).
- For stuck in_progress rows, implement TTL: if in_progress and last_update older than threshold, allow another run to take over or fail the previous run by setting in_progress=false and recording an incident.

Rate limits and backoff
- Implement exponential backoff and retry in API Query component or Python component.
- Respect X-Rate-Limit headers; if API returns retry-after, sleep accordingly.
- Throttle concurrency: limit parallel API calls and use a token bucket if required.

Example control-table update order (safe)
1) Start run -> set in_progress=true, run_id=uuid
2) Do all pages -> push to staging
3) Run MERGE (atomic)
4) If MERGE success:
   - update control set last_committed_bookmark=end_bookmark, last_success_ts=now(), in_progress=false, run_id=null
5) If MERGE or load fails:
   - log error, leave last_committed_bookmark unchanged, clear in_progress only after safe failure handling or manual intervention

Example MERGE (Snowflake-like pseudo-SQL)
MERGE INTO target t
USING (
  SELECT * FROM staging WHERE extract_window_id = :run_id_or_window
) s
ON t.source_id = s.source_id
WHEN MATCHED AND s.last_modified > t.last_modified THEN
  UPDATE SET col1 = s.col1, last_modified = s.last_modified
WHEN NOT MATCHED THEN
  INSERT (source_id, col1, last_modified) VALUES (s.source_id, s.col1, s.last_modified);

Matillion components mapping
- Table Input: read control table
- Calculator / Create Variable: compute start/end/bookmark
- While: pagination loop
- API Query (or Python): call API and parse response
- S3 Put or S3/Cloud Storage components: stage raw JSON if desired
- Database Query / Table Output: load parsed rows into staging table
- Transformation Job: use Table Input and SQL Script to MERGE into target
- Table Update / SQL Script: update control table with new bookmark
- Failure handling: use Try/Catch (Job Failure strategy), send alerts, rollback if necessary

Edge cases and practical tips
- Use a safety_lag (e.g., 5–10 minutes or configurable) to avoid missing in-flight writes on source systems.
- For APIs that expose change streams or distinct “cursor” tokens, store raw cursor tokens in control table.
- For high-volume sources, break the time window into chunks and process sequentially to reduce memory and runtime.
- Add monitoring/alerting on long-running runs, repeated failures, or significant data drift.
- Keep raw API payloads for a retention period for debugging replay.

Summary (one-sentence)
Persist bookmarks in a warehouse control table, stream API pages into staging, MERGE idempotently into the target, and only update the bookmark after a successful commit — checkpoint carefully, handle rate limits and retries, and build dedupe/upsert logic so retries and partial failures are safe.

[Top](#top)

## How do you parse nested JSON and flatten arrays/objects into relational tables efficiently?
Short answer: stage the raw JSON into the target (or a staging table), then push the flattening into the target database using its native JSON/array functions (FLATTEN/UNNEST/VARIANT/SUPER) from a Matillion Transform job. Use Matillion orchestration only to load and kick off SQL-based transforms; use Python/JSON components only when the database can’t do it or the dataset is small.

Why this approach
- Databases (Snowflake, BigQuery, Redshift RA3) are massively parallel and have native JSON/array operators; pushing flatten work into them is orders of magnitude faster and simpler than row-by-row parsing in Matillion.
- Matillion is optimized for SQL pushdown: use it to orchestrate and run the SQL that does the heavy lifting.

Concrete pattern (high-level)
1. In an Orchestration job: load raw JSON files into a staging table (one column with VARIANT/JSON/SUPER or VARCHAR containing the JSON). Use S3/Blob -> staging table components.
2. In a Transform job: run SQL (via “Table Input / SQL Query” or “Bulk Load / Insert” components) that:
   - extracts top-level scalar fields,
   - uses the DB’s lateral-flatten/unnest functions to explode arrays into rows,
   - repeats lateral flattening for nested arrays (join the flatten results),
   - casts and writes results into normalized relational tables (dimension/fact).
3. Commit/swap tables or use insert/upsert components to populate final tables.
4. Record and isolate malformed JSON rows (error table) using TRY_*/IS_VALID checks.

Examples

Snowflake (recommended pattern)
- Load JSON into a VARIANT column raw.data.
- Use FLATTEN + LATERAL to explode arrays.

Example: one parent object with children array
SELECT
  r.metadata:id::STRING      AS parent_id,
  child.value:child_id::STRING AS child_id,
  child.value:name::STRING     AS child_name
FROM staging.raw_json r,
LATERAL FLATTEN(input => r.data:children) child;

Two-level nested arrays:
SELECT
  r.data:id::STRING                    AS id,
  p.value:product_id::STRING           AS product_id,
  opt.value:option_name::STRING        AS option_name
FROM staging.raw_json r,
LATERAL FLATTEN(input => r.data:products) p,
LATERAL FLATTEN(input => p.value:options) opt;

BigQuery
- Load JSON as STRING or Native JSON type; use JSON_EXTRACT_SCALAR/JSON_EXTRACT_ARRAY + UNNEST.

Example:
SELECT
  JSON_EXTRACT_SCALAR(parent, '$.id') AS parent_id,
  JSON_EXTRACT_SCALAR(child, '$.child_id') AS child_id
FROM dataset.staging,
UNNEST(JSON_EXTRACT_ARRAY(json_col, '$.parents')) AS parent,
UNNEST(JSON_EXTRACT_ARRAY(parent, '$.children')) AS child;

Redshift (RA3 with SUPER / PartiQL)
- Load JSON into SUPER column and use PartiQL FLATTEN or SELECT ... FROM table, l, r.

When to use Matillion components instead of DB SQL
- Small datasets or one-off transforms where writing SQL is heavier than using a Matillion "JSON Extract" or a Python Script component.
- When you must call an API that returns paginated JSON and iterate inside Matillion (use Iterator components and JSON parsing).
- When your target DB lacks decent JSON support and the volume is manageable.

Matillion-specific components and usage notes
- Use Orchestration job components to land files to S3/GCS/Azure and load into staging tables.
- Use Transform job “SQL” components to run flatten/unnest queries; prefer these for scale.
- There’s a JSON Extract/JSON Iterator in Matillion for simple extraction and for iterating API results; use them for control-flow tasks or small extractions, not large-scale flattening.
- Use Matillion Python components when you need custom parsing or complex normalization that’s easier in code, but be aware these run on the Matillion worker and don’t scale like the database.

Performance and reliability tips
- Push work to the DB (set-based lateral joins), avoid row-by-row processing in Matillion.
- Stage the raw JSON in a native JSON/variant type (Snowflake VARIANT, BigQuery JSON, Redshift SUPER) to preserve structure and speed parsing.
- Filter early and only select necessary fields before flattening.
- Flatten in stages if the JSON is deeply nested: create intermediate CTEs or temp tables for each level to reduce intermediate row explosion complexity.
- Type cast early and validate with TRY_CAST/IS_VALID_JSON to route bad rows to an error table.
- For massive files, load compressed files directly and use parallel COPY/LOAD.
- Add provenance columns (source_file, load_ts, raw_json) to help debug parsing issues.

Error handling and schema evolution
- JSON is schemaless — define a canonical schema for your relational tables and document expected paths.
- Handle missing keys with NULLs via safe extractors (JSON_EXTRACT_SCALAR/::) and use defaults where appropriate.
- Capture raw JSON for rows that fail validation and create automated alerts or a retry path.

Summary checklist
- Stage raw JSON into DB (VARIANT/JSON/SUPER).
- Use DB native FLATTEN/UNNEST in Matillion Transform SQL.
- Extract into normalized tables with set-based SQL.
- Use Matillion orchestration for loading and orchestration; use Python/JSON components only when DB pushdown is not feasible.
- Validate, type-cast, and capture errors.

End of answer.

[Top](#top)

## How do you create custom connectors using Matillion’s Connector SDK and manage OAuth/token refresh securely?
High-level approach
- Use the Matillion Connector SDK to implement a connector that exposes the required metadata, authorization endpoints, schema discovery and data-read logic. The SDK provides scaffolding and a runtime model for Matillion to call into your connector.
- Implement OAuth as part of the connector’s authorization flow (Auth Code + PKCE for user-interactive flows; Client Credentials or JWT for backend flows).
- Do token storage and refresh server-side (in the Matillion instance or in an external secrets store) — never embed long-lived secrets in client-side code or in repository text.
- Implement robust refresh logic: refresh proactively before expiry, rotate refresh tokens when the provider returns a new one, handle refresh failures (reauthorize), and protect against concurrent refresh races.

Steps to create a connector with Matillion’s Connector SDK
1. Scaffold
   - Install the Connector SDK and use its scaffold/CLI (or download the template from Matillion docs) to create a new connector project folder.
   - The scaffold gives you the manifest/spec file and stubbed handlers (spec/metadata, authorize, token exchange, discover/schema, read/export).

2. Define connector metadata
   - Fill out the connector manifest/spec with connector name, description, configuration fields (client_id, client_secret, callback URL, scopes), and which OAuth flow(s) you support.
   - Mark sensitive fields so Matillion can treat them as encrypted/secret in the UI.

3. Implement OAuth handlers
   - Implement the authorization URL generator (Auth Code: generate authorize URL including PKCE if appropriate).
   - Implement the token exchange handler (exchange authorization code for access_token + refresh_token).
   - Implement the token refresh handler (call token endpoint using refresh_token).

4. Implement data operations
   - Implement schema discovery and read/ingest logic using the access_token.
   - Use the SDK-provided request context and lifecycle hooks for authentication.

5. Testing
   - Unit tests for token logic and schema parsing.
   - Integration tests against the real provider (sandbox) to verify full OAuth flow and refresh behavior.

6. Package and deploy
   - Package the connector as the artifact format required by Matillion (zip/manifest).
   - Upload/activate via Matillion Admin UI or the connector management API.
   - Configure the connector in Matillion; mark credential fields as encrypted or point them at a secrets store.

Securely managing OAuth and token refresh
- Use the right OAuth flow
  - Authorization Code + PKCE for interactive user flow (keeps client_secret out of browser).
  - Client Credentials or JWT for machine-to-machine connectors (no user refresh tokens required).
- Store secrets safely
  - Preferred: external cloud secrets manager (AWS Secrets Manager, Azure Key Vault, GCP Secret Manager). Give the Matillion instance a narrow IAM role to read/update only the specific secret(s).
  - Acceptable: Matillion encrypted project variables / encrypted component parameters when an external secret manager is not available.
  - Never store client_secret or refresh_token in source control or plain text.
- Token refresh pattern
  - Refresh proactively with a safety buffer (e.g., refresh if token_expires_at - now < 60–300 seconds).
  - If the token endpoint returns a new refresh_token, atomically replace the stored refresh token.
  - On refresh failure (invalid_grant / revoked token), fail and surface a clear error so the user re-authorizes.
- Concurrency and race conditions
  - Avoid multiple simultaneous refreshes. Use a simple lock around refresh (in-memory lock if single Matillion instance; distributed lock if multiple workers) or implement compare-and-swap on the secret (store token with version and only update if version matches).
- Logging and monitoring
  - Log token refresh attempts, failures, and HTTP response codes (avoid logging raw tokens).
  - Alert on repeated refresh failures or authorization errors so reauthorization can be done quickly.
- Rotation & least-privilege
  - Request minimal scopes and short token lifetimes when possible.
  - Rotate client secrets periodically and drive reconfiguration through the secrets manager.
- TLS and network security
  - Always use HTTPS to call provider token endpoints.
  - Validate certificate chains and use up-to-date TLS cipher suites.

Example refresh flow (conceptual Node.js snippet)
- This illustrates safe refresh: call token endpoint, handle returned tokens, update secret store atomically, and use a buffer to refresh early.

const axios = require('axios');
const qs = require('querystring');

// Token store abstraction — implement with Secrets Manager / Matillion encrypted variable
async function readTokenRecord() { /* returns { access_token, refresh_token, expires_at, version } */ }
async function updateTokenRecord(newRecord, expectedVersion) { /* CAS update; return success/fail */ }

async function refreshIfNeeded() {
  const tokenRec = await readTokenRecord();
  const now = Date.now() / 1000;
  const buffer = 120; // seconds
  if (tokenRec.expires_at && tokenRec.expires_at - now > buffer) return tokenRec.access_token;

  // Acquire refresh: basic CAS lock via versioning
  const response = await axios.post(TOKEN_URL, qs.stringify({
    grant_type: 'refresh_token',
    refresh_token: tokenRec.refresh_token,
    client_id: CLIENT_ID,
    client_secret: CLIENT_SECRET, // or use JWT assertion / client cert
  }), { headers: { 'Content-Type': 'application/x-www-form-urlencoded' }});

  const data = response.data;
  const newExpiresAt = now + (data.expires_in || 3600);

  const newRecord = {
    access_token: data.access_token,
    refresh_token: data.refresh_token || tokenRec.refresh_token, // rotate if provider returned one
    expires_at: newExpiresAt,
    // bump version handled by updateTokenRecord implementation
  };

  const ok = await updateTokenRecord(newRecord, tokenRec.version);
  if (!ok) {
    // Another process updated the token concurrently. Read and return latest.
    const latest = await readTokenRecord();
    return latest.access_token;
  }

  return newRecord.access_token;
}

Practical Matillion-specific options
- Use Matillion encrypted component parameters or project variables for storing client_id/client_secret when external secrets manager is not available. Mark them as "encrypted" in the UI.
- On Matillion EC2/GCE/VM, prefer attaching an IAM role or VM identity so the connector code can call AWS Secrets Manager / GCP Secret Manager / Azure Key Vault without long-lived credentials.
- Store tokens in Secrets Manager (with read/update permission). This centralizes token lifecycle and avoids putting tokens into Matillion project files.

Failure modes to handle
- Refresh token revoked or expired: surface a clear error and require reauthorization.
- Provider rate-limits or transient errors: exponential backoff and retry with jitter.
- Token rotation: if provider invalidates old refresh token on use, ensure your update is atomic to avoid losing the new refresh token.

Testing checklist
- Full OAuth dance: authorize + exchange + refresh.
- Simulate refresh failures (invalid_grant) and verify connector surfaces reauth requirement.
- Simulate concurrent refresh requests to verify locking/CAS works.
- Verify secrets are not present in logs or repository.

Summary (concise)
- Scaffold connector with Matillion Connector SDK; implement OAuth handlers and data operations.
- Use Authorization Code + PKCE for interactive auth; Client Credentials/JWT for server-to-server.
- Store client secrets and tokens in an external secrets manager or Matillion encrypted fields; avoid source-control or client-side leakage.
- Implement proactive, atomic token refresh with rotation handling, concurrency protection, monitoring and clear user-facing errors on reauthorization.

[Top](#top)

## How do you validate and mock external APIs for CI tests and protect credentials in test runs?
Short answer
- Mock external APIs (WireMock/MockServer/Mockoon/Mountebank/Postman Mock Servers, LocalStack for cloud services) and point Matillion jobs at the mock endpoint via injected variables.
- Validate responses via schema/contract tests (JSON Schema, Pact) and assertions inside Matillion (Python scripts, SQL checks) or in the CI job that polls Matillion.
- Protect credentials by never hard-coding them: use Matillion Credentials/Project or Environment variables, and supply secrets from a secret store (AWS Secrets Manager/Azure Key Vault/GCP Secret Manager/HashiCorp Vault or CI secret variables). Use short‑lived, least‑privilege test credentials, encrypted storage and avoid logging secrets.

How to implement it (concise blueprint)

1) Build reliable mocks
- Choose a mock tool:
  - WireMock / MockServer / Mountebank for HTTP stubbing
  - LocalStack for AWS APIs
  - Postman Mock Server or Mockoon for lightweight mocks
- Capture real interactions (record) and create canned responses for deterministic CI runs. Parameterize responses for different scenarios (success, timeouts, errors).

2) Make Matillion switchable to mock vs real
- Parameterize every endpoint and credential in Matillion using Project/Environment variables (or Matillion Credentials).
- In job components that call external APIs, reference those variables rather than literals.
- In CI runs, set the variable values to the mock server URL and test credentials.

3) Validate responses and behavior
- Schema checks: validate payloads against JSON Schema inside a Python Script component or in the CI step.
- Behavior checks: assert expected rows/columns in staging tables or use SQL queries to confirm transformations.
- Contract tests: use Pact or a consumer-driven contract approach to validate that consumer expectations align with the provider.
- Negative tests: include error and retry scenarios using mocks to simulate latency, 4xx/5xx, throttling.

4) CI integration and orchestration
- In CI (GitHub Actions / GitLab CI / Jenkins):
  - Start mock server as a container (docker-compose) or point to a persistent mock service.
  - Inject secret values (mock credentials, API keys) via CI secrets (not committed files).
  - Trigger Matillion jobs through Matillion’s REST API or CLI, passing environment variables/parameters so the job runs against the mock.
  - Poll job status via Matillion API and run post-run assertions (check DB, check job log).
  - Tear down mocks after tests.

5) Protect credentials in test runs
- Do not commit credentials to Git or Matillion job XMLs.
- Use Matillion Credentials (encrypted) and/or environment/project variables, but do not export them in plain text to repos.
- Use CI secret storage to inject secrets at runtime. Ensure CI secrets are encrypted and access-limited.
- Prefer managed secret stores (AWS Secrets Manager, Azure Key Vault, GCP Secret Manager, HashiCorp Vault):
  - CI runner or Matillion instance retrieves secrets at runtime with IAM roles or short-lived tokens.
  - Use dynamic/semi-ephemeral credentials for tests (rotate frequently or issue ephemeral tokens).
- Avoid logging: mask or avoid printing secrets in Matillion job logs and CI output.
- Network controls: run mocks in isolated test network or use VPCs, and restrict production API endpoints from test environments (so tests can’t accidentally talk to production).
- Principle of least privilege: test credentials only allow the minimal operations required.

6) Observability, flakiness control, and maintenance
- Keep tests deterministic: prefer mocked responses in CI for API interactions that are non-deterministic or rate-limited.
- Periodically run integration tests against real endpoints in a scheduled integration pipeline (not every CI run) to detect provider changes.
- Maintain mock recordings and update them as APIs evolve; use contract tests to detect breaking changes early.

Example CI flow (high level)
1. CI starts mock server container with canned scenarios.
2. CI injects mock URL and secrets via Matillion REST API run call or via variables in Matillion project.
3. CI triggers Matillion orchestration job to execute the API-calling transformation.
4. CI polls Matillion for job completion and retrieves logs/status.
5. CI performs assertions (DB checks, JSON schema validation, contract verification).
6. Clean up mock server and revoke/rotate any ephemeral test credentials.

Key security rules to state in interviews
- Never hard-code secrets; use secret stores or CI secret mechanisms.
- Limit test credentials to least privilege and short lifetime.
- Prevent secrets from being printed in logs.
- Use network isolation to prevent accidental production access.
- Prefer mocked deterministic tests in unit/CI; schedule live integration tests separately.

Done.

[Top](#top)

## How do you ingest files from S3/ADLS/GCS and choose file formats, compression, and partitioning strategies?
High-level approach
- Configure cloud credentials in the Matillion Project (AWS IAM role or keys for S3, service principal for ADLS Gen2, service account JSON for GCS).
- Use the storage-specific components to discover/stream files (S3 List / S3 Iterator / S3 Get Object; Azure Data Lake Storage List/Iterator/Get; Google Cloud Storage List/Iterator/Get) and the load components to move data into the target warehouse (S3 Load / GCS Load / ADLS Load or the target-specific “Load” components for Snowflake, Redshift, BigQuery, Synapse).
- Choose file format, compression, and partitioning according to data characteristics, target capabilities and performance/cost tradeoffs. Automate using Iterators and variables and handle errors by moving bad files to quarantine folders and logging metadata.

Concrete Matillion steps
1. Add cloud credentials to Project -> Manage Credentials (or use instance profile/role).
2. Use List/Iterator components to enumerate files (support wildcards and folder paths). Use variables to pass path/file to downstream components.
3. For staged loads:
   - For Snowflake/Redshift: use S3 Load (or the target-specific S3/GCS/ADLS Load) which issues COPY commands into the target.
   - For BigQuery: use “Load from Google Cloud Storage” or the BigQuery load components.
   - For Azure Synapse: use ADLS/Blob components with PolyBase or COPY into dedicated pools.
4. Configure the Load component: file format, compression, delimiter/schema mapping, error handling and batch/parallel settings. Use Iterators/Parallel Groups to load multiple files concurrently.
5. Post-load: apply transformations, maintain partitions/metadata, archive or delete processed files.

Choosing file format
- Parquet (recommended for analytics): columnar, compressed natively, efficient IO and predicate pushdown, good for schema-stable, large analytical datasets.
- ORC: similar benefits to Parquet (often used in Hadoop ecosystems).
- Avro: row-oriented with explicit schema support and good for evolving schemas and streaming/producer-driven ingestion.
- CSV/TSV: simple and universal but expensive to parse and no schema metadata — use only when producers force it.
- JSON: use for semi-structured data; store raw JSON or flatten into columns; slower to query than columnar formats.

Compression choices
- For columnar formats (Parquet/ORC): use internal compression codecs — Snappy (fast, good default), ZSTD (better ratio, more CPU), GZIP (higher compression at more CPU). Snappy is a safe default for parallel reading.
- For text formats (CSV/JSON): gzip is common and widely supported; consider zstd if your target supports it and CPU cost is acceptable.
- Ensure target warehouse supports the compression codec (Snowflake/Redshift/BigQuery/Synapse differ slightly in support).
- Tradeoffs: higher compression = lower IO cost but higher CPU during load; pick based on CPU availability and cloud transfer cost.

Partitioning strategies (file-level + table-level)
- File/directory partitioning: organize files by logical partitions in storage, e.g., /year=YYYY/month=MM/day=DD/ or /dt=YYYYMMDD/. This enables partition pruning when the loader or query engine supports it.
- Partition by ingestion or event time for time-series data. Use coarse granularity (daily) unless queries require hourly.
- Avoid very high-cardinality partition keys (do not partition by user_id).
- Target-specific considerations:
  - Snowflake: micro-partitions are automatic; still use date-based file layout and larger files (100–250MB compressed) to let Snowflake ingest efficiently. Use clustering keys for frequent filters.
  - Redshift: use COPY with many files in parallel; cluster/ sort keys matter for query performance — partition files by load date and choose distribution style to match joins.
  - BigQuery: prefer partitioned tables (ingestion time or column) and use directory-based partitions for external tables. Use clustering on high-selectivity columns.
  - Synapse: use folder partitioning and PolyBase/COPY with properly sized files; rowgroup/Parquet settings matter.

Operational and performance guidance
- File size: Aim for larger files (tens to a few hundreds of MB compressed). Avoid millions of tiny files which increase metadata and load overhead.
- Parallelism: Break source into multiple files for parallel COPY ingestion; Matillion can iterate and run parallel groups to maximize target loaders.
- Manifests: Use manifest files when ordering or explicit file lists are needed; manifests also simplify ingestion for Snowflake and Redshift.
- Schema evolution: Use Avro/Parquet for better schema handling. For evolving columns, implement automated schema detection and ALTER TABLE steps in Matillion.
- Error handling: Use COPY/LOAD options (ON_ERROR, MAXERRORS) and capture rejected rows. Move failed files to an error folder and notify.
- Security: Use least-privilege credentials, SSE/KMS or CMEK for storage, and VPC endpoints or private connectivity. Ensure credentials are rotated and stored in Matillion credentials.
- Cost/control: Consider egress/scan costs — columnar compressed files reduce scan cost. Partitioning reduces amount scanned by queries if pruning works.

Examples (short)
- Snowflake: Push Parquet files with snappy compression into an S3 staging path structured by /year=/month=/day/. Use Matillion S3 List + Iterator to call Snowflake S3 Load (COPY INTO) in parallel, then apply clustering keys for heavy filters.
- BigQuery: Load Parquet or Avro from GCS into partitioned tables (partition by date column). Use Matillion GCS List + Load to import into a partitioned table or create an external table addressing partition pseudo-columns.
- ADLS -> Synapse: Write Parquet files partitioned by date into ADLS Gen2, then use PolyBase/COPY to load into Synapse dedicated SQL pool in parallel.

Quick rules of thumb
- Prefer Parquet/Snappy for analytics workloads.
- Partition by date at the directory level; archive processed partitions.
- Keep files big enough to amortize overhead (~100MB compressed target) but not so big that a single file is a bottleneck.
- Use Matillion Iterators and parallel orchestration to maximize COPY/LOAD parallelism and to process many files reliably.

[Top](#top)

## How do you size and batch files to avoid the small-files problem and maximize parallel load performance?
Goal: produce a reasonable number of reasonably‑sized files so the target loader can read them in parallel without huge overhead from many tiny files or single big files that serialize work.

Key principles
- Prefer columnar/splittable formats (Parquet/ORC) with a fast codec (snappy, zstd) over gzipped CSV. Splittable formats allow multiple reader threads per file.
- Target compressed file sizes in the hundreds of MB (not KBs). Too-small files add overhead; too-large files reduce parallelism and increase recovery time.
- Make number of files per load at least equal to the target system’s parallel units (slices/slots/slots × nodes), but not orders of magnitude larger.
- Partition files logically (date, tenant, region) so you can load just relevant partitions and produce files sized per partition.

Recommended sizing (practical guidance)
- Snowflake: aim for ~100–250 MB compressed per file as a sweet spot; 100 MB–1 GB is acceptable depending on your warehouse size and parallelism. Avoid many < 10 MB files.
- Redshift: aim for 10s–100s of MB compressed per file (typical guidance ~64–256 MB); ensure #files ≥ #slices to get good distribution.
- BigQuery: aim for 100 MB–1 GB per file for load jobs; be mindful of the 10k source URI limit per load job and split into multiple jobs if needed.
- Parquet/ORC row-group size: target ~128–512 MB files with row groups sized for efficient column reads (e.g., 64–128 MB row groups).

Compression/format considerations
- Avoid non‑splittable compression (gzip) for very large datasets that you want to read in parallel. Use Parquet/ORC with snappy/zstd or use splittable compression.
- For CSV/JSON, prefer uncompressed or splittable compression (if available) and then rely on many mid‑sized files — but better to convert to Parquet upstream.

Batching strategies
- Upstream compaction: compact small files into target‑sized files before loading. Run periodic compaction jobs (Spark/Glue/EMR) or use Matillion orchestration to kick off compaction.
- Partition-aware batching: write files per partition (e.g., date=YYYY-MM-DD) and size them individually. This keeps compaction and reprocessing scoped.
- Bucketing: if you need parallel writers, shard by a hashing key (e.g., customer_id mod N) to produce N roughly-equal files per partition.
- Control parallel producers so they create files of roughly consistent sizes (rather than many tiny final files).

Matillion-specific tactics
- Orchestration jobs: use Matillion to schedule and orchestrate compaction jobs (AWS Glue, EMR, or a Matillion Python/Script component) to merge small objects into target sized files on object store (S3/GCS/Azure).
- Use Matillion’s file iterator and S3/GCS components to discover files and call compaction or loader steps only when thresholds are met (file count or total size).
- For Snowflake/Redshift/BigQuery components in Matillion: load from staged, compacted files (S3/GCS) and leverage COPY/COPY INTO settings (parallelism, manifest files, patterns).
- Manifest files: when you must load many files, create a manifest to control exactly which files the loader sees. For BigQuery avoid exceeding URL limits by splitting into multiple load jobs.

Sizing calculation example
- If you produce 1 TB (≈1024 GB) per day and target 250 MB compressed files:
  - 1 TB = 1024 GB = 1,048,576 MB → 1,048,576 / 250 ≈ 4,194 files/day.
  - If your warehouse has 256 parallel slices, you’ll have plenty of files to keep all slices busy; if you only have 8 slices you could reduce number of files (bigger files) to reduce overhead.

Operational controls and monitoring
- Monitor load times and CPU/IO for COPY operations; if COPY spends most time opening files/metadata, you have too many small files.
- Track per-file sizes and counts per partition; enforce compaction thresholds (e.g., run compaction if >100 files or total < threshold).
- Perform A/B tests: vary file size (e.g., 64 MB vs 256 MB) and measure end‑to‑end load throughput and query performance.

Quick checklist to implement
1. Choose columnar format (Parquet) and splittable compression.
2. Decide target compressed file size (start ~128–256 MB).
3. Partition data and determine number of shards per partition to match warehouse parallelism.
4. Implement compaction (Spark/Glue/Matillion-script) to produce target-size files.
5. Use manifests or patterned loads from Matillion to feed target warehouse.
6. Monitor and iterate.



[Top](#top)

## How do you design landing zones and lifecycle policies on cloud storage for raw, staged, and curated layers?
Goal: enforce secure, cost-effective, auditable handling of incoming data (landing), ephemeral staging for transforms, and durable curated outputs. Design covers naming/partitioning, access & immutability, ingestion patterns, monitoring, and concrete lifecycle rules for each layer.

Layers and purpose
- Raw (landing zone)
  - Immutable, append-only copy of source data exactly as received (for replay, audit, lineage).
  - Retain relatively long, compressed/archived for cost savings.
- Staged (working / temp)
  - Short-lived files used by ETL/transform jobs (intermediate formats, small-file compaction).
  - Ephemeral; safe to delete quickly after successful pipeline completion.
- Curated (production analytics)
  - Cleaned, transformed, partitioned, columnar (Parquet/ORC) optimized for queries.
  - Retained according to business/regulatory needs, moved to cheaper classes over time.

Naming, partitioning, formats
- Bucket/container naming: <env>-<team>-<purpose>-<layer> (e.g., prod-data-raw, prod-data-staged, prod-data-curated).
- Folder/partition convention: source=SOURCE/ingest_date=YYYY/MM/DD/ingest_ts=YYYYMMDDHHMMSS/file.parquet
  - Enables partition pruning in Athena/Redshift Spectrum/BigQuery.
- File formats:
  - Raw: store original format (JSON/CSV/AVRO) and optionally a compressed copy (.gz/.snappy).
  - Curated: Parquet/ORC, snappy or zstd compression, schema evolution strategy.
- Small file control: compact small files in Staged as part of Matillion orchestration before writing to Curated.

Access, security, and immutability
- Restrict write access to ingestion roles/services only; use separate principal for Matillion jobs to read/write.
- Use VPC endpoints (S3) or private access; block public access on buckets.
- Encryption: provider-managed or KMS customer-managed keys (SSE-KMS). Limit key admins.
- Versioning and object-lock for Raw: enable versioning and optionally object lock (WORM) for regulated data.
- Use bucket/container tags for ownership, retention policy, and environment.
- Audit: enable access logs (S3 access logs or CloudTrail), and lifecycle changes auditing.

Ingestion & Matillion patterns
- Landing: Matillion can push incoming files to Raw (S3 Put/GCS Upload/Azure Blob). Use run_id/job_id path to avoid collisions.
- Staged: create per-job tmp path: staged/<job_name>/<run_id>/ ; after successful loads, use Matillion Delete component to purge staged path.
- Curated: Matillion orchestration writes partitioned Parquet to curated path and registers/updates table in catalog (Athena/Glue/BigQuery).
- Idempotency: include ingest metadata and a manifest file; use object naming with timestamps and checksums.

Lifecycle policy guidelines (high-level)
- Staged: TTL short (3–14 days). Delete automatically to avoid cost.
- Raw:
  - Keep hot for 30–90 days for fast replay.
  - Transition to infrequent/archival after 90–180 days.
  - Consider 1–7 year retention depending on compliance; archive to Glacier/Archive and optionally expire after retention period.
  - Use versioning+object-lock for regulatory WORM requirements.
- Curated:
  - Keep frequently-accessed partitions in standard storage for 30–90 days.
  - Transition older partitions to IA after 30–90 days, and to archive after e.g. 365 days.
  - Expire/delete after business-specified retention (e.g., 3–7 years).

Concrete lifecycle examples

AWS S3 example (JSON lifecycle)
- Staged: expire in 7 days.
- Raw: transition to STANDARD_IA after 60 days, GLACIER after 365 days, delete after 1825 days (5 years).
- Curated: transition to INTELLIGENT_TIERING or STANDARD_IA after 30 days, GLACIER after 365 days, delete after 1460 days (4 years).

Example lifecycle rule JSON (simplified)
{
  "Rules": [
    {
      "ID": "staged-expire-7days",
      "Prefix": "staged/",
      "Status": "Enabled",
      "Expiration": {"Days": 7}
    },
    {
      "ID": "raw-transition-and-expire",
      "Prefix": "raw/",
      "Status": "Enabled",
      "Transitions": [
        {"Days": 60, "StorageClass": "STANDARD_IA"},
        {"Days": 365, "StorageClass": "GLACIER"}
      ],
      "Expiration": {"Days": 1825}
    },
    {
      "ID": "curated-tiering",
      "Prefix": "curated/",
      "Status": "Enabled",
      "Transitions": [
        {"Days": 30, "StorageClass": "STANDARD_IA"},
        {"Days": 365, "StorageClass": "GLACIER"}
      ],
      "Expiration": {"Days": 1460}
    }
  ]
}

Google Cloud Storage example (lifecycle JSON)
{
  "rule": [
    {"action": {"type": "Delete"}, "condition": {"age": 7, "matchesPrefix": ["staged/"]}},
    {"action": {"type": "SetStorageClass", "storageClass": "NEARLINE"}, "condition": {"age": 60, "matchesPrefix": ["raw/"]}},
    {"action": {"type": "SetStorageClass", "storageClass": "COLDLINE"}, "condition": {"age": 365, "matchesPrefix": ["raw/"]}},
    {"action": {"type": "Delete"}, "condition": {"age": 1825, "matchesPrefix": ["raw/"]}},
    {"action": {"type": "SetStorageClass", "storageClass": "NEARLINE"}, "condition": {"age": 30, "matchesPrefix": ["curated/"]}}
  ]
}

Azure Blob Storage example (management policy)
- Create lifecycle management policy rules for staged/raw/curated with filters on prefixes and storage tier actions (Hot -> Cool -> Archive and Delete after X days).

Operational considerations
- Test lifecycle rules in staging environment before applying to prod.
- Ensure Matillion orchestration handles eventual consistency and transition timings (don’t rely on immediate availability after transitioning).
- Ensure analytics engines can read archived objects if you plan queries on archived data (may require restore).
- Compaction / re-partitioning: lifecycle rules do not merge small files—schedule Matillion jobs to compact and rewrite into partitioned Parquet before transitioning to long-term storage.
- Monitoring/alerts: track storage growth, lifecycle transitions, and failed deletes; alert on unusual deletes or access patterns.
- Cost modeling: estimate storage & retrieval costs for transitions (Glacier retrieval can be expensive/slow).

Recommended baseline policy (example parameters to adapt)
- Staged: expire 3–7 days.
- Raw: hot 30–90 days; transition to IA at 60 days; archive at 365 days; expire per compliance (1–7 years).
- Curated: hot 30 days; IA at 30–90 days; archive at 365 days; expire 3–7 years.

Design checklist (quick)
- Naming & partitioning: consistent, query-friendly.
- Security: IAM, VPC endpoints, encryption, object-lock/versioning for raw when needed.
- Lifecycle rules: set per-prefix rules; test first.
- Matillion jobs: write to tmp staged path with run_id, compact files, purge staged after success.
- Metadata & catalog: update Glue/Athena/BigQuery after curated writes.
- Monitoring & audit logs.

This design balances immutability for raw auditability, ephemeral staging for cost and performance, and lifecycle-managed curated data for query efficiency and long-term retention.

[Top](#top)

## How do you control file deletion, archiving, and quarantine of bad files with clear operational runbooks?
High-level approach
- Never delete blindly. Use move/copy + then delete (or lifecycle) so files are recoverable.
- Keep a strict landing/staging/processed/quarantine folder pattern in object storage (e.g., s3://bucket/landing, /staging, /archive, /quarantine).
- Mediate all file operations through Matillion orchestration jobs and an ingestion control table so operations are auditable and idempotent.
- Automate validation, quarantine and archive as part of the pipeline; use lifecycle/versioning for final deletion.

Design patterns implemented in Matillion
- Landing → Validate → Load → Archive or Quarantine:
  - Orchestration job lists landing files, iterates per file (For Each).
  - Child job validates schema/row counts/checksum/header/filename patterns.
  - Success path: load into target (ELT), move file to archive/processed (timestamped path), update control table and logs.
  - Failure path: move file to quarantine with a companion .error or .metadata file describing validation failures, update control table and logs, trigger alert.
- Move vs delete:
  - Prefer S3/GCS/Azure move (copy+delete) to a guarded archive/quarantine folder. Final deletion handled by lifecycle policy or manual approval process.
- Control table / audit log:
  - Central table (file_name, size, checksum, received_ts, processed_ts, status, error_message, operator, job_run_id) updated by Matillion via JDBC components or API.
- Notifications and operators:
  - On quarantine, send alert via Matillion Notify/REST call (Slack, email, PagerDuty, SNS/SQS) with direct link to object and control table row id.
- Cloud-native protections:
  - Use object versioning and MFA-delete (S3) or soft-delete features as extra protection.
  - Apply lifecycle rules for archive tiering and eventual deletion (e.g., quarantine files auto-delete after 90 days).

Operational runbook template (concise)
Sections:
- Purpose / scope
- Responsible teams / escalation contact list (on-call, owners)
- Preconditions (permissions, job names, storage locations)
- Runbook steps for common scenarios
- Commands/snippets and Matillion job names
- Troubleshooting checklist and logs
- Rollback / recovery steps
- Post-mortem notes and retention

Runbook snippets (operator actions)

1) Routine successful ingest
- Confirm Matillion orchestration job (name) finished OK; check Matillion job run ID.
- Verify control table entry shows status=PROCESSED with archive path.
- Archive retention: confirm file exists in s3://.../archive/YYYYMMDD/<filename> and lifecycle applies.

2) File failed validation (quarantine)
- Matillion job will move file to s3://bucket/quarantine/YYYYMMDD/<filename>.
- Confirm an error file was created: <filename>.error or <filename>.metadata containing validation failures and job_run_id.
- Check control table: status=QUARANTINED, error_message populated.
- Inspect Matillion task logs (Job Run details → Task logs) and any transformation error output.
- Notify owner via PagerDuty/Slack using pre-populated message (file path, job id, error).
- If file must be reprocessed after fix: move corrected file to landing and trigger child job or rerun orchestration job; update control table with reprocess attempt details.

3) Emergency manual deletion (rare)
- Preconditions: required approvals from data owner & security (documented).
- Steps:
  - Take snapshot/copy to a restricted retention bucket OR ensure versioning retention exists.
  - Execute move to s3://bucket/deleted-with-approval/<date>/<filename>, or use cloud console with audit trail.
  - Update control table: status=DELETED, deleted_by, approval_id.
  - Record deletion in ticketing system.

Matillion-specific implementation details
- Components:
  - Use "Get/Directory/List" to enumerate files, "For Each" to iterate, and either built-in storage components (S3 Put/Delete/Move, Azure Blob components, GCS components) or a Python component for more complex copy/move semantics.
  - Use the "Run Orchestration" component to call child jobs for validation and load.
  - Use "Update Variable" + JDBC Query components to write control table records.
  - Use "Run Python Script" or "Run Bash" (if using Matillion’s API runner or environment) to generate .error metadata files and upload them to quarantine.
  - Use REST components to call notification endpoints (Slack, PagerDuty, SNS).

Control table example (simple)
- CREATE TABLE ingestion_control (
  file_name varchar,
  object_path varchar,
  received_ts timestamp,
  processed_ts timestamp,
  status varchar,
  rows_expected bigint,
  rows_loaded bigint,
  checksum varchar,
  error_message text,
  job_run_id varchar,
  owner varchar
);
- Populate on file discovery, update on validation/load/quarantine/delete.

Example validation checks (and where to put them)
- Filename conventions, timestamp, source id: orchestration pre-check.
- Header counts and schema conformance: child job using SQL or Python.
- Row counts/non-null checks: transformation job after load into staging.
- Checksums and row-hash: optional; store checksum in control table.

Quarantine contents and metadata
- Keep original file untouched in quarantine + add:
  - <filename>.error: validation summary, Matillion job id, timestamp.
  - <filename>.meta: original S3 metadata, checksum, uploader info.
  - Optionally a sanitized copy for debugging.

Monitoring and alerting
- Matillion job status -> Cloud monitoring integration (CloudWatch, Stackdriver, Azure Monitor) or via Matillion’s REST API hooking into Slack/PagerDuty.
- Alert on:
  - Any QUARANTINE event.
  - Repeated failures for same source or file pattern.
  - Backlog growth in landing bucket.
- Keep dashboards showing files in landing/staging/quarantine counts and age distributions.

Retention and final deletion
- Use lifecycle rules for final deletion:
  - Archive retention: e.g., move to Glacier/Archive after 30–90 days.
  - Quarantine retention: auto-delete after 90 days unless manually extended.
- Keep object versioning/retention for compliance windows if needed.

Troubleshooting checklist (for operators)
- Check Matillion job logs and task-level logs; capture job_run_id.
- Verify control table state and timestamps.
- Check storage bucket permissions and object ACLs.
- Re-run validation against copy of file in quarantine.
- If needed, restore previous version from versioning or from an archive copy.

Best practices summary
- Implement move-first (no immediate deletes), control table auditing, and automated quarantine with descriptive error artifacts.
- Automate notifications and integrate with on-call systems.
- Use cloud lifecycle and versioning for final deletion, and document any manual delete with approvals.
- Keep runbooks short, actionable, and include exact Matillion job names, SQL snippets and commands operators must run.

This yields deterministic handling of bad files, preserves recoverability, and makes operator actions repeatable and auditable.

[Top](#top)

## How do you bulk load to Snowflake using external/internal stages, file formats, copy options, and error handling?
High‑level flow
- Stage files (external: S3/Azure/GCS; or internal: Snowflake stage via PUT).
- Define a Snowflake FILE FORMAT that matches the file type (CSV/JSON/PARQUET/etc.).
- Run COPY INTO <table> FROM <stage> with appropriate COPY options (pattern/files, FORCE, PURGE, ON_ERROR, etc.).
- Inspect load results (COPY_HISTORY / ACCOUNT_USAGE) or use validation mode to find/review bad rows and take remediation (skip, fix and reload, move to quarantine).

Concrete examples and key options

1) Define file format(s)
- CSV example:
  CREATE FILE FORMAT my_csv_fmt
    TYPE = 'CSV'
    FIELD_DELIMITER = ','
    SKIP_HEADER = 1
    FIELD_OPTIONALLY_ENCLOSED_BY = '"'
    TRIM_SPACE = TRUE
    NULL_IF = ('NULL','')
    COMPRESSION = 'AUTO';

- Parquet example:
  CREATE FILE FORMAT my_parquet_fmt TYPE = 'PARQUET';

Why: explicit file formats make COPY INTO simple and consistent across loads.

2) Stages
- Internal stage (table or named stage):
  CREATE STAGE my_int_stage;
  PUT file://local/path/*.csv @my_int_stage AUTO_COMPRESS = TRUE;

  You can also use the per-table stage @%schema.table_name (no CREATE required), and PUT to @%table_name.

- External stage (S3 example):
  CREATE STAGE my_s3_stage
    URL = 's3://my-bucket/path/'
    CREDENTIALS = (AWS_ROLE = 'arn:aws:iam::123456789012:role/SnowflakeRole')
    FILE_FORMAT = (FORMAT_NAME = 'MY_CSV_FMT');

Why: external stages let you leave raw data in cloud storage; internal stages are useful for ad‑hoc or secure staging within Snowflake.

3) COPY INTO usage (typical form)
COPY INTO my_schema.my_table
FROM @my_s3_stage/path
FILE_FORMAT = (FORMAT_NAME = 'MY_CSV_FMT')
PATTERN = '.*\\.csv(\\.gz)?'    -- pick files by regex
FORCE = FALSE                   -- avoid reloading files already loaded
SINGLE = FALSE                  -- set TRUE to concatenate multiple files into a single load stream
PURGE = FALSE;                  -- set TRUE on internal stages to delete after successful load

4) Important COPY options and what they do
- FILES = ('file1.csv','file2.csv') vs PATTERN = 'regex' — explicit files or regex selection.
- FORCE = TRUE|FALSE — reprocess files even if they are marked as loaded.
- PURGE = TRUE|FALSE — for internal stages: remove files on successful load.
- ON_ERROR = 'ABORT_STATEMENT' | 'CONTINUE' | 'SKIP_FILE' | 'SKIP_FILE_n' | 'SKIP_FILE_<pattern>' — controls behavior on row/file errors.
  - ABORT_STATEMENT (default): fail the load at first error.
  - CONTINUE: load other rows and report errors.
  - SKIP_FILE / SKIP_FILE_n: skip problematic file(s).
- SINGLE = TRUE|FALSE — treat multiple files as a single stream (affects performance and parallelism).
- VALIDATION_MODE (preview) — validate files and return errors without writing rows (useful to pre-check inputs).
- MATCH_BY_COLUMN_NAME = CASE_SENSITIVE | CASE_INSENSITIVE — map JSON/variant / file columns by name.
- ENFORCE_LENGTH, TRIM_SPACE, EMPTY_FIELD_AS_NULL — data cleansing behaviors.

5) Error handling and debugging
- Use ON_ERROR to control immediate behavior during COPY: choose ABORT (strict), SKIP_FILE to quarantine bad files, or CONTINUE to maximize ingestion and inspect errors later.
- Pre-validate files with VALIDATION_MODE (or run COPY with VALIDATION-like mode) to get all errors without altering data.
- Inspect load history: query Snowflake copy history to find per-file and per-row failures:
  - ACCOUNT_USAGE.COPY_HISTORY or INFORMATION_SCHEMA.COPY_HISTORY (table function) provides metadata about each COPY operation (rows loaded, errors reported, bytes, etc.).
- For rejected rows:
  - If ON_ERROR = CONTINUE, subsequent rows are loaded and errors are reported in COPY_HISTORY; capture the error_count and error_message.
  - If you need the actual bad rows, use VALIDATION_MODE or run COPY INTO an intermediate table or VARIANT column and then run SELECT ... WHERE TRY_CAST(...) IS NULL to find rows failing conversion; or use staged error output (if you implement a manual process to COPY bad files to an error stage).
- Audit and retry:
  - Use metadata (e.g., load time, file names) from COPY_HISTORY to automate retries for only failed files.
  - If using internal stages with PURGE=FALSE you can re-run COPY on the same staged files (or set FORCE=TRUE if you need to reprocess despite metadata).
- Logging in Matillion:
  - Matillion returns the COPY output and status from Snowflake. Capture that output in task logs and/or have an orchestration flow that queries COPY_HISTORY after the load to detect errors and branch (success vs. failure handling).

6) Matillion specifics (how Matillion implements this)
- Components: use the Snowflake “S3 Load / Azure Blob Load / Google Storage Load” or the Snowflake “Bulk Load” component depending on your Matillion version.
- Configuration steps in Matillion:
  - Source: point to your cloud storage location (S3/Blob) OR choose internal stage option if Matillion should PUT files.
  - Stage name: select/create a Snowflake stage (or use per-table stage @%table).
  - File format: reference the Snowflake FILE FORMAT you created (or set file-format options in the component).
  - Pattern/Files: set PATTERN or file list to target desired files.
  - Copy options: set ON_ERROR, FORCE, PURGE, VALIDATION_MODE as component properties.
  - Compression: indicate whether files are compressed (GZIP) — Matillion can auto-decompress/preserve depending on COPY settings.
  - Matillion will perform PUT (for internal stage loads) and then run the COPY INTO command under the hood; it will return Snowflake’s result and allow orchestration branching on success vs error.
- Error handling in Matillion:
  - Use the component’s “On Failure” behavior to branch pipeline execution.
  - After the COPY step, add a SQL Query or Python Script that queries COPY_HISTORY for this job’s files and parses error_count / error_message for alerting or moving bad files to a quarantine S3/Blob location.
  - For remediation, use Matillion to move bad files to a quarantine external/internal stage and then trigger an ETL to parse and fix.

7) Best practices
- Prefer columnar formats (Parquet/ORC) for large bulk loads; they are faster and self-describing.
- Compress files (gzip/snappy) to reduce network I/O.
- Create FILE FORMAT objects to centralize parsing rules.
- Use PATTERN or explicit FILES lists to control which files are picked.
- Use IAM roles (S3) rather than static keys for external stages.
- Use VALIDATION_MODE or a small test load before full load to catch schema mismatches.
- Keep an automated audit: store COPY_HISTORY results, file names, row counts, and error counts for reconciliation.
- For incremental loads, use FORCE=FALSE and file metadata to avoid double-processing.

Quick sample end‑to‑end
1) CREATE FILE FORMAT my_csv_fmt ...
2) CREATE STAGE my_s3_stage URL='s3://bucket/path' CREDENTIALS=(AWS_ROLE='arn:...') FILE_FORMAT=(FORMAT_NAME='MY_CSV_FMT');
3) In Matillion: S3 Load component -> Stage = my_s3_stage, File format = my_csv_fmt, Pattern = '.*\\.csv', ON_ERROR = 'CONTINUE', PURGE = FALSE
4) After load: SELECT * FROM SNOWFLAKE.ACCOUNT_USAGE.COPY_HISTORY WHERE TABLE_NAME='MY_TABLE' AND START_TIME > ...; parse error_count and messages, move failed files if needed and reprocess.



[Top](#top)

## How do you tune Snowflake COPY options (ON_ERROR, VALIDATION_MODE, TRUNCATECOLUMNS, FORCE) and stage credentials?
Short, practical answers you can give in an interview.

ON_ERROR
- Purpose: controls behavior when an error is encountered during COPY (row or file-level errors).
- Tuning guidance:
  - Strict QA: use ABORT_STATEMENT (or default) so any problem stops the load and forces investigation.
  - Production incremental loads: use SKIP_FILE (or SKIP_FILE_n) to skip whole bad files, or CONTINUE to skip bad rows if losing some rows is acceptable.
  - Trade-offs: looser settings reduce pipeline failures but mask data-quality issues. Loosen only after you have monitoring/alerts and downstream compensating logic.
- Practical tip: pre-validate problem-prone sources and only relax ON_ERROR for mature feeds.

VALIDATION_MODE
- Purpose: run validation-only passes of the COPY without committing rows (useful for pre-flight checks).
- Tuning guidance:
  - Use a validation pass (VALIDATION_MODE) on a representative subset or on new feed layouts to catch mapping/format problems before the main load.
  - Don’t run full validation on huge datasets routinely — it costs extra time and compute. Run sampling or run validation only on new/changed files.
- Practical tip: perform a validation run as a pre-step in Matillion orchestration; then run the real COPY if no critical errors.

TRUNCATECOLUMNS
- Purpose: if incoming field length > target column width, TRUNCATECOLUMNS=TRUE truncates instead of erroring.
- Tuning guidance:
  - Only enable when truncation is acceptable/intentional (e.g., legacy varchar limitations).
  - Prefer schema changes or wider target columns if you need the data intact; truncation can silently lose data.
- Performance/operational: turning it on avoids failures but increases risk of undetected data loss — pair with logging/alerts.

FORCE
- Purpose: whether to reload files that Snowflake’s metadata indicates were already loaded.
- Tuning guidance:
  - Normal incremental loads: set FORCE=FALSE so Snowflake will skip files already processed (avoids duplicates).
  - Reprocessing/reloads: set FORCE=TRUE when you intentionally want to reload files (backfills, repairs).
- Practical tip: rely on Snowflake's load history and file tracking for idempotence; avoid FORCE=TRUE in scheduled pipelines unless explicitly required.

Putting the options together (recommended patterns)
- Pre-flight validation: run COPY with VALIDATION_MODE and ON_ERROR set to RETURN_ERRORS/ABORT (strict) on a sample.
- Production: COPY with VALIDATION_MODE disabled, ON_ERROR=SKIP_FILE or ABORT depending on SLA, TRUNCATECOLUMNS only if acceptable, FORCE=FALSE.
- Error handling: capture COPY errors (Snowflake returns error rows/metadata). In Matillion, run COPY inside a Try/Catch Orchestration and record results to a control table for alerting and reprocessing.

Stage credentials — security and operational tuning
- Best practice: use Snowflake Storage Integration (external stage) + cloud-native role (AWS IAM role, Azure AD, GCP service account) rather than embedding access keys in the COPY command.
  - Benefits: no long-lived keys in SQL, automatic use of cloud IAM, easier rotation, least privilege via IAM policy, easier audit.
- If you must use keys/SAS tokens:
  - Store them securely (Matillion Environment/Project variables marked secure, or a secrets manager).
  - Scope keys with least privilege (restrict to the bucket/container and prefix).
  - Rotate regularly and/or use short-lived tokens where supported.
- Matillion specifics:
  - Use the “Create External Stage” or run a controlled CREATE STAGE with STORAGE_INTEGRATION in Snowflake, then invoke COPY FROM @mystage in Matillion components.
  - For S3: prefer STORAGE_INTEGRATION (IAM role). If using access key/secret, put them in secure environment variables and reference them from the Snowflake COPY CREDENTIALS clause only when necessary.
  - For Azure: use storage integration or SAS tokens stored securely; for GCS: use a service-account key or storage integration.
  - Let Matillion orchestrate validation and COPY steps: do validation run, then COPY with chosen ON_ERROR/TRUNCATECOLUMNS/FORCE, log results to a control table.

Performance considerations
- Snowflake parallelizes COPY across files — favor multiple moderately sized files (e.g., 100MB–250MB compressed) rather than a single huge file.
- Avoid expensive validation on full datasets; sample or validate schema changes only.
- Minimize per-file overhead by grouping many small files or staging larger files.
- If you need concurrency, run multiple COPY INTO commands in parallel from Matillion (respecting Snowflake warehouse size).

Short example COPY pattern (conceptual)
COPY INTO schema.table
FROM @my_stage/path
FILE_FORMAT = (TYPE = CSV ...)
ON_ERROR = 'SKIP_FILE'
TRUNCATECOLUMNS = TRUE
FORCE = FALSE;

Key operational rules
- Use VALIDATION_MODE for pre-flight; don’t mix validation and production runs.
- Use FORCE=FALSE for idempotent, incremental processing.
- Only enable TRUNCATECOLUMNS when truncation is acceptable and tracked.
- Prefer storage integration/IAM roles for credentials, and store any keys securely in Matillion.



[Top](#top)

## How do you implement Snowflake MERGE at scale and manage clustering/ordering and micro-partitions?
High-level approach
- Treat MERGE as a set operation, not a row-by-row operation. At scale you must control the input size, transaction size, and how Snowflake writes micro-partitions.
- Common patterns: stage incoming rows into a staging table (or files on S3), then either (A) run a single set-based MERGE from that staged data, (B) run a series of chunked MERGEs (micro-batches) to limit transaction size, or (C) rebuild the table (CTAS) and swap for very large changes. Choose based on percent of rows changing and service-level constraints.

Matillion implementation patterns
- Ingest: use Matillion orchestration to land files to S3 or push directly to Snowflake staging. Use the Snowflake Bulk Load component (S3 -> COPY INTO) when loading large volumes; configure file sizes so Snowflake creates well-sized micro-partitions (see below).
- Stage: load to a transient or staging table in Snowflake. Keep staging tables transient to avoid long time-travel charges.
- Merge: use Matillion’s "Snowflake Query" / "Execute" components (or a built-in Merge component) to run your MERGE SQL. Use Matillion variables + ForEach loops to implement partitioned merging if batching is needed.
- Rebuild (when required): use Matillion to run a CTAS or CREATE OR REPLACE TABLE ... AS SELECT ... ORDER BY <cluster_key> then swap/rename to replace the production table in a controlled window (preserve grants/constraints as needed).

MERGE-at-scale patterns and when to use them
1) Single set-based MERGE (best for moderate-sized deltas)
- Load all changes into staging table.
- MERGE INTO target USING staging ON key
  WHEN MATCHED THEN UPDATE ...
  WHEN NOT MATCHED THEN INSERT ...
- Pros: simple, single transaction, minimal table churn if delta is not huge.
- Risks: large deltas create many small micro-partitions and big transactions → higher compute and storage/time-travel cost.

2) Micro-batch / chunked MERGE (best for large continuous loads)
- Partition the staging dataset (by hash(key), date ranges, key ranges) and loop over partitions from Matillion.
- For each chunk: MERGE only that partition. Keep chunk size to avoid long-running transactions.
- Pros: reduces transaction size, lowers contention and temp-storage spikes.
- Risks: more orchestration overhead; must ensure idempotency and ordering for dependent updates.

3) Rebuild/CTAS + swap (best when a large fraction of rows change or to reclaim fragmentation)
- Create a new table with desired clustering: CREATE TABLE new_table CLUSTER BY (col) AS SELECT ... FROM target LEFT JOIN staging ... ORDER BY <cluster_key>;
- Swap names or rename tables during a quick maintenance window.
- Pros: produces optimal micro-partition layout, one clean result, faster later query pruning.
- Risks: heavier compute during rebuild; careful handling of grants/constraints and time-travel.

Micro-partitions and file sizing recommendations
- Micro-partitions are Snowflake’s internal units (roughly built from contiguous ranges of rows, targeted compressed size ~16 MB but variable).
- COPY INTO creates micro-partitions; file size and row ordering affect micro-partition boundaries.
- Best practice: aim for source file sizes that produce good micro-partition fill (practical guidance: compressed files in the 50–250 MB range for large loads; smaller files lead to many small micro-partitions).
- For streaming/small updates use batching to accumulate to several MBs before COPY or use staged table batching.

Clustering keys, ordering and maintenance
- Choose clustering key(s) driven by your most common query predicates and join keys (date, customer_id, region, etc.).
- Define clustering with: ALTER TABLE <t> CLUSTER BY (col1, col2).
- Options for maintenance:
  - Automatic Clustering service (Snowflake-managed) — paid background service that continuously reclusters based on clustering key.
  - Manual recluster: periodically rebuild or reorganize the table (CTAS with ORDER BY or recreate via INSERT...SELECT ordered by clustering key) and swap. This is the common approach when you control costs.
- Monitor clustering health with SYSTEM$CLUSTERING_INFORMATION('<schema>.<table>') and INFORMATION_SCHEMA queries. Look at clustering depth and micro-partition stats to decide when to rebuild.

Time Travel, staging table type and storage impact
- MERGE and large DML create time-travel delta storage. Use transient tables for staging to reduce retention costs.
- Reduce TIME_TRAVEL_RETENTION_SECONDS temporarily for target staging rebuilds if acceptable to reclaim storage quickly.
- Watch long-running large transactions — they increase storage usage due to retained historical data.

Transaction and concurrency considerations
- Each MERGE is transactional. Large merges can hold resources and block DDL operations; keep transactions reasonably sized.
- If multiple writers update the same target, coordinate via orchestration (Matillion scheduling, locks or single-writer pattern) to avoid unexpected conflicts.

Metrics, monitoring and tuning
- Monitor query profiles (QUERY_HISTORY), query plans, bytes scanned, and execution times.
- Use SYSTEM$CLUSTERING_INFORMATION to measure clustering efficiency and micro-partition pruning effectiveness.
- Use Snowflake resource monitors and Matillion job alerts to detect failed merges, long-running jobs, or credit spikes.

Practical Matillion implementation checklist
- Stage files to S3 using Matillion connectors; target file sizes ~50–250MB compressed for bulk loads.
- Bulk-load into transient staging table via Snowflake Bulk Load (COPY INTO).
- Run set-based MERGE where possible. Use Matillion variables + ForEach loops to implement chunked MERGEs if the staging set is very large.
- If > X% of rows change (rule of thumb: many customers use ~10–30% as a tipping point), consider CTAS + swap to rebuild clustered table.
- Define CLUSTER BY on large, frequently filtered tables. Use automatic clustering if you require always-optimal clustering and are willing to pay.
- Periodically run SYSTEM$CLUSTERING_INFORMATION and rebuild when clustering depth or clustering ratio degrades.
- Use transient tables for staging to avoid time-travel costs, and consider lowering retention during rebuilds if appropriate.

Example SQL snippets
- MERGE:
  MERGE INTO prod.target t
  USING staging.s_changes s
    ON t.id = s.id
  WHEN MATCHED THEN UPDATE SET col1 = s.col1, col2 = s.col2
  WHEN NOT MATCHED THEN INSERT (id, col1, col2) VALUES (s.id, s.col1, s.col2);

- Define clustering:
  ALTER TABLE prod.target CLUSTER BY (customer_id, event_date);

- CTAS rebuild:
  CREATE OR REPLACE TABLE prod.target_new CLUSTER BY (customer_id, event_date) AS
    SELECT ... FROM prod.target t
    LEFT JOIN staging.s_changes s ON t.id = s.id
    -- compute final state
    ORDER BY customer_id, event_date;

Operational best-practices summary
- Stage first, operate set-based, limit transaction size, and pick the pattern (single MERGE, micro-batch MERGE, or CTAS+swap) that matches delta size and SLA.
- Size your files for efficient micro-partitioning, pick clustering keys aligned with query patterns, and proactively monitor clustering metrics.
- Use Matillion orchestration and variables to implement batching, retries, and table-swaps; use transient tables to reduce storage/time-travel overhead.

[Top](#top)

## How do you use Snowflake Streams and Tasks with Matillion to build incremental pipelines and orchestrate dependencies?
Short answer
- Use Snowflake Streams to capture row-level changes (CDC) on source tables.
- Use Snowflake Tasks to run the MERGE/processing logic inside Snowflake (on a schedule or chained graph) so the stream gets consumed transactionally.
- Use Matillion as the orchestrator: trigger tasks (EXECUTE TASK), kick off stored-procs, or run final dependent jobs; poll Snowflake TASK_HISTORY or a status/flag table to sequence downstream Matillion jobs and handle failures.

How it fits together (pattern)
1) Capture changes: create a STREAM on the source table. The stream presents changed rows to be consumed by a transactional statement.
2) Apply changes inside Snowflake: create a TASK that runs MERGE (or calls a stored procedure) against your target table using the STREAM as the source. When the MERGE completes successfully, the stream is advanced (consumed).
3) Orchestrate & monitor from Matillion: either have Matillion trigger the TASK on demand or let the TASK run on schedule and have Matillion poll for completion or read a status flag to launch downstream work.

Concrete implementation steps and examples
- Create stream on source table:
  CREATE STREAM analytics.src_table_stream ON TABLE raw.src_table;

- Build a MERGE that consumes the stream (handles insert/update/delete):
  MERGE INTO analytics.target_table tgt
  USING (SELECT *, METADATA$ACTION AS action FROM raw.src_table_stream) s
    ON tgt.id = s.id
  WHEN MATCHED AND s.action = 'DELETE' THEN DELETE
  WHEN MATCHED THEN UPDATE SET col1 = s.col1, ...
  WHEN NOT MATCHED THEN INSERT (id, col1, ...) VALUES (s.id, s.col1, ...);

- Create a Snowflake TASK to run that MERGE (or call a stored proc enclosing MERGE logic):
  CREATE TASK analytics.task_merge_src
    WAREHOUSE = wh_small
    SCHEDULE = 'USING CRON * * * * * UTC'  -- or INTERVAL = '5 MINUTE'
    AS
    -- either MERGE directly or CALL proc:
    CALL analytics.proc_merge_src();

- Option A — Let Snowflake run tasks on schedule and chain tasks:
  Use CREATE TASK ... AFTER other_task to build dependency graphs inside Snowflake. This keeps latency low and consumes streams automatically in Snowflake.

- Option B — Matillion triggers tasks and orchestrates downstream Matillion jobs:
  In a Matillion Orchestration Job:
  - Use a Snowflake Query component to run: EXECUTE TASK analytics.task_merge_src;
  - Immediately poll TASK history to detect completion and status:
    SELECT *
    FROM SNOWFLAKE.ACCOUNT_USAGE.TASK_HISTORY
    WHERE TASK_NAME = 'ANALYTICS.TASK_MERGE_SRC'
      AND START_TIME >= DATEADD(minute, -10, CURRENT_TIMESTAMP())
    ORDER BY START_TIME DESC
    LIMIT 1;
  - Use Matillion If/Branch components and Wait loops to re-query until you see SUCCESS or FAILURE. Use variables to control retries/timeouts.

Alternative triggering patterns
- Execute TASK from Matillion (EXECUTE TASK) to run on-demand.
- Matillion runs the MERGE SQL itself (Snowflake Query component) against the stream — same effect as TASK but execution is driven by Matillion rather than Snowflake task scheduling.
- TASK chains inside Snowflake using AFTER are preferred when you want Snowflake-native micro-batch orchestration and minimal Matillion involvement.

Handling idempotence, concurrency, and errors
- Ensure MERGE logic is idempotent and deterministic. Streams are advanced only when the consuming transaction commits. If MERGE fails, stream not consumed; retry is safe.
- Use single consumer per stream or create separate streams if multiple consumers are needed.
- Control concurrency: TASKs can be configured to use an appropriate warehouse. Avoid running overlapping executions against same stream/target unless logic supports it.
- Use TASK_HISTORY / INFORMATION_SCHEMA or a status table for reliable monitoring. Matillion can poll these to orchestrate downstream jobs.
- Use stored procedures for complex transformations so the TASK remains simple (CALL proc).

Matillion-specific implementation notes
- Use Snowflake Query components to run EXECUTE TASK, CALL proc, MERGE SQL, or queries against ACCOUNT_USAGE.TASK_HISTORY.
- Use Wait components to back off between polls and If components to branch on success/failure.
- Use Matillion variables for task names, time windows, retry counters, and dynamic SQL.
- Grant Matillion's Snowflake role permission to EXECUTE TASK, USAGE on warehouse, and read TASK_HISTORY / ACCOUNT_USAGE views.

Best practices
- Prefer Snowflake Tasks + Streams for low-latency, transactional CDC processing inside Snowflake.
- Use Matillion for higher-level orchestration, long-running transforms, cross-system dependencies, and alerting.
- Keep TASKs small and focused; chain them inside Snowflake when steps are purely SQL-based and tightly coupled.
- Monitor TASK_HISTORY, set sensible retries/timeouts, and design MERGE logic to be safe on retries.
- Size warehouses for expected concurrency and set auto-suspend for cost control.

Security/permissions
- The Matillion service role must have rights to EXECUTE TASK (or to run the MERGE/CALL directly), USAGE on the target warehouse, and SELECT on the stream/source or proper ownership if needed.
- For ACCOUNT_USAGE access, grant the role appropriate privileges or use a view that exposes required task history.

Typical architectures
- Near real-time micro-batch: Stream + Task runs every 1–5 minutes; Matillion only monitors and triggers downstream ETL.
- On-demand orchestration: Matillion executes tasks or runs MERGE SQL on-demand, then starts transformation jobs when task completes.
- Hybrid: Tasks handle source-to-staging merges; Matillion handles heavy transformations and cross-schema joins after confirming tasks finished.

Results you get
- Transactional consumption of CDC with Streams (no missed or double-applied changes if MERGE committed).
- Lower data movement and compute overhead by running MERGE inside Snowflake.
- Centralized orchestration in Matillion for downstream processes, notifications, and cross-system dependencies.

[Top](#top)

## How do you load into BigQuery with load jobs vs query jobs and manage write dispositions and partitioned/clustered tables?
Short answer: In Matillion you can load into BigQuery either with a Load Job (use the BigQuery Load component to ingest files from GCS into a BigQuery table) or with a Query Job (use the BigQuery Query component to run SQL that writes results to a table). Use Load Jobs when ingesting files (Parquet/Avro/CSV/JSON) — they are cheaper and faster for straight ingestion. Use Query Jobs when you need SQL transformations, MERGE/upsert logic, or to create tables via CTAS/DDL — they incur query processing costs.

How they differ (practical points):
- Source:
  - Load Job: reads data from GCS objects.
  - Query Job: reads existing BigQuery tables or external sources and runs SQL.
- Cost/perf:
  - Load Job: billed for load operations and storage; no byte-scanned query charges.
  - Query Job: billed by bytes processed by the query.
- Transformations:
  - Load Job: minimal (schema transforms, field mapping). Heavy transforms require subsequent Query Jobs.
  - Query Job: full SQL power (CTAS, MERGE, windowing, etc.).
- Typical Matillion usage:
  - Stage files to GCS, use BigQuery Load to populate staging/landing tables, then use BigQuery Query components to transform and MERGE into target tables.

Write dispositions (mapping to BigQuery behavior) and how to set them:
- BigQuery writeDisposition values:
  - WRITE_TRUNCATE — overwrite target (whole table or, if used with partition decorator, just that partition).
  - WRITE_APPEND — append rows to target table/partition.
  - WRITE_EMPTY — fail if target table/partition is not empty (useful for safe-first-load).
- In Matillion:
  - BigQuery Load component exposes an action/table behavior (Append / Overwrite / Create / Fail etc.) or a Write Disposition parameter — set according to the behavior you want.
  - BigQuery Query component: when saving query results you can choose "Create table", "Create or replace" (which uses CREATE OR REPLACE TABLE), or run INSERT/MERGE statements explicitly.
- Replacing only a partition:
  - Use a partition decorator in the destination name and WRITE_TRUNCATE. Example: load into dataset.table$20250801 with WRITE_TRUNCATE to replace that date partition only — avoids rewriting the entire table.
  - With Query Jobs you can write to table$YYYYMMDD or use DML to DELETE/INSERT or MERGE filtered to that partition.

Partition and clustering management:
- Creating partitioned/clustered tables:
  - Prefer creating the table with PARTITION BY and CLUSTER BY via DDL (Query Job) or create it once using Matillion table-action that supports DDL. Example:
    CREATE TABLE dataset.sales
    PARTITION BY DATE(order_date)
    CLUSTER BY customer_id, product_id AS
    SELECT ... ;
  - For Load Jobs you can also pass partitioning parameters when creating a table in some UI/CLI flows, or load into an existing partitioned table.
- Loading patterns:
  - Preferred: keep a persistent partitioned/clustered target table; load incoming partition files into staging (or directly into the target partition) and then MERGE/apply logic.
  - If your source already produces partitioned files (e.g., daily files), load each file into the matching partition using table decorator and WRITE_TRUNCATE or WRITE_APPEND depending on idempotency.
- Clustering:
  - Cluster keys are set at table creation time. Loading into a clustered table preserves clustering; if you overwrite a table (CREATE OR REPLACE) you must specify clustering again or it will be lost.
  - Use clustering on columns used heavily in WHERE, GROUP BY, and JOIN predicates to reduce query scan cost.
- Upserts and deduping:
  - Use Query Job with MERGE to perform transactional upsert into a partitioned/clustered table. Typical pattern in Matillion: load raw file to staging partition table via Load Job, then run a Query Job MERGE into the final partitioned/clustered table using partition filter in the ON clause for efficiency.

Examples (illustrative):
- Load job to a partition (via decorator) and truncate that partition:
  - In Matillion BigQuery Load component: Destination table = mydataset.mytable$20250801, Write Disposition = WRITE_TRUNCATE, Source = gs://bucket/file.parquet
- Overwrite entire table using Query Job (CTAS with partition/cluster):
  - SQL run by BigQuery Query component:
    CREATE OR REPLACE TABLE mydataset.mytable
    PARTITION BY DATE(event_date)
    CLUSTER BY user_id AS
    SELECT ... FROM mydataset.staging;
- Upsert into partitioned/clustered target:
  - Load new rows to mydataset.staging (Load component), then run:
    MERGE mydataset.target T
    USING mydataset.staging S
    ON T.id = S.id AND T.event_date = S.event_date
    WHEN MATCHED THEN UPDATE SET ...
    WHEN NOT MATCHED THEN INSERT (...);

Best practices for Matillion + BigQuery:
- Stage files to GCS and use Load Jobs for bulk ingestion; use Query Jobs for transformations and merges.
- Create partitioned/clustered tables once (DDL) and load into them; avoid repeated CREATE OR REPLACE unless you re-specify partitioning/clustering.
- For daily loads, load per-partition with table decorators and WRITE_TRUNCATE to achieve idempotency and avoid scanning full tables.
- Use MERGE for CDC/upsert rather than overwriting whole tables when possible — combine staging (Load) + MERGE (Query).
- Mind costs: Query Jobs are convenient but can be expensive if scanning large tables; partitioning/clustering plus targeted loads significantly reduce costs.

Matillion-specific knobs to check:
- In BigQuery Load components: source format, destination table name (allow decorators), action/write disposition, autodetect/schema options, partitioning options if available.
- In BigQuery Query components: output table creation mode (Create/Replace/Append), use of DDL/DML statements (MERGE, CREATE TABLE ... PARTITION BY ... CLUSTER BY ...), and job priority/labels.

This gives you the operational differences, how to set write dispositions in Matillion components, and how to handle partitioned and clustered table workflows.

[Top](#top)

## How do you optimize BigQuery costs using partition pruning, clustering, and slot reservations vs on-demand?
Partition pruning, clustering, and slot reservations are the most effective levers to reduce BigQuery query costs. Below is a focused, implementation-oriented explanation — including how to apply them when running ELT with Matillion.

1) Partitioning (reduce bytes scanned)
- Principle: Partitioned tables limit scanned data to specific partitions when queries include a partition filter, dramatically lowering bytes scanned.
- Best partition choices: date/time columns (event_date, log_date) or ingestion-time for simple pipelines. Choose a column you filter on frequently.
- How to enable pruning:
  - Use equality/range filters on the partition column (e.g., WHERE event_date = '2025-08-28' or WHERE event_date BETWEEN …). Avoid wrapping the partition column in functions.
  - Use _PARTITIONDATE/_PARTITIONTIME system columns or partition decorators (table$YYYYMMDD) if practical.
- Matillion-specific:
  - Ensure Matillion-generated SQL includes explicit WHERE clauses on the partition column. In Table Input / Query components, push the date/filter into the SQL, not as a downstream filter step.
  - When loading with Matillion’s BigQuery Output components, set partitioning options (partition column or ingestion-time) at table create/write time.
- Operational tips:
  - Enforce partition filters with required partition filter policies if appropriate.
  - Use partition expiration to remove old data and reduce storage costs.

2) Clustering (reduce scan within a partition)
- Principle: Clustering sorts data within partitions by up to 4 columns so BigQuery can skip data ranges inside a partition.
- When to use: for high-cardinality, frequently-filtered columns (user_id, device_id, status) used in WHERE, JOIN or GROUP BY.
- How it reduces cost: combines with partition pruning — instead of scanning the whole partition, BigQuery reads fewer blocks if cluster columns narrow the range.
- Matillion-specific:
  - Define clustering keys when creating/loading the table with BigQuery Output components (Clustered by columns).
  - Periodically rewrite tables (CTAS or create table as select) to recluster data if insert patterns are append-heavy and clustering gets fragmented.
- Limitations:
  - Clustering benefit accrues over time as data is ingested and reorganized; short-lived or small tables see less benefit.
  - Avoid low-cardinality columns (booleans, tiny enums) as cluster keys.

3) Query patterns and SQL practices (enabling pruning/clustering)
- Push filters down: always include partition/cluster column predicates in the SQL issued to BigQuery (Matillion should generate those in-source).
- Avoid SELECT *; project only required columns.
- Avoid functions or casts on partition/cluster columns in WHERE clauses.
- Use table decorators for point-in-time reads when appropriate to avoid scanning full tables.
- Use materialized views or derived tables for repeated heavy aggregations.

4) Slot reservations vs on-demand (cost/control tradeoffs)
- On-demand:
  - Charged by bytes processed. Best when workloads are infrequent, unpredictable, or low overall bytes.
  - Easy to operate: no capacity management, pay per use.
- Slot reservations (flat-rate/flex):
  - You buy compute capacity (slots) for predictable cost and consistent performance. Good for sustained, high-volume query workloads.
  - Use reservations to avoid spikes in on-demand charges when you have high concurrency or heavy queries.
  - Flex slots (short-term hourly) are available for transient spikes; monthly commitments reduce unit cost for steady demand.
- Which to choose:
  - If monthly on-demand costs are high and usage is predictable, calculate break-even for a capacity commitment. If you have recurring heavy ETL/analytics queries (large Matillion jobs), reservations usually save money.
  - If workloads are spiky or light, on-demand is often cheaper.
- Matillion-specific:
  - Assign Matillion-run projects or service accounts to a reservation via the Reservations API/console so Matillion-generated queries consume reserved slots.
  - Coordinate Matillion job schedules to even out concurrency, maximizing slot utilization.
- Additional controls:
  - Use autoscaling patterns: schedule heavy Matillion jobs in off-peak windows or stagger them.
  - Combine reservations with optimized SQL, partitioning, clustering, and materialized views to minimize the slot minutes required.

5) Monitoring and tuning
- Track bytes scanned per query (INFORMATION_SCHEMA.JOBS_BY_PROJECT and audit logs).
- Use Query Plan and Query Timeline to see scanned bytes and slot utilization.
- If reservation underutilized, downsize or reassign capacity; if overutilized, either optimize queries or add capacity.
- Monitor partition usage (INFORMATION_SCHEMA.PARTITIONS) and clustering effectiveness (bytes read distribution).

6) Practical sequence to optimize cost with Matillion + BigQuery
- Analyze query patterns and identify frequent filters and hot columns.
- Partition tables on the most-used date column and change Matillion loads to write to partitions.
- Add clustering on frequently-filtered, high-cardinality columns; rewrite tables periodically to maintain clustering.
- Refactor Matillion transformations to push filters into the SQL executed in BigQuery.
- Consider materialized views or pre-aggregated tables for repeated workloads.
- Evaluate spend: if on-demand costs remain high and usage is steady, purchase slot reservations (or flex slots for spikes); configure Matillion queries to use the reservation.
- Continue monitoring and iterate.

Keep in mind BigQuery pricing and slot products evolve; always validate current pricing and test expected cost vs reservation pricing using historical query volumes.

[Top](#top)

## How do you load into Redshift using COPY from S3, choose dist/sort keys, and schedule VACUUM/ANALYZE?
Load into Redshift from S3 (in Matillion)
- Use an Orchestration job. Add a S3 Load component (or Execute SQL with a COPY if you prefer full control).
- Configure source: S3 bucket/path (or manifest), file format (CSV/JSON/Parquet/ORC), compression (GZIP/BZIP2).
- Authentication: supply an IAM role ARN that grants Redshift COPY permission (recommended) or provide AWS keys. If using server-side encryption/KMS, include the appropriate COPY options/KMS key.
- COPY options to set in Matillion (or in your COPY SQL):
  - FORMAT AS PARQUET for Parquet files, or specify CSV/JSON options for text.
  - DELIMITER, IGNOREHEADER, REMOVEQUOTES, FILLRECORD, TIMEFORMAT, TRUNCATECOLUMNS as needed.
  - COMPUPDATE OFF and STATUPDATE OFF during large bulk loads to speed the load; run ANALYZE after load.
  - MAXERROR to tolerate bad rows, or MAXERROR 0 to fail on first error.
  - Use MANIFEST for many files or to ensure particular file lists are loaded.
- Example COPY (can be executed with Matillion Execute SQL component):
  COPY schema.table
  FROM 's3://my-bucket/path/'
  IAM_ROLE 'arn:aws:iam::111122223333:role/RedshiftCopyRole'
  FORMAT AS PARQUET;
- Alternative for CSV:
  COPY schema.table
  FROM 's3://bucket/path/file.csv'
  IAM_ROLE 'arn:aws:iam::...'
  DELIMITER ','
  IGNOREHEADER 1
  GZIP
  COMPUPDATE OFF STATUPDATE OFF;

Choosing distribution and sort keys
- Distribution style:
  - DISTKEY on the column most often used in joins with a large co-joined table. Use KEY when you need to colocate rows to avoid network shuffle.
  - ALL for small dimension tables (< few MBs) that are joined frequently — replicates table to all nodes.
  - EVEN when there’s no obvious join key or when you want even data distribution.
- Distribution key selection rules:
  - Pick the column that is frequently used in equality joins with large tables.
  - Prefer moderate-to-high cardinality keys (not extremely low cardinality like boolean flags).
  - Avoid using a monotonically increasing key if inserts are skewed across slices.
- Sort keys:
  - Use sort keys to improve range scans, ORDER BY, GROUP BY and to speed merge joins that benefit from sorted input.
  - Compound SORTKEY(col1, col2...) preserves leading-column order; best when queries filter on the first column(s).
  - Interleaved SORTKEY(colA, colB, ...) gives equal weight across listed columns; good when queries filter on different columns non-hierarchically.
  - Choose columns used in WHERE clauses, range queries, or ordering. Date columns are common leading sort keys for time-partitioned workloads.
- Example CREATE TABLE:
  CREATE TABLE schema.events (
    user_id bigint,
    event_time timestamp,
    event_type varchar(50),
    ...
  )
  DISTKEY(user_id)
  SORTKEY(event_time);
- Compression encodings: run ANALYZE COMPRESSION once on a sample table or use AMAZON recommended encodings, or let CREATE TABLE AS with COPY infer encodings. Use COMPUPDATE/ANALYZE COMPRESSION offline for tuning.

VACUUM and ANALYZE: when and how to schedule in Matillion
- Why:
  - ANALYZE updates planner statistics (essential after large loads if STATUPDATE was OFF).
  - VACUUM reclaims space and re-sorts rows for tables with many deletes/updates or when inserts leave unsorted inserts (COPY creates new sorted and unsorted blocks).
- Recommended pattern for bulk loads:
  1. COPY with COMPUPDATE OFF STATUPDATE OFF.
  2. Run ANALYZE table_name (or ANALYZE VERBOSE) to update stats.
  3. Run VACUUM [FULL | SORT ONLY | DELETE ONLY] depending on need:
     - VACUUM SORT ONLY table; use when you need to restore sort order but have few deletes.
     - VACUUM DELETE ONLY table; use when many deleted rows need to be reclaimed.
     - VACUUM FULL is more expensive but does both.
- How to implement in Matillion:
  - Add Execute SQL components after the S3 Load step to run:
    - ANALYZE schema.table;
    - VACUUM SORT ONLY schema.table; (or VACUUM FULL schema.table;)
  - Alternatively add a SQL Script component to run both commands in sequence.
  - Use the Table Metadata/Row Count output from the load step to conditionally run VACUUM only when inserted rows exceed a threshold (use Variables and If/Branch components).
- Scheduling:
  - Create an Orchestration job that does: COPY -> ANALYZE -> (conditional VACUUM).
  - Use Matillion’s built-in Scheduler to run that job on your desired cadence (hourly/daily/nightly) or trigger via API/EventBridge.
  - For very large tables, run VACUUM during off-peak hours; ANALYZE is usually lightweight and can be run more frequently.
- Monitoring and thresholds:
  - Track table bloat (deleted/deleted_rows) using STL_DELETING or SVV_TABLE_INFO; schedule VACUUM when unsorted/deleted rows exceed a threshold (for example >10% of table).
  - For RA3 nodes with automated vacuum/maintenance enabled, rely more on ANALYZE and less on manual VACUUM unless needed.

Practical tips
- Prefer Parquet loads with COPY for best performance and smaller I/O when source can produce Parquet.
- Use IAM roles for COPY for security and simplicity.
- Disable STATUPDATE/COMPUPDATE during large loads, and run a single ANALYZE and (if needed) VACUUM after the load.
- Use Matillion variables and conditional flow to avoid unnecessary VACUUMs.
- Test dist/sort key choices on representative data and test common queries to measure performance impact.

[Top](#top)

## How do you leverage Redshift Spectrum external tables from Matillion and manage Glue Catalog metadata?
Short answer: treat Matillion as the orchestration/SQL runner and use Glue Data Catalog + Redshift Spectrum for metadata and external table definitions. Use Matillion to (a) run the Redshift DDL that maps to Glue, (b) invoke Glue crawlers or Glue APIs to manage/refresh metadata and partitions, and (c) orchestrate the workflow (wait for crawler, then run Spectrum queries or CTAS). Below are practical steps, commands, IAM requirements and best practices.

1) Architecture / roles
- Redshift Spectrum reads table metadata from the AWS Glue Data Catalog. Your Redshift cluster needs an IAM role (attached to the cluster) that grants:
  - Glue read actions: glue:GetDatabase, glue:GetDatabases, glue:GetTable, glue:GetTables, glue:GetPartition, glue:GetPartitions, glue:GetTableVersion, glue:GetTableVersions
  - S3 actions for the underlying data: s3:GetObject, s3:ListBucket, s3:GetBucketLocation
  - kms:Decrypt if objects are KMS-encrypted
- If you use Lake Formation, you must grant Redshift access in Lake Formation or use appropriate Lake Formation APIs. Lake Formation can block Glue Catalog access if not configured.
- Minimal example IAM policy (not exhaustive):
  {
    "Version":"2012-10-17",
    "Statement":[
      {"Effect":"Allow","Action":["glue:GetDatabase","glue:GetDatabases","glue:GetTable","glue:GetTables","glue:GetPartition","glue:GetPartitions"],"Resource":"*"},
      {"Effect":"Allow","Action":["s3:GetObject","s3:ListBucket","s3:GetBucketLocation"],"Resource":["arn:aws:s3:::my-bucket","arn:aws:s3:::my-bucket/*"]},
      {"Effect":"Allow","Action":["kms:Decrypt"],"Resource":"arn:aws:kms:region:acct:key/key-id"}
    ]
  }

2) Create the external schema in Redshift (run from Matillion)
- Use a Matillion "Run Query" / "Execute SQL" component against Redshift to create the external schema that points at the Glue DB:
  CREATE EXTERNAL SCHEMA ext_schema_name
  FROM DATA CATALOG
  DATABASE 'glue_database_name'
  IAM_ROLE 'arn:aws:iam::account:role/RedshiftSpectrumRole'
  CREATE EXTERNAL DATABASE IF NOT EXISTS;
- Do this once per Glue DB or per logical group.

3) How Glue metadata is created/managed
- Two common approaches to populate Glue Catalog metadata for Spectrum:
  a) AWS Glue crawler: configure crawlers to scan S3 prefixes and create/refresh table definitions and partitions in the Glue Catalog. Matillion orchestrates by invoking/starting the crawler and polling for completion.
  b) Explicit DDL/API: create Glue tables and partitions via Glue APIs (boto3) or by running DDL (CREATE EXTERNAL TABLE ... STORED AS PARQUET LOCATION 's3://...') in Athena or by calling the Glue REST API. Matillion can run Python Script components (boto3), or call AWS CLI via Command components, to create/update Glue metadata.
- Recommended: use Glue Crawlers for discovery and partition management for raw landing zones; use explicit Glue table definitions when you need strict control.

4) Partition management
- Redshift Spectrum reads partitions from the Glue Catalog; Spectrum itself does not scan S3 to discover partitions.
- Options to keep partitions up to date:
  - Let Glue crawler detect partitions (recommended for dynamic datasets).
  - Run Athena MSCK REPAIR TABLE to populate Glue partitions (works if Athena has access and you want a simple approach).
  - Programmatically call Glue create_partition / batch_create_partition via boto3 (Matillion Python component) whenever new partitions are added.
- Avoid relying on listing S3 from Redshift for partition discovery — maintain partitions in the Glue Catalog.

5) Using Matillion to orchestrate the flow
- Typical Matillion orchestration job:
  1. Upload/land files to S3 (S3 Put components or external processes).
  2. Start Glue crawler or invoke Glue job / Glue API (Matillion Python Script uses boto3.client('glue').start_crawler(...) or start_job_run).
  3. Poll/wait for crawler completion (boto3 get_crawler or get_job_run status).
  4. Run Redshift DDL/queries (Matillion "Run Query" components) against external tables: SELECT from ext_schema.table, or CREATE TABLE AS (CTAS) to internal Redshift tables, or run transformations using external tables directly.
  5. Optionally drop/refresh external schema/tables if you re-create metadata.
- Use Matillion Environment Variables for Glue database name, crawler name, IAM role ARN, S3 paths to keep jobs portable.

6) Example flows / SQL snippets
- Create external schema:
  CREATE EXTERNAL SCHEMA ext_poc
    FROM DATA CATALOG
    DATABASE 'my_glue_db'
    IAM_ROLE 'arn:aws:iam::123456789:role/RedshiftSpectrumRole'
    CREATE EXTERNAL DATABASE IF NOT EXISTS;
- Querying external table from Matillion transformation: use the Redshift Query component to run:
  SELECT * FROM ext_poc.my_external_table WHERE dt = '2025-08-28';
- CTAS into Redshift internal table:
  CREATE TABLE analytics.tbl_daily AS
  SELECT col1, col2, SUM(...) FROM ext_poc.my_external_table WHERE dt='2025-08-28' GROUP BY 1,2;
- Invoking Glue crawler via Python Script (pseudocode):
  import boto3
  glue = boto3.client('glue')
  glue.start_crawler(Name='my-crawler')
  # poll glue.get_crawler(Name='my-crawler')['Crawler']['State'] or use get_crawler_metrics

7) Best practices and gotchas
- IAM & Lake Formation: confirm Glue catalog access is not blocked by Lake Formation policies. If Lake Formation is enabled, grant SELECT/Describe to the Redshift role or register the role with Lake Formation.
- Use a single external schema for a Glue DB and let Glue manage the table set; avoid creating many external schemas unnecessarily.
- Partition wisely (e.g., dt=yyyy/mm/dd); keep partition cardinality reasonable.
- Performance: Spectrum reads directly from S3; consider CTAS to Redshift for hot query patterns or compressed Parquet/ORC file formats and columnar layouts.
- Catalog consistency: schedule Glue crawlers or trigger crawlers as part of Matillion orchestration after data landing—don’t assume immediate automatic discovery.
- Security: ensure S3 encryption and IAM least privilege. If using KMS, add kms:Decrypt to Redshift role.
- Drift: If you change table locations or format, update Glue catalog; run ALTER TABLE in Glue or re-run crawler and then refresh external schema as needed.

8) Troubleshooting
- "Table not found" in Redshift: verify external schema maps to correct Glue DB and the Glue table name exists; check IAM role permissions.
- Missing partitions: confirm Glue catalog partitions were created (Glue console or boto3 get_partitions); if not, run crawler or create partitions programmatically.
- Permission denied on S3: check S3 bucket policy and role permissions and KMS keys.
- Lake Formation access denied: grant necessary LF permissions to the Redshift IAM principal or disable LF for that catalog.

Summary of responsibilities
- Matillion: orchestrate S3 landing, start/monitor Glue crawlers or call Glue APIs, execute Redshift SQL (create external schema, queries, CTAS), and handle workflow logic.
- Glue Catalog: holds external table and partition metadata.
- Redshift Spectrum: uses Glue metadata and S3 for query execution.
- IAM/Lake Formation/S3/KMS: ensure correct permissions and configuration.

This approach gives you declarative metadata management (Glue), automated discovery (crawlers or API-driven), and orchestration + SQL execution (Matillion) with Redshift Spectrum serving as the query layer over S3.

[Top](#top)

## How do you load into Synapse using COPY INTO/PolyBase, manage external data sources, and tune parallelism?
Short, practical guide (Matillion-focused) on loading into Azure Synapse with COPY INTO or PolyBase, managing external data sources/credentials, and tuning parallelism.

1) High-level workflow
- Stage files in Azure Blob Storage or ADLS Gen2 (same region as Synapse).
- Create/manage credentials and an External Data Source pointing to that storage.
- Use either COPY INTO (recommended for many scenarios) or PolyBase/External Tables for mass loads.
- Tune file sizing, file count, distribution keys and resource class to maximize parallelism.

2) COPY INTO — when and how
- Good for fast, simple loads from ADLS/Blob into dedicated SQL pool or Synapse serverless.
- No need to create External Tables; credentials can be passed inline or via a database scoped credential.
Example (simplified):
COPY INTO dbo.target_table
FROM 'https://<account>.dfs.core.windows.net/container/path/'
WITH (
  FILE_TYPE = 'PARQUET',                  -- or 'CSV'
  CREDENTIAL = (IDENTITY = 'Shared Access Signature', SECRET = '<sas-token>'),
  MAXERRORS = 0
);

- You can also pass Storage Account Key or SAS. For managed identity / service principal patterns, create a database scoped credential and reference it.

3) PolyBase / External Tables — when and how
- Use PolyBase when you prefer external tables or when using dedicated SQL pool bulk loading semantics (can be highly parallel).
Typical steps:
- Create a database scoped credential (for storage key or SAS):
CREATE DATABASE SCOPED CREDENTIAL MyCred
WITH IDENTITY='SHARED ACCESS SIGNATURE', SECRET='?sv=...';

- Create external data source:
CREATE EXTERNAL DATA SOURCE MyExt
WITH ( TYPE = HADOOP,
       LOCATION = 'abfss://container@account.dfs.core.windows.net',
       CREDENTIAL = MyCred );

- Create external file format:
CREATE EXTERNAL FILE FORMAT ParquetFormat
WITH ( FORMAT_TYPE = PARQUET );

- Create external table:
CREATE EXTERNAL TABLE dbo.ext_table
( col1 INT, col2 VARCHAR(100), ...)
WITH ( LOCATION = '/path/', DATA_SOURCE = MyExt, FILE_FORMAT = ParquetFormat );

- Load from external table:
-- CTAS (preferred for best throughput)
CREATE TABLE dbo.target WITH (DISTRIBUTION = HASH(col1), HEAP)
AS SELECT * FROM dbo.ext_table;

Or:
INSERT INTO dbo.target SELECT * FROM dbo.ext_table;

4) Managing external data sources & credentials (best practices)
- Prefer service principal or Managed Identity for production (avoid long-lived storage keys in SQL).
- If using SAS, use short-lived SAS refreshed by orchestration (Matillion job or Azure Function).
- Maintain a clear lifecycle: CREATE/ALTER/DROP database scoped credentials and external data sources as part of deployment scripts.
- Scope the credential only to required containers/folders and give least privilege.
- For Matillion: upload stage files using the S3/ADLS/Blob components or via API, then run SQL components to create or reference external data objects and run COPY/INSERT.

5) Tuning parallelism and performance
- File sizing and file count:
  - Aim for many medium-to-large files rather than one huge file. Recommended target: ~100 MB to 1 GB per file for best throughput.
  - Ensure the number of files is sufficient to saturate the Synapse load parallelism (for dedicated SQL pool there are 60 compute nodes backing 960 distributions). Practical rule: create dozens to hundreds of files so work can be parallelized across distributions.
- Distribution and skew:
  - Choose a good distribution column for your target table (HASH on a well-distributed key) to avoid skew.
  - If you can’t choose a good hash key, use ROUND_ROBIN for staging then redistribute as needed.
- Use CTAS for fastest loads (CREATE TABLE AS SELECT) because it minimizes logging and uses parallel CTAS paths.
- Resource class and concurrency:
  - For dedicated SQL pool, use an appropriate resource class for heavy loads (DW_LOAD or larger) to allocate memory.
  - Matillion jobs can parallelize multiple COPY INTO/INSERT streams; coordinate concurrency so you don’t oversubscribe IO or memory.
- Compute sizing:
  - Increase Synapse performance level (DWUs / vCores) if ingest throughput is the bottleneck.
- Storage performance:
  - Use premium storage account tiers, ensure same region, and use optimized endpoints (Blob vs ADLS endpoint) to maximize throughput.
- PolyBase specifics:
  - PolyBase mapper count corresponds to distributions; balance file count and file sizes so mappers have similar work.
  - Avoid tiny files: overhead kills throughput. Avoid enormous single files that underutilize parallelism.
- Statistics and post-load:
  - After load, update statistics or create indexes/partitions to ensure downstream query performance.
- Monitoring:
  - Monitor copy/insert durations, Data Movement Coordinator waits, DMVs for distribution skew, and storage throughput metrics.

6) Matillion-specific notes
- Use Matillion’s components to stage files into ADLS/Blob (S3/Cloud Storage components or API).
- Use an "Execute SQL" or "Run Script" component to create DB scoped credentials/external data sources (version-control these scripts).
- Matillion has specific Synapse Bulk Load or Copy components (depending on version); they wrap COPY INTO or PolyBase patterns. Choose the COPY option for simplicity and resiliency; use PolyBase/External Table when you need external table patterns or control over file formats.
- Orchestrate credential rotation (SAS/service principal refresh) via Matillion orchestration jobs.

7) Quick checklist for a performant load
- Stage files in same region and premium storage.
- Break data into many ~100MB–1GB files.
- Use COPY INTO or CTAS from external table (PolyBase) — prefer CTAS for fastest ingestion.
- Choose good distribution key and check skew.
- Use proper credential model (SP/Manged Identity) and rotate SAS tokens.
- Scale Synapse compute/resource class if needed.
- Update statistics and monitor.

Summary: COPY INTO is quick and simple for many loads; PolyBase/external tables + CTAS can give maximum throughput if you prepare file sizes and counts to match Synapse distribution/mapper parallelism. Manage data sources via database scoped credentials (prefer SP/managed identity), and tune parallelism primarily by file sizing/count, distribution choices, resource class, and compute/storage sizing.

[Top](#top)

## How do you compare Matillion’s performance patterns across Snowflake, BigQuery, Redshift, and Synapse?
Short answer: Matillion is an ELT tool that tries to push work into the target warehouse; so performance patterns follow how well the target scales, concurrency behaves, and supports bulk loads. Matillion’s own instance size matters only for components that run on the Matillion VM (Python, API calls, file transforms). Below are platform-specific patterns and practical tuning points.

Common factors that determine Matillion job performance
- Pushdown-first: most Matillion transformation components generate SQL executed in the target. Speed is therefore dominated by the target warehouse’s compute and how well SQL is optimized there.
- Local components: Python, Bash, API, JDBC reads/writes and some connectors run on the Matillion instance — size these instances to avoid CPU/IO bottlenecks.
- Staging format & location: using cloud-native object storage (S3/GCS/ADLS) and columnar formats (Parquet) speeds bulk loads and reduces scan cost.
- Parallelism: Matillion can run components in parallel, but overall throughput is gated by warehouse concurrency limits and Matillion instance resources.
- Network and region: colocate Matillion, storage, and warehouse in same region to avoid egress latency/costs.

Snowflake
- Pattern: Excellent pushdown; high concurrency; compute separable from storage; automatic, near-instant cluster scaling with multi-cluster warehouses.
- Strengths: Complex SQL transformations push down very well; automatic micro-partitioning and result cache reduce repetitive cost; scaling is simple (increase warehouse size or enable multi-cluster).
- Weak points: Cost can grow if warehouses are oversized or run unnecessarily; improper micro-partition/clustering can still cause hot scans.
- Matillion specifics: Matillion-generated SQL runs with minimal overhead. Use COPY from S3/GCS into Snowflake stages or use bulk loads via Snowpipe for continuous loads. Keep Python/other on-VM work small to maximize pushdown.
- Tuning: right-size warehouses, use multi-cluster for concurrency spikes, cluster keys where necessary, compress/designed staging in Parquet, avoid row-by-row transforms on VM.

BigQuery
- Pattern: Serverless, massively parallel; Matillion pushes SQL via BigQuery jobs. Performance is fast for large scans but depends on data layout and partitioning/clustering.
- Strengths: Zero-cluster management; excellent for ad-hoc large-scale analytical scans; charges by bytes processed which can be cost-efficient with good partitioning.
- Weak points: Cost model: naively pushing heavy wide-table scans can be expensive. Concurrency quotas and API rate limits can affect many simultaneous Matillion jobs. Complex iterative/row-wise transforms may suffer if done outside BQ.
- Matillion specifics: Use load-from-GCS and native BigQuery SQL pushdown. Prefer clustered/partitioned tables and columnar (native) storage. Control query costs by restricting scanned columns/partitions.
- Tuning: partition & cluster, use approximate methods where acceptable, use flat-rate slots for predictable high concurrency, batch smaller files into Parquet/ORC before load.

Redshift
- Pattern: Clustered, provisioned compute. Matillion uses COPY/UNLOAD and pushes SQL to the cluster. Performance depends heavily on distribution keys, sort keys, and node type (RA3 vs older nodes).
- Strengths: Predictable performance for tuned analytic workloads; UNLOAD/COPY from S3 is efficient; RA3 separates compute and storage which helps scaling.
- Weak points: Concurrency limits and queueing with high simultaneous jobs; requiring careful distribution/sort tuning; resizing nodes is heavier than Snowflake/BigQuery autoscale.
- Matillion specifics: Matillion’s SQL pushdown works well but you must design schema (distkey/sortkey) for joins and aggregations. Avoid running heavy transformation logic on the Matillion VM.
- Tuning: choose RA3 for flexible storage, tune dist/sort keys, use WLM and concurrency scaling to handle spikes, consolidate small files before COPY.

Synapse (Azure Synapse Analytics)
- Pattern: Two main modes — dedicated SQL pool (provisioned MPP) and serverless SQL pool (on-demand). Matillion can push SQL to dedicated pools efficiently; serverless has limits.
- Strengths: Dedicated pool gives good performance for tuned MPP workloads; tight ADLS/Blob integration and PolyBase/CTAS + COPY patterns for fast bulk loads.
- Weak points: Dedicated pool requires careful distribution (hash/round-robin) and indexing; scaling is manual/resize slow; serverless is convenient but has features and concurrency limitations and no persisted metadata optimizations.
- Matillion specifics: For heavy ELT, use dedicated SQL pool and load via PolyBase/COPY from ADLS. Avoid excessive Matillion-side transformations. For serverless, be mindful of limitations on CTAS and write operations.
- Tuning: pick correct distribution strategy and partitioning, use dedicated pools sized for workload, minimize cross-distribution shuffles, use CTAS and CTAS-based staging strategies.

Practical comparison summary
- Best for hands-off scaling and heavy concurrent SQL pushdown: Snowflake.
- Best for serverless, ad-hoc large scans with no infra to manage, but watch cost: BigQuery.
- Best for predictable, tuned workloads where schema optimizations are used and you want cluster control: Redshift (especially RA3) and Synapse dedicated.
- Most Matillion-friendly across the board: any platform that executes most work in-database and supports efficient bulk loads (Snowflake, BigQuery, Redshift, Synapse dedicated). Performance problems generally stem from doing procedural work on Matillion VM or poor warehouse table design.

Quick checklist when using Matillion across warehouses
- Maximize pushdown: prefer SQL components over Python/JDBC where possible.
- Use cloud storage staging in the target platform’s native region and columnar formats.
- Size Matillion instance for non-pushdown components (API calls, file processing).
- Tune warehouse-specific elements: warehouses & multi-cluster for Snowflake, slots/partitioning for BigQuery, dist/sort + WLM for Redshift, distribution and DWU sizing for Synapse.
- Monitor concurrency and API quotas; introduce batching or job orchestration if you hit limits.

No recommendations beyond these platform-specific behaviors; performance will track how well Matillion can push actual compute into the target and how that target is architected and tuned.

[Top](#top)

## How do you orchestrate Databricks or Delta Lake targets from Matillion and implement Delta MERGE?
Short answer
- Orchestrate by using a Matillion Orchestration job to extract and stage data (S3/ADLS/Blob), then call Databricks (Databricks Notebook / Run Job / Run Query component) to load/stage into Delta and run a MERGE. Use Matillion components to monitor status and handle errors.
- Implement Delta MERGE inside Databricks via spark.sql MERGE, the DeltaTable API in PySpark, or a SQL notebook cell. Matillion triggers the job and passes parameters (paths, table names, run-id, batch keys).

Key Matillion pieces to use
- Orchestration job (top-level flow)
- Components: Databricks Notebook, Databricks Run Job / Submit Run, Run Command/Run Script (depending on Matillion version), S3/Blob/ADLS Put and Get components, and Wait / If / Get Job Status for monitoring.
- Transformation jobs only for lightweight SQL against a JDBC if using Databricks SQL connector; heavy processing belongs in Databricks compute.

Recommended orchestration pattern (common)
1. Extract source data with Matillion into staged files (S3/ADLS/Blob) or into a staging Delta table (bronze).
2. Call Databricks (Notebook or Job) from Matillion, passing parameters: location(s) of staged files, target delta table name, batch id, load mode (full/CDC).
3. Inside the Databricks notebook:
   - Read staged data into a DataFrame (spark.read.format or Auto Loader).
   - Prepare the source DF (dedupe, cast types, add batch metadata).
   - Run Delta MERGE to upsert into the target Delta table (silver).
   - Optionally run OPTIMIZE / ZORDER / VACUUM as post-merge maintenance.
4. Matillion monitors job status, reacts to success/failure, archives staging, and triggers downstream jobs.

Example MERGE implementations
- SQL (in a Databricks SQL notebook cell or spark.sql):
  MERGE INTO delta.`/mnt/delta/target` AS t
  USING delta.`/mnt/delta/staging` AS s
  ON t.id = s.id
  WHEN MATCHED THEN UPDATE SET
    t.col1 = s.col1,
    t.col2 = s.col2,
    t.updated_at = s.updated_at
  WHEN NOT MATCHED THEN INSERT (id, col1, col2, created_at, updated_at)
    VALUES (s.id, s.col1, s.col2, s.created_at, s.updated_at);

- PySpark using DeltaTable API (inside Databricks notebook launched by Matillion):
  from delta.tables import DeltaTable
  source_df = spark.read.parquet("/mnt/staging/mybatch/")
  delta_table = DeltaTable.forPath(spark, "/mnt/delta/target")
  delta_table.alias("t") \
    .merge(source_df.alias("s"), "t.id = s.id") \
    .whenMatchedUpdateAll() \
    .whenNotMatchedInsertAll() \
    .execute()

- Using a temp view (option if source is an in-memory DataFrame):
  source_df.createOrReplaceTempView("src")
  spark.sql("""
    MERGE INTO delta.`/mnt/delta/target` t
    USING src s
    ON t.id = s.id
    WHEN MATCHED THEN UPDATE SET *
    WHEN NOT MATCHED THEN INSERT *
  """)

Passing parameters from Matillion
- Configure the Databricks Notebook/Run Job component with parameters: input_path, target_path, batch_id, env, schema/table.
- Use Matillion variables/encryption for credentials and tokens.
- Use the Get Job Status and Wait components to poll until the Databricks job completes; branch on success/failure.

CDC / SCD patterns
- For CDC/upsert: load incoming changes to a staging path, MERGE on primary key + comparison of last_updated to apply updates.
- For SCD Type 2: MERGE with WHEN MATCHED AND (source.last_updated > t.last_updated) THEN UPDATE SET current = false, end_date = source.last_updated; plus WHEN NOT MATCHED THEN INSERT with current=true, start_date=batch_ts.
- Handle deletes by treating delete flags in source and mapping to a DELETE action in MERGE or by marking rows as inactive.

Error handling & idempotency
- Use batch_id or file_checksum to avoid re-processing duplicates.
- Wrap MERGE logic to be idempotent — dedupe staging by primary key and highest timestamp before MERGE.
- In Matillion, catch Databricks job failures, capture log output, and route to retry or alert logic.

Performance and tuning
- Read source from cloud storage as parquet/Delta to avoid heavy serialization.
- Partition Delta tables on high-selectivity columns; use ZORDER for common filter columns.
- For very large merges, minimize source size (pre-filtering) and consider splitting into partition-level merges.
- Run OPTIMIZE and ZORDER after significant upserts for query performance.
- Use appropriate cluster size and autoscaling for Databricks jobs invoked by Matillion.

Security and connectivity
- Configure Databricks connection in Matillion with workspace URL and token or use instance profiles / managed identity for S3/ADLS access.
- Ensure Matillion has permissions to trigger runs and the Databricks job/notebook has permissions to read staged data and write Delta tables.

Example Matillion orchestration flow (concise)
- Orchestration job:
  1. Extract source and write /mnt/staging/batch123/
  2. Databricks Notebook component -> run notebook "process_and_merge" with params (input=/mnt/staging/batch123, target=/mnt/delta/target, batch_id=123)
  3. Wait/Get Job Status -> If success: Archive staging and update control table; If failure: fetch logs and alert.

Common pitfalls
- Forgetting to stage into a consistent format (parquet or Delta) causes schema drift errors.
- Running MERGE with different schemas (types mismatched) — always cast/validate columns first.
- Large MERGE without pruning leads to full-scan and long runtimes — pre-filter or partition by keys.

Summary (single-line)
Use Matillion orchestration to stage and trigger Databricks compute (Notebook/Job), then perform Delta MERGE inside Databricks via SQL or DeltaTable API with proper parameterization, idempotency, monitoring, and tuning.

[Top](#top)

## How do you integrate Matillion with dbt for modeling while keeping orchestration and ingestion in Matillion?
Short answer
- Keep Matillion for ingestion and orchestration; call dbt to do modeling. Orchestration jobs in Matillion load staging schemas/tables, then trigger dbt (Cloud or CLI) to run the model layer and tests. Capture exit status and artifacts and fail the Matillion job on dbt failure.

Integration patterns (two common approaches)
1) dbt Cloud (recommended if you use dbt Cloud)
   - Let Matillion trigger dbt Cloud jobs via API (Matillion has a dbt Cloud component or you can call the API with Run Command / HTTP calls).
   - Matillion handles upstream ingestion; when ingestion completes it calls dbt Cloud to run specified job (or job with selectors/tags).
   - Poll dbt Cloud for run_id status; propagate success/failure into the Matillion orchestration flow.

2) dbt Core/CLI running from Matillion
   - Install dbt on the Matillion instance (or use a sidecar/runner you control) and have Matillion run the dbt CLI via "Run Shell Script" or "Python Script" components.
   - Typical command: activate virtualenv -> cd to dbt project -> dbt deps && dbt run --models <selector> --profiles-dir <path> --target <env> && dbt test --models <selector>.
   - Capture exit code, upload artifacts (target/manifest.json, run_results.json) to a storage location if needed.

Step-by-step (dbt Cloud example)
1. In Matillion orchestration job: ingest and load source -> staging schema/tables.
2. Use an HTTP/Run Command component to POST to dbt Cloud API to start a job (or use built-in dbt Cloud component).
   - Send account_id, job_id, and optional JSON for job arguments (e.g., selector, vars).
3. Capture the returned run_id; poll dbt Cloud run-status endpoint until completion.
4. On success: optionally call dbt Cloud artifacts or docs endpoints to fetch run_results or upload artifacts to S3; continue downstream steps in Matillion.
5. On failure: fail the Matillion job, send alerts, and surface dbt error logs.

Step-by-step (dbt Core on Matillion example)
1. Prepare Matillion instance with dbt installed and dbt project in Git (pull to a known path).
2. In Matillion orchestration job: ingest to staging.
3. Add Run Shell Script or Python Script component that:
   - Pulls latest dbt code (git pull).
   - Activates virtualenv.
   - Runs dbt deps (if needed) then dbt run --models <selector> --profiles-dir /etc/dbt --target prod.
   - Optionally run dbt test and dbt docs generate.
4. Read exit code. If non-zero, fail the Matillion job and capture logs. If zero, continue.

How to select which models to run
- Use dbt selectors: model name, tag:, path:, state:, +model etc. Pass the selector from Matillion variables to the dbt CLI or dbt Cloud job arguments to run only downstream models of the changed tables.
- Use dbt’s state comparison (dbt run --models state:modified) when you want runs based on changes.

Passing variables and credentials
- dbt Cloud: store credentials in dbt Cloud, pass runtime variables through the job run payload.
- dbt Core: keep profiles.yml outside the repo and supply credentials via environment variables or profiles.yml that references secrets stored in Matillion Secure Variables or a secrets manager.
- Use Matillion variables to pass dynamic selectors, run timestamps, or env names.

CI/CD and version control
- Keep dbt project in git. Use dbt Cloud jobs / CI to validate PRs and run tests.
- For dbt Core, use Matillion to pull specific branches or tags to control which dbt version runs in each environment.
- For production promotions, align Matillion pipeline and dbt project versions (same commit/tag).

Logging, artifacts, and monitoring
- Capture dbt logs, run_results.json, and manifest.json. Upload to S3/GCS or to your monitoring system.
- Let Matillion surface failure reasons; store detailed dbt logs accessible for debugging.
- Use dbt test results to fail Matillion job or to branch handling of test failures.

Error handling and retries
- Treat dbt exit codes as authoritative. On failure, fail the orchestration job or route to error-handling workflow.
- Implement retries at the Matillion orchestration level only for transient failures; avoid automatic re-running of ingestion that might introduce duplicates unless idempotency is guaranteed.

Best practices and gotchas
- Keep ingestion deterministic and idempotent so dbt models can safely run against staging tables.
- Use incremental models and unique keys in dbt for large tables; ensure ingestion provides the necessary keys/timestamps.
- Minimize cross-tool state: prefer dbt to handle modeling state (tests, artifacts) and Matillion to handle schedule/dependency orchestration.
- Align environments: profiles.yml target in dbt must point to the same warehouse/schema Matillion writes to; use different schemas per environment.
- Security: do not bake secrets into code. Use Matillion Secure Variables or a secrets manager and feed them to dbt via environment variables or protected profiles.
- Concurrency: ensure dbt runs don’t conflict with other Matillion jobs writing to the same tables; use locks or scheduling where needed.

Summary checklist when implementing
- Decide: dbt Cloud (API trigger) vs dbt Core (CLI on Matillion runner).
- Make sure dbt has correct credentials and profile mapping to Matillion schemas.
- Use Matillion to load staging, then trigger dbt (selector, vars).
- Surface dbt results and fail Matillion on dbt failures.
- Store artifacts/logs, use git for versioning, and design CI/CD for promotion.

This keeps Matillion as the ingestion/orchestration engine and dbt as the authoritative modeling layer while providing clear control, logging, and environment separation.

[Top](#top)

## How do you balance business logic between SQL components, Python/Batch components, and warehouse-native SQL?
High-level rule: keep set-based, large-data work in the warehouse; keep orchestration, I/O, and lightweight transformations in Matillion; use Python/batch only for logic that cannot be expressed efficiently in SQL or that requires external libraries/services.

Principles to apply
- Performance/scalability: push CPU- and I/O-heavy, set-based work to the warehouse to leverage MPP, columnar storage, and vectorized SQL engines. Avoid pulling large volumes into Matillion/Python.
- Cost: weigh warehouse compute costs vs Matillion/VM compute. Pushing more work to the warehouse can increase billable compute; heavy Python on Matillion VMs has separate cost.
- Maintainability & ownership: put enterprise business rules that multiple consumers must share into warehouse-native artifacts (views, materialized views, or stored procedures) to centralize and ensure consistent results.
- Observability & testability: prefer SQL and warehouse objects when you need built-in explain plans, query profiling, and easy row-level diagnostics. Use Matillion components for pipeline-level logging and orchestration visibility.
- Security & governance: keep sensitive transformations and access controls in the warehouse where RBAC and auditing are strongest.
- Complexity & expressiveness: use Python when you need libraries, complex control flow, ML inference, calling external APIs, or text processing that is impractical in SQL.
- Reuse & modularity: centralize reusable logic (shared SQL, stored procs, or named transformation jobs). Avoid duplicating complex SQL in multiple Matillion jobs.

Decision checklist (when to use each)
- Warehouse-native SQL
  - Use when: large joins/aggregations, window functions, set-based transforms, materialized results for many consumers, or when you need query tuning and explain plans.
  - Advantages: speed/scale, single source of truth, DB-level security, easier to tune.
  - Risks: higher warehouse compute cost, possible vendor lock-in for procedural code (stored procs).
- Matillion SQL components (transformations)
  - Use when: orchestration, staging, incremental loads, column-level cleaning, small to medium transforms, running parameterized SQL jobs, building pipelines that stitch steps together.
  - Advantages: low-friction ETL orchestration, easy to parameterize and schedule, best for pipeline orchestration rather than heavy compute.
  - Risks: generated SQL can become complex and fragmented if business logic is scattered across many components.
- Python/Batch (Matillion Python components or external batch)
  - Use when: external API calls, advanced text processing, ML model scoring, use of Python libraries (pandas, scikit-learn), file parsing, or procedural logic that’s hard to express in SQL.
  - Advantages: expressiveness, third-party integrations, good for specialized tasks.
  - Risks: poor performance on large data sets if data is moved out of the warehouse; reduced visibility into set-based performance; harder to maintain if not documented/tested.

Patterns and anti-patterns
- Pattern: Stage raw data in the warehouse via Matillion orchestration, run heavy transforms in warehouse SQL, then use Matillion to orchestrate downstream jobs and publish results.
- Pattern: Use Matillion for incremental CDC logic (detect/merge changed rows) and then push full aggregations into warehouse materialized views.
- Pattern: Prototype complex logic in Python for correctness, then, when scale demands it, rewrite set-based parts in SQL and keep only orchestration or specialized parts in Python.
- Anti-pattern: Extracting whole tables to Matillion/Python to do large joins/aggregations — results in network I/O, memory pressure, and slow runs.
- Anti-pattern: Hard-coding business logic across many Matillion components; instead centralize in views/stored procs or single reusable jobs.

Operational controls
- Refactor loop: monitor query/runtime costs, identify hotspots, and refactor from Matillion/Python into warehouse SQL when necessary.
- Versioning & CI: keep Matillion job definitions in Git, unit-test SQL where possible, and use query regression tests.
- Audit & lineage: use Matillion logging plus warehouse query history to maintain data lineage and to validate changes.
- Security: store secrets in Matillion credentials vault and rely on warehouse roles for in-warehouse objects.

Concrete quick rules of thumb
- If it’s set-based and touches lots of rows → warehouse SQL.
- If it’s pipeline control, file movement, or small structural transforms → Matillion components.
- If it needs external libraries, complex text/ML, or third-party integrations → Python/batch, but only after minimizing dataset size via SQL.

Example scenarios
- Large nightly aggregation for dashboards: do joins/aggregations in the warehouse, materialize results, use Matillion to schedule and load.
- Enrichment via external API for a small set of changed rows: Matillion identifies changed rows; Python calls API for those rows and writes back to staging.
- Complex entity resolution with fuzzy matching libraries: prototype in Python; if data volume grows, isolate fuzzy parts to an ML service or implement approximate matching in-database (or via specialized UDFs).

Use the above tradeoffs to map each business rule to the best execution location, and re-evaluate periodically as data volumes and cost profiles change.

[Top](#top)

## How do you prevent anti-patterns like row-by-row Python loops and replace them with set-based SQL?
Why avoid row-by-row Python loops
- They pull logic out of the database engine, forcing network round-trips or row-level operations that are O(n) or worse.
- They bypass the DB optimizer, indexes, vectorized execution and parallelism.
- They scale poorly and make job execution time linear with row-count.

How to prevent the anti-pattern in Matillion (practical steps)
1. Identify the anti-pattern
   - Search Transformation jobs for Python Script components or Orchestration jobs that iterate rows.
   - Look for explicit for/while loops reading/writing rows, cursor usage, or repeated single-row queries.
   - Measure runtime and row counts to justify conversion.

2. Choose the right push-down strategy
   - Preferred: push logic to the database as set-based SQL (MERGE, UPDATE...FROM, CTEs, window functions, aggregates).
   - If logic is complex but can be expressed in SQL, implement as SQL in Matillion (SQL Script component, Table Input + Table Output, or the DB-specific Merge component).
   - If logic requires procedural code, implement it as a DB-side stored procedure/UDF (Snowflake/BigQuery/Redshift), then call that from Matillion.
   - When data is small and in-memory processing is acceptable, use Python in Matillion but operate on whole DataFrames (vectorized Pandas) — not row loops.

3. Typical conversion pattern (use Matillion components)
   - Stage input data into a staging table using Table Output or Bulk Load.
   - Use one SQL statement (CTE + MERGE/UPDATE/INSERT) to apply changes to the target table.
   - Use Matillion’s "SQL Script" or database-specific "Merge" component to run set-based statements.
   - Validate results and drop staging objects.

Concrete example: converting a row-by-row update to a set-based MERGE (Snowflake)
Row-by-row Python pseudo anti-pattern:
- For each row in staging:
  - compute new_value via lookups
  - execute UPDATE target SET value = new_value WHERE id = row.id

Set-based alternative (recommended)
- Stage the incoming rows in table staging.updated_rows (id, new_value)
- Single MERGE statement:

MERGE INTO target_table t
USING staging.updated_rows s
  ON t.id = s.id
WHEN MATCHED THEN
  UPDATE SET t.value = s.new_value
WHEN NOT MATCHED THEN
  INSERT (id, value) VALUES (s.id, s.new_value);

If you need derived values from multiple tables, do the full computation in SQL:

WITH calc AS (
  SELECT s.id,
         CASE
           WHEN x.flag = 'A' THEN s.base * 1.1
           WHEN y.status = 'Z' THEN s.base * 0.9
           ELSE s.base
         END AS new_value
  FROM staging.updated_rows s
  LEFT JOIN lookup_x x ON s.key = x.key
  LEFT JOIN lookup_y y ON s.key = y.key
)
MERGE INTO target_table t
USING calc c ON t.id = c.id
WHEN MATCHED THEN UPDATE SET t.value = c.new_value
WHEN NOT MATCHED THEN INSERT (id, value) VALUES (c.id, c.new_value);

Redshift/BigQuery variation: use UPDATE ... FROM or INSERT .. SELECT patterns if MERGE not available.

4. Use Matillion components to implement the SQL flow
   - Orchestration job: load source -> Table Input -> Table Output (staging)
   - Transformation job or SQL Script component: run the MERGE/UPDATE/INSERT
   - Use Matillion “Database Query”/“SQL Script” to run multi-statement SQL
   - Use Matillion’s visual components (Join, Calculator, Aggregator) when SQL expressions are simple

5. If you must use Python
   - Read full dataset into a single DataFrame (pandas.read_sql or Matillion’s Table Input to Python DataFrame).
   - Apply vectorized operations in pandas (no for-loops).
   - Write results back in bulk (to staging table), then run a single DB-side MERGE.
   - Avoid issuing per-row inserts/updates from Python.

6. Validate and measure
   - Compare outputs between old and new implementations (row counts, hashes, sample rows).
   - Use EXPLAIN/Query Profile to check performance of your set-based SQL.
   - Monitor Matillion job logs and DB query time to confirm improvements.

7. Governance and patterns to enforce
   - Code review: flag Python/row loops and insist on justification.
   - Templates: provide ready-made Matillion templates that stage and MERGE.
   - Doc and training: show common SQL idioms (MERGE, UPDATE...FROM, window functions) for ETL logic.
   - Automated tests: run small/full-data comparisons after refactor.

When to keep procedural code
- If algorithmic complexity cannot be expressed efficiently in SQL and data volumes are small, keep it in Python but vectorized.
- If DB lacks features and performance is acceptable, use DB-side UDF/stored proc called from Matillion.

Result
- Replacing row-by-row Python loops with set-based SQL reduces network chattiness, leverages DB parallelism, and improves scalability and maintainability.

[Top](#top)

## How do you cache and broadcast small reference datasets efficiently for joins in transformation jobs?
Short answer
- Stage the small reference dataset once (temporary/transient table or Matillion Lookup), then join to that copy. For Redshift specifically use DISTSTYLE ALL to replicate the table to all nodes. For Snowflake/BigQuery rely on the warehouse optimizer (or materialize a temp table/CTE) so the small set can be broadcast cheaply.

How to implement in Matillion (patterns and components)
1) Use a Lookup component for very small reference tables
- Matillion’s Lookup (Database Lookup) is intended for small reference sets and caches them in-memory for fast row-by-row lookups in a transformation. Use it for key/value enrichment where the lookup table is tiny.

2) Stage a temp/transient table in the target DB (recommended pattern)
- In an Orchestration or Transformation job: extract the reference dataset once, write it into a temporary/transient/staging table using components like Create Table / Database Query / Table Output / Bulk Load.
- Then use normal Join or SQL components to join your main dataset to that staged table.
- Clean up the temp table at the end.

Database-specific notes
- Redshift: CREATE TABLE ... DISTSTYLE ALL (or CREATE TEMP TABLE ... DISTSTYLE ALL) to replicate the small table to every slice; this avoids redistribution and gives true broadcast performance. Example:
  CREATE TEMP TABLE tmp_ref DISTSTYLE ALL AS SELECT ...;
  -- then join tmp_ref to your big table
- Snowflake: create a TEMP/TRANSIENT table or CTE to materialize the small set; Snowflake’s optimizer will typically broadcast small tables automatically. Example:
  CREATE TEMP TABLE tmp_ref AS SELECT ...;
- BigQuery: CREATE TEMP TABLE tmp_ref AS SELECT ...; BigQuery will prefer a broadcast (broadcast/hash join) for very small tables. Materializing as a temp table avoids repeatedly scanning a large source.

Practical tips
- Use a temp/transient table when the reference dataset is used multiple times in the same job to avoid re-reading and reprocessing it.
- Keep the reference set small; for Redshift replication costs can grow if the table is too large—use DISTSTYLE ALL only for truly small tables.
- Run ANALYZE (Redshift) or appropriate statistics collection if the warehouse requires it after loading the temp table so the optimizer can make the right plan.
- Drop temp tables after the job to avoid clutter and storage charges.

Example (Redshift, Matillion steps)
1. Orchestration job: Run Database Query component:
   CREATE TEMP TABLE tmp_ref DISTSTYLE ALL AS SELECT id, code FROM staging.ref_source;
2. Transformation job: Join component – join large table to tmp_ref.
3. Orchestration job: optionally run DROP TABLE tmp_ref (if not temp) or let the session-scoped temp table auto-drop.

This approach minimizes network shuffle and repeated reads, and leverages the target warehouse’s best mechanism for broadcasting small datasets.

[Top](#top)

## How do you handle skewed joins and repartitioning strategies in warehousing engines from Matillion SQL?
Start by framing the problem: find where the skew is (which table, which key, which values), then choose one of three basic approaches: co-locate data (avoid shuffles), broadcast/replicate the small side, or repartition/salt the large side so work is balanced. In Matillion you implement the solution by pushing engine-native SQL/DDL (CTAS, ALTER, hints) or using engine-specific components (Create Table, SQL Query, Python/Spark components for Databricks). Below are detection steps, a general decision flow, and concrete engine-specific tactics.

Detection and measurement
- Collect row counts by join key (group by key, count) to spot hot keys.
- Use the target warehouse’s query profile / explain plan (Matillion returns the query id so you can open the warehouse UI) to see data movement, skew across slices/nodes, and if a broadcast or repartition occurred.
- Check table stats (ANALYZE/SHOW STATS/INFORMATION_SCHEMA) and system tables (Redshift STL tables, Snowflake Query Profile, Spark UI) to quantify skew.

Decision flow
1. If small lookup table: prefer broadcast/replicate.
2. If both large and keys line up: co-locate via distribution/cluster keys.
3. If single hot-key(s) cause skew: use salting (hash buckets) or split the hot-key path.
4. If engine supports adaptive execution: enable it (Spark/AQE) and let runtime handle skew.

Engine-specific approaches (what you do inside Matillion SQL jobs)

Amazon Redshift
- Co-locate large tables: set the same DISTKEY on the join column (or use DISTSTYLE KEY). Use SORTKEY where appropriate to improve local joins.
  Example CTAS: CREATE TABLE t_dist AS SELECT ... DISTSTYLE KEY DISTKEY(join_col);
- Replicate small table: use DISTSTYLE ALL for small lookup tables to avoid network reshuffle.
- Salting for hot keys: add a salt column (0..N-1), populate with hash(join_col) % N on both sides, and join on (join_col, salt).
- Repartition workflow: rebuild tables with desired DISTKEY via CTAS to repartition data; run VACUUM and ANALYZE to refresh stats.
- Monitor skew with STL_ALL and SVV_TABLE_INFO.

Snowflake
- Snowflake has no user-controlled distribution; rely on micro-partitions and choose clustering keys to co-locate data for the join key: CREATE TABLE ... CLUSTER BY (join_col).
- For small-side broadcasting, use Snowflake query hints: /*+ BROADCAST(alias) */ to force broadcasting of a small table.
- Salting still works: add a salt column and join on (key, salt) to spread a hot-key over multiple partitions.
- Pre-aggregate or materialize intermediate results (temporary or transient tables) to reduce join volume.
- Use Query Profile to inspect skew and SYSTEM$CLUSTERING_INFORMATION to check clustering health.

Google BigQuery
- BigQuery chooses join strategy automatically; you cannot explicitly set distribution. Influence it by:
  - Partitioning and clustering tables on the join key to reduce scanned data and enable better locality.
  - Reducing the amount of data shuffled via pre-filtering or pre-aggregation (CTAS staging tables).
  - Using salting for skewed keys (create salted key and join on it).
- Monitor using the BigQuery Execution Details and slot utilization; rewrite queries to reduce shuffled bytes where possible.

Databricks / Spark SQL
- Prefer broadcast join for a small table: use the broadcast hint or API (SQL hint: /*+ BROADCAST(t_small) */ or programmatic: broadcast(df_small)).
- Explicit repartition to co-locate data: df.repartition(numPartitions, "joinCol") or repartitionByRange if appropriate.
- Enable AQE and skew handling: spark.sql.adaptive.enabled=true and spark.sql.adaptive.skewedJoin.enabled=true to let Spark split large skewed partitions.
- Salting: create salt and join on (key, salt) after repartitioning.
- Recreate bucketed tables (bucketing) or use sorted partitions where you can.
- Use Spark UI and the Matillion Databricks component to surface job/SQL diagnostics.

Implementation in Matillion
- Use the SQL Query / Create Table components to push CTAS, ALTER, CLUSTER, or DISTSTYLE DDL to the warehouse.
- Put ANALYZE/VACUUM or statistics-gathering statements in orchestration steps after CTAS to improve optimizer decisions.
- For Databricks, use Matillion’s Spark/Notebook components or Python components to set Spark configs (AQE, broadcast thresholds).
- For repeated repartition/salting patterns, parameterize the salt bucket count using Matillion variables and implement as a reusable transformation job.
- Capture the target query id in Matillion job logs (Query component returns id) and use the warehouse’s UI for deep profiling.

Practical patterns
- Broadcast small side: smallest overhead and fastest when one table is << memory threshold.
- Co-locate via dist/cluster key: best when both tables are large and stable on the same join key.
- Salting: use when a few hot keys dominate; pick salt buckets roughly equal to the number of compute slices/partitions.
- Materialize intermediate aggregates: often cheaper than full joins (CTAS aggregated staging tables).
- Iterate: change distribution/cluster, re-run workloads, and verify with query profiles.

Summary checklist to apply from Matillion SQL
- Profile to prove skew.
- Choose broadcast vs co-location vs salting.
- Implement engine-native DDL/hints via Matillion components (CTAS, CLUSTER BY, DISTSTYLE, SQL hints).
- Refresh stats and monitor profile; adjust bucket counts or repartitioning strategy as needed.

[Top](#top)

## How do you manage temporary and transient tables, schemas, and cleanup to control storage costs?
Key principles
- Minimize duplicate copies of data and the window they exist.
- Use the right object type (temporary vs transient vs permanent) per warehouse semantics and Matillion connection behavior.
- Automate deterministic cleanup (job end and scheduled housekeeping) and lifecycle for external storage (S3/GCS).
- Track what you create (naming, audit table or metadata) so orphaned objects can be found and removed.

Matillion-specific constraints to know up front
- Matillion components generally open separate DB sessions per component. That makes session-scoped TEMPORARY tables unreliable for multi-component jobs in many warehouses (notably Snowflake). Don’t rely on temp tables unless you explicitly control session reuse (rare).
- Use Matillion orchestration components (Execute SQL, Delete Table, File Delete, S3/GCS Delete) to create/drop staging objects and to remove files.

Recommended patterns implemented in Matillion
1) Use a dedicated staging schema
   - Create one schema per environment (dev/test/prod) and optionally per team or pipeline.
   - Put intermediate/transient objects there so IAM and lifecycle rules are easier to apply.

2) Prefer transient or short-retention tables (warehouse-specific)
   - Snowflake: use TRANSIENT tables or set DATA_RETENTION_TIME_IN_DAYS to the minimum acceptable. Transient avoids fail-safe and reduces time-travel storage.
   - Redshift: use CREATE TEMP TABLE only if the session is preserved; otherwise create staging tables and drop them. After deletes, run VACUUM/ANALYZE as needed to reclaim space.
   - BigQuery: use table expiration (set table expiration or default dataset expiration) or partition expiration; avoid long-lived full copies.
   - Synapse: use temporary tables or external tables depending on pattern, and remove external files with lifecycle rules.

3) Name / tag objects deterministically
   - Use environment variables and job variables to include job name, timestamp or UUID (e.g., staging.myjob_<env>_<yyyyMMddHHmmss>) so cleanup queries can identify age.
   - Tag or insert metadata rows into an audit/staging_metadata table at creation time to record owner, created_at, purpose.

4) Swap instead of copy where possible
   - Build result in a staging/transient table then swap/rename or use CREATE OR REPLACE / MERGE to replace the production table. That avoids maintaining two full copies for long.

5) Cleanup in-job (always) + scheduled cleanup (daily)
   - At job end, drop staging objects explicitly with Execute SQL / Drop Table components using IF EXISTS so jobs are idempotent.
   - Have a scheduled Matillion orchestration job that:
     - Queries INFORMATION_SCHEMA (or equivalent) to find staging objects older than a threshold and drops them.
     - Removes external staging files (S3/GCS) older than X hours (use S3 List + S3 Delete or cloud lifecycle policies).

6) External staging (S3/GCS) handling
   - Use cloud storage lifecycle rules to expire staging objects automatically.
   - In Matillion, use S3 List + S3 Delete (or GCS equivalents) as a final step or for emergency cleanup.
   - For Snowflake named stages, use REMOVE @stage after COPY INTO when you staged files.

Practical implementation steps in Matillion (example flow)
- Orchestration job variables: env, job_id (UUID), created_at.
- Create staging table using Execute SQL:
  - Snowflake: CREATE TRANSIENT TABLE staging.myjob_<id> AS SELECT ...;
  - BigQuery: CREATE TABLE dataset.staging_myjob_<id> OPTIONS(expiration_timestamp=TIMESTAMP_ADD(CURRENT_TIMESTAMP(), INTERVAL 1 HOUR)) AS SELECT ...;
- Do transformations in Transformation job reading from staging table.
- Publish final output with atomic swap:
  - CREATE OR REPLACE TABLE prod.mytable AS SELECT * FROM staging.myjob_<id>;
  OR
  - BEGIN; ALTER TABLE prod.mytable RENAME TO prod.mytable_old; ALTER TABLE staging.myjob_<id> RENAME TO prod.mytable; DROP TABLE prod.mytable_old; COMMIT;
- Drop staging table explicitly:
  - Execute SQL: DROP TABLE IF EXISTS staging.myjob_<id>;
- Delete any staged S3/GCS files using Matillion S3 Delete / GCS Delete components or rely on lifecycle rules.

Warehouse-specific notes
- Snowflake
  - Use TRANSIENT tables to avoid fail-safe overhead. Transient reduces long-term storage cost after drop.
  - Avoid TEMPORARY tables unless you can guarantee session reuse — Matillion typically will not.
  - Minimize DATA_RETENTION_TIME_IN_DAYS if business allows.
  - Use REMOVE @stage to purge stage files.
- Redshift
  - Deleting rows does not immediately free space; use VACUUM (or VACUUM FULL) or DROP/CREATE to reclaim storage.
  - Use temporary tables only if the same session is used; otherwise use staging schema + DROP.
- BigQuery
  - Use table expiration and partition expiration aggressively for staging data.
  - Prefer partitioned tables rather than multiple per-run copies.
- External object storage (S3/GCS)
  - Enforce lifecycle rules to auto-expire staging directories.
  - Use Matillion file-delete components for immediate cleanup when needed.

Automation and monitoring
- Audit table: log created staging objects and drops; scheduled job reconciles and removes or alerts on orphans.
- Housekeeping job: nightly/ hourly Matillion orchestration job that finds objects older than threshold and purges them.
- Alerts: failed cleanup should escalate; use Matillion notifications or external monitoring.
- Cost review: periodically run queries against INFORMATION_SCHEMA and cloud billing to validate the cleanup effectiveness.

Common anti-patterns to avoid
- Relying on TEMPORARY tables across Matillion components (session isolation).
- Keeping a copy of full dataset during promotion for long periods (avoid two full copies).
- Leaving staged files in S3/GCS without lifecycle policy.
- Not accounting for time-travel / retention settings that keep dropped data charged.

Short checklist to control storage costs in Matillion pipelines
- Use staging schema and deterministic names.
- Prefer transient/short-retention objects; set expirations where supported.
- Use atomic swaps or MERGE instead of long-lived copies.
- Explicitly drop staging objects in-job.
- Automate scheduled cleanup and use cloud storage lifecycle policies.
- Audit and monitor for orphans and unexpected growth.

[Top](#top)

## How do you structure medallion (bronze/silver/gold) layers and enforce contracts between layers?
Short answer
- Bronze: raw landing (immutable), keep source schema + metadata.
- Silver: cleansed, typed, deduped, conformed.
- Gold: business-ready aggregates/BI marts.
- Enforce contracts with explicit contract definitions (DDL + rules), automated validation jobs between layers, quarantining rejects, versioning contracts, and failing upstream jobs when checks fail. Implement all of the above using Matillion orchestration + transformation jobs, SQL checks, control tables, variables, and the Matillion job flow (If/Fail/Notify).

How I structure the layers (concrete)
- Bronze (raw)
  - One raw table per source (or per file type/partition), stored as-is.
  - Persist metadata columns: source_system, source_filename, raw_loaded_at, ingestion_id, partition_key.
  - Minimal processing: file to staging table, persist original types/text, no business logic.
  - Keep original unique keys and natural keys, no dedupe.
- Silver (cleaned, conformed)
  - Standardized types, validated columns, curated surrogate keys, deduplicated records, enriched lookups.
  - Implement referential validations here (report missing lookups), normalize and conform naming and data formats.
  - Store audit columns: row_inserted_at, row_source_ingestion_id, row_status (valid/rejected).
- Gold (marts/semantic layer)
  - Business aggregates, denormalized marts, star schemas or consumer-specific tables.
  - Materialized views, partitioning/clustering tuned for queries.
  - Strict schema and business rule enforcement.

How I define a contract
- Contract components:
  - DDL: expected schema (column names, types, nullability).
  - Semantics: primary keys/natural keys, surrogate key generation rules.
  - Data expectations: null thresholds per column, allowed value sets, ranges, freshness/watermark, uniqueness.
  - SLA: expected row counts or minimum sample rate, freshness deadline.
  - Version: contract version number and change log.
- Store contract definitions:
  - As SQL DDL files in Git alongside Matillion jobs.
  - Represent operational checks as rows in a control table (contract_id, version, expected_columns, thresholds, check_sql).

Enforcing contracts in Matillion (patterns)
- Orchestration entry-point
  - Ingest to Bronze with an orchestration job (S3/GCS/Azure load, create table, copy).
  - After load, call a contract-validation orchestration job that runs a sequence of checks.
- Implement checks with Matillion building blocks
  - Use Run SQL / Execute Query components to run metadata queries (information_schema) and data checks (counts, null %, duplicates).
  - Use If/Else or Branch components with variables to evaluate check results.
  - On failure use Fail Job or raise an exception (or write to a rejection audit table and notify).
  - Use Send Email/Slack components to alert and capture context.
- Typical checks to implement
  - Schema presence: compare expected column list to information_schema.columns.
  - Type compatibility: check ability to cast or use TRY_CAST; detect incompatible types.
  - Null thresholds: SELECT COUNT(*) WHERE col IS NULL / total > threshold.
  - Uniqueness: SELECT key FROM table GROUP BY key HAVING COUNT(*) > 1 LIMIT 1.
  - Referential integrity: LEFT JOIN to lookup to find orphaned keys; if > threshold then fail.
  - Freshness: SELECT MAX(updated_at) and compare to expected watermark.
  - Row count sanity: compare to expected min/max or to prior run using a delta threshold.
- Example SQL snippets (pseudo)
  - Schema check:
    SELECT column_name FROM information_schema.columns WHERE table_name='bronze_table';
    Compare result set to expected columns stored in control table.
  - Null pct check:
    SELECT SUM(CASE WHEN col IS NULL THEN 1 ELSE 0 END)::float / COUNT(*) FROM bronze_table;
  - Uniqueness:
    SELECT COUNT(*) FROM (SELECT natural_key, COUNT(*) AS c FROM bronze_table GROUP BY natural_key HAVING COUNT(*)>1) x;
- Automate branching
  - If all checks pass -> trigger transformation job (bronze->silver).
  - If some checks fail -> move offending rows to reject/quarantine table, write DQ results to a monitoring table, then Fail or Pause pipeline depending on severity.

Quarantine and partial acceptance
- Don’t block entire dataset for small anomalies.
  - Route bad rows into a rejects table (include reason code), continue processing valid rows.
  - For contract-breaking schema changes (missing column or type incompatible), treat as hard-fail and stop until contract is updated.
- Store rejects with source metadata to simplify troubleshooting and replay.

Contract versioning and change management
- Keep contract DDLs and validation SQL in Git; increment version on breaking changes.
- Include contract_version as a Matillion variable passed to jobs.
- Before deploy, run CI tests that validate migrations against sample bronze files and contract checks.
- Record applied contract_version in an ingestion audit table; if an incoming source declares a newer contract version than expected, fail and require review.

Operationalization and observability
- Maintain a DQ results table: run_id, table, check_name, status, metric (value), threshold, message.
- Surface DQ results in an operational dashboard (Looker/Tableau/QuickSight).
- Use Matillion job metadata and notifications for run history and failures.
- Keep audit rows in every layer (source_ingestion_id, batch_id, run_id, loaded_at).

Warehouse specifics and limitations
- Use native warehouse DDL where possible (CREATE TABLE with column types, NOT NULL). Note some warehouses (Snowflake) don’t strictly enforce foreign keys/unique constraints—so you must enforce in SQL checks.
- For performance, push checks into SQL (set-based) rather than row-by-row Matillion logic.
- Use clustering/partitioning for large tables (Gold) to make checks and transforms efficient.

CI/CD, testing and governance
- Unit test transformation jobs against sample datasets in dev.
- Run contract validation jobs in CI pipeline before promoting jobs to higher environments.
- Use Matillion Git integration and export job artifacts (and contract SQL) for review.
- Maintain changelog and owner for each contract.

Summary of practical implementation in Matillion
1. Bronze ingestion orchestration job: load raw, insert audit row, call contract-validation job.
2. Contract-validation orchestration: run metadata/data checks via SQL, write DQ results to control table, If passes -> call silver transformation; If severe fail -> Fail/Notify; If partial -> write rejects and continue.
3. Silver transformation job: consume validated bronze rows, produce conformed tables with audit columns and contract_version.
4. Gold jobs: build aggregates from silver; enforce stricter business rules and tests before exposing to BI.
5. Governance: contract files in Git, contract versions tracked in control table, CI runs validation before deploy.

This approach keeps bronze immutable, enforces clear contracts between stages, automates gating and notifications in Matillion, and provides traceability for changes and failures.

[Top](#top)

## How do you manage CDC with Matillion Data Loader/CDC Agent for sources like MySQL, Postgres, and SQL Server?
Summary architecture
- Matillion Data Loader provides CDC by running an on‑prem/edge CDC Agent (Debezium-based) inside your network to read database change logs, stream changes to Matillion’s cloud service, and apply them into the target data warehouse. Typical flow: initial snapshot (full load) → ongoing change stream (binlog/WAL/transaction log) → Matillion processes and writes inserts/updates/deletes into the target.
- Use the CDC Agent when your source is behind a firewall or not directly reachable from Matillion Data Loader.

Key concepts you must manage
- Initial snapshot vs streaming-only: initial snapshot captures existing rows; streaming then captures changes. Choose timing and approach to avoid locking/impact.
- Offsets & replication slots: the agent stores progress (offsets) so it can resume where it left off. For Postgres/MySQL you’ll create replication slots / binlog offsets; for SQL Server CDC, the agent tracks CDC log positions.
- Schema evolution: Debezium/Matillion handle many add-column scenarios automatically, but renames/drops often need manual mapping/ETL changes.
- Primary keys: CDC needs a way to identify rows. Tables should have stable primary keys; lacking a PK complicates upserts and delete handling.

Per-source requirements and common settings

MySQL
- Use row-based binlog: set binlog_format=ROW and binlog_row_image=FULL.
- Enable binary logging and ensure server_id is unique among replication clients.
- Configure retention long enough so agent can catch up (expire_logs_days / binlog_expire_logs_seconds).
- Create a replication user with REPLICATION SLAVE and REPLICATION CLIENT privileges (plus SELECT on DBs if snapshot required).
- Ensure time zone and character set consistency.
- Agent notes: Debezium reads the MySQL binlog. If you need minimal impact, consider doing an out-of-band initial snapshot for very large tables.

PostgreSQL
- Enable logical decoding: set wal_level=logical.
- Increase max_replication_slots and max_wal_senders as needed.
- Install/choose logical decoding output plugin supported by the agent (pgoutput or wal2json; confirm Matillion-supported plugin/version).
- Create a replication role with REPLICATION privilege and replication slot permissions; allow replication connections from the agent host.
- Ensure WAL retention settings are sufficient (so WAL segments are not removed before agent reads them).
- Be careful with RDS/Aurora: you must follow vendor-specific ways to enable logical replication and use supported plugins.

SQL Server
- Use SQL Server’s CDC feature (SQL Server 2016+ for full Debezium support) or enable transaction log access as required by the connector.
- Enable CDC at the database and table levels (sys.sp_cdc_enable_db and sys.sp_cdc_enable_table).
- Create a user with appropriate permissions (often db_owner or specific CDC permissions).
- Configure retention of CDC change tables and log retention so the agent can catch up after outages.
- For AlwaysOn/replicas, ensure agent connects to the correct node and that CDC is supported on that topology.

CDC Agent deployment & configuration
- Deploy the CDC Agent inside the network where the source DBs are reachable (Docker container, VM image provided by Matillion).
- Configure connectivity: DB host/port, credentials, replication slot or CDC enablement, and the agent’s connection to Matillion Data Loader (agent registers with your Data Loader workspace).
- Configure each connector in the agent with the tables to capture, snapshot mode (initial, schema-only, none), and transformations/mappings if supported.
- The agent maintains offsets and schema history locally; back up agent config and monitor agent logs.
- Secure the agent: use TLS for agent-to-Matillion communications, follow credential rotation, and run agent under least-privilege accounts.

Operational best practices
- Preflight: verify DB settings (binlog/wal_level/CDC enabled), replication user permissions and network connectivity before starting.
- Retention: increase binlog/WAL/CDC retention so temporary outages don’t cause data gaps.
- Stagger initial snapshots for large tables or take an out-of-band bulk load if snapshotting would cause performance issues.
- Monitoring: watch agent health, lag metrics, and Matillion Data Loader ingestion rates. Track offsets and replication slot usage.
- Schema change policy: document how you’ll handle adds vs renames/drops. Automate mapping updates where safe; otherwise, schedule maintenance windows.
- Capacity planning: CDC generates additional I/O on source DBs; plan for resource usage and tune batch sizes/polling intervals.

Troubleshooting common issues
- Agent can’t connect: check firewall, network routes, TLS, and DB host binding. For cloud DBs, ensure public/private endpoint and security groups/VPC rules.
- Missing events / gaps: usually due to insufficient binlog/WAL retention or replication slot deletion. Increase retention and inspect DB logs.
- Permission errors: ensure replication user has REPLICATION privileges (MySQL/Postgres) or CDC/db_owner rights (SQL Server).
- Snapshot failures or long-running snapshots: offload full loads to a controlled bulk load process, or snapshot smaller chunks.
- Schema drift: check agent logs for schema-change events; reconcile Matillion mappings if columns renamed/dropped.

Limitations and gotchas
- Not all schema changes are automatic; renames and complex type changes require manual handling.
- Tables without stable PKs are problematic for deletes/upserts.
- Latency is near real-time but depends on network, agent performance, and DB load.
- Agent version compatibility matters — match Matillion Data Loader docs and Debezium/connector versions.
- Cloud-managed DBs (RDS, Aurora, Azure) have vendor-specific requirements to enable logical replication or CDC; follow vendor docs.

Security and compliance
- Keep the CDC Agent inside the customer network; encrypt agent-to-Matillion traffic.
- Use minimum required DB privileges and rotate credentials.
- Audit and log agent activity; be mindful of PII exposure in change streams.

When to use CDC Agent vs other approaches
- Use CDC Agent when you need low-latency streaming from databases behind your firewall or when log-based capture is required to minimize source impact.
- For one-off bulk loads or sources without reliable transaction logs, use batch extracts instead of CDC.

Short checklist to get started
1. Confirm Matillion Data Loader subscription and enable CDC in workspace.
2. Deploy CDC Agent in network reachable to source DBs.
3. Prepare DB: enable binlog/WAL/CDC settings, create replication user, increase retention/slots.
4. Configure connectors in the agent: snapshot mode, tables, mapping.
5. Run initial snapshot (or do separate bulk load), then enable streaming.
6. Monitor agent health, lag, and schema events; adjust retention and resources as needed.

[Top](#top)

## How do you configure CDC agents, secure network access, and handle initial snapshots vs ongoing replication?
Configure CDC agents
- Deployment options
  - Run the Matillion CDC agent inside your source network (VM, container, Kubernetes, or dedicated EC2/GCE/Azure VM). Agents must be able to reach the source database and outbound to Matillion’s controller endpoints (HTTPS).
  - Use a single agent per network segment/VPC or multiple agents for scale/high-availability; each agent registers to Matillion with a token.

- Installation & registration
  - Download the agent package from Matillion UI (or repo), install on the chosen host, start the agent service and register it with the Matillion instance using the registration token (displayed in the Matillion CDC area).
  - Configure agent runtime parameters (proxy, TLS, memory/cpu) as required for your environment.

- Database prerequisites & permissions (examples)
  - PostgreSQL: wal_level=logical, max_replication_slots and max_wal_senders set high enough; create a logical replication user with REPLICATION privileges; agent uses a replication slot or Matillion creates one.
  - MySQL/MariaDB: binlog enabled, binlog_format=ROW, server_id unique, log_slave_updates if needed; grant replication privileges to the agent user.
  - SQL Server: enable database CDC or configure transaction log read permissions for the agent/service account.
  - Oracle: enable supplemental logging or use supported capture mechanism per Matillion documentation.
  - Ensure the agent user has the minimum required privileges for logical replication/log read and for any snapshot exports.

- Matillion side
  - In Matillion create a CDC configuration (select agent, supply source credentials, choose tables, schema mappings and target staging settings). Configure staging (S3/GCS/Azure Blob) and target warehouse credentials for bulk snapshot load and ongoing apply.

Secure network access
- Agent placement and isolation
  - Run agents inside the customer VPC/VNet (never enable DB public access). Use private subnets and bastion/VPN for admin access.
- Firewall & security groups
  - Allow inbound DB access only from agent host(s) on the DB port.
  - Allow agent outbound HTTPS (port 443) to Matillion controller endpoints and outbound access to cloud storage endpoints and data warehouse endpoints for staging/loads.
- Fixed egress / IP allow-lists
  - If Matillion or target services require allow-listing, provide the agent’s static egress IP (NAT gateway, NAT instance, or firewall) or use AWS/GCP/Azure egress NAT to guarantee fixed IPs.
- Private connectivity options
  - Prefer VPC peering, Transit Gateway, PrivateLink, Cloud Interconnect/Peering or VPN between Matillion and your cloud environment when supported. For Snowflake/Redshift/BigQuery use their private connectivity options.
- Encryption & authentication
  - Use TLS for all agent-to-controller and agent-to-database connections.
  - Store credentials/tokens in Matillion credential manager or integrate with Secrets Manager (AWS Secrets Manager / GCP Secret Manager / Azure Key Vault).
  - Use IAM roles for cloud storage and warehouse access rather than long-lived keys where possible.
- Least privilege & rotation
  - Grant replication and storage privileges only to the agent’s accounts and enforce credential rotation and strong passwords/keys.
- Monitoring & auditing
  - Log agent activity to central logging, monitor replication lag and failures, and audit access to secrets and agent registration tokens.

Initial snapshot vs ongoing replication (how to handle them safely)
- Two phases
  - Initial snapshot (baseline): capture a consistent full image of the selected tables into the target.
  - Ongoing replication: stream changes from the database transaction log (binlog/WAL/transaction log) and apply them to the target continuously.

- Ensuring no gaps or duplication
  - Start the change capture mechanism (create replication slot or enable binlog position capture) before or as part of the snapshot operation so the agent records the log position (LSN/binlog coordinate) at the time the snapshot started. This ensures all changes after the snapshot are captured.
  - Common pattern:
    1. Agent registers a replication slot or records current log coordinate.
    2. Agent takes the consistent snapshot/export using a method that’s consistent with the recorded log position.
    3. Snapshot is loaded to staging/target.
    4. Agent replays changes from the recorded coordinate forward and applies them on top of the snapshot (ordering by sequence).
  - For MySQL use mysqldump --master-data or equivalent; for PostgreSQL use a consistent dump that records LSN or leverage logical replication snapshot features.

- Large data sets / zero-downtime strategies
  - Use parallelized bulk export into cloud storage (S3/GCS/Azure Blob) for the initial snapshot to avoid long locks.
  - Capture changes during the bulk export and apply them after the bulk load (or stream-applied concurrently if agent supports ordering guarantees).
  - For very large tables consider table-level reinitialization or phased load (load historical partitions first then switch to real-time for recent partitions).

- Idempotency and ordering on target
  - Apply changes as upserts using primary keys and include ordering columns (LSN/SCN/log sequence number/timestamp) so repeated records or out-of-order events do not corrupt the result.
  - Handle deletes explicitly (tombstone handling) and ensure soft-delete vs hard-delete semantics are agreed.

- Schema changes
  - Decide whether to quiesce DDL during snapshot or allow DDL capture. If DDL is frequent, enable DDL capture and test how Matillion maps/propagates changes; otherwise schedule snapshots during maintenance windows.
  - For breaking schema changes, reinitialization of affected tables may be required.

- Checkpointing, failures & resync
  - Agents persist offsets/positions back to Matillion so on restart they resume from the last applied position.
  - If corruption or missed changes occur, re-run snapshot for impacted tables (or perform selective re-sync/backfill).
  - Monitor lag and set alerts for stalled agents or replication gaps.

Best-practice checklist
- Validate DB settings (logical replication/binlog/CDC enabled) and ensure the agent account has minimal replication privileges.
- Place agents in a private subnet with least network exposure; use fixed egress IPs when allow-lists are needed.
- Use staging (S3/GCS/Azure) for initial snapshots, and use IAM roles instead of static keys.
- Start replication capture before taking snapshot; use LSN/binlog coordinates to guarantee no gaps.
- Implement idempotent upserts with ordering columns on the target and monitor replication health and lag.
- Test snapshot+replication in a dev environment and document re-sync procedures.

Key point: run the CDC agent inside your network, enable DB-level log-based capture, record log position at snapshot time, load the snapshot to staging/target, then apply log changes continuously with idempotent upserts and strict access controls.

[Top](#top)

## How do you apply CDC changes to targets with MERGE, resolve out-of-order events, and handle schema changes?
High-level approach
- Ingest CDC events into a landing/staging area (raw format: JSON/Avro/CSV) preserving transaction metadata (LSN/commit_ts, tx_id, change_seq, op type, pk values).
- Canonicalize and deduplicate ordering-sensitive events in a transformation step (row_number()/LAST_VALUE over pk ordering by LSN/commit_ts/tx_seq).
- Apply to the target using an idempotent MERGE/UPSERT that only applies an event if its sequence (LSN/commit_ts/tx_seq) is newer than what was last applied for that row.
- Handle schema evolution by detecting changes in the landing stream, applying safe DDL (ALTER ADD columns, casting/backfills, or storing unknowns in a variant/json column), and keeping an audit/raw copy.

Applying CDC with MERGE — pattern and SQL template
1) Add a last-applied-sequence column to the target (e.g., last_lsn or last_commit_ts).
2) Stage incoming changes and deduplicate so you have at most one change per target PK per apply batch (pick the highest sequence for each PK).
3) MERGE using the deduped source and check sequence > target.last_lsn to avoid re-applying older events.

Example canonical SQL pattern (generic — adapt to Snowflake/Redshift/BigQuery syntax):
- Source dedupe CTE:
  WITH source_dedupe AS (
    SELECT *
    FROM (
      SELECT *, ROW_NUMBER() OVER (PARTITION BY pk_col ORDER BY lsn DESC, txn_seq DESC) rn
      FROM staging_table
    ) WHERE rn = 1
  )

- MERGE:
  MERGE INTO target_table t
  USING source_dedupe s
    ON t.pk_col = s.pk_col
  WHEN MATCHED AND s.op = 'D' AND s.lsn > t.last_lsn
    THEN DELETE
  WHEN MATCHED AND s.op <> 'D' AND s.lsn > t.last_lsn
    THEN UPDATE SET
      col1 = s.col1,
      col2 = s.col2,
      last_lsn = s.lsn
  WHEN NOT MATCHED AND s.op <> 'D'
    THEN INSERT (pk_col, col1, col2, last_lsn)
         VALUES (s.pk_col, s.col1, s.col2, s.lsn);

Key points in that template:
- Use row_number() (or equivalent) to remove duplicates per batch and pick latest event per PK.
- Use an explicit comparison (s.lsn > t.last_lsn) so older/delayed events do not overwrite newer state.
- Treat deletes as first-class operations (either delete or set a tombstone flag) based on retention/soft-delete policies.
- Persist last_applied sequence per row for idempotence and ordering.

Resolving out-of-order events
- Rely on a stable sequence: LSN, commit_timestamp, or (tx_id, change_seq). Order by that value when deduping and when deciding whether to apply.
- Maintain last_applied_lsn on target and only apply incoming events with a greater sequence.
- For late-arriving newer events (higher LSN) simply re-apply: MERGE is idempotent because of the last_lsn check.
- For late-arriving older events, drop them (lsn <= last_lsn) or send them to an audit/repair queue.
- For concurrent changes within the same transaction, use tx_id and change_seq to preserve their intra-transaction order.
- If strict global ordering is required across partitions/streams, use a re-sequencer stage keyed by pk that buffers until commit_ts is safe (increases latency) or rely on source DB guarantees + LSN.

Handling schema changes
- Capture schema metadata in landing files (with record envelopes) or use a schema registry. Keep raw events unchanged for replay.
- Common options:
  - Auto-ALTER: detect new columns in incoming payloads and run ALTER TABLE ADD COLUMN before merging. Populate new columns with NULL/defaults; then backfill if needed.
  - Flexible storage: write raw events into a variant/JSON column (or data lake raw layer) and parse selected fields into relational columns. Use this when schema evolves quickly.
  - Controlled migrations for destructive changes: renames and type-narrowing should be done explicitly (add new column, backfill, switch consumers, drop old column).
- Practical Matillion pattern:
  - Landing (raw) job writes full envelope.
  - Orchestration job inspects schema for new fields (compare incoming schema to target metadata).
  - If new fields exist, execute ALTER TABLE ADD for the target (SQL component) or add to mapping pipeline.
  - Transformation job maps fields to target and runs MERGE.
- Type changes: coerce/cast values during transform; for incompatible narrowing, add new column and migrate in steps to avoid data loss.
- Column renames: treat as add + backfill + retire old column; maintain mapping metadata for downstream consumers.
- Keep raw audit history so you can re-run transforms after schema changes.

Operational best practices
- Keep a raw immutable landing zone for replays and audits.
- Persist last_applied sequence per row and keep CDC metadata (tx_id, lsn, commit_ts) with each applied row.
- Small, frequent merge batches to reduce contention and make retries simpler.
- Keep an audit/failure queue for events that cannot be applied (schema mismatch, older-than-last_lsn, validation failure).
- Automate schema-detection and DDL when safe, but review or gate breaking changes manually.
- Test reconcilers that compare source row counts/checksums against target periodically.

Behavior for specific targets
- Snowflake: MERGE is supported; use VARIANT for flexible columns or ALTER TABLE ADD COLUMN; maintain clustering if needed.
- Redshift: MERGE support exists; consider VACUUM/ANALYZE and distribution keys when large merges occur.
- BigQuery: MERGE supported; ALTER TABLE ADD COLUMN is straightforward; you can store evolving payloads in STRUCT/JSON.

Summary
- Use a staged dedupe-and-order step keyed by pk + LSN/commit_ts/tx_seq.
- Use a MERGE that checks incoming sequence > target.last_applied_sequence so out-of-order older events are ignored.
- Keep a raw event store and a strategy for schema evolution (ALTER for additive changes, JSON/variant for flexible fields, controlled migrations for renames/type changes).

[Top](#top)

## How do you detect CDC lag, backpressure, and recover from agent restarts or network partitions?
Short answer: treat CDC as a streaming pipeline—monitor offsets/LSNs and queue depth, watch processing latency and staging/backlog, and design for durable checkpoints and buffering so agents can restart and catch up without data loss. Below are detection signals, how to act, and recovery/playbook steps tuned to Matillion CDC deployments.

Detection — what to monitor and where to look
- Source-position vs consumer-position (the authoritative lag metric)
  - Track source change position (binlog position, Postgres LSN, SQL Server change version) and the agent/connector’s last-processed position. Lag = source position − consumer position (or time since last processed change).
  - Where to surface it: Matillion job/component state, agent logs/metrics, or external monitoring that polls source DB positions.
- Time-based latency
  - “Time since last event processed” per table or stream. Alert if it exceeds SLA (e.g., > 5 min).
  - Compare event generation timestamp vs ingestion timestamp.
- Queue/backlog indicators (backpressure)
  - Staging storage build-up: S3/GCS prefixes or files waiting for load.
  - Message queue lag: Kafka consumer lag, Kinesis iterator age, SQS queue size.
  - Matillion job queue: many outstanding orchestration/load jobs or growing run times.
  - Resource saturation: agent CPU, memory, disk I/O, or write throughput to the warehouse slowing.
- Errors / retries
  - Increasing connector retries, write timeouts, HTTP/DB errors in agent logs.
  - Heartbeat or health-check failures from the Matillion CDC agent (agent marked offline or not responding).
- Operational signals for agent/network problems
  - Missing heartbeat, agent process down (systemd/container not running), repeated connection errors in Matillion job logs, last-success timestamp older than threshold.

How to detect in practice (Matillion-specific points)
- Use Matillion Monitor and Job History to see last-run and error logs for CDC orchestration jobs.
- Check the CDC Agent health/heartbeat in the Matillion UI (agents shown as online/offline) and agent logs on the host for exceptions.
- Instrument source DB replication metrics (binlog lag, WAL retention) in CloudWatch/Prometheus/Datadog and alert on thresholds.
- Monitor staging (S3/GCS) with bucket/object metrics and warehouse load job success rates/latencies.

Immediate mitigation steps for backpressure/lag
- Pause or throttle upstream change generation if possible (application-side throttling).
- Reduce batch/transaction size and increase parallelism for loader jobs (careful with warehouse concurrency).
- Offload writes to scalable staging (S3/GCS) and make loads more parallel (smaller, concurrent COPYs).
- Temporarily prioritize critical tables and run catch-up jobs for high-priority data only.
- Scale the Matillion environment: add more worker nodes, increase instance size for the agent host, or scale Kafka/queue consumers.

Recovery from agent restarts and network partitions
- Persistent checkpoints
  - Matillion CDC agents/components persist processing position (offset/LSN). After a planned or unplanned restart they should resume from the last committed checkpoint. Confirm offset persistence in your agent configuration and logs.
- Restart workflow
  - Verify agent service is running (systemctl/docker restart) and agent has network access to source/Matillion cloud.
  - Check agent logs for errors and last processed offset. Validate agent resumes processing and begins catching up.
- Handling network partition where WAL/binlog retention may expire
  - If source logs are still available: agent will catch up automatically once connectivity is restored.
  - If logs expired during the outage: you must reinitialize the CDC snapshot for affected tables (full reload / snapshot) and re-establish CDC state. Plan this step into runbooks.
- Durable buffering
  - Architect pipelines so the agent can buffer changes to durable storage (local disk, S3, Kafka) during transient network problems. This gives time to restore connectivity without losing change data.
- Idempotency and deduplication
  - Ensure load steps are idempotent (upserts or dedupe keys) so retries and replays do not corrupt target state during catch-up.
- Re-processing backlog
  - If backlogged events are large, create dedicated catch-up orchestrations: increase commit throughput, scale workers, or temporarily increase warehouse resources to drain backlog faster.
- When automated resume is insufficient
  - Run a controlled full refresh of the affected tables into staging and swap over (truncate+copy or staging->replace) after verifying consistency.

Operational best practices to prevent and shorten outages
- Instrument and alert:
  - Alert on consumer lag, time-since-last-event, staging backlog size, agent offline, and rising error rates.
- Retention planning:
  - Set source DB WAL/binlog retention to cover worst-case outage + recovery window.
- Durable checkpoints and buffering:
  - Use a durable queue or object store between agent and loader; ensure agent persists offsets across restarts.
- Capacity and scaling:
  - Right-size agent hosts and warehouse load concurrency; autoscale where feasible.
- Runbooks and automation:
  - Have scripted procedures to restart agents, check offsets, trigger snapshot reloads, and run catch-up jobs.
- Test recovery:
  - Periodically simulate agent downtime and exercise the full recovery path (resume from offset, replay, and full reload if logs expired).

Example quick runbook (incident flow)
1. Detect: alert on CDC lag > threshold or agent offline.
2. Triage: check Matillion UI job history, agent health, source binlog/LSN, staging backlog.
3. Fix connectivity/agent: restart agent service, check network routes/security groups; confirm agent has last-offset and resumes.
4. If agent resumes and WAL present: monitor catch-up until lag under SLA.
5. If WAL expired or agent lost state: schedule a full snapshot for affected tables and perform controlled reload; validate data.
6. Post-mortem: adjust retention, scaling, and alerts to prevent recurrence.

Keep detection tight around offsets/LSNs, backlog size, and processing latency. Design the pipeline for durable checkpoints and buffering so restarts and partitions are survivable; have clear runbooks to reinitialize CDC when log retention is exceeded.

[Top](#top)

## How do you compare Matillion CDC to vendor tools (Fivetran, Debezium, StreamSets) for your requirements?
Short answer: pick Matillion CDC when you already run Matillion for ELT and want a tightly integrated, lower‑ops CDC path into cloud warehouses; pick Fivetran for a fully managed, wide‑connector, zero‑ops SaaS experience; pick Debezium when you need open‑source, Kafka‑centric, highly customizable low‑latency streaming; pick StreamSets when you need flexible DataOps/pipeline control and complex hybrid/transform logic in transit.

Comparison by dimension

- Architecture / deployment
  - Matillion CDC: integrated into the Matillion ecosystem (ELT/orchestration). Cloud‑oriented, intended to feed cloud DWHs and Matillion jobs.
  - Fivetran: SaaS, fully managed connectors and replication.
  - Debezium: open‑source, runs as Kafka Connect source connectors (you manage Kafka/connect cluster).
  - StreamSets: pipeline platform (collector/transformer), can run on-prem or cloud; more hands‑on.

- CDC method & latency
  - Matillion CDC: typically log‑based CDC for supported DBs with continuous replication; low to near‑real‑time, tuned for ELT cadence.
  - Fivetran: log‑based where supported, near‑real‑time to minutes; optimized for simplicity.
  - Debezium: log‑based, sub‑second to seconds latency (Kafka streaming).
  - StreamSets: supports log and query CDC patterns; latency depends on pipeline design.

- Supported sources & targets
  - Matillion CDC: focused on common OLTP DBs and cloud DWs; best fit when target is Snowflake/Redshift/BigQuery and you use Matillion for transforms.
  - Fivetran: very broad SaaS and DB connector catalog and many DW targets.
  - Debezium: supports major DBs (MySQL, Postgres, SQL Server, MongoDB, Oracle via connectors) but requires Kafka plumbing; targeting streaming consumers.
  - StreamSets: broad connectivity and custom processors; good for hybrid environments.

- Transformation and workflow integration
  - Matillion CDC: strong because it feeds directly into Matillion jobs; simpler handoff to ELT and orchestration.
  - Fivetran: minimal in‑flight transforms; assumes ELT post-load.
  - Debezium: no built‑in ELT — integrate with stream processors or sink into DW then transform.
  - StreamSets: supports transformations in pipeline (schema mapping, masking, enrichment), useful when you need in‑flight logic.

- Schema evolution & DDL handling
  - Matillion CDC: handles DDL changes in supported sources and maps into Matillion pipeline models (depends on connector coverage).
  - Fivetran: automatic schema evolution for most connectors.
  - Debezium: emits schema change events; you control how to apply them to sinks.
  - StreamSets: explicit pipeline logic to react to schema changes; flexible but manual.

- Operational overhead & monitoring
  - Matillion CDC: lower overhead if you already run Matillion; monitoring integrated into Matillion UI.
  - Fivetran: minimal ops; managed monitoring/alerts.
  - Debezium: higher ops (Kafka, offsets, broker tuning) but fine‑grained control.
  - StreamSets: moderate ops; good observability for pipelines but you manage runtime.

- Cost model
  - Matillion CDC: typically license/subscription within Matillion offerings — economical if consolidating tools.
  - Fivetran: pay‑per‑usage (rows/volume) can be expensive at scale.
  - Debezium: open‑source software cost (infrastructure, SRE time).
  - StreamSets: enterprise license; cost reflects features/scale.

- When each is the right fit
  - Matillion CDC: you use Matillion ETL/Orchestration, target cloud DWs, want integrated CDC with minimal additional tooling, moderate customization needs.
  - Fivetran: want fastest path to replicate many SaaS/DB sources with zero ops and automatic schema handling.
  - Debezium: require event streaming architecture, sub‑second latency, full control, and have Kafka expertise.
  - StreamSets: need rich pipeline logic, hybrid on‑prem + cloud flows, data quality / masking in transit, and enterprise DataOps.

Practical tradeoffs for requirements
- If priority = minimal ops + many SaaS connectors → Fivetran.
- If priority = tight integration with Matillion ELT, unified orchestration, moderate connector set → Matillion CDC.
- If priority = low‑latency streaming and custom processing, and you can run Kafka → Debezium.
- If priority = complex pipelines, in‑flight transforms and hybrid sources → StreamSets.

Follow‑ups I need to recommend decisively: which sources (DBs/SaaS), target DW, expected throughput (rows/sec/day), latency SLO, budget model, and team skillset (SRE/Kafka experience or preference for managed SaaS).

[Top](#top)

## How do you design near-real-time pipelines with CDC feeding warehouse tasks and downstream transformations?
High-level goal: capture row-level changes from OLTP sources and make them visible in the cloud warehouse within seconds-to-minutes, then apply deterministic downstream transforms (e.g., SCD Type 2, aggregation marts) in a robust, idempotent way. Design centers on reliable capture, low-latency landing, deterministic application (MERGE/upsert), small micro-batches or event-driven triggers, and observability.

Recommended architecture (typical, vendor-neutral)
- Source DB -> CDC capture (Debezium / vendor CDC / cloud change-stream)  
- Change stream -> message bus or connector (Kafka, Kinesis, Pub/Sub) or direct connector -> short-lived cloud storage (S3/GCS) or streaming ingest endpoint  
- Warehouse ingestion layer: streaming ingestion or micro-batch auto-ingest (Snowpipe, BigQuery Streaming/Datastream, Redshift Streaming COPY patterns) into raw CDC staging tables (raw-change records with op, ts, txid, source metadata)  
- Matillion orchestration jobs to: 1) detect/claim new change batches, 2) run deterministic merge/upsert in the warehouse into curated staging/landing tables, 3) run downstream transformation jobs (SCD, facts, aggregates)  
- Monitoring, error handling, DLQ, schema-evolution handling, and backfill controls

Detailed design and Matillion role

1) CDC capture and message transport
- Capture low-level changes including operation type (I/U/D), primary key, changed columns, commit timestamp, and transaction ordering metadata (LSN/txid).  
- Use a connector that preserves ordering where required or expose transaction boundaries. If using Kafka, rely on partitioning by primary key to preserve order for that key.

2) Landing/raw staging in the warehouse
- Always land raw CDC messages in a raw schema/table (or files) exactly as produced (JSON/AVRO). Include metadata: source, partition/offset, op, commit_ts, txid.  
- Partition/stage by ingestion_time to make micro-batch scans efficient. Keep raw data immutable to support replays/backfills.

3) Micro-batch vs event-driven
- Micro-batch: schedule Matillion orchestration jobs to run frequently (30s–5m depending on SLA). Each run claims the next batch(s) from the staging layer and processes them. Simpler and often easier to scale/cost-manage.  
- Event-driven: trigger Matillion orchestration via REST/webhook/Lambda when new files arrive or when Snowpipe notification arrives. Useful for lower latency (<1m) but requires robust dedupe and concurrency control.

4) Matillion orchestration patterns
- Use a small “CDC ORCHESTRATION” job that:
  - Reads batch boundaries (new file list, MAX(ingest_ts) since last watermark, or Kafka offset ranges tracked externally).  
  - Sets Matillion variables (batch_id, watermark, file list, offsets).  
  - Invokes a transformation job (or SQL steps) passing those variables. Matillion jobs can be invoked via the API or nested job components.
- Use a separate “CDC APPLY” transformation job that:
  - Loads batch data into a warehouse staging table (if not already landed by Snowpipe). Use Matillion bulk load/Copy components or SQL insert from staged files.  
  - Deduplicates by (pk, txid, sequence) to keep last change per key per batch.  
  - Executes an idempotent MERGE/UPSERT into the target table using operation semantics (INSERT/UPDATE/DELETE) and change metadata. Use single MERGE statements if supported for performance.
  - Updates watermark/offset checkpoint table atomically after successful MERGE.

5) CDC semantics and implementation details
- Idempotency: design MERGE statements so reprocessing the same change is safe. Use commit_ts or version column to ensure newer records win.  
- Ordering & transactions: use transaction id and commit_ts to maintain ordering per PK. If only eventual ordering is available, implement sequence logic (apply only changes newer than current version).  
- Deletes: represent deletes as tombstones and apply accordingly in MERGE. For SCD Type 2, mark current record as closed.  
- Dedup: when ingesting batches, dedupe based on (pk, source_txid, change_seq) so you only apply the final state for that pk in the batch.  
- Schema evolution: include a discovery job to detect schema changes. Do not assume column sets; use JSON columns or dynamically alter tables as needed and communicate changes via pipeline versioning.

6) Downstream transformations
- After the core MERGE is successful (atomic checkpoint), trigger downstream Matillion transformation jobs to:
  - Apply SCD Type 2 logic (MERGE using effective_from/effective_to).  
  - Recompute dependent aggregates or materialized views. Prefer incremental transforms — operate only on changed keys.  
  - Publish to marts or BI schemas. Matillion can chain jobs: orchestration job triggers transform job(s) with batch_id parameter.  
- For heavy aggregates, use incremental aggregation patterns rather than full rebuilds. Use change tables to drive incremental re-aggregation.

7) Triggering & concurrency control
- Use checkpoint table in the warehouse to store last-processed offset/watermark. Matillion reads/writes that to coordinate runs.  
- If multiple concurrent workers, partition by key ranges or Kafka partitions to avoid conflicts. Use optimistic concurrency via version columns or transactional MERGE semantics in the warehouse.

8) Monitoring, observability and error handling
- Track latency (source commit -> warehouse apply), throughput (rows/sec), and lag by source partition/stream.  
- Maintain a DLQ for malformed records. Surface counts of rejected rows.  
- Emit job-level metrics to Prometheus/CloudWatch and alerts for thresholds. Matillion has job history and logging; push important metrics to centralized monitoring.  
- Implement retry/backoff for transient failures; for fatal errors, stop and alert with clear diagnostics and the batch_id for replay.

9) Backfill and replay
- Because raw CDC is preserved, design replay workflows to reprocess historical ranges safely (re-run apply jobs with checkpoint override). Provide schema migrations tools to reapply transforms when logic changes.

10) Cost and performance trade-offs
- Smaller micro-batches give lower latency but higher warehouse overhead. Group changes into sensible batches (e.g., 30s–5m) to balance latency and cost.  
- Use warehouse clustering/partitioning and appropriate compute sizing for MERGE-heavy workloads. Batch MERGE into a single transaction when possible for efficiency.

11) Security and governance
- Ensure least-privileged IAM roles for connectors and Matillion. Encrypt data in transit and at rest. Audit pipeline operations and maintain lineage metadata (what change produced what downstream update).

Common pitfalls
- Relying on order across partitions—partition by PK to ensure ordering per key.  
- Not checkpointing offsets atomically—leads to data loss or duplicates. Update watermark only after successful apply.  
- Applying raw events without dedupe or using non-idempotent operations—causes inconsistency on retries.  
- Ignoring schema evolution—pipeline fails for new columns.

Example concrete flow (Snowflake + Debezium + S3 + Snowpipe + Matillion)
- Debezium -> Kafka -> Kafka Connect S3 sink writes JSON files to S3.  
- Snowpipe auto-ingests S3 files into snowflake.raw_cdc table. Snowflake sends notification to SQS when files ingested.  
- Lambda reads notification and triggers Matillion orchestration job via Matillion REST API (passes list of files or watermark).  
- Matillion job loads raw rows into staging table, dedupes by pk/txid, runs MERGE into curated table, updates checkpoint table.  
- Matillion triggers downstream transform job to apply SCD Type 2 changes and incremental aggregates. Metrics/alerts are emitted on job completion.

Matillion-specific practices
- Use Matillion orchestration jobs to manage control-flow and variables (batch id, watermark).  
- Use Matillion transformation jobs to run SQL MERGE/UPSERT statements or bulk loads. Use reusable components (jobs) to implement the “apply” and “transform” steps.  
- Use the Matillion REST API to trigger jobs from cloud functions or event notifications for near-real-time execution.  
- Store checkpoints, DLQ metadata, and lineage in the warehouse so Matillion jobs can inspect and resume deterministically.

Key takeaways
- Keep raw CDC data immutable and auditable.  
- Apply deterministic, idempotent MERGE logic in the warehouse.  
- Use short micro-batches or event-driven triggers and update checkpoints only after success.  
- Implement strong monitoring, DLQs, schema evolution handling, and backfill capability.  
- Use Matillion orchestration + transformation jobs to coordinate ingestion, MERGE, and downstream transforms while storing control state in the warehouse.

[Top](#top)

## How do you design replay and backfill strategies that do not double-apply CDC changes?
Short answer: make CDC apply idempotent and track what you’ve applied. Use checkpoints, per-change IDs/LSNs, staging + dedupe, and MERGE/UPSERT logic that only applies newer changes. For backfills, don’t blindly replay overlapping CDC ranges — either compute deltas or use versioning to decide acceptance. In Matillion you implement this with orchestration jobs to manage offsets, transformation jobs to stage and dedupe events, and SQL MERGE semantics to ensure idempotency.

Key principles
- Idempotency: every apply should be safe to run more than once without changing final state (use MERGE/upsert, last_update checks, or unique constraints).
- Persistent checkpoints: store the CDC position (LSN, binlog file+pos, Kafka offset, change_id) for each source/table and only advance it after successful commit.
- Per-change identity & ordering: persist change_id + sequence/timestamp so you can detect duplicates and order operations correctly.
- Deduplicate within a batch: coalesce multiple changes for the same PK in the batch so you only apply the final state for that PK.
- Atomic apply + checkpoint update: commit the data change and the checkpoint update together (or ensure a safe two-step commit) so a rerun won't reapply already committed changes.
- Reconciliation/backfill vs replay: backfill should typically use snapshots/diffs or targeted reconciliation, while replay should use stored offsets/change_ids and idempotent applies.

Matillion implementation pattern (practical steps)
1) Checkpoint table
- Create a persistent table in your target DB like cdc_checkpoints(source, table_name, last_offset, last_change_id, updated_at, batch_id).
- Orchestration job reads checkpoint to determine start_offset.

2) Extract CDC into staging
- In an Orchestration job call the CDC extractor (or API) with start_offset = checkpoint.last_offset.
- Insert raw change events into a staging table with columns: change_id, change_seq, pk_cols, op_type, before_json, after_json, change_ts, source_table, batch_id.

3) Deduplicate and collapse per-PK
- In a Transformation job run SQL to keep only the last change per primary key in the staging batch:
  - Use row_number() OVER (PARTITION BY pk ORDER BY change_seq DESC) and keep row_number=1.
  - Or group by pk and take max(change_seq) with the corresponding after image.

4) Apply with idempotent MERGE
- MERGE target using the collapsed staging rows:
  - MERGE ... ON target.pk = src.pk
  - WHEN MATCHED AND src.change_seq > COALESCE(target.last_change_seq,0) THEN UPDATE (set columns, last_change_seq = src.change_seq)
  - WHEN NOT MATCHED THEN INSERT (columns, last_change_seq = src.change_seq)
  - WHEN MATCHED AND src.op_type = 'D' THEN DELETE (or soft-delete)
- Ensure target has last_change_seq or last_change_ts column to compare.

5) Atomicize commit and checkpoint update
- In a single transaction (if DB supports) update the target and write new last_offset/last_change_id to cdc_checkpoints.
- If single transaction is not possible, use an “apply marker” table or outbox pattern: write data + marker, then update checkpoint only after verifying marker exists. On restart, replay logic will skip already-marked batches.

6) Prevent duplicate apply via unique constraint
- Keep an applied_changes table keyed by change_id (or composite) and enforce uniqueness. When inserting raw changes, let duplicates be rejected/ignored.
- Or de-duplicate by join: apply only changes whose change_id > max_applied_change_id for that pk or table.

Backfill strategies (don’t double-apply)
- Snapshot + reconcile: load a full snapshot for the backfill range and MERGE into target using the same last_change_seq rules. This is safest when you need to rebuild correctness.
- Delta/diff against snapshot: compute deltas between snapshot and current target and apply only missing/changed rows.
- Controlled CDC replay: if you must replay old CDC logs, ensure you:
  - Temporarily disable automatic checkpoint advancement, and
  - Apply changes in strict chronological order and compare change_seq/last_change_seq so older changes don’t overwrite newer state.
- Use separate backfill batch_id and idempotency checks so repeated backfill runs won’t reapply already integrated changes.

Handling deletes and out-of-order events
- Treat deletes explicitly in MERGE (delete action or soft-delete flag).
- Guard against out-of-order events by using a change_seq or commit_lsn to decide whether to apply: only apply if incoming change_seq > stored last_change_seq.
- If source guarantees ordering per-partition/PK, you can rely on that; otherwise, collapse and order in staging by change_seq.

Concurrency and overlapping windows
- Use batch_id + checkpoint per partition/table so overlapping runs don’t race.
- Locking: use a lightweight job-level lock (Matillion has job-level controls) or DB advisory lock while performing apply+checkpoint updates.
- If parallelism is required, partition by key (hash) and maintain per-partition checkpoints.

Matillion-specific notes
- Use Orchestration Jobs to manage offsets, call extractors, and control backfill windows.
- Use Transformation Jobs to run staging/dedupe SQL and then MERGE into the target (Snowflake/Azure/Redshift SQL MERGE works well).
- Store checkpoints and applied_changes in your target DB so Matillion orchestration can read/write them with components (Database Query, Table Input, Table Output).
- Use Matillion variables to pass start/end offsets, batch_id, and run state between jobs.

Example MERGE logic (pseudo-SQL)
- staging_collapsed(pk, col1, col2, change_seq, op_type)
- target(pk, col1, col2, last_change_seq)

MERGE INTO target t
USING staging_collapsed s
ON t.pk = s.pk
WHEN MATCHED AND s.change_seq > t.last_change_seq AND s.op_type <> 'D' THEN
  UPDATE SET col1 = s.col1, col2 = s.col2, last_change_seq = s.change_seq
WHEN MATCHED AND s.change_seq > t.last_change_seq AND s.op_type = 'D' THEN
  DELETE
WHEN NOT MATCHED AND s.op_type <> 'D' THEN
  INSERT (pk, col1, col2, last_change_seq) VALUES (s.pk, s.col1, s.col2, s.change_seq);

When to re-run vs rebuild
- Minor failures: re-run the same job — idempotency + checkpointing prevents double-apply.
- Data corruption or schema drift: perform a snapshot rebuild or reconciliation backfill rather than replaying CDC.

Failure recovery checks
- On restart, read checkpoint and applied_changes; skip already-applied change_id or start from last_offset+1.
- Validate row counts or checksums after big backfills and compare to source.

Tradeoffs
- Tracking per-change IDs adds storage/index overhead but gives robust dedupe.
- MERGE with last_change_seq enforces idempotency but requires storing last_change_seq on the target.
- Full snapshots for backfill are heavier but simpler and safest for correctness.

Summary
- Always make the apply idempotent (MERGE, last_change_seq).
- Persist offsets and change_ids and atomically advance checkpoints.
- Collapse multiple changes per PK before applying.
- For backfill, prefer snapshot/diff or controlled replay with version checks so older changes cannot overwrite newer ones.

[Top](#top)

## How do you stage and validate fine-grained deletes and GDPR erasures across downstream tables?
High-level approach
- Treat erasure as a staged, auditable pipeline: collect erasure requests into a staging table, propagate deletes to downstream tables in dependency order using controlled SQL operations, validate that no target PII remains, and record an immutable audit trail.
- Implement as Matillion orchestration jobs that call transformation SQL operations in the target warehouse (Snowflake/Redshift/BigQuery), with transaction control, batching and retry logic.

Components and artifacts to prepare
- erasure_requests table (staging): request_id, subject_key (or hashed identifier), source_table(s), request_ts, requestor, status, reason, processing_metadata.
- erasure_audit table: request_id, table_name, rows_before, rows_deleted, rows_after, sql_text, run_ts, user, checksum_before, checksum_after.
- tombstone / soft-delete column if you use soft deletes for propagation.
- downstream-dependency graph: ordered list of tables to process (foreign-key -> child-first deletes or parent-first depending on FK constraints).
- Matillion orchestration job(s): one to ingest requests, one to orchestrate deletes, separate transformation jobs per target table (or a generic transformation that takes table name/SQL via variables).

Staging and execution pattern (stepwise)
1) Ingest request
   - Create single-record per subject in erasure_requests (store hashed subject_key if needed to minimize PII in control tables).
   - Validate request metadata (consent checks, duplicates).
2) Build working set
   - Use Matillion transformation or SQL Script to expand the request to a list of affected primary keys per downstream table and persist to a per-request staging table (e.g. erasure_work_<request_id>).
   - Include minimal identifying columns needed to delete (keys only).
3) Orchestrate deletes in ordered batches
   - Orchestration job iterates through ordered list of target tables (child tables first to avoid FK violations).
   - For each table, call a transformation job that:
     - Starts a transaction (where supported) via SQL Script.
     - Option A: Run DELETE ... USING (SELECT key FROM erasure_work) or DELETE FROM table WHERE key IN (SELECT key) — prefer join/delete-using for performance.
     - Option B (for warehouses where DELETE is expensive): CREATE TABLE new_table AS SELECT * FROM orig_table WHERE key NOT IN (erasure_work); then swap/rename.
     - Commit transaction.
   - Use batching for very large deletes (LIMIT or partitioned ranges).
4) Snapshot/audit before delete
   - Capture rows_before count and optional checksums/hashes (e.g., MD5 of concatenated PII columns) into erasure_audit (to prove what was removed).
   - Optionally persist encrypted backup of removed rows if policy requires but ensure legal constraints (retention of PII may conflict with erasure).
5) Finalization
   - Mark erasure_requests.status completed with timestamps and summary.
   - Generate audit record with SQL, counts, and operator.

Validation strategies (automated)
- Existence check (expected = 0):
  - SELECT COUNT(*) FROM target_table t JOIN erasure_work e ON t.key = e.key
  - Expect 0 rows.
- Orphan detection:
  - For parent tables, ensure no residual child rows referencing erased parent keys remain: SELECT COUNT(*) FROM child c JOIN erasure_work e ON c.parent_key = e.key
- Pre/post counts and checksums:
  - Compare rows_before and rows_after stored in erasure_audit.
  - Use row-level hashes: checksum_before vs checksum_after should reflect removal.
- Sampling / spot-checks:
  - Fetch sample records from each table for manual verification.
- Cross-system validation:
  - If downstream copies or BI layers exist, run the same existence checks against published tables/views.
- Automated assertion step in Matillion orchestration job:
  - Use If components to fail the job if validation queries return non-zero counts; write errors to audit table.
- Continuous monitoring:
  - Daily job that scans erasure_audit and erasure_requests for any incomplete or failed operations.

Handling backups, CDC, and third-party sinks
- Backups: Document that logical backups and immutable snapshots may keep PII beyond deletion; include this in audit and legal scope; if required, rotate backups per policy.
- CDC / downstream systems: propagate deletes via CDC topics or a tombstone table. For Kafka/stream consumers, emit tombstone messages for the keys to ensure all downstream consumers remove PII.
- For BI extracts/denormalized datasets: schedule refresh or run same erasure pipeline against derived tables.

Practical Matillion implementation details
- Use Orchestration Jobs to sequence work and manage variables (request_id, batch_size, table_name).
- Use “Run SQL Script” / “Database Query” components for transactional SQL and audits.
- Use Iterators to loop through table list and batch ranges.
- Use Python Script component if you need API calls (e.g., to a GDPR portal) or complex logic for building SQL.
- For Snowflake: use MERGE USING erasure_work or DELETE USING pattern.
- For Redshift: prefer CTAS/rename for large deletes (DELETE is slow); Matillion can orchestrate CREATE TABLE AS SELECT, drop and rename atomically.
- For BigQuery: use DML with JOIN or create a new partitioned table and swap.
- Capture job metadata (Matillion job run id, start/stop) into audit rows.

Security and compliance controls
- Limit who can view erasure_work and audit tables; store only hashed subject identifiers where possible.
- Record operator identity and SQL executed.
- Encrypt any retained backups; avoid retaining raw PII in audit logs (store hashes or summaries).
- Retain immutable audit records per your compliance retention policy.

Edge cases and performance tips
- Large-volume deletes: process incremental batches, or rebuild tables instead of repeated deletes.
- Referential constraints: either drop/disable FKs during large ops (with care) or enforce proper child-first ordering.
- Concurrent updates: use transactions and isolation levels consistent with your warehouse to avoid race conditions.
- Monitor long-running operations and implement retry logic and idempotency.

Audit evidence to provide regulators
- erasure_requests entries with timestamps and operator.
- erasure_audit rows with per-table counts, SQL text executed, and checksums.
- Validation query outputs proving zero residual PII.
- CDC/tombstone emissions logs for downstream systems and third-party confirmations if available.

Example concise SQL patterns
- Delete using staging (Snowflake-style):
  DELETE FROM target_table USING erasure_work ew WHERE target_table.key = ew.key;
- Validation:
  SELECT COUNT(*) FROM target_table t JOIN erasure_work ew ON t.key = ew.key;
- Redshift CTAS pattern:
  CREATE TABLE tmp AS SELECT * FROM target_table WHERE key NOT IN (SELECT key FROM erasure_work);
  DROP TABLE target_table;
  ALTER TABLE tmp RENAME TO target_table;

Summary checklist to implement in Matillion
- Ingest request into erasure_requests (staging)
- Build erasure_work per request (keys only)
- Orchestrate deletes by dependency order in Matillion jobs
- Capture pre/post counts and checksums to erasure_audit
- Run automated validation queries and fail on residuals
- Emit tombstones/CDC messages for downstream systems
- Record immutable audit evidence and secure access to those tables



[Top](#top)

## How do you incorporate data masking/tokenization for PII during ingestion and transformation?
Short answer
- Treat masking/tokenization as part of ingestion or the first transformation step. Either (A) tokenize/mask at-source or (B) land encrypted/raw in a locked staging area and tokenise within Matillion before making data available downstream.
- Implement tokenization/masking in Matillion by (1) using native warehouse crypto/UDFs when available, or (2) calling a tokenization/encryption service (KMS, Vault, TokenEx, Protegrity, external API) via HTTP or Python components, or (3) applying deterministic/non-deterministic masking using Matillion transformations (Calculator / SQL). Store keys/secrets in secure credential managers (AWS Secrets Manager / Azure Key Vault / GCP Secret Manager or Matillion credentials).

Architectural options and trade-offs
- Tokenize at source
  - Pros: PII never lands in staging; lower risk surface.
  - Cons: May require changes to source systems and schema; limits debugging and some analytics.
- Tokenize in a secure landing zone (recommended if you need raw data for audit)
  - Pros: Full audit trail, easier to support re-tokenization/detokenization.
  - Cons: Need tight access controls, short TTL storage, and encryption-at-rest.
- Tokenize in-target DW via native functions
  - Pros: High performance for bulk data, leverages DW scale.
  - Cons: May be less flexible for reversible tokenization unless DW supports it or you use external functions.

Matillion-specific implementation patterns
1) Use native DB functions (best for hashing/one-way masking or DB-side encryption)
   - In a Transformation Job use Table Input / SQL components to run SQL that replaces columns with HASH/SHA2 or built-in encryption functions (Snowflake: SHA2, MD5; BigQuery: AEAD with Cloud KMS; Redshift: UDFs or crypto functions).
   - Pros: Fast, leverages DW compute. Use when one-way masking or DB-native crypto is acceptable.

2) Call an external tokenization/encryption service from Matillion
   - Use Orchestration components:
     - HTTP Query (or Python Script) to call a tokenization API for each record or batched payload.
     - Python Script component to call SDKs (AWS KMS, HashiCorp Vault) or third-party tokenization libraries.
   - Flow: Orchestration job receives raw file → batch POST to tokenization API → write tokenized output to staged table → Transformation job consumes staged tokenized data.
   - Pros: Supports reversible/tokenized values stored safely in token vault; deterministic tokens for joins.

3) Implement masking in Matillion transformations without external services
   - Use Calculator or SQL components to apply masking expressions (left/right substring + stars), regex-based redaction, or hashing.
   - Useful for format-preserving masking or obfuscation when full tokenization is not required.

Example Matillion job flow (tokenization in Matillion)
- Orchestration Job:
  - Get file from S3/Blob/GCS (Get/Download components).
  - Push batch to tokenization service using HTTP Query or Python Script; use project/environment variables for API credentials (encrypted).
  - Write tokenized batch to staging table (Table Output).
- Transformation Job:
  - Run SQL to join/stage data into curated tables using masked/tokenized columns.
  - Drop/hard-delete raw staging data as per retention policy.

Deterministic vs non-deterministic vs reversible
- Deterministic tokenization/hashing: same input → same token. Use when you need joins across datasets without detokenization. Protect salts/keys separately.
- Non-deterministic (randomized) masking: better privacy but breaks joins.
- Reversible tokenization/encryption: required when you must detokenize for authorized users/processes. Keep mapping/tokens in a secure vault and log all detokenize operations.

Secrets, keys, and credentials
- Never hard-code keys in jobs. Use:
  - Matillion Credentials and Project/Environment variables (encrypted at rest).
  - External secret stores: AWS Secrets Manager, Azure Key Vault, GCP Secret Manager.
- Restrict which Matillion roles/nodes can read secrets. Enable audit logging for secret access and tokenization APIs.
- Rotate keys and tokens regularly; design re-tokenization path if keys rotate.

Logging, audit and governance
- Ensure job logs do not contain PII — mask log outputs and sanitize exceptions.
- Maintain audit trail for tokenization/detokenization events (who, when, why).
- Implement RBAC on Matillion projects/roles so only authorized users can design jobs that access PII.
- Retention policy: delete raw/unmasked landing files quickly; keep token vault separate with limited access.

Performance and operational considerations
- Bulk tokenization in the DW or via batch API calls is more efficient than per-row synchronous API calls.
- Monitor throughput and cost of external tokenization services; consider parallelizing batch calls in Matillion Orchestration with concurrency controls.
- Test join correctness if using deterministic tokens/hashes and be careful with salts/collisions.

Compliance and design checklist
- Identify and classify PII fields.
- Choose masking/tokenization type per field (one-way hash, format-preserving encryption, reversible token).
- Decide where tokenization happens (source, Matillion, DW).
- Use secure secret management.
- Limit and audit access; scrub logs.
- Plan for key rotation and re-tokenization.
- Validate downstream use cases (analytics, joins, detokenization needs).

Short concrete examples
- Hash email deterministically for analytics: Transformation Job runs SQL: email_hash = SHA2(CONCAT(email, :salt), 256). Store salt in Secrets Manager referenced through Matillion variable.
- Reversible tokens via Tokenization API: Orchestration job batches PII rows, calls HTTP Query to tokenization service with API key stored in Matillion credentials, writes tokenized result to target.
- Format-preserving mask for SSN: Calculator or SQL to replace middle digits: CONCAT(LEFT(ssn,3),'-XX-','RIGHT(ssn,4)') or use an FPE library via Python Script for stronger preservation.

Answer emphasis (interview-style)
- Prefer tokenization as early as practical. Use secure staging if you need auditing or re-tokenization. Implement tokenization in Matillion by combining native SQL crypto when possible, or by calling external tokenization/KMS services via HTTP/Python components. Always protect keys with a secrets manager, avoid PII in logs, enforce RBAC, and audit token/detoken operations.

[Top](#top)

## How do you enforce row-level/column-level security downstream and ensure Matillion jobs respect access policies?
Short answer: enforce RLS/CLS in the data platform (warehouse) and make Matillion run under least‑privilege credentials and job design patterns that never expose raw data. Use warehouse-native Row/Column security (policies, masking, secure/authorized views) and make Matillion either switch to the appropriate role/connection or only write curated tables while consumers access only the secured views.

Key parts and practical steps

1) Implement security downstream (authoritative)
- Row-level security: use the warehouse’s native RLS (Snowflake Row Access Policies, BigQuery Row Access Policies, SQL Server/Synapse Row‑Level Security via SECURITY POLICY, Redshift patterns/views/RLS if supported). Attach policies to base tables or use secure views that filter rows based on CURRENT_USER(), CURRENT_ROLE(), session context, or attributes.
- Column-level security: use masking policies (Snowflake masking policies), column-level access controls/policy tags (BigQuery Data Catalog IAM + column-level access), dynamic data masking (SQL Server/Synapse), or expose only allowed columns via views.
- Prefer secure/authorized views or stored procedures that encapsulate logic and are the only objects granted to downstream roles.

2) Matillion connection/role strategy
- Use least-privilege service accounts for Matillion jobs. Don’t run Matillion with broad privileged credentials for user-facing queries.
- Create separate connections in Matillion tied to different roles (e.g., ingestion/admin role vs. consumption role). Choose the connection that has only the privileges necessary for the job step.
- Where supported, issue a role switch at runtime (e.g., run SQL "USE ROLE <rolename>;" in Snowflake) from Matillion SQL components to ensure subsequent statements execute under the intended role.
- Alternatively, call procedures or run SQL that executes with ownership-based rights (e.g., stored procedures that run as definer/owner and enforce policies inside the warehouse).

3) Job and pipeline design patterns
- Landing/Raw layer: Matillion writes raw data into secure internal schemas that only the ETL service account can access.
- Curated layer: transforms into curated tables owned by a privileged schema; then create secured views and apply RLS/masking. Grant consumer roles access only to views, not base tables.
- Never embed sensitive data in exported artifacts or logs. Use Matillion masking/encryption only for transit; authoritative masking belongs in the warehouse.
- For parameterized transforms that must take caller identity into account, pass user/session attributes into the DB (session variables, context table) and let the DB policy use them to filter results.

4) Governance, CI/CD and operational controls
- Store jobs in Git, use code review to prevent jobs that bypass security (e.g., creating tables in consumer schemas or granting broad permissions).
- Use environment variables and Matillion credentials vault for connection segregation. Limit who can edit connections/environments in Matillion.
- Enforce the principle of least privilege on Matillion IAM and cloud service accounts (instance/role attached to Matillion instance).
- Use logging and audit trails (warehouse access logs, Matillion activity logs) to detect jobs that issued privilege-escalating SQL.

5) Testing and validation
- Automate tests that run representative queries under different roles/users and verify row/column visibility matches policy.
- Periodically query object grants and policy attachments (e.g., SHOW ROW ACCESS POLICIES, INFORMATION_SCHEMA) to ensure policies are still applied.
- Simulate attacker scenarios: attempt direct table access from consumer connections to ensure permissions are blocked.

6) Concrete examples (patterns)
- Snowflake: attach a ROW ACCESS POLICY that references CURRENT_ROLE() or CURRENT_USER() and apply it to the table; create a secure view for analysts and grant them only the view. In Matillion, either use a connection with a limited role or run "USE ROLE ETL_ROLE;" then perform writes, then create views as owner.
- BigQuery: attach row access policies to tables or expose authorized views; assign column access via Data Catalog policy tags. Matillion should write to base tables and not expose service account keys to consumers.
- SQL Server/Synapse: use CREATE SECURITY POLICY … ADD FILTER PREDICATE(...) to enforce RLS; use masking functions for columns.

Summary checklist to ensure Matillion jobs respect access policies
- Enforce policies in the warehouse (RLS/CLS/masking/views).
- Run Matillion components under least-privilege connections or switch roles per-step.
- Publish only secured views to consumers; revoke direct base-table access.
- Lock down Matillion connections, environments and editor permissions.
- Use CI/CD, code review, tests and audits to prevent and detect policy bypass.

Avoid implementing primary enforcement in Matillion; treat Matillion as an orchestration/ELT tool and make the data platform the source of truth for access control.

[Top](#top)

## How do you publish curated datasets to BI platforms and keep schema contracts and documentation in sync?
High-level principles
- Treat the curated dataset schema as a contract (machine-readable, versioned, single source of truth) separate from physical implementation.
- Publish a stable interface to BI tools (views or thin, well-documented tables) and keep the implementation behind the interface free to change.
- Automate validation and documentation updates in the ETL pipeline so publication fails if contract is violated.
- Keep human documentation and programmatic descriptions (YAML/JSON/schema files, column comments, data catalog entries) generated from the same source so they cannot drift.

Concrete architecture / workflow using Matillion
1. Define the contract
   - Store schema contract files in Git (YAML/JSON) that list field names, types, nullability, descriptions, semantic types and version/semver.
   - Optionally use dbt model YAMLs or a schema registry format as the canonical contract.

2. Build the curated dataset in Matillion
   - Transformation job writes to a canonical physical table (or staging tables) in the warehouse (Snowflake/Redshift/BigQuery).
   - Expose a stable read interface as a view or a curated table named for the dataset (e.g., analytics.my_event_v1).
   - Use Matillion variables/environments for dataset name/version so you can create vN views without changing downstream.

3. Validate against the contract (automated test)
   - Add a Matillion step after load that runs a SQL validation job comparing INFORMATION_SCHEMA / catalog metadata to the contract file.
   - Implement checks for column presence, data type compatible changes, nullability, new columns (allowed vs breaking), etc.
   - Use Matillion components to run SQL and conditionally fail the job if the checks fail. Alternatively call a tests framework (dbt tests, Great Expectations) from Matillion (Bash/Python/API components).

4. Update programmatic metadata and docs automatically
   - After successful validation, generate documentation artifacts:
     - Extract column comments and metadata from the warehouse or from the contract YAML and write out Markdown/HTML/JSON.
     - Use a Matillion Python or Bash component to write the artifacts into your docs repo or push them to a data catalog (DataHub, Amundsen, Alation) via API.
   - Keep column descriptions in the warehouse (COMMENT statements) so BI tools and catalogs can read them. Implement this as a Matillion SQL step that syncs comments from the contract file.

5. Publish/refresh the dataset in BI platforms
   - Use Matillion API/Script components to call BI platform APIs to create/update dataset artifacts or trigger refreshes:
     - Tableau: use Tableau REST/Server API to publish TDS/TDSX or refresh extracts (Matillion can generate .hyper via scripts and push via API).
     - Looker: update LookML or use the Looker API to update models/dimensions (or generate LookML from contract).
     - Power BI: use Power BI REST API to push dataset changes and refresh.
     - Google Data Studio / Looker Studio: ensure the underlying view/table is visible and refresh as needed.
   - Prefer pointing BI tools at the stable view/dataset name; keep materialized extract refresh in Matillion orchestration.

6. Release/version and notify
   - Tag the contract in Git and record the dataset version in the warehouse metadata (table/view name or a version column).
   - If changes are breaking, deploy a new version (v2) and keep v1 for consumers until they migrate. Automate deprecation notices (email/Slack) from Matillion on deployment.

Practical Matillion components you’ll use
- Transformation job components to write curated tables/views.
- SQL components (Execute SQL) to run schema checks and set table/column comments.
- Python Script or Bash Script components to:
  - Read contract YAML/JSON from Git or S3.
  - Call external APIs (data catalog, BI REST APIs, dbt/cloud).
  - Generate documentation files and push to docs repo or S3.
- API Query components to call REST endpoints.
- Orchestration jobs to sequence: load → validate → doc sync → publish → notify.
- Git integration in Matillion for job version control and triggering CI/CD.

Schema-contract enforcement patterns
- Fail-fast: validation step must succeed before publish/refresh.
- Compatibility rules:
  - Allow additive, nullable column additions without breaking.
  - Disallow renames/type downgrades without explicit contract version bump.
- Automated tests: row-level and schema-level tests (Great Expectations or dbt tests invoked by Matillion).
- Use views as stable interfaces: change underlying tables but keep view columns fixed until you publish a new contract version.

Keeping documentation in sync
- Single source: keep contract files in repo and generate both docs and database column comments from it.
- Auto-generate docs in pipelines:
  - Use SQL queries against information_schema to produce a current schema export and compare to contract, then render docs.
  - Push docs to a doc site, data catalog, or BI platform (descriptions in datasets).
- Update BI dataset descriptions programmatically so the BI UI shows current field-level docs.

Example end-to-end job sequence (Matillion)
- Orchestration job:
  1. Run transformation to build curated table (Transformation job).
  2. Execute SQL: sync column comments using contract file.
  3. Run validation (SQL or call Great Expectations/dbt); fail on mismatch.
  4. Generate docs (Python/Bash): export schema JSON/Markdown → push to docs repo or catalog via API.
  5. Publish/refresh BI dataset (API Query or Python call).
  6. Post deploy: tag Git, write dataset version to a metadata table, send notification.

Operational / governance best practices
- CI pipeline: run contract validation and unit tests on PRs before merging changes to contract or Matillion jobs.
- Audit trail: log schema changes into a metadata table with who/when/why.
- Catalog integration: ingest the warehouse schema and contract metadata into a catalog (Amundsen/DataHub) so analysts can discover and see lineage.
- Consumer communications: automated change notifications and migration guides when breaking changes are unavoidable.

Why this works
- Contracts in Git + automated validation prevent unexpected breaking changes.
- Views and versioning let you evolve implementation without breaking consumers.
- Generating docs from the contract prevents drift between code, warehouse metadata, and BI platform descriptions.
- Matillion is used as the orchestrator to run ETL, tests, metadata sync and API calls so the whole process can be automated and repeatable.

[Top](#top)

## How do you handle object dependencies in Matillion (Run Orchestration/Run Transformation) to avoid cycles and deadlocks?
Key principles
- Treat Matillion jobs like nodes in a directed acyclic graph (DAG). Design so control flow is one-way (parent → child) and avoid mutual invocation.
- Make dependencies explicit and synchronous when you need strict ordering; use asynchronous + polling when you need concurrency and later join.
- Build idempotent jobs and use explicit state/lock primitives (metadata table or lock file) so jobs can detect whether upstream work is finished or already claimed.

How to implement in Matillion

1) Synchronous Run Orchestration / Run Transformation
- Use Run Orchestration / Run Transformation in synchronous mode (wait for result) to create a blocking dependency edge. This is the simplest way to guarantee ordering and avoid race conditions.
- To avoid cycles: never have child jobs call back a parent synchronously. Flatten or redesign any mutual calls into a single direction.

2) Asynchronous runs + polling (when you need parallelism)
- Launch downstream job asynchronously, then have a dedicated “join” job poll for completion (via Matillion API or a status table/file). This prevents two jobs from blocking each other and allows controlled rejoin logic (timeouts, retries).
- Use the Matillion REST API to check job run status if you need programmatic polling.

3) Use an explicit control/metadata table or S3 lock file
- Implement a control table (or S3/GCS object) that records job name, run_id, status, start/end timestamps. Acquire a lock atomically (INSERT ... WHERE NOT EXISTS, MERGE with transactions) to prevent concurrent runs.
- Acquire/release the lock at job start/end. Have TTLs and clean-up logic for stale locks so deadlocks don’t persist.
- This pattern is language- and warehouse-agnostic and works for cross-job synchronization and mutual exclusion.

4) Centralized orchestrator / single source of control
- Move top-level sequencing into a single orchestrator job that invokes workers. Shared logic should be extracted to reusable jobs so two jobs don’t try to call each other.
- Keep workers idempotent so the orchestrator can safely retry.

5) Break shared dependencies into separate jobs
- If two jobs need the same upstream work, extract that work into a single reusable job that both call (but do not have them call each other).

6) Deadlock avoidance and timeouts
- Add timeouts on waits and polling loops. If a timeout occurs, fail fast or trigger remediation logic to release locks or notify operators.
- Ensure cleanup steps run in finally/failure handling to remove locks or mark runs as failed.

7) Detect cycles programmatically
- Export job definitions (JSON) and build a call graph (edges = Run Orchestration / Run Transformation calls). Run a topological sort or cycle-detection algorithm (DFS) to find cycles before deployment.
- Enforce a rule that jobs must form a DAG; block CI/CD deployments that introduce cycles.

8) Practical locking examples
- S3 lock file: create an object at start; check existence to acquire; delete on finish. Use naming + atomic Put (or conditional checks) and TTL handling for stale locks.
- DB lock: control table with unique key per resource; INSERT for acquire, DELETE for release. Use a transaction to avoid races. Support cleanup for orphaned locks.

Recovery and observability
- Emit run metadata (start/stop, status, run_id) to a central table and expose job run metrics.
- Implement watchdog jobs to detect and clear stale locks or runs that have exceeded expected duration.

Summary patterns to avoid cycles/deadlocks
- One-way orchestration (master → workers), synchronous when strict order needed.
- Asynchronous launches + polling for parallelism and joins.
- Explicit locks/state via DB or object storage with TTL and cleanup.
- Centralized orchestrator and reusable jobs to remove mutual calls.
- Automated cycle detection from exported job graphs and timeouts/cleanup for deadlock recovery.

[Top](#top)

## How do you build conditional flows based on data checks or metadata lookups (e.g., run downstream only if new data)?
Short answer: run a small metadata/data-check query, capture the result in a variable, and use an If component or a component-level Run If expression to branch — only run the downstream job when the variable indicates new data. Persist watermarks to an environment variable if you need state across runs.

How to implement (common patterns and concrete steps)

1) Decide the check
- Row-count/exists: SELECT COUNT(*) ...
- Watermark: SELECT MAX(updated_at) ...
- File presence: S3 List / Check file exists
- Table present or partition present: Table Exists / catalog query

2) Run the check and capture results
- In an Orchestration Job add a DB Query (or S3 List / API call) that returns the metric you need.
- Map the returned value(s) to job variables (e.g., row_count, max_ts). Matillion supports returning query results into variables.

Example SQL for a watermark check:
SELECT COUNT(*) AS cnt, MAX(updated_at) AS max_ts
FROM source_table
WHERE updated_at > '${env.LAST_RUN_TS}';

Map cnt -> ${cnt}, max_ts -> ${max_ts}.

3) Branch on the variable
Two options:
a) If component
- Add an If component with condition ${cnt} > 0 (or ${max_ts} > ${env.LAST_RUN_TS}).
- Connect the True branch to a Run Orchestration / Run Transformation component to run downstream work.
- Connect the False branch to end or to alternate logic.

b) Component-level Run If
- Put the Run Orchestration (or other component) in the flow and set its Run If property to ${cnt} > 0 (or appropriate boolean). That avoids an explicit If component.

4) Persist/update metadata only on success
- After downstream job finishes successfully, use a Set Variable (or DB update) to update your environment variable LAST_RUN_TS = ${max_ts}.
- Wire the update step from the success (true) connector of the downstream job so you only advance the watermark on successful completion.
- Use failure connectors if you want alternate handling on error.

5) Variants / tips
- Use environment variables for watermarks that must persist across jobs/executions; use job variables for one-run logic.
- For file checks use S3 List component or a small Python script, capture filenames/counts into variables, branch the same way.
- For orchestration chaining use Run Orchestration component to call downstream job(s). Use Run If on that component or connect it via the If True branch.
- Add logging and notifications on the False branch if you need to record “no new data” runs.
- Use Try/Catch-like flow: link failure connectors to clean-up or to avoid updating watermark when downstream fails.

Example minimal flow
1) DB Query -> set ${cnt}, ${max_ts}
2) If condition ${cnt} > 0
   - True -> Run Orchestration (child job) -> On success -> Set env.LAST_RUN_TS = ${max_ts}
   - False -> End / Log “no new data”

This ensures downstream only runs when new data is present and the watermark moves forward only after successful downstream processing.

[Top](#top)

## How do you construct dynamic SQL safely and prevent SQL injection when using variables and metadata tables?
Threat model in one line: Matillion variable interpolation is string substitution — if you concatenate variables into SQL you invite SQL injection. Mitigation requires parameterization where possible, strict validation/whitelisting for anything that cannot be parameterized (identifiers), and limiting privileges.

Concrete rules and patterns

- Prefer parameterized queries / prepared statements
  - Use a connector or scripting component that supports bind parameters (Python Script component with DB-API, Snowflake/Redshift connectors that expose prepared statements). Example (Python DB-API style):
    cur.execute("SELECT * FROM sales WHERE customer_id = %s AND year = %s", (customer_id, year))
  - Never build literals by string-concatenating user input into SQL.

- Treat identifiers (schema, table, column) differently
  - Most DBs do not allow binding identifiers. Do not accept arbitrary identifier strings.
  - Use a whitelist or metadata mapping: keep a metadata table or config that maps safe keys to actual schema.table names, and only allow values that appear in that table.
    - Example mapping approach: user passes key "orders_2024" → job looks up metadata table and returns "prod.orders_2024". Use that exact value (already vetted) in SQL.
  - Alternatively validate with strict regex and length limits (e.g., ^[A-Za-z0-9_]{1,64}$) and then apply DB-specific identifier quoting if needed.

- Use metadata-driven validation
  - Query your metadata table first to confirm the requested object exists and get canonical name or internal id.
  - Use the returned internal id or canonical name (which you control) as the only allowed substitution.
  - Do not trust metadata table entries that were themselves populated from untrusted input unless you control their creation.

- Use DB-side stored procedures or prepared statements for dynamic logic
  - Move dynamic SQL generation into stored procedures that accept parameters and perform internal validation. Call those procedures from Matillion with safe parameter binding.
  - This reduces client-side string-building.

- For lists (IN (...) ) or bulk values
  - Avoid building comma-separated lists from untrusted input. Use:
    - Temporary staging table + join
    - Array binding / table-valued parameter if DB supports it
    - OR validate each list element strictly before concatenation

- Proper quoting/escaping when necessary
  - Prefer parameter binding. If you must quote, use DB-provided quoting functions (e.g., quote_literal, quote_ident in databases that have them) rather than homemade escaping.
  - Escaping user input manually is error-prone.

- Principle of least privilege and logging
  - Use a database user with least privilege needed for the job (no superuser).
  - Audit queries and monitor jobs that accept external inputs.

Matillion-specific implementation patterns

- Use Python Script component
  - Use Python DB connectors (snowflake-connector-python, psycopg2, etc.) to prepare and execute parameterized statements rather than relying on ${variables} interpolation inside a SQL component.
  - Example pseudo-code inside Python Script:
    conn = snowflake.connector.connect(...)
    cur = conn.cursor()
    cur.execute("SELECT * FROM table WHERE col = %s", (safe_var,))
- Use Orchestration job steps to validate first
  - Add a Table Input step to check the metadata table for the requested key. If found, save the canonical name into a Matillion variable. Use that variable only after validation.
- Avoid putting user input directly into the SQL property of a Table Input / Run SQL component unless you have validated or mapped it.
  - Matillion variable substitution (${var}) is plain text substitution — treat it as potentially unsafe.

Examples (pseudo)

- Safe identifier via metadata lookup:
  1) Table Input: SELECT canonical_name FROM metadata WHERE key = ${key_var}
  2) If result exists, set variable canonical_table to that value
  3) Run SQL: SELECT * FROM ${canonical_table} WHERE id = %s — executed via Python connector with parameter binding for id

- Safe value parameters in Python:
  cur.execute("SELECT * FROM customers WHERE email = %s", (email_var,))

Checklist before using any variable in a SQL statement
- Is it a value parameter? If yes, use bind parameters.
- Is it an identifier? If yes, validate against a whitelist/metadata or strict regex; do not directly interpolate unvalidated strings.
- Are you passing a list? If yes, use a temp table or array binding.
- Are privileges minimized and inputs logged? Ensure both.

Outcome: parameterize values, whitelist/validate identifiers via metadata mapping, use DB quoting functions only when necessary, and use Matillion orchestration + Python components to enforce the safe flow.

[Top](#top)

## How do you test jobs locally or in a sandbox with sample data and seedable randomness for deterministic results?
High level approach
- Run everything in a dedicated dev/sandbox Matillion environment (separate Matillion instance or at least a separate Environment within Matillion) pointed at small sample data stores (dev schemas, S3/GCS/Azure dev buckets).  
- Make randomness explicit and controlled: create a SEED job/project/environment variable and pass it into every place you use randomness. Log the seed with the job run so tests are reproducible.  
- Use deterministic techniques in the components that don’t support explicit seeding (hashing, seeded DB functions, deterministic ORDER BY).  
- Wrap tests in “test jobs” that load sample data, run the transformation, and assert expected outcomes (row counts, checksums, sample-row equality). Fail the job on mismatch so CI can detect regressions.

Concrete steps and examples

1) Provision sandbox and sample data
- Create a Matillion dev Environment (or a separate Matillion instance) and dev database/schema or a small set of CSV/Parquet files in a dev bucket.  
- Keep the datasets small and representative. Use Environment variables for paths and connection targets so switching between prod/dev is a one-field change.

2) Add a seed variable
- Add a Job-level or Project-level variable like SEED (integer). Set it in the test job (hard-coded for deterministic runs, or injected by CI). Always store the seed in an audit/test-results table.

3) Seed randomness in Python components
- Use ${SEED} substitution to put the seed into the script. Example in a Python Script component:
  - seed = int("${SEED}")
  - import random, numpy as np
  - random.seed(seed)
  - np.random.seed(seed)
- All subsequent random calls will be deterministic for that seed.

4) Seed randomness in SQL components
- If the target DB has a seed function: call it at the start of the session. Example in PostgreSQL:
  - SELECT setseed(${SEED}::double precision / 2147483647.0);
  - SELECT random();  -- deterministic after setseed
- If DB has no seedable RNG, derive pseudo-random values deterministically from a hash of seed + unique key:
  - Generic pattern: pseudo_rand = abs(hash(concat(seed, unique_id))) normalized to [0,1)
  - BigQuery example using FARM_FINGERPRINT:
    - SELECT id,
      ABS(FARM_FINGERPRINT(CONCAT(CAST(${SEED} AS STRING), CAST(id AS STRING)))) / 9223372036854775807.0 AS pseudo_rand
      FROM table;
  - If your engine exposes MD5/FNV/FARM_FINGERPRINT use that + convert to numeric and normalize.
- Deterministic shuffling: ORDER BY md5(concat(${SEED}, id)) or ORDER BY FARM_FINGERPRINT(concat(seed, id)) – gives the same “random” order for a given seed.

5) Deterministic sampling / splits
- Use the same hash trick to split rows into buckets: bucket = ABS(hash(seed||id)) % N. This yields stable sampling per seed.

6) Test job pattern in Matillion
- Test Orchestration job steps:
  1. Set SEED variable (hard-coded or passed in)
  2. Load sample data into test schema or reference small files
  3. Run transformation jobs that reference ${SEED} for any RNG
  4. Run assertion steps:
     - Table Count components or Table Input -> If Condition to check counts
     - Calculate checksum/hashes of output table and compare to expected snapshot value
     - Compare a few deterministic sample rows to expected rows
  5. Write test results and the SEED into an audit table or test artifact
  6. Fail the job (use Stop/Fail components) if any assertion fails

7) Integrate with CI/CD / automation
- Use Matillion’s REST API or CLI to trigger the test job and pass SEED as a parameter. Capture logs and audit rows. Run tests on every commit or before releases. Vary the seed in multiple runs to cover more randomness — but always record the seed so failing runs are reproducible.

8) Practical tips and pitfalls
- Always log the seed with run metadata. Without it you cannot reproduce the failure.  
- Prefer hash-based deterministic methods for SQL if your DB doesn’t support session seeding. They’re portable and easy to reason about.  
- Keep random-dependent logic central (one place that reads ${SEED} and produces deterministic values) to avoid missing a spot.  
- Avoid external non-deterministic APIs in tests; if needed, mock or snapshot responses.  
- Maintain expected-output snapshots for small sample datasets; compare checksums rather than full-row-by-row in large outputs.

Summary (one-line)
- Use a dev Matillion environment + sample data, expose a SEED variable, explicitly seed Python/DB where possible, otherwise derive pseudo-random values by hashing seed+key, and implement test jobs with assertions that fail on mismatch so CI can run deterministic tests.

[Top](#top)

## How do you separate configuration from code and use environment-driven settings without code changes?
Short answer
Externalize everything that varies between dev/test/prod into Matillion Environments and Variables, store secrets in secure places (password type variables or cloud secret stores), and reference those variables in jobs/components. Switch Environments or override variables at runtime or via the API — the job logic never changes.

How to do it in Matillion (practical steps)
1. Use Environments for connection-level config
- Create one Matillion Environment per target (dev, test, prod). Each Environment holds the connection settings for the target data warehouse, S3/Blob settings, credentials, and other environment-specific properties.
- When you run a job, choose the Environment; the job will use the target connections for that Environment without changing job logic.

2. Create Project variables for non-connection configuration
- Define Project-level variables for values that vary by environment: schema names, S3 bucket names, file paths, table prefixes, feature flags, etc.
- Use appropriate variable types (String, Number, Boolean, Password). Mark secrets as Password so they are masked in the UI and logs.

3. Set/override variable values per Environment
- Assign different values to the same Project variables for each Environment (so the variable name in the job stays the same, but its value comes from the Environment).
- You can also set variables at job runtime via the “Set Variable” component, job parameters, or via the Matillion REST API to override defaults without editing the job.

4. Reference variables inside jobs
- Use ${variable_name} (the Matillion variable reference) in component properties, SQL statements, file paths, and orchestration components. The job code uses the variable token and never embeds environment-specific literals.

5. Secure secrets using secret stores
- For credentials, either use Matillion password variables or integrate with cloud secret managers (AWS Secrets Manager, Azure Key Vault, GCP Secret Manager) and reference secrets via Environment or custom routines so credentials are not hard-coded.

6. Deployment & CI/CD
- Store jobs in Git. Promote jobs between Environments (dev → test → prod) without changing code. Environment and variable values stay outside source-controlled job logic.
- Use Matillion’s Deployment Manager or CI tooling to set variables for target Environments during deployment if you need automated substitution.

7. Runtime overrides and automation
- Use the REST API or job parameters to trigger runs with different variable values (useful for ad-hoc runs, automation, or CI pipelines).
- Use “Set Variable” or “Get Variable” components within jobs to build dynamic behavior based on environment values.

Best practices (concise)
- Never hard-code connection strings, credentials, schema names, or paths in jobs.
- Use meaningful variable names (e.g., DW_SCHEMA, S3_RAW_BUCKET).
- Use Password variable type or a cloud secret store for secrets.
- Keep jobs environment-agnostic; control behavior entirely via Environments and variables.
- Test environment-specific values after deployment to confirm behavior without modifying code.

Result
Jobs remain identical across dev/test/prod; switching Environment or changing variable values controls runtime behavior, enabling environment-driven settings without code changes.

[Top](#top)

## How do you parameterize warehouse sizes, role names, and storage locations for different environments?
Short answer
- Define environment-specific values as Matillion Environment Variables (or Project Variables if shared) and reference them in your jobs. Use those variables in SQL or component fields to set warehouse size, role, and storage paths at runtime.

How to do it (step-by-step)
1. Create separate Matillion Environments
- Create one Matillion Environment per lifecycle (dev/test/prod). Each Environment can hold different connection credentials and environment-variable values.

2. Add Environment Variables (recommended)
- In Matillion UI: Manage → Environment Variables (or Project → Variables if you need project-wide defaults).
- Create variables like:
  - WAREHOUSE_SIZE (String) e.g. XSMALL / SMALL / MEDIUM
  - WAREHOUSE_NAME (String)
  - SNOWFLAKE_ROLE (String) e.g. ETL_ROLE
  - S3_BUCKET or STORAGE_ACCOUNT (String)
  - STORAGE_PREFIX (String) e.g. raw/dev
  - STORAGE_INTEGRATION (String) for Snowflake external stage
- Set different values for each Matillion Environment.

3. Reference variables in jobs/components
- Use the variable placeholders in component fields or Execute SQL code: ${VARIABLE_NAME}
- Examples:
  - Set role:
    - Execute SQL component: USE ROLE ${SNOWFLAKE_ROLE};
  - Resize warehouse (Execute SQL):
    - ALTER WAREHOUSE ${WAREHOUSE_NAME} SET WAREHOUSE_SIZE='${WAREHOUSE_SIZE}';
  - Storage location for stages or COPY:
    - CREATE OR REPLACE STAGE my_stage URL='s3://${S3_BUCKET}/${STORAGE_PREFIX}' STORAGE_INTEGRATION=${STORAGE_INTEGRATION};
    - COPY INTO my_table FROM 's3://${S3_BUCKET}/${STORAGE_PREFIX}/file.csv' CREDENTIALS=(aws_key_id='${AWS_KEY}' aws_secret_key='${AWS_SECRET}'); (or use a preconfigured Storage Integration)

4. Use job variables for runtime overrides
- If you occasionally need to override these per-run, expose job variables and set them at runtime (or use Set Variable component early in an orchestration job to adapt values).

Best practices
- Prefer Environment Variables for environment-specific settings; Project Variables for defaults that are consistent across environments; Job Variables for run-time values.
- Keep credentials and secrets masked and use Matillion’s secure variable type or external credential stores when possible.
- Use separate Matillion Environments for clear separation of resources and to avoid accidental runs against production.
- For Snowflake: use STORAGE_INTEGRATION or IAM roles rather than embedding keys; pass only the integration name as a variable.
- Template SQL in Execute SQL components so the same job works across environments purely by changing variables.

Example snippets
- Start/resize warehouse:
  ALTER WAREHOUSE ${WAREHOUSE_NAME} SET WAREHOUSE_SIZE='${WAREHOUSE_SIZE}';
- Set role:
  USE ROLE ${SNOWFLAKE_ROLE};
- S3 path:
  s3://${S3_BUCKET}/${STORAGE_PREFIX}/raw/${TABLE_NAME}/

This pattern gives you a single set of jobs that behave differently per environment by simply changing the Environment Variable values.

[Top](#top)

## How do you warm up warehouses or pre-stage data to bound pipeline latency during scheduled runs?
Short answer
- Use a small pre-run orchestration job (scheduled a few minutes before the main pipeline) that: resumes/scales the warehouse, executes small read queries to load relevant data partitions into cache, and/or loads pre-staged data into staging tables. Chain that job into the main job (or schedule with an offset) so your main transforms start with compute and data already “warm.” Matillion provides orchestration components and Execute SQL to do all of this.

Detailed tactics and concrete patterns

1) Resume/scale compute first
- Use an orchestration job to run the vendor control commands (via Matillion Execute SQL or built-in components). Examples:
  - Snowflake: ALTER WAREHOUSE <w> RESUME or use a Matillion “start warehouse” action if present.
  - Redshift / Synapse: resume/pool/scale the cluster or adjust DWU.
  - BigQuery: not applicable the same way (serverless), but you can increase slot commitments ahead of run if you control reservations.
- Scale up temporarily if the main run needs more concurrency and scale down after it finishes.

2) Warm caches / micro-partitions / local blocks
- Execute lightweight queries that touch the same tables/partitions the pipeline will read:
  - SELECT 1 for connection heat‑check.
  - Small scans that hit the target partitions (e.g., SELECT count(1) FROM table WHERE load_date >= X) or SELECT * LIMIT 1 on key tables.
  - For Snowflake, a targeted micro-partition scan helps warm storage metadata and cache.
  - For Redshift, small full reads prime local SSD buffers.
- Put these in the pre-run orchestration job and wait for completion before firing the main pipeline.

3) Pre-stage data into staging tables
- If extraction from a remote source is slow, pre-copy data to your warehouse staging area (or cloud storage) earlier:
  - Use Matillion’s load components to stage files into staging tables (S3 -> Snowflake/Redshift/GCS -> BigQuery).
  - Create pre-aggregated or denormalized staging tables that the transformation jobs consume directly.
- For incremental runs, apply CDC or incremental staging so only deltas are pre-copied.

4) Pre-compute expensive joins/aggregations
- Run a pre-compute transformation job that writes intermediate results to persistent tables (materialized views or summary tables) on a schedule. Main pipeline reads those instead of recomputing everything.
- Use Matillion transformation jobs to build those pre-calculated artifacts.

5) Coordinate in Matillion
- Use orchestration jobs to implement the warm-up sequence: Start/scale warehouse → warm queries → run “Run Transformation” to execute main job.
- Use “Run Orchestration” / “Run Transformation” components to chain jobs and ensure sequential execution.
- Use Wait/Timer components to enforce appropriate lead times or polling when necessary.
- Use Matillion’s API or external scheduler to trigger warm-up and then the main job if you prefer external orchestration.

6) Monitor and size the warm-up window
- Measure cold start times (resume/scale + cache load) and add a buffer. Automate the pre-run to start that amount of time before the scheduled main job.
- Log timings in Matillion job metadata and iterate until SLA is met.

Warehouse-specific notes
- Snowflake: rely on RESUME and ALTER WAREHOUSE for scaling; targeted scans help warm micro-partitions; consider result/materialized views or clustering keys.
- Redshift: resume/resize and run small scans so blocks are loaded to SSD; consider WLM and concurrency/queue settings.
- BigQuery: serverless; warming is mostly about cached query results and materialized views or sharded tables; use precomputed tables rather than trying to “wake” compute.
- Synapse: resume DWU and run small queries to warm cache; scale up for heavy scheduled runs.

Operational advice
- Prefer warming only what you need (targeted partitions) to minimize cost.
- Automate scale-up and scale-down to control spend.
- Run periodic dry-runs to validate the warm-up remains effective after schema/volume changes.

Example sequence (Matillion orchestration job)
1. Execute SQL: ALTER WAREHOUSE prod_wh RESUME;
2. Execute SQL: ALTER WAREHOUSE prod_wh SET WAREHOUSE_SIZE = 'LARGE'; (if scaling)
3. Execute SQL: SELECT 1;
4. Execute SQL: SELECT COUNT(1) FROM analytics.orders WHERE order_date >= CURRENT_DATE - 7;
5. Run Transformation: main_transform_job
6. Execute SQL: ALTER WAREHOUSE prod_wh SUSPEND; or scale down

This pattern bounds pipeline latency by ensuring compute and the relevant data paths are active and any heavy extraction/aggregation work is pre-staged.

[Top](#top)

## How do you implement SLA tracking per pipeline and enforce deadlines or timeout policies for long steps?
Short answer
- Matillion doesn’t have a built‑in “SLA” object you can toggle per job; you implement SLA tracking and timeouts by wrapping pipelines in orchestration jobs (or an external scheduler) that record start/end, launch the real work via the Matillion REST API, poll status, and cancel/alert when a deadline is hit. Use job variables / a central SLA table for configuration and Matillion notification components (Email/Slack/PagerDuty) for alerts.

Implementation pattern (recommended)
1) Define SLA metadata
   - Store SLA per pipeline as a job variable, environment variable, or in a central configuration table (e.g., pipeline_name, max_runtime_seconds or deadline_timestamp, on_breach_action).
2) Start & register
   - Orchestration wrapper job:
     - Capture start_time.
     - Insert a record into an SLA tracking table (target DB / S3 / metadata store) with start_time, expected_end, status=RUNNING.
3) Launch pipeline and capture task id
   - Run the pipeline as a separate job by calling Matillion’s REST API (or using the “Run Orchestration/Transformation” component in non-blocking mode if you want background execution).
   - The REST call returns a task id (or job run id). Persist that in the SLA table.
4) Poll & enforce
   - Poll the Matillion REST API periodically (e.g., every 30–120s) to get task status and elapsed time.
   - Compare now (or elapsed) to SLA deadline. If exceeded:
     - Call Matillion REST API to cancel/abort the task.
     - Update SLA tracking record status=BREACHED, record breach_time and reason.
     - Fire alerts/notifications (Email/Slack/PagerDuty).
     - Optionally run compensating cleanup jobs.
5) On normal completion
   - Update SLA record status=SUCCESS/FAILED, record finish_time and duration.
   - Send success/failure notifications if required.

How to implement timeouts for long steps
- Break long steps into independent jobs (best practice). Each heavy or long-running component becomes a child job so you can apply per-step timeout and track it separately.
- Use the wrapper+poll pattern for each child job to enforce per-step timeout. That allows precise kill/alert per step.
- For DB queries: use the database driver/query timeout settings where available (e.g., JDBC/ODBC query timeout). If that’s not available, run the query in a child job and kill via Matillion API when exceeded.
- For commands/scripts: run them in a child job or call them from a Python/Bash component that includes its own process-level timeout logic.

Concrete components & APIs to use
- Matillion REST API to run jobs, retrieve task status and cancel tasks. Use a Python Script, Run Command or HTTP client component to call the API.
- Transformation/Orchestration Jobs as children (separate jobs for supervise-able units).
- Notification components: Email, Slack, PagerDuty to notify on breach or success.
- Database/target table to record SLA events for audit and reporting.

Example pseudocode (wrapper orchestration job)
- Variables: pipeline_name, max_runtime_seconds
- Steps:
  1. start_time = now(); expected_end = start_time + max_runtime_seconds
  2. call POST /run-job (returns task_id). insert into sla_table (pipeline_name, task_id, start_time, expected_end, status=RUNNING)
  3. loop:
       sleep(poll_interval)
       status = GET /task-status(task_id)
       if status == FINISHED:
         update sla_table set status=SUCCESS, end_time=now()
         break
       if now() > expected_end:
         POST /cancel-task(task_id)
         update sla_table set status=BREACHED, breach_time=now()
         call notification component
         break
4. exit wrapper (success or failure accordingly)

Best practices
- Make SLA values configurable per environment and pipeline (job variables or central table).
- Keep polling interval reasonable (don’t poll too frequently).
- Make child jobs idempotent so a forced stop and re-run are safe.
- Record detailed audit info: task id, host, start/end timestamps, exit codes, breach reason.
- Integrate with external monitoring (CloudWatch / Datadog / ELK) using the SLA table or Matillion logs for dashboards/alerts.
- Implement compensating cleanup for partial data or locks on SLA breach.

Failure/edge-case handling
- Handle REST API transient failures with retries and exponential backoff when polling or cancelling.
- If cancel fails, escalate (send high-priority alert) and mark SLA as breached.
- Consider a “soft breach” notification before forced cancel (notify owners, give manual override).

This pattern gives per‑pipeline SLA tracking, per‑step timeouts by splitting work into supervise-able jobs, reliable audit records, and automated enforcement (cancel + alert) using Matillion tooling and its REST API.

[Top](#top)

## How do you implement retry with exponential backoff and jitter for transient warehouse/storage/API errors?
Short answer
- Implement retries at the orchestration level with a controlled loop: detect a transient error, retry up to N times, wait between tries using exponential backoff with jitter, then fail or open a circuit.
- In Matillion the usual ways are: implement the loop with orchestration components (variables, If/Repeat/While patterns, Wait), or implement the retry logic inside a Python Script or Run Command component for API calls/complex logic. Use environment/job variables for configuration, log attempts, and ensure idempotency.

Why exponential backoff + jitter
- Exponential backoff reduces request rate after failures so you don’t amplify overload.
- Jitter prevents synchronized retries (“thundering herd”) by randomizing waits.

Key design rules
- Classify transient vs permanent errors (HTTP 429 & 5xx, DB deadlocks/timeouts, storage throttling → transient; 4xx client/auth errors → usually permanent).
- Limit retries (typical 3–8 attempts).
- Cap maximum backoff (e.g., 30s–2m).
- Add jitter (full jitter or equal jitter recommended).
- Enforce per-attempt timeout and a total timeout.
- Make operations idempotent or detect/undo duplicates.
- Log attempt number, wait interval, and error details to job logs and metrics.

Jitter strategies (implement one)
- Full jitter (recommended by AWS): sleep = random(0, base * 2^attempt)
- Equal jitter: sleep = base * 2^(attempt-1) / 2 + random(0, base * 2^(attempt-1) / 2)
- Decorrelated jitter: sleep = min(cap, random(base, previous_sleep * 3))

Recommended defaults
- base = 500 ms to 1 s
- max_attempts = 4–6
- cap = 30s–60s
- per-attempt timeout = depends on API/warehouse (e.g., 60–120s)
- total timeout = max_attempts * (avg_attempt_time + avg_backoff)

Matillion implementation options

1) Orchestration-level loop (no custom code)
- Use job variables: attempt (int), max_attempts, base_backoff_seconds, cap_seconds.
- Flow:
  1. Set attempt = 1.
  2. Call target component (Execute Orchestration / Run Command / Query).
  3. On success -> continue downstream.
  4. On failure -> route to a component that inspects the error (If component or Python to parse error) and decide transient vs permanent.
  5. If permanent -> fail.
  6. If transient and attempt < max_attempts -> compute sleep_seconds using exponential backoff + jitter (Calculator or Python), Wait for that duration, increment attempt, go back to step 2.
  7. If attempt >= max_attempts -> fail/notify.
- Use Wait component for sleep and “If” to branch by response.

2) Python Script component (recommended for API calls or precise control)
- Implement retry loop and jitter inside Python; it gives better control for parsing HTTP codes and handling timeouts.
- Expose config via Matillion environment/job variables.
- Example Python pseudo-code (use inside Python Script component):

  import os, time, random, requests

  base = float(os.environ.get('BASE_BACKOFF', '0.5'))  # seconds
  cap  = float(os.environ.get('MAX_BACKOFF', '30'))
  max_attempts = int(os.environ.get('MAX_ATTEMPTS', '5'))

  def is_transient(status, resp_text):
      if status is None:
          return True
      if status >= 500 or status == 429:
          return True
      # add vendor-specific checks (SQL states, error messages)
      return False

  attempt = 1
  while attempt <= max_attempts:
      try:
          resp = requests.get('https://api.example.com/endpoint', timeout=30)
          if resp.ok:
              print('OK')
              break
          elif not is_transient(resp.status_code, resp.text):
              raise Exception(f'Permanent error: {resp.status_code}')
      except Exception as e:
          transient = is_transient(getattr(e, 'response', None) and e.response.status_code, str(e))
          if not transient:
              raise
      # compute full jitter backoff
      sleep = random.random() * min(cap, base * (2 ** (attempt - 1)))
      print(f'Attempt {attempt} failed, sleeping {sleep:.2f}s')
      time.sleep(sleep)
      attempt += 1
  else:
      raise Exception('Max retry attempts reached')

3) SQL/Query components against warehouses
- Wrap the SQL call in an orchestration loop as above.
- Classify errors using SQLSTATE or looking at exception messages (deadlock, query cancelled, resource exceeded).
- For idempotent loads: use staging + merge; don’t commit until final success or implement unique run IDs to avoid duplicates.

4) HTTP Query component with retry
- HTTP Query has limited built-in retry behavior. For robust exponential backoff use Python Script or Run Command (curl + shell loop) which lets you implement backoff/jitter.

Other operational practices
- Circuit breaker: if many failures in short time, stop retries and alert (avoid repeated expensive attempts).
- Metrics & alerts: emit attempt counts, failure reasons, and durations to your monitoring (CloudWatch, Datadog). Matillion job logs can be scraped.
- Use job/environment variables for all tunables (max attempts, base, cap, timeouts).
- Respect vendor rate limits and read any Retry-After header (prefer server-specified wait if present).
- Use backoff only for idempotent or safely retryable operations.

Error classification examples
- HTTP: 429, 500–599 => transient; 401/403/400 => usually permanent.
- Snowflake/Redshift/BigQuery: lock, timeout, resource busy, transient network => transient; syntax error or missing table => permanent.
- S3: 5xx or throttling => transient.

Summary implementation checklist for Matillion
- Choose orchestration loop or Python Script depending on complexity.
- Expose settings via job/env variables.
- Classify transient errors precisely.
- Use exponential backoff with jitter (full jitter recommended).
- Cap wait, cap attempts, enforce timeouts.
- Make operations idempotent and log everything.
- Use circuit breaker and alerts for repeated failures.



[Top](#top)

## How do you validate schema before load and reject or quarantine records that fail constraints?
Short answer: do row-level validation in the transformation, or load into a permissive staging area and validate with SQL (or use the target DB’s bulk-load error options). Route valid rows to the target and write invalid rows to a quarantine store with an error/reason column so they can be audited and replayed.

How to implement in Matillion (practical options)

1) Row-level validation inside a Transformation job (recommended for predictable, explainable failures)
- Pipeline pattern:
  - Source -> Calculator(s) to create validation flags and an error_reason column (one rule per check or a concatenated message).
  - Filter (or multiple Filters) split the stream into valid and invalid outputs.
  - Valid output -> Table Output to target table.
  - Invalid output -> Table Output to a quarantine table (or write to S3 using S3 Put / S3 Load).
- Advantages: immediate routing, simple to monitor, easy to add business rules.
- Typical checks implemented with Calculator expressions:
  - numeric: is_numeric or regex match for digits (or CAST safe functions where available)
  - length: LENGTH(col) <= N
  - mandatory: col IS NOT NULL AND TRIM(col) <> ''
  - enum: col IN ('A','B','C')
  - date: use parsing functions or DB-specific TRY_* functions if available
- Add metadata columns (source filename, row_number, job_run_id, validation_timestamp) before quarantine so you can debug and reprocess.

2) Staging-first and validate with database SQL (good for bulk loads and heavy validation logic)
- Load source into a staging table with broad types (VARCHAR/VARIANT).
- Run an orchestration SQL step (DB Query component) to:
  - INSERT INTO target SELECT ... WHERE validation passes (using safe casts/TRY functions), and
  - INSERT INTO quarantine SELECT original_row, reason FROM staging WHERE validation fails.
- Use DB-specific safe-cast / try functions to detect invalid conversions:
  - Snowflake: TRY_CAST(col AS NUMBER), TRY_TO_TIMESTAMP(col,'fmt'), or TRY_PARSE -> returns NULL on failure
    - Example: WHERE TRY_CAST(a AS INTEGER) IS NOT NULL AND TRY_TO_TIMESTAMP(b,'YYYY-MM-DD') IS NOT NULL
  - BigQuery: SAFE_CAST(col AS INT64) (returns NULL if invalid)
  - Redshift: no TRY_CAST — use regex or CASE WHEN (e.g., col ~ '^[0-9]+$' for integers) or write PL/pgSQL/COPY error capture; load to VARCHAR then validate via regex/CASE.
- Advantages: leverages DB power for complex joins/constraints, easier for large volumes.

3) Use target DB bulk-load error features where available (useful for file loads)
- Snowflake COPY INTO: use VALIDATION_MODE=RETURN_ERRORS or ON_ERROR options and/or stage bad files; you can preview errors and capture rejected rows.
- Redshift COPY: errors get logged to stl_load_errors; you can set MAXERROR and inspect error logs or use a staging load and parse stl tables.
- BigQuery load jobs provide error details and can be configured to skip invalid rows; you can inspect job.errors.
- In Matillion: use the relevant Load component (Snowflake Bulk Load, Redshift Bulk Load, BigQuery Load), then parse the returned job result or error table and move those rows to a quarantine location.

Quarantine practices and metadata
- Quarantine store: a database table (quarantine table) or object storage (S3/GCS) with one row per rejected record plus:
  - reason(s) for rejection (human-readable and/or code)
  - original payload (full row as JSON or original columns)
  - source_file, row_number, job_run_id, timestamp
- Make quarantine auditable and replayable: include a reprocess flag and minimal transform job that reads quarantine rows, fixes, and reinserts.
- Keep small partitioned quarantine tables/files for performance.

Example Matillion pipeline (concise)
- Orchestration: Download file(s) -> Transformation job
- Transformation:
  - Input -> Calculator: add is_valid_int = REGEXP_MATCH(col,'^[0-9]+$'), parsed_date = TRY_TO_TIMESTAMP(date_col,'YYYY-MM-DD') (use DB-specific logic) -> Calculator: error_reason = CASE WHEN NOT is_valid_int THEN 'bad_int' WHEN parsed_date IS NULL THEN 'bad_date' ELSE NULL END
  - Filter1 (error_reason IS NULL) -> Table Output (target)
  - Filter2 (error_reason IS NOT NULL) -> Table Output (quarantine)

Monitoring and alerting
- After load steps, use Row Count components or Orchestration “If” checks on returned counts to fail job or raise alerts when quarantine_count > 0.
- Persist job_run_id and counts to a job_audit table for SLA tracking.

Summary checklist
- Decide where to validate: in-pipeline (fast feedback) vs staging+SQL (DB-level robustness) vs bulk-load error handling (leverages DB loader).
- Implement clear rule logic and capture a reason column.
- Route invalid rows to quarantine with full context.
- Provide tooling to inspect and reprocess quarantined rows.
- Use DB-specific safe-cast/try functions where possible to simplify validation.

[Top](#top)

## How do you remediate malformed files and partial loads using copy error tables and retry logic?
Pattern: let the warehouse COPY ingest the good rows while capturing the bad rows, then use Matillion orchestration to examine the error table/logs, attempt automated fixes or retries for the failing files/rows, and quarantine/alert when retries exhaust. Key elements: COPY options that return errors, an error table or system log, a file-tracking table, idempotent staging/merge, and a Matillion retry loop.

Concrete steps and implementation pattern

1) Configure COPY to allow partial loads and capture errors
- Use COPY options so good rows load and errors are recorded instead of aborting the job:
  - Snowflake: ON_ERROR = 'CONTINUE' (or VALIDATION_MODE to surface errors), or use the warehouse’s error table/logging features.
  - Redshift: COPY with MAXERROR and check stl_load_errors / svl_load_errors.
  - BigQuery: load job with skipInvalidRows=true and inspect job.errors.
- Target a staging table for the good rows, not the final production table, so partial loads are isolated and idempotent.

2) Capture and persist error details
- Persist the COPY error details to an error table (or query system error tables) with these columns: source_file, row_number (if available), error_code, error_message, load_timestamp, attempted_format_options.
- Also record file-level status in a file-tracking table (file_name, source_path, load_attempts, last_status, last_error_summary, processed_at).

3) Matillion orchestration: detect failures and iterate per-file
- Orchestration job pattern:
  - Get list of files to load (S3/GCS list or metadata table).
  - For each file (use Iterator or Table Iterator), attempt a file-specific COPY INTO target_staging (pass FILEs or pattern).
  - After the COPY, run a SQL check that queries the error table or system log to see if error_count > 0 for that file.
  - If error_count = 0 → mark file processed and MERGE/UPSERT staging into production.
  - If error_count > 0 → push error rows to a quarantine area and/or record errors in file-tracking table, then enter retry logic.

4) Retry logic (Matillion implementation)
- Use Matillion variables: attempts (int), max_attempts (configurable), backoff_seconds (optional).
- Loop logic:
  - Initialize attempts = 0.
  - While attempts < max_attempts:
    - Run COPY for the single file.
    - Query error log for that file.
    - If no errors: break and continue to merge.
    - Else attempts = attempts + 1; optionally modify COPY options (e.g., try a different file format, change DATE_FORMAT or TRIM_SPACE, adjust escape settings) or run a quick remediation transform (see next).
    - Wait backoff_seconds before next try (use Wait component).
  - If attempts == max_attempts and still failing → move file to quarantine bucket/prefix, insert detailed error rows into an error store, set last_status = 'FAILED', and trigger alert (Email/Slack).

5) Automated remediation steps you can attempt before giving up
- Relax or adjust file format parameters (change date format, set trim_space, change escape or null_if).
- Convert file encoding (UTF-8 vs Latin1) or remove bad characters.
- Pre-parse and cleanse file with Matillion Python Script or Cloud Function: detect and drop malformed rows or fix column counts, then rewrite a cleaned file and re-run COPY.
- If errors are a small subset of rows, isolate and load good rows (which COPY with ON_ERROR already does), and persist the bad rows for manual review.

6) Handling partial loads and ensuring idempotency
- Load first into a staging table with a file_name and load_batch_id column.
- Use MERGE/UPSERT into the production table keyed by primary key and load_batch_id to avoid duplicate rows on retries.
- Use transactional or atomic swap pattern: if your warehouse supports it, stage data into a staging table and only swap/merge when the file has been fully processed or validated.
- Keep a table of processed file_names to avoid reprocessing a previously-completed file.

7) Monitoring, alerting, and remediation workflow
- Push error detail rows and file-level failures to a central error schema or object store.
- Send alerts when a file hits max_attempts, including file path, error_summary, and link to the quarantined file.
- Provide a manual remediation workflow: a Matillion job that accepts a quarantined file, runs cleansing rules, and attempts re-load.

Minimal Matillion component map
- Get Metadata / S3 List (list files)
- Iterator / Table Iterator (per-file loop)
- Run SQL Script / Snowflake Bulk Load / Copy Components (execute COPY)
- Run Query component to check error table / system logs
- If / Switch (branch on error_count)
- Set Variable / Wait / Retry loop
- Move S3 File / Put File (quarantine)
- Python Script (optional cleansing)
- Orchestration job to chain to transformation (MERGE) job

Example pseudo-flow (per-file)
1. attempts := 0
2. while attempts < max_attempts:
   - Run COPY FOR file X with ON_ERROR=CONTINUE into staging
   - SELECT COUNT(*) FROM error_table WHERE file_name = X → err_cnt
   - if err_cnt = 0:
       - MERGE staging rows for X into target
       - mark file processed, break
     else:
       - attempts += 1
       - Optionally run automated cleanse or tweak COPY options
       - wait backoff
3. if err_cnt > 0 after max_attempts:
   - MOVE file X to quarantine
   - INSERT error rows into error_store
   - ALERT/LOG failure

Notes and best practices
- Prefer per-file COPY (or small batches) so you can precisely identify and retry problematic files.
- Keep COPY idempotent and use staging + MERGE to avoid duplicates on retry.
- Centralize error captures so remediation jobs can act deterministically.
- Start with conservative max_attempts (2–3) and automated fixes that are safe (e.g., trimming whitespace, changing encoding). Escalate to manual review only when automated remediation fails.

This pattern gives you deterministic partial loads (good rows land), clear error records for bad rows, automated retries with configurable remediation attempts, and safe handling (quarantine + alert) when automated retries fail.

[Top](#top)

## How do you manage time-partitioned data and retention policies and automate partition pruning/cleanup?
Approach overview (Matillion-centric)
- Treat retention/partition cleanup as an orchestration job that runs on a schedule or is event-triggered.
- Use job variables (retention_days, cutoff_date, environment) so the same job works across environments.
- Use a query to list candidate partitions (or S3/GCS prefixes) older than cutoff, iterate over the list, perform safe delete/drop actions, record outcomes to an audit table, and optionally run compaction/optimize/vacuum.
- Use built-in components: SQL/connector Query components, Iterator, If/Branch, Python Script (for complex logic or API calls), S3/GCS List & Delete, Run Command, and notification components.

Typical Matillion orchestration flow
1. Calculate cutoff_date variable (e.g., current_date - retention_days).
2. Run a "List partitions" query or storage-list component:
   - For SQL warehouses: SELECT DISTINCT partition_col FROM table WHERE partition_col < :cutoff_date
   - For object store: list S3/GCS prefixes with S3 List / GCS List
3. Capture results into a Table or use the Iterator over the result set.
4. For each partition:
   - Validate (sanity checks, rowcount, min/max date) and log to audit table.
   - Execute platform-appropriate drop/delete action (Run Query, S3 Delete, API call).
   - Optionally compact/rebuild/optimize the table after a threshold of deletions.
   - Insert an audit record of success/failure and number of rows/files removed.
5. Post-cleanup: run maintenance (VACUUM/ANALYZE, OPTIMIZE, compaction) if required by the engine.
6. Send final job status/alerts.

Platform-specific patterns and concrete examples

BigQuery
- Best option: use partitioned tables and set partition_expiration_days at table creation or via ALTER TABLE to let BigQuery auto-expire partitions.
- Matillion implementation when manual removal needed:
  - Query example: DELETE FROM dataset.table WHERE _PARTITIONDATE < DATE_SUB(CURRENT_DATE(), INTERVAL @retention_days DAY)
  - Or use partition filter: WHERE _PARTITIONTIME < TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL @retention_days DAY)
  - Use BigQuery Query component; schedule job or use Table Iterator on INFORMATION_SCHEMA.PARTITIONS if enumerating.
- Advantage: partition expiration is cheaper and automatic; avoid full-table scans.

Snowflake
- Snowflake uses micro-partitions; no explicit partition DROP. Implement retention by deleting rows older than cutoff:
  - DELETE FROM schema.table WHERE date_col < DATEADD(day, -:retention_days, CURRENT_DATE());
- After large deletes, reclaiming storage for immediate usage is limited by Time Travel:
  - Set DATA_RETENTION_TIME_IN_DAYS appropriately for clones and time travel.
  - Re-clone or CTAS (CREATE TABLE AS SELECT) to rebuild a compacted copy if you need immediate physical reclamation: CREATE OR REPLACE TABLE schema.table AS SELECT * FROM schema.table WHERE date_col >= cutoff;
- Matillion: use Snowflake Query component to run DELETE or CTAS; use Python for complex orchestration; log deletions to audit table.

Redshift (managed tables) and Redshift Spectrum (S3 partitions)
- Redshift managed tables: DELETE ... WHERE date_col < cutoff; then VACUUM and ANALYZE:
  - DELETE FROM schema.table WHERE date_col < :cutoff_date; VACUUM; ANALYZE;
- Redshift Spectrum / external tables on S3:
  - Partitions are S3 prefixes + Glue/Athena catalog entries. Use S3 List/Delete for files and Glue API/Athena to drop partitions.
  - Matillion pattern: use S3 List to find prefixes older than cutoff -> S3 Delete to remove files -> run an external catalog update (via Glue API or run an ALTER TABLE DROP PARTITION via Athena).
- Matillion: use Run Command to call AWS CLI, Python Script to call boto3, or use the JDBC/ODBC components against Athena/Glue to update partitions.

Delta Lake / Databricks
- Partition prune is automatic if queries filter on partition column. For retention:
  - DELETE FROM table WHERE date_col < cutoff;
  - OPTIMIZE table WHERE date_col >= ??? (or full OPTIMIZE) to compact files.
  - VACUUM table RETAIN 168 HOURS (or other value) to remove old files (respecting time-travel retention).
  - Or use ALTER TABLE DROP PARTITION if small number of partitions you can remove by partition metadata.
- Matillion: use Databricks/Delta SQL or Spark Job components; run Python/Notebook if needed. Use Iterator for partition names and then execute DROP PARTITION.

Azure Synapse / SQL Server partitioned tables
- Use partitioned tables and sliding-window pattern:
  - SWITCH OUT old partition into staging table, then DROP staging table (fast metadata operation).
  - If SWITCH not available for the external engine, DELETE then REBUILD indexes.
- Matillion: run T-SQL via Synapse connector; orchestrate SWITCH operations, then drop staging; maintain audit.

S3/GCS-based time-partitioned files (external tables or lakehouse)
- List prefixes older than cutoff (S3 List / GCS List), delete files (S3 Delete/GCS Delete), then update external metastore (Glue/Athena/Hive) to remove partitions.
- Matillion: use built-in S3 components or Python/Boto3 to remove prefixes and call Glue/Athena for partition metadata changes. Use iterators for bulk deletes and ensure idempotency.

Automation, safety, and best practices
- Use variables for retention and cutoff so changes are controlled via environment/config.
- Dry-run mode: add a flag to only log partitions that would be deleted.
- Audit and logging: record partition name, rows/files removed, timestamp, user/job id, and checksum if needed.
- Idempotency: make script safe to re-run; use transactions where supported; use partition-level DROP or SWITCH for atomicity.
- Backups & Time Travel: understand and respect Time Travel (Snowflake) or versioning (Delta) when expecting immediate space reclamation.
- Throttle/Batch deletes: avoid long-running table locks or spikes; process partitions in batches and schedule out-of-hours if needed.
- Notifications & alerts: send success/failure messages via Matillion notification/Slack/email integrations.
- Test on staging first: validate partition selection logic and retention values in non-prod.

Example Matillion component mapping (high-level)
- Variables: retention_days, cutoff_date, dry_run, batch_size
- Components:
  - Calculator / Python to set cutoff_date
  - Query component to list partitions (or S3/GCS List)
  - Iterator over result rows
  - Within iterator:
    - If (dry_run) -> Log only
    - Else -> Run Query / S3 Delete / API call to drop partition
    - Run Query to insert audit record
  - Post-loop: Run maintenance SQL (VACUUM/OPTIMIZE/ANALYZE) as needed
  - Email/Notification component for job result

Summary of recommended choices
- Prefer native partition-expiration settings when available (BigQuery partition_expiration_days).
- For data warehouses that require deletes, do per-partition deletes and rebuilds (Snowflake CTAS, Redshift VACUUM).
- For file-based partitions, delete files and sync the metastore (Glue/Athena/Hive).
- Implement this as a parameterized Matillion orchestration job with auditing, dry-run, batching, and post-cleanup maintenance.

[Top](#top)

## How do you compress and encode data optimally for the target warehouse (ZSTD, Snappy, GZIP, column encodings)?
Short answer
- Prefer columnar file formats (Parquet/ORC/Avro) over CSV for analytic warehouses. Use Snappy for fastest CPU throughput and fast parallel reads, ZSTD for better compression ratio (and often similar or better decompression speed), GZIP only when compatibility or max compression ratio is needed despite CPU cost. Column encodings are warehouse-specific — Redshift exposes encodings (use ANALYZE COMPRESSION to decide), Snowflake/BigQuery manage physical encodings themselves.

Details and recommended settings by target

Snowflake
- Files: Parquet (preferred) or compressed CSV/JSON if necessary.
- Compression: ZSTD or Snappy for Parquet. ZSTD gives best size + speed tradeoff; Snappy gives predictable low CPU overhead. Snowflake supports ZSTD, GZIP, BROTLI, etc.
- Column encodings: Not user-controlled. Snowflake does micro-partitioning and columnar storage automatically. Use clustering keys or materialized views for query performance where needed.
- Matillion implementation: Use a "Create File" / "Write Parquet" or S3 Put component to write Parquet + Compression=ZSTD/SNAPPY. In the Snowflake Load component or CREATE FILE FORMAT use TYPE=PARQUET COMPRESSION='ZSTD' (or 'SNAPPY').

Amazon Redshift (including Serverless)
- Files: Parquet preferred. COPY from Parquet/ORC is efficient; can also COPY from compressed CSV.
- Compression: Parquet+Snappy or Parquet+ZSTD. For COPY from text files use GZIP/LZO/LZOP if required. Parquet with Snappy yields fast parallel loads; ZSTD improves compression ratio and can reduce I/O.
- Column encodings: Redshift exposes ENCODEs. Best practice:
  - Run ANALYZE COMPRESSION on representative data to get suggested encodings.
  - Typical choices: low-cardinality VARCHAR -> BYTEDICT; high-cardinality VARCHAR -> ZSTD or LZO; integers with sequential patterns -> DELTA/DELTA32K; floats -> AZ64 (or RAW if unsupported); repeated values -> RUNLENGTH.
  - You can let COMPUPDATE ON during COPY to auto-select encodings, then create table DDL from recommendations.
- Matillion implementation: Use Redshift Bulk Load / S3 Load component. Write Parquet files (Compression=SNAPPY/ZSTD). In the COPY options set FORMAT AS PARQUET or specify GZIP for CSV. After load, run ANALYZE COMPRESSION and apply recommended ENCODEs in table DDL.

Google BigQuery
- Files: Parquet or Avro preferred; BigQuery handles columnar storage internally.
- Compression: Parquet/Avro + Snappy is the common default (fast). GZIP gives smaller files but slower load. BigQuery storage is columnar and optimized; file compression affects load/ingest time and storage transfer cost.
- Column encodings: Not exposed. BigQuery chooses internal encodings; optimize via schema types (use INTEGER/TIMESTAMP/NUMERIC instead of STRING).
- Matillion implementation: Use Write Parquet/Avro to GCS with Compression=SNAPPY/ZSTD if supported, then use the BigQuery Load component to load from GCS.

Azure Synapse / Azure SQL Data Warehouse
- Files: Parquet/ORC for PolyBase loads.
- Compression: Parquet + Snappy is commonly used for performance; ZSTD can be used if supported in your stack.
- Column encodings: For Dedicated SQL Pools, columnstore compression is automatic; rowstore tables can use page or row compression. For best results use columnstore and appropriate distribution/sort keys.
- Matillion implementation: Write Parquet to ADLS/S3 and use PolyBase or COPY to load; choose compression=SNAPPY/ZSTD in file write components.

General rules & best practices (applies across warehouses)
- Prefer columnar formats (Parquet/ORC/Avro) over CSV/JSON for analytic warehouses.
- Choose compression by trade-off:
  - Snappy: fastest read/write CPU; good for heavy parallel IO and query latency.
  - ZSTD: best overall ratio and often similar or better decompression speed; good when network/I/O is the bottleneck.
  - GZIP: best compression ratio in some cases but high CPU and non-splittable in many contexts; avoid for very large single files.
- File sizing and parallelism: Aim for many reasonably sized files so the target can parallelize loads. Common guideline: 64–512 MB compressed per file (Snowflake often recommends ~100–250 MB compressed). Too many tiny files cause load overhead; one big file limits parallelism.
- Row-group / Parquet block sizing: Use 50–256 MB row groups to get good compression and read performance.
- Data types and pre-encoding: Use native types (ints, timestamps, booleans) instead of strings to improve compression and query performance.
- Use warehouse tooling to pick encodings:
  - Redshift: run ANALYZE COMPRESSION and apply ENCODE recommendations.
  - Snowflake/BigQuery: rely on micro-partitions/internal encodings; focus on proper data types, partitioning, clustering keys.
- Loading workflow in Matillion:
  - Produce Parquet/ORC with Compression=SNAPPY or ZSTD in a transformation job.
  - Push files to staging (S3/GCS/ADLS) with Matillion connectors.
  - Use the appropriate Load/Bulk component (Snowflake Load, Redshift Bulk Load, BigQuery Load, Synapse COPY/PolyBase) and set FORMAT/COMPRESSION parameters.
  - After load, run VACUUM/ANALYZE (Redshift) or run statistics gathering where applicable.
- Test with a representative sample: run cost/performance tests comparing Snappy vs ZSTD vs GZIP on your data and query patterns; test different file sizes and rowgroup sizes.

Concrete examples (commands)
- Snowflake file format: CREATE OR REPLACE FILE FORMAT pf TYPE = 'PARQUET' COMPRESSION = 'ZSTD';
- Redshift COPY from Parquet: COPY schema.table FROM 's3://bucket/prefix' IAM_ROLE 'arn:...' FORMAT AS PARQUET;
- Redshift column encoding in DDL: CREATE TABLE t (id INT ENCODE DELTA, name VARCHAR(200) ENCODE BYTEDICT, value DOUBLE PRECISION ENCODE AZ64);

Summary checklist for Matillion pipelines
- Write Parquet (or ORC/Avro) from Matillion Transform, set Compression=SNAPPY (fast) or ZSTD (better ratio).
- Target-specific: instruct Load component to expect Parquet and compression type; use COPY/LOAD options.
- After initial loads, run warehouse-specific compression/analysis tools (Redshift ANALYZE COMPRESSION; Snowflake clustering) and apply any recommended DDL changes.
- Tune file sizes, rowgroup sizes and test performance with real workloads.

[Top](#top)

## How do you write quality-of-service tests to guard against performance regressions after job changes?
High-level approach
- Treat Matillion jobs like any other software: define measurable performance SLAs, create repeatable tests that exercise representative workloads, run them automatically on job changes, and fail merges when regressions exceed pre-defined thresholds.
- Use a combination of Matillion execution metadata, target-warehouse query/plan/usage data, and pipeline-level timings to get reliable, component-level signals.

What to measure
- End-to-end job wall-clock runtime.
- Per-component run-times inside Matillion (SQL components, Python/Bash, transforms).
- Key query metrics from the target warehouse: query elapsed time, rows processed, bytes scanned, query plan / EXPLAIN output.
- Throughput: rows/sec or MB/sec for heavy loads.
- Resource / cost metrics: Snowflake credits, Redshift CPU/IO, BigQuery slot usage.
- Percentiles (p50, p95, p99) and variance, not just averages.

How to build the tests
1. Define baselines and thresholds
   - Run your job on a representative dataset (full or scaled) to create baseline metrics.
   - Define acceptance criteria (absolute thresholds or percent increase: e.g., p95 runtime must not exceed baseline by more than 20%). Store baselines in a table or artifact repository.

2. Create deterministic test data
   - Use masked or synthetic production-like snapshots that are stable between runs. Keep data volume representative or scale it deterministically (e.g., 10% sample with scaling factor).
   - Ensure data distribution preserves cardinality/skew so performance behavior is faithful.

3. Automate job run + metric collection
   - Trigger Matillion jobs programmatically via Matillion’s REST API or CI integration.
   - Collect Matillion execution metadata (start/end times, component durations, execution logs). Persist these to a metrics DB or S3.
   - Pull query execution details from the target warehouse (e.g., Snowflake QUERY_HISTORY/ACCOUNT_USAGE, Redshift STL_QUERY/STL_WLM_QUERY, BigQuery job metadata) to capture query-level latency and resource usage.
   - Optionally instrument the job with timestamp writes (Python/Bash tasks or SQL writes to an audit table) to get fine-grained timing where Matillion metadata is insufficient.

4. Compare against baseline and detect regressions
   - Compare the same metrics against stored baselines using clear rules: absolute, relative, and percentile-based.
   - Apply statistical smoothing (rolling median or historical percentiles) to avoid false positives from noisy outliers.
   - Fail the CI pipeline or block merges when thresholds are breached.

5. Examine query plans and diffs
   - Automate EXPLAIN/PROFILE capture for critical SQL produced by Matillion components before and after changes.
   - Detect changes in join order, plan operators, or large scans. Flag plan regressions even if runtime doesn’t immediately spike.

6. Test concurrency and scale
   - Run concurrent instances or synthetic load to validate WLM and concurrency behavior.
   - Test on different warehouse sizes to check scaling characteristics and cost tradeoffs.

7. CI/CD integration
   - Run performance tests on PRs or on merge-to-main using your CI (Jenkins/GitLab/GitHub Actions).
   - Deploy Matillion job changes to a test environment automatically (using Matillion Git or API), run the performance suite, and gate merges on results.

8. Alerting, visualization and historical tracking
   - Store results over time in a metrics store and visualize trends (Grafana, Looker, etc.).
   - Configure alerts for trend-based regressions and repeated small degradations which accumulate over time.

Practical tips specific to Matillion
- Use Matillion’s REST API to trigger jobs and to pull execution logs and metadata programmatically.
- Capture component-level times: Matillion execution history has component timings; if finer detail is needed add timestamp writes from Python/Bash tasks or use a small “audit” SQL component to record start/finish for critical steps.
- If SQL components are auto-generated or complex, extract the SQL and run EXPLAIN/PROFILE in the warehouse to compare plans.
- Keep job-run environment consistent: same warehouse size, concurrency settings, and network locality. Differences here cause noisy measurements.
- For noisy environments, prefer p95 or p99 over p50 and run multiple iterations to compute stable statistics.

Example testing workflow (concise)
1. CI job triggers Matillion job via API on a dedicated test warehouse.
2. Test job runs against deterministic dataset (e.g., scaled snapshot).
3. CI collects Matillion execution metadata + target-warehouse query stats and EXPLAINs.
4. CI compares results to stored baseline rules (e.g., p95_time <= baseline * 1.2).
5. If failed, CI posts detailed component-and-query diffs to the PR and blocks merge.

Common failure modes to detect
- New full-table scans replacing indexed/filtered access.
- Additional joins or cartesian products introduced by component changes.
- Changes in data distribution (skew) that blow up join sizes.
- Unexpected materializations or staged writes increasing IO.
- Concurrency/WLM contention not visible in single-run tests.

Summary checklist for adoption
- Baseline dataset + stored baselines.
- Automated job invocation via Matillion API.
- Metric collection: Matillion logs + warehouse query history + audit timestamps.
- CI integration with pass/fail thresholds.
- EXPLAIN/plan capture and automated plan-diff where possible.
- Concurrency and scale tests for critical jobs.
- Historical dashboarding for trend detection.

[Top](#top)

## How do you simulate scale and concurrency in pre-prod to validate warehouse sizing and autosuspend policies?
High-level approach: reproduce realistic peak workloads in pre-prod by generating representative data and query patterns, run many concurrent Matillion jobs (or parallel steps) against a pre-prod warehouse instance sized like production, measure queueing/latency/credits and autosuspend/resume behavior, then iterate on warehouse size / multi-cluster settings / autosuspend timeout until metrics meet your SLAs.

Concrete steps

1) Define workload and success criteria
- Identify the workload mix: number of concurrent pipelines, long-running transforms (large joins, aggregations), short user/BI queries, and data-load patterns.
- Define target SLAs: 95th/99th percentile latency, throughput (rows/sec), max acceptable queue wait, credit spend budget, acceptable resume latency when autosuspend triggers.

2) Prepare representative data
- Use scaled-up copies of production schema if possible (anonymize if needed).
- If not available, generate synthetic data using:
  - TPC-DS / TPC-H datasets (scale factor).
  - Custom scripts to replicate table cardinalities and distribution skew.
- Stage data in the same storage format/profiles as prod (same file sizes, compression, partitioning).

3) Create test jobs in Matillion
- Build Matillion orchestration jobs that mirror production jobs (same SQL, same transformation logic, same number of tasks).
- For parallelism: split work into many smaller transformation jobs or use a parent orchestration job that triggers multiple transformation jobs concurrently.
- Use the “Start Job” / “Run Job” pattern in orchestration, or the Matillion REST API to kick off many independent job runs in parallel.

4) Drive concurrency at scale
- Use Matillion REST API or a simple script (Python, bash) to spawn N concurrent Matillion job runs. The REST API lets you pass variables so you can parameterize slices of data.
- Alternatively use the snowflake-connector / SnowSQL or JDBC scripts to open many concurrent connections and issue the same query patterns to emulate BI traffic.
- Ramp up concurrency in stages (ramp test): e.g., 10, 50, 100, 200 simultaneous jobs/queries, holding each steady for a period.

5) Test autosuspend and resume behavior
- Configure the warehouse autosuspend value to your candidate setting.
- Run a burst of activity, then let the warehouse go idle and observe whether it suspends at the expected timeout. Measure:
  - Time to suspend.
  - Time to resume on new workload (cold start latency).
  - Impact on first-run query latency (cold cache).
- Repeat for different autosuspend timeouts to evaluate trade-offs between cost savings and resume latency.
- For Snowflake specifically, test multi-cluster settings by setting MIN_CLUSTER=1, MAX_CLUSTER=N and observe scaling under concurrency spikes.

6) Capture metrics and logs
- From the data warehouse:
  - Snowflake: QUERY_HISTORY, WAREHOUSE_LOAD_HISTORY, ACCOUNT_USAGE views (or Snowsight Query Profile).
  - Redshift: STL_QUERY/STL_WLM/CONCURRENCY scaling metrics.
  - BigQuery: slot usage and reservation metrics.
- From Matillion: job run times, failed tasks, concurrency/timeouts from job history and logs.
- Cloud monitoring: CloudWatch / Stackdriver / Azure Monitor for CPU, network, disk, and Matillion instance metrics.
- Track credits/costs consumed during tests.

7) Analyze results and tune
- If you see queueing and long wait times, options:
  - Increase warehouse size (bigger cluster/node type).
  - For Snowflake, enable multi-cluster warehouses (increase MAX_CLUSTER) and tune MIN_CLUSTER.
  - For Redshift, increase node count or change WLM concurrency/queues.
  - Repartition or optimize the SQL (cluster keys, sort keys, distribution styles).
- If autosuspend/resume latency is unacceptable, consider:
  - Increasing autosuspend timeout to reduce resume frequency.
  - Keeping a small always-on warehouse for short queries and using larger warehouses for heavy ETL.
- Re-run the ramp tests to validate changes.

Practical tooling examples
- Use Matillion REST API to trigger many runs programmatically rather than manual UI starts.
- Use Python with the Snowflake connector in threads/processes to create synthetic concurrent SQL load.
- Use orchestration job loops and parallel components to simulate multiple pipelines started from a single Matillion job.
- Use load generators like JMeter (JDBC) when you need many concurrent lightweight queries.

Test plan template (recommended)
- Cold-cache single run to measure baseline.
- Warm-cache steady state (sustained load for X minutes).
- Ramp-up: increase concurrency across steps.
- Spike test: sudden jump to peak concurrency.
- Idle/resume cycles to exercise autosuspend/resume repeatedly.
- Run each test for enough time to capture steady-state metrics and variability.

Acceptance checklist
- 95th/99th percentile latencies within SLA under target concurrency.
- No unexpected queueing/error rates.
- Credit/cost profile within budget.
- Autosuspend suspends/resumes reliably; resume latency acceptable or mitigated by design.
- Scaling behavior predictable (multi-cluster / concurrency scaling works as expected).

Notes on cost and safety
- Run tests in a dedicated pre-prod account/warehouse to avoid impacting prod.
- Be mindful of credit consumption — ramp tests and sustained large-data operations can be costly.
- Use sampling and scaled-down tests where practical, but always validate at a full-scale step before production rollout.

[Top](#top)

## How do you tune Snowflake warehouse size, auto-suspend/auto-resume, and statement concurrency for Matillion workloads?
Key principles
- Treat warehouse sizing and concurrency as a policy problem: separate workloads (orchestration, bulk loads, transforms, BI) and tune each warehouse to the workload pattern rather than using one monolithic warehouse for everything.
- Measure first: use Snowflake ACCOUNT_USAGE / QUERY_HISTORY / WAREHOUSE_LOAD_HISTORY and Matillion query/job logs to identify whether queries are CPU-bound, I/O-bound, or being queued for concurrency.
- Use horizontal scaling (multi-cluster) for many short, concurrent queries. Use vertical scaling (bigger warehouse size) for few long, compute-heavy queries (large joins/aggregations).

How to tune warehouse size
- Start from observed query profiles:
  - If queries have long execution times with high compute (large shuffle, long CPU times), increase warehouse size (S → M → L → XL) until CPU-bound time drops and SLAs are met.
  - If many small queries are slow because they are queued, a larger single cluster won't help; use multi-cluster (auto-scale) to add clusters for concurrency.
- Typical pattern for Matillion:
  - Orchestration / control jobs: X-Small or Small.
  - Bulk COPY loads: Small→Medium (COPY is I/O/parallel load work—scale to finish within SLA).
  - Transformations (heavy SQL): Medium→2XL depending on dataset and join complexity.
- Use Snowflake query profile to check where time is spent (compile, scan, shuffle, output). If shuffle/compute dominate, scale up; if many queries are waiting, scale-out.

How to tune auto-suspend / auto-resume
- Auto-resume: ON (true) for Matillion-driven jobs so warehouses start on demand.
- Auto-suspend:
  - Low interactive/continuous workloads: 60–300 seconds to avoid paying for idle time.
  - Frequent bursts (many jobs within short intervals): use a longer suspend (300–900s) to avoid repeated resume delays and costs of frequent starts. Resume has a small latency and may add queuing at start; tune by observing frequency of resume events.
  - Batch nightly pipelines: set suspend to cover expected idle time between steps if jobs run in bursts to avoid repeated resumes.
- Use MATILLION orchestration timing: if orchestrator schedules sequential tasks with small gaps, extend suspend a bit so the warehouse stays up for the whole pipeline.

How to tune concurrency (multi-cluster / statement concurrency)
- Concurrency = (concurrency per cluster) × (number of clusters). Snowflake will queue statements if concurrency capacity is exhausted unless additional clusters can be started.
- For many short Matillion queries (lots of small transformations, many COPYs launched in parallel):
  - Use multi-cluster warehouse: set MIN_CLUSTER_COUNT = 1 and MAX_CLUSTER_COUNT to expected peak clusters (e.g., 2–10). Use SCALING_POLICY = 'STANDARD' for rapid scaling for spiky loads.
  - Monitor QUEUED_STATEMENTS and cluster spin-up events. If you see many QUEUED events, increase MAX_CLUSTER_COUNT.
- For few very heavy queries:
  - Prefer increasing warehouse size rather than many small clusters; a single large cluster gives more CPU/IO to a single query.
- Limit Matillion-side parallelism:
  - Control Matillion job parallelism (Parallel components, orchestration concurrency settings) so you don’t overwhelm the warehouse. If you use a single warehouse for multiple jobs, limit the number of concurrent child jobs to match warehouse capacity.
- Use separate warehouses for workloads that must not contend (e.g., critical transformations vs many small loads).

Practical commands (examples)
- Resize warehouse:
  ALTER WAREHOUSE my_wh SET WAREHOUSE_SIZE = 'LARGE';
- Change auto-suspend / auto-resume:
  ALTER WAREHOUSE my_wh SET AUTO_SUSPEND = 300;
  ALTER WAREHOUSE my_wh SET AUTO_RESUME = TRUE;
- Enable multi-cluster scaling:
  ALTER WAREHOUSE my_wh SET MIN_CLUSTER_COUNT = 1 MAX_CLUSTER_COUNT = 5 SCALING_POLICY = 'STANDARD';

Monitoring and iterative tuning
- Key Snowflake views:
  - SNOWFLAKE.ACCOUNT_USAGE.WAREHOUSE_LOAD_HISTORY (show load, queued time, average queued/active)
  - SNOWFLAKE.ACCOUNT_USAGE.QUERY_HISTORY for expensive queries and their warehouses
  - QUERY_HISTORY + QUERY_PROFILE for individual query bottlenecks
- Track: queued time, average credits per hour, cluster spin-up frequency, and Matillion job durations.
- Tune iteratively: change one variable at a time (size vs max clusters vs Matillion parallelism), run representative workloads, observe effects on runtime and cost.

Cost/control considerations
- Multi-cluster increases cost because concurrent clusters bill in parallel. Use MAX_CLUSTER_COUNT conservatively and rely on Matillion-side throttling if cost must be tightly controlled.
- Use Resource Monitors to cap runaway costs and alerts to detect unexpected scaling.
- Compare cost for scaling up vs scaling out—sometimes a single larger warehouse can be cheaper and more effective for heavy transforms than many smaller clusters.

Example recommendations (starting points)
- Dev/QA: X-Small warehouse, AUTO_SUSPEND=60, AUTO_RESUME=TRUE, single cluster.
- Regular ELT pipelines with moderate concurrency: Medium warehouse, AUTO_SUSPEND=300, AUTO_RESUME=TRUE, MIN=1 MAX=2–3 (standard scaling).
- High-concurrency pipelines (many small Matillion components run in parallel): Medium warehouse with MIN=1 MAX=5 (STANDARD), tune Matillion parallelism to avoid over-saturation.
- Heavy complex transformations: Large or XL warehouse, AUTO_SUSPEND=300–900, AUTO_RESUME=TRUE, single cluster (or small MAX if a mix of heavy + concurrent workloads).

Matillion-specific controls
- Use separate Snowflake connections/warehouses for different job types in Matillion projects.
- Reduce Matillion orchestration/component parallelism when you see Snowflake queued time; increase warehouse clusters/size only if necessary.
- Use Matillion job design (staging and then sequential transforms) to reduce concurrent heavy SQL running against a single warehouse.

Concise tuning workflow
1. Baseline: run representative Matillion job(s), capture query and warehouse load history.
2. Diagnose: decide if bottleneck is CPU/shuffle (scale up) or queuing/concurrency (scale out or reduce concurrency).
3. Change one setting (resize or adjust MAX_CLUSTER_COUNT or Matillion parallelism), retest under representative load.
4. Monitor costs and resume/suspend events; set auto-suspend to balance resume latency vs cost.
5. Lock critical workloads to dedicated warehouses where needed and use resource monitors.

No boilerplate: implement these steps using your Matillion job parallelism controls and Snowflake ALTER WAREHOUSE settings; iterate based on observed query profiles and warehouse load metrics.

[Top](#top)

## How do you tune BigQuery reservation slots and concurrency for Matillion-driven transformations?
High-level goal: size BigQuery slots to cover the peak aggregate slot demand from Matillion jobs, and limit Matillion’s parallelism so it doesn’t exhaust that reservation and cause query queuing (longer runtimes).

What to measure first
- Measure actual slot consumption by Matillion-driven queries:
  - BigQuery job-level metric: query_stats.total_slot_time (ms) in INFORMATION_SCHEMA.JOBS_* or BigQuery monitoring metrics. That value gives slot-ms consumed per job.
  - BigQuery Reservation UI / Cloud Monitoring: slot utilization (slots in use over time) and active slot count.
- Capture distribution: average slot usage per query, typical query durations, and peak aggregate slot-ms per minute (or per chosen interval).

Useful example SQL to estimate required slots (per-minute peak):
- Per-minute peak slot requirement:
  WITH per_min AS (
    SELECT
      TIMESTAMP_TRUNC(creation_time, MINUTE) AS minute,
      SUM(query_stats.total_slot_time) AS total_slot_ms
    FROM `region-us`.INFORMATION_SCHEMA.JOBS_BY_PROJECT
    WHERE creation_time > TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 1 DAY)
      AND job_type='QUERY'
    GROUP BY minute
  )
  SELECT
    minute,
    CEIL(total_slot_ms / (60*1000)) AS required_slots_for_that_minute
  FROM per_min
  ORDER BY required_slots_for_that_minute DESC
  LIMIT 10;

Sizing a reservation (practical formulas)
- Slot-seconds concept:
  - A job that consumes S slots for T seconds uses S * T slot-seconds (or slot-ms = S * T * 1000).
- Choose an interval (60s or 300s) and calculate the peak total_slot_ms in that interval.
  - Required_slots ≈ ceil( peak_total_slot_ms / (interval_seconds * 1000) )
- Add buffer (20–30%) for safety, metadata overhead, BI queries, ad-hoc queries, and short bursts.
- Example: peak_total_slot_ms over 60s = 120,000,000 ms → required_slots = ceil(120,000,000 / 60,000) = 2000 slots. Add 20% → ~2400 slots.

Reservation strategy options
- Flat-rate reservation: buy steady capacity sized to cover normal peak.
- Flex slots (short-term): use for unpredictable bursts (60-second minimum); combine with a base flat reservation.
- Multiple reservations & assignments: create reservations per environment/team and assign projects to reservations to isolate Matillion workloads.

How Matillion interacts and what you control
- Matillion issues many BigQuery queries concurrently (SQL components, transformation orchestration). Each query consumes some number of slots.
- Control Matillion parallelism to avoid over-saturating your reservation:
  - Limit number of concurrent transformation or orchestration jobs running by:
    - Job-level settings: number of threads / parallel component execution (set per job).
    - Project/instance settings: maximum concurrent jobs/workers (Matillion administration/project settings).
    - Component-level parallel flags (Execute SQL, Python/SQL scripts executed in parallel branches).
  - Use semaphores / throttles or a small “pooling” job to gate bursts if needed.
- Map Matillion concurrency to slots: set Matillion concurrency = floor(reservation_slots / avg_slots_per_query) * safety_factor.
  - Example: reservation = 2000 slots, average query uses 200 slots → theoretical concurrent queries = 2000/200 = 10. Use conservative factor (e.g., 0.8) → set to 8 concurrent queries.

Practical tuning workflow (iterative)
1. Baseline: collect 7–14 days of slot usage and Matillion job concurrency patterns.
2. Calculate required slots for target SLAs using the formula above; choose base reservation + flex slots for bursts.
3. Set reservation and assign the Matillion project to it.
4. Configure Matillion concurrency:
   - Set job-level thread limits and project max-concurrent-jobs to the derived concurrency.
   - Throttle particularly heavy components (large joins/aggregations) so they don’t run simultaneously.
5. Monitor:
   - BigQuery Reservation → slot utilization charts and queueing (if any).
   - Matillion job runtimes / failures / queue times.
   - INFORMATION_SCHEMA.JOBS_BY_PROJECT for total_slot_time trends.
6. Iterate: reduce/increase reservation or Matillion concurrency based on observed latency and cost.

Other optimizations to reduce slot demand
- Optimize SQL: rewrite heavy queries, reduce shuffle, prune columns/partitions, use clustering/partitioning.
- Use batch priority for non-urgent jobs so they wait longer but cost less in contention scenarios.
- Consolidate many small queries when possible (small, highly concurrent queries spike concurrent slot usage inefficiently).
- Use flex slots for short bursts rather than permanently sizing a big reservation.

Edge cases and cautions
- Some job types (load jobs, streaming inserts) do not consume slots in the same way as queries; verify which operations are driving slot usage.
- Slot contention increases query runtime rather than causing immediate failures — watch for latency increases before critical failures.
- Factor in other projects/users assigned to the same reservation or default on-demand usage.

Short checklist to implement immediately
- Run the per-minute slot query to find peak required slots.
- Pick reservation = peak_required_slots * (1 + 0.2 buffer) (plus flex slots if bursty).
- Compute Matillion concurrency limit = floor(reservation_slots / avg_slots_per_query) * 0.8.
- Apply concurrency settings in Matillion and assign project to the reservation.
- Monitor and iterate.

[Top](#top)

## How do you tune Redshift WLM/Workload Manager and queue priorities for Matillion ETL jobs?
Goal: keep interactive/BI queries fast while letting Matillion ETL run heavy loads without blocking the cluster. Tune WLM to separate short/ad-hoc queries from long ETL queries, and limit the concurrency of heavy ETL work.

High-level workflow
- Profile your Matillion workload: identify which queries are short/interactive vs long-running transforms, large COPY/UNLOADs, vacuum/ddl, ANALYZE, etc.
- Classify those workloads into WLM queues (short/BI, ETL/bulk, maintenance).
- Assign users/session tags so Redshift routes Matillion queries to the ETL queue.
- Allocate queue memory and concurrency to match workload characteristics.
- Add query monitoring rules to terminate runaway queries and protect short queries.
- Monitor and iterate with STL_WLM_* tables, SVL and CloudWatch metrics.

Practical steps

1) Identify and classify Matillion queries
- Capture examples and timings from STL_QUERY, SVL_STATEMENTTEXT, STL_WLM_QUERY, and AWS Console Query Monitoring.
- Typical classes:
  - Short/interactive (BI dashboards, quick SELECTs) — many small queries, latency sensitive.
  - ETL/batch (COPY, large INSERT/CREATE AS SELECT, large UPDATE) — high memory/cpu and long-running.
  - Maintenance (VACUUM, ANALYZE, DDL) — infrequent, heavy.

2) Tag Matillion sessions so queries go to the right queue
- Use a dedicated DB user for Matillion and map that user to the ETL queue in WLM; OR set a query_group per session:
  - Example (run as session pre-SQL in Matillion or at job start): SET query_group TO 'matillion_etl';
- Matillion allows running a SQL at the start of a job (use Pre-SQL, or a small “SET” component) to apply a tag for all session queries.
- You can also set user-based classification in WLM (map user to a queue).

3) Design WLM queues (classic WLM)
- Create separate queues. Common pattern:
  - Queue A (short queries / BI): higher concurrency (more slots), smaller memory allocation per query. This keeps many short queries responsive.
  - Queue B (Matillion ETL): low concurrency (1–3), large memory per slot for big queries.
  - Queue C (maintenance): single-slot, reserved memory for VACUUM/DDL.
- Memory % must sum to 100 (plus RM for service classes). Example starting point (adjust to cluster size and workload):
  - Short/BI queue: concurrency 6–10, memory_percent 15–25%
  - Matillion ETL queue: concurrency 1–3, memory_percent 60–75%
  - Maintenance: concurrency 1, memory_percent 5–10%
- If you have many small queries, enable Short Query Acceleration (SQA) or a dedicated short-query queue to prioritize them.

4) Concurrency vs memory tradeoff
- More concurrency => smaller memory per query => good for many small queries.
- Fewer slots for ETL => each ETL query gets more memory and runs faster without thrashing.
- For COPY operations, allow some concurrency but avoid letting many large COPYs run concurrently if they saturate I/O.

5) Use Query Monitoring Rules (QMR)
- Configure rules to log/abort queries based on runtime, scanned rows, or memory usage to prevent long-running ad-hoc queries from blocking queues.
- Example: abort SELECTs > X minutes in the short-query queue, or move them to a different queue.

6) Monitor and iterate
- Useful system views and logs:
  - STL_WLM_QUERY, STL_WLM_SERVICE_CLASS_CONFIG, STL_QUERY, SVL_STATEMENTTEXT, STL_QUERY_METRICS
  - CloudWatch: WLMQueueWaitTime, CPUUtilization, ReadIOPS/WriteIOPS, Disk-based metrics
- Look for high WLM queue wait times, high average slot utilization, frequent queue timeouts.
- If short queries are waiting behind ETL, increase short-queue slots or reduce ETL concurrency/memory usage.

7) Matillion-side concurrency control
- Matillion job design can create many concurrent SQL operations. Control concurrency in jobs:
  - Serialize critical heavy components (run sequentially instead of parallel).
  - Use parallelism only where independent tables can be loaded without resource contention.
  - Use per-job pre-SQL to set query_group or use a Matillion-dedicated DB user.
- If you need high throughput ETL and BI at same time, consider multiple Matillion instances or scheduling big ETL during off-hours.

8) Other cluster features to leverage
- Concurrency Scaling (for Redshift managed storage / RA3) can help short queries during peaks — but test cost and behavior with ETL workloads.
- Resize cluster for consistent capacity if ETL demands continually starve BI queries.
- Use distribution/sort key, compression, and optimized COPY file sizing to reduce ETL time (shorter queries = less WLM impact).

Example WLM layout (illustrative)
- Queue 1 (short/BI): concurrency 8, memory_percent 20, SQA enabled
- Queue 2 (Matillion ETL): concurrency 2, memory_percent 70
- Queue 3 (maintenance): concurrency 1, memory_percent 10
- Matillion sessions set query_group='matillion_etl' or use a Matillion DB user mapped to Queue 2.

How to verify changes
- Run a representative Matillion job while monitoring STL_WLM_QUERY and CloudWatch WLMQueueWaitTime; confirm ETL queries land in the ETL queue and short queries have low wait times.
- Adjust concurrency and memory_percent iteratively until both workload classes have acceptable performance.

Closing principle
- Separate workloads by queue and session tags, give ETL large memory but low concurrency, give BI higher concurrency with smaller memory per slot, and control Matillion concurrency in job design. Tune and iterate using the Redshift logs and CloudWatch metrics.

[Top](#top)

## How do you tune Synapse DWU/compute pools and concurrency for Matillion pipelines?
High-level approach: treat Matillion as an orchestrator that pushes work into Synapse (ELT). Tune two things separately but together: (A) Synapse compute sizing (DWU / pool size and resource-class/workload management) to give enough CPU/memory and concurrency slots for your queries, and (B) Matillion pipeline concurrency (how many parallel tasks/threads you launch) so you don’t overload Synapse or cause distribution skew/queueing. Steps and practical tactics:

What to tune on the Synapse side
- Right-size DWU (compute)
  - Scale up to reduce run time for CPU/IO-bound queries and for heavy concurrent workloads; scale down when idle to save cost.
  - Use burst/scale during your ETL window: scale up before the batch, run Matillion jobs, scale down after.
  - Measure impact: run representative load tests at different DWU levels and plot throughput (rows/hr or job latency) vs DWU to find diminishing returns.
- Use resource classes / workload management
  - Assign large resource class for a few heavy, long-running transformations; assign small resource class for many small queries.
  - This prevents one large job from monopolizing memory/slots and lets many short jobs run concurrently.
- Use appropriate ingest mechanism
  - Use COPY/PolyBase/Bulk load into staging (Azure Storage) rather than many single-row INSERTs. Matillion components can stage to blob and use PolyBase/COPY for parallel bulk load.
  - Bulk loads reduce pressure on SQL compute and are much faster.
- Distribution and table design
  - Choose HASH distribution on join keys to minimize data movement; use ROUNDROBIN only for transient staging when appropriate.
  - Monitor and fix distribution skew; create clustered columnstore indexes for analytics tables.
- Separate workloads where necessary
  - If ETL competes with BI queries, isolate them: separate dedicated SQL pools, or separate resource groups/workload groups, or run ETL in off-hours.
- Monitor system-level metrics and query waits
  - Use sys.dm_pdw_exec_requests, sys.dm_pdw_nodes_exec_requests, sys.dm_pdw_waits, Query Store and Azure Monitor metrics (CPU, DWU utilization, queue length) to find queueing, memory pressure, skew, or long-running steps.

What to tune on the Matillion side
- Control Matillion concurrency
  - Limit the number of parallel tasks launched against Synapse (Parallel components, multiple Load components, orchestration job concurrency) so aggregate concurrency matches Synapse capacity.
  - Use Matillion orchestration components like “Parallel” but set an appropriate degree of parallelism; serialize high-impact steps.
- Batch and chunk data
  - Send larger, fewer files to COPY/PolyBase instead of many small files. Tune file sizes to balance parallel input streams and overhead (typical target: tens to hundreds of MB per file, tuned by testing).
- Use efficient Matillion components/patterns
  - Push transformations into Synapse using SQL components (Table Input/SQL Script/Transformation) rather than extracting and transforming in Matillion where possible.
  - Use “Load from Blob”/“Copy to Table” patterns to exploit Synapse parallel bulk loading.
- Coordinate pool state
  - If you pause dedicated pools to save cost, Matillion must resume them before jobs run. Automate resume/scale up before the pipeline starts and scale down/pause after.

Concurrency sizing strategy (practical)
- Determine an “average concurrency unit” by running one representative transformation and observing its resource usage and duration at a baseline DWU.
- Estimate how many such units you want concurrently (e.g., 4 heavy transforms + 6 small transforms). Multiply required units to pick a DWU that gives acceptable per-job latency.
- Use resource classes so the “heavy” transforms consume more memory/slots and the many small ones are limited to small resource classes.
- Throttle Matillion to not exceed the concurrency your chosen DWU + resource class configuration supports.

Monitoring & iterative tuning
- Baseline: measure job runtimes, per-query resource usage and wait types at current DWU and concurrency.
- Change one variable at a time: increase DWU, or reduce Matillion concurrency, or change distribution, then measure impact.
- Watch for these signs:
  - Queued requests / long wait times → increase DWU or reduce concurrency.
  - High distribution skew → change distribution keys or RESHUFFLE/RECREATE table.
  - Memory grant failures / spills → assign larger resource class or increase DWU.
  - Diminishing returns when scaling DWU → optimize queries, distribution, or change design.

Example scenarios (guidelines)
- Large nightly bulk load (many files, heavy CTAS/aggregations)
  - Scale DWU up for the window, use PolyBase/COPY with large staged files, run parallel loads but keep parallel transforms limited to avoid contention, use large resource class for the big aggregation jobs.
- Many small incremental loads throughout day (lots of concurrent small writes)
  - Use smaller DWU but tune for concurrency: use small resource class, reduce per-job memory, possibly route these to a separate pool or lower-impact time windows to avoid affecting analytics queries.
- Mixed environment (ETL + ad hoc BI queries)
  - Isolate ETL into its own pool or use workload management resource classes to protect BI queries.

Operational automation
- Automate scaling with Azure APIs/CLI/Automation runbooks (scale/resume before jobs, scale down/pause after).
- Add checks in Matillion jobs to wait until pool is online and healthy (simple test query/health check) before heavy loads.

Summary checklist
- Design ELT to push work into Synapse and use bulk loads.
- Right-size DWU for the expected parallel workload; scale up during ETL windows and scale down afterward.
- Use resource classes and workload management to partition concurrency.
- Throttle Matillion parallelism to match Synapse capacity and avoid queueing/skew.
- Monitor DMVs, Query Store, and Azure metrics; iterate with measured load tests.



[Top](#top)

## How do you instrument end-to-end latency from source arrival to publish and identify bottlenecks at each step?
Break the problem into measurable stages, capture timestamps at each boundary in a consistent timebase, centralize the measurements, visualize/alert on percentiles, and then correlate with resource/DB/query metrics to find the bottleneck. Implementation in Matillion typically uses orchestration wrappers, audit rows in the warehouse, Matillion logs/API, and external monitoring.

1) Define the stages you care about
- Source event time (if available from the source system)
- Source arrival (e.g., S3 object last_modified, Kafka publish time, Pub/Sub publish_time)
- Ingestion start (Matillion orchestration job / extract job start)
- Ingestion end / staging loaded (rows available in staging)
- Transformation start
- Transformation end / transformed data landed
- Load/publish start (e.g., copy into final table, materialization start)
- Publish available / downstream visible (target table view ready, message published)
- End-to-end latency = publish_available_ts - source_arrival_ts

2) How to capture timestamps reliably
- Use the target warehouse’s CURRENT_TIMESTAMP to record timestamps in the same clock as queries (avoid relying on Matillion host time). Insert audit rows from SQL components using the warehouse timestamp.
- Capture source event timestamps where available and add them to each record (e.g., Kafka/CDC event_time, S3 object created_time).
- At job/step boundaries in Matillion:
  - Use a top-level orchestration job that calls sub-jobs (extract/transform/load).
  - At each boundary use a SQL component to INSERT/UPDATE an audit table row with stage_name, start_ts (CURRENT_TIMESTAMP), end_ts, row_count, run_id, job_name, status.
  - Use Matillion Set Variable / Python components if you need variable propagation, but prefer writing times in the warehouse for consistent analysis.
- Use Matillion Execution History and the Matillion REST Job Run API to obtain job start/end and status programmatically if you want to validate job-level metrics in addition to row-level audit.

3) Audit table pattern (simple schema)
- columns: source_id, run_id, stage_name, start_ts, end_ts, duration_ms, row_count, status, error_text, shard/file_id
- Use one row per stage-per-run (or per-file/chunk if you want finer granularity).
- Example logic:
  - Before running extract: INSERT audit(stage='ingest', start_ts=CURRENT_TIMESTAMP, status='running', run_id=…)
  - On completion: UPDATE audit SET end_ts=CURRENT_TIMESTAMP, duration_ms=datediff(ms,start_ts,end_ts), row_count=…, status='success'

4) Metrics to compute and visualize
- Per-stage metrics: duration_ms, throughput (rows/sec), row_count distribution
- End-to-end histograms and percentiles p50/p95/p99
- SLA breach counts and rolling error rates
- Job concurrency and queue times (Matillion or warehouse queues)
- Visualize in Grafana/Looker/QuickSight/Datadog from the audit table or push metrics to CloudWatch/Prometheus/Stackdriver

5) How to identify bottlenecks
- Compare stage percentiles: whichever stage consumes most p95/p99 time is the likely bottleneck.
- Drill down by dimensions: source, file size, partition, day/hour, tenant, run_id.
- Correlate with resource metrics:
  - Warehouse/query metrics: CPU, memory, disk spill, queue/wait times, query runtime, query profile/plan.
  - Storage/network: S3 throughput, object size, number of files (many small files slow COPY).
  - API rate-limits and retries for API-based sources.
  - Matillion worker concurrency and orchestration contention.
- For DB-heavy transforms: inspect the query execution plan, check for large sorts/shuffles, use proper distribution/cluster keys, increase warehouse size or change cluster settings.
- For loads: ensure file sizes are optimal (e.g., fewer larger files for COPY), compression used, parallelism tuned; for Snowflake/BQ/Redshift there are known tuning knobs (micro-partitions/clustering, COPY options, DISTKEY/KEYSORT).
- For extraction: check the producer/system latency (source arrival vs ingestion start). If many files are waiting, examine polling/triggering mechanism.

6) Practical Matillion implementation steps
- Create a top-level orchestration job:
  - Step A: INSERT audit row (stage = "ingestion", start_ts = CURRENT_TIMESTAMP)
  - Step B: Call extraction job(s)
  - Step C: On extraction success: UPDATE audit row with end_ts, row_count
  - Step D: INSERT audit row (stage = "transform", start_ts = CURRENT_TIMESTAMP)
  - Step E: Call transformation job(s)
  - Step F: UPDATE transform audit row with end_ts
  - Step G: Same for load/publish
- Use SQL components to write/read audit table; use Return Status or dependencies to branch on success/failure.
- Optionally call Matillion REST API at the start/end of the wrapper to capture Matillion job run metadata into audit.
- If you need per-record tracing, propagate source_event_ts into staging rows and compute lag per row in the warehouse.

7) Example queries to analyze latency (conceptual)
- Per-run stage durations:
  SELECT run_id, stage_name, avg(duration_ms) AS avg_ms, percentile_cont(0.95) WITHIN GROUP (ORDER BY duration_ms) AS p95_ms
  FROM audit GROUP BY run_id, stage_name;
- End-to-end:
  SELECT run_id, max(case when stage_name='publish' then end_ts end) - min(case when stage_name='ingest' then start_ts end) AS e2e_ms
  FROM audit GROUP BY run_id;

8) Alerts and SLAs
- Alert on p95 > SLA threshold, or any stage duration above threshold, or unexpected increases in queueing.
- Use anomaly detection on rolling baselines.

9) Common bottlenecks and remedies
- Many small files: combine files, increase parallelism, tune COPY settings.
- Slow warehouse queries: rewrite SQL to push down predicates, add clustering, increase warehouse size.
- Network/throughput: use region-aligned buckets, optimize staging/transfer methods.
- API source throttling: batch and backoff, parallelize only up to rate limits.
- Orchestration serialization: parallelize independent tasks where safe.

10) Additional notes
- Prefer using the warehouse for authoritative timestamps and metrics to avoid clock skew across systems.
- Capture unique run_id per pipeline run and pass it to all stages to join events easily.
- Use percentiles (p95/p99) not just averages to expose tail latency issues.

This approach produces per-stage, per-run visibility, lets you compute end-to-end latency, surface the slowest stages, and then correlate with query/warehouse/IO metrics to identify and fix the bottleneck.

[Top](#top)

## How do you expose operational metrics and KPIs for platform health to stakeholders and on-call engineers?
High-level approach
- Treat platform health as a product: define SLIs/SLOs, instrument for those signals, surface them in role-appropriate views, and integrate automated alerting + runbooks for on-call execution.
- Split visibility by audience: executives/stakeholders need high-level KPIs (uptime, SLA compliance, data freshness), on-call engineers need actionable telemetry (task-level failures, resource metrics, traces, context).

Which metrics / KPIs to expose
- Availability / reliability: pipeline success rate, jobs passed vs failed, SLA attainment (% of datasets meeting freshness windows).
- Latency & freshness: end-to-end pipeline latency (ingest → ready), time-to-first-row, dataset age.
- Throughput & volume: rows/sec, bytes processed per job, records per minute by pipeline.
- Errors & quality: failure counts, error types, retry rate, data-quality check failures (null %, schema drift).
- Performance & capacity: warehouse CPU/Memory/IO, Matillion worker/container CPU/memory, queue length, concurrency.
- Cost & efficiency: cost per run, cost per TB, wasted retries.
- Operational metrics: mean time to detect (MTTD), mean time to recover (MTTR), on-call escalations, alert counts by severity.
- Business KPIs (for stakeholders): SLAs for key reports, downstream consumer availability, late-report incidents.

Instrumentation & data collection
- Use Matillion built-in telemetry: job history, task timings, audit logs, and Matillion REST API to pull run metadata and errors.
- Emit structured events from Matillion jobs: use Notify / HTTP components or webhook integrations to send status and context to your monitoring pipeline.
- Forward Matillion and system logs (application logs, container logs) to a central log store (ELK/Cloud Logging/Sumo/Datadog).
- Capture underlying infra metrics via cloud-native monitoring (CloudWatch / Azure Monitor / GCP Stackdriver) or Prometheus node exporters for VMs.
- Record business-level checks (row counts, checksum, referential integrity) as metrics into your metrics system.
- Correlate with data warehouse metrics (query runtime, slots, concurrency, queue length) via the warehouse’s monitoring APIs.

Metrics pipeline & storage
- Ingest metrics into a metrics backend (Prometheus/Datadog/Cloud Monitoring) and logs into an ELK/Datadog/Cloud Logging stack.
- Use a time-series DB with appropriate retention/aggregation to support both real-time alerting and historical trending.
- Tag metrics with environment, team, pipeline, dataset, and correlation IDs to enable fast triage.

Dashboards & presentation
- Role-based dashboards:
  - Executive dashboard: SLA attainment, major incidents (count & severity), MTTR trend, cost trend (single-pane).
  - Product/ops dashboard: dataset freshness, top failing pipelines, trending errors, SLA breaches.
  - On-call dashboard: real-time failed jobs, last 24h runs with timestamps/errors, infra metrics, links to logs and runbooks.
- Include drill-down links from dashboard items to job run details, logs, and the Matillion job definition.
- Provide daily/weekly health reports for stakeholders with trendlines and action items.

Alerting & incident routing
- Define alert severity levels (P0/P1/P2) with measurable thresholds tied to SLIs.
- Alert types:
  - Immediate page (PagerDuty/OpsGenie) for P0 (total outage, SLA breach).
  - Slack/email for warnings (P2) or informational events.
- Include context in alerts: job id, pipeline name, last successful run, error message, run link, suggested remediation steps.
- Prevent alert fatigue: dedupe related failures (group by pipeline/dataset), set rate limits, use alert suppression during maintenance windows.

Runbooks & automated remediation
- For each common alert create a runbook: symptoms, immediate checks, rollback steps, quick fixes, escalation path, postmortem checklist.
- Automate common remediations where safe: auto-retry with backoff, restart worker, scale warehouse cluster, schema roll-back.
- Keep runbooks versioned and accessible via the incident ticket or alert payload.

SLOs, error budgets and review cadence
- Define SLOs for critical pipelines and track error budget consumption; escalate when budgets are at risk.
- Weekly/bi-weekly operational review: triage repeated failures, tune alerts, review MTTR/MTTD trends, and actions from postmortems.

Practical Matillion-specific implementation notes
- Use Matillion REST API to extract job history, run times, and error metadata into your monitoring pipeline on a polling cadence.
- Use Notify/HTTP components at the end of workflows to emit structured success/failure events into your event stream or metrics collector.
- Capture component-level timing by instrumenting start/end times in variables and pushing them as custom metrics.
- Forward Matillion logs (UI logs, task logs) to centralized logging and index by job_id, execution_id for easy pivoting.
- Leverage cloud-native autoscaling for Matillion workers and tie scale events to dashboards/alerts.

Operational hygiene & governance
- Standardize metric names and tags; document thresholds and ownerships.
- Set sensible retention for raw logs and aggregated metrics to balance cost vs. investigability.
- Ensure RBAC: stakeholders see summary dashboards; on-call engineers have access to detailed probes, logs, and runbooks.

Example end-to-end flow (concise)
- Matillion job finishes → Notify component posts structured event to metrics pipeline → metrics backend increments job.success / job.duration; logs forwarded to central logging → alert rules evaluate SLIs and page on-call if threshold breached → alert includes run links + runbook → engineer triages using dashboard + logs → fix and record incident.

Metrics you’d surface immediately to stakeholders vs on-call
- Stakeholders: uptime/SLA %, on-time report %, significant incidents in period, MTTR trend, business impact.
- On-call: current failing jobs, last failed error messages, infra anomalies, pipeline latency, retry attempts, links to remediation steps.

[Top](#top)

## How do you encrypt data at rest and in transit across storage, warehouses, and Matillion components?
Short answer
- Encrypt everything at rest with cloud-provider encryption + customer-managed keys where you need control (KMS/CMEK/HSM).
- Encrypt everything in transit with TLS (HTTPS / JDBC/ODBC TLS), and prefer private networking (VPC endpoints, PrivateLink, VPC peering, Cloud Interconnect) for bulk transfers.
- Protect Matillion runtime and metadata with disk encryption, encrypted project/credential storage, HTTPS for the UI/API, and proper IAM/network controls.

Details and actionable controls

1) Object storage (S3 / GCS / Azure Blob)
- At rest: enable server-side encryption (SSE-S3, SSE-KMS on AWS; CMEK/CSEK options on GCP; Storage Service Encryption + CMK via Azure Key Vault). Use customer-managed keys (KMS/CMEK) for key control and rotation if required.
- In transit: always use HTTPS (TLS). Enforce TLS by bucket/container policies (S3 bucket policy "aws:SecureTransport": true, Azure allow only HTTPS, etc.).
- Network: use provider private endpoints (S3 VPC endpoints, Private Service Connect, Azure Private Endpoint) to avoid public internet for data movement.
- Staging for warehouses: when Matillion stages files to storage for load operations, ensure the staging location is encrypted and accessed via HTTPS or private endpoints.

2) Cloud warehouses (Snowflake, Redshift, BigQuery, Synapse, etc.)
- At rest:
  - Snowflake: data encrypted at rest by default; use Customer-Managed Keys (Tri-Secret / CMK/HSM) if you require direct key control.
  - Redshift: enable encryption on cluster and snapshots with AWS KMS or HSM; ensure Spectrum/External tables use encrypted S3.
  - BigQuery: default encryption at rest; choose CMEK via Cloud KMS to bring your own keys.
  - Synapse/SQL DW: Transparent Data Encryption (TDE) and customer key control via Azure Key Vault.
- In transit: enable and enforce TLS (most providers default to TLS 1.2+). Ensure JDBC/ODBC connections from Matillion include SSL parameters and verify server certificates.
- Network: prefer private connectivity (VPC peering, PrivateLink, Snowflake Private Connectivity, GCP/VPN or Interconnect) to avoid exposing data over the public internet.

3) Matillion components (ETL instance, metadata DB, job artifacts, credentials)
- Matillion server/VM:
  - Disk: enable cloud VM disk encryption (EBS encryption on AWS, Persistent Disk CMEK on GCP, Azure Disk Encryption) for OS and local storage.
  - Backups/snapshots: ensure snapshots are encrypted as well.
  - Network: place Matillion in a private subnet, restrict access via security groups, use an Application Load Balancer/ALB or reverse proxy for TLS termination if needed.
  - UI/API: enable HTTPS for the Matillion UI and APIs, install a trusted certificate (ACM/Key Vault/managed certs or your CA).
- Metadata and credentials:
  - Matillion stores job metadata and credentials (embedded PostgreSQL by default). Ensure that DB storage is encrypted and access is limited.
  - Use Matillion’s encrypted context variables/credential vault features to store secrets; where possible use external secret managers (AWS Secrets Manager, Azure Key Vault, GCP Secret Manager) and reference them rather than embedding secrets.
  - Rotate credentials frequently and manage access via IAM/service accounts, not long-lived static credentials.
- Inter-node/transforms: any connectors that stream data (SFTP, JDBC, API) should be configured with encryption (SFTP over SSH, TLS-enabled database drivers).

4) Data in transit specifics
- Always use TLS for:
  - Matillion <> cloud storage (HTTPS)
  - Matillion <> warehouse (JDBC/ODBC with SSL mode)
  - Matillion UI/API (HTTPS)
  - API connectors and third-party endpoints
- Validate certificates and enforce certificate pinning or strict hostname verification when supported.
- For higher security, use provider private networking: VPC endpoints, PrivateLink, VPC peering, VPN/Direct Connect, Interconnect, Private Service Connect.

5) Key management and rotation
- Use cloud KMS/HSM (AWS KMS, Cloud KMS, Azure Key Vault/HSM) to manage encryption keys and enable auditing.
- Use CMEK/CMK when you must control keys or revoke access.
- Implement key rotation policies and test recovery/restore workflows with rotated keys.

6) Additional controls
- Least privilege: IAM roles for Matillion to access S3/GCS/Blob/warehouse; do not use full admin keys.
- Audit & monitoring: enable CloudTrail / Audit Logs, S3/GCS storage access logs, database audit logs, and Matillion audit logs.
- Data classification & tokenization: for very sensitive fields consider field-level encryption, tokenization or use warehouse-native encryption-at-column-level where supported.
- Secure development: do not commit secrets into Git/remote project without encryption; use Matillion’s secure job settings or external secret stores.

Quick checklist to implement immediately
- Enable SSE-KMS/CMEK on storage buckets and warehouse (where supported).
- Turn on HTTPS-only for storage and Matillion UI.
- Configure JDBC/ODBC connectors to require SSL and validate certificates.
- Deploy Matillion in a private subnet with encrypted disks and restrict inbound access.
- Use private connectivity (VPC endpoint/PrivateLink/peering) for warehouse & storage access.
- Store secrets in encrypted context variables or an external secrets manager and rotate keys regularly.
- Enable audit logging for all components.

This approach ensures layered protection: encrypted disks and object storage at rest; TLS and private networking in transit; KMS/HSM key control and strict IAM/policy enforcement for access control.

[Top](#top)

## How do you rotate secrets, keys, and tokens used by Matillion and test rotations without downtime?
High-level approach
- Inventory everything Matillion uses: data warehouse credentials (Redshift, Snowflake, BigQuery, Synapse), cloud storage (S3, GCS, ADLS), API tokens, SSH/Git keys, OAuth refresh tokens, any service-account JSON/private keys, and Matillion admin/API tokens.
- Prefer identity/role-based auth (IAM roles, GCP service accounts, Azure managed identities) or external secrets stores (AWS Secrets Manager, GCP Secret Manager, Azure Key Vault) so keys aren’t long-lived.
- Rotate by creating the new credential alongside the old, test it, then switch jobs to the new credential (or update the credential in-place) so you never have a period where no valid credential exists.
- Automate and test every rotation in a non-prod environment before production. Have a rollback plan (old credential stays enabled until verification).

Concrete, repeatable process (no-downtime pattern)
1) Prepare new secret
- Create a new key/token/service-account in the target system (e.g., new AWS access key, new GCP service account key JSON, new Snowflake key-pair, new API token).
- Do not delete or disable the old secret yet.

2) Add the new secret to Matillion (two safe options)
Option A — Edit in-place
- Open Matillion Credentials manager (Project → Manage Credentials or equivalent).
- Edit the existing credential record and replace the secret with the new one, keeping the credential name/ID the same.
- This is the simplest zero-downtime approach because jobs reference the credential ID and will pick up the new secret immediately for subsequent runs.

Option B — Create new credential and switch
- Create a new credential object in Matillion with the new secret.
- Update jobs/environments to reference the new credential. Use environment variables or a single “credential pointer” variable to make switching easy.
- This gives you the ability to test the new credential side-by-side before switching production jobs.

3) Test the new secret
- Run Matillion’s Test Connection for the credential.
- Run a set of smoke/canary jobs that exercise the credential (small extracts, metadata checks). Run these in parallel if using a new credential object so the old jobs keep running on the old credential.
- Monitor for errors and latency regressions.

4) Switch traffic and verify
- If you created a new credential object and tested it, update production jobs or the environment-level pointer variable to the new credential. If you edited in-place, jobs will automatically use it after the next run.
- Run a final set of canaries across all critical jobs. Monitor logs and job status for failures.

5) Decommission old secret
- After a safe verification window, revoke or delete the old secret from the remote system.
- If you need an auditable gap, disable (don’t delete) the old secret first and confirm no failures, then delete.

Examples for common systems
- AWS access keys (S3, Redshift COPY using keys)
  - Best: use an IAM role attached to Matillion or use role assumption from Matillion to avoid keys.
  - If you must rotate keys: create new access key, add as new Matillion credential, Test Connection, switch jobs, then delete old access key.
- Snowflake with private key
  - Generate new key-pair, upload new public key to Snowflake (ALTER USER ... SET RSA_PUBLIC_KEY = '<pub>'), update Matillion credential private key (edit credential or create new), Test Connection, run canaries.
- BigQuery / GCP service-account JSON
  - Create new service account key JSON, add to Matillion as new credential or edit in-place, Test Connection, run small query job, then revoke old key file.
- Git/SSH keys
  - Add new deploy key to repo and to Matillion, set up new key in Matillion Git settings, test pull/commit actions, then remove old key.
- API tokens (third-party connectors)
  - Create new token in third-party app, update Matillion credential, call a small API-based job to verify scope and rate limits, then revoke old token.

Testing strategies to avoid downtime
- Canary jobs: small, fast jobs that exercise each type of credential.
- Parallel run: create duplicate versions of critical jobs that use the new credential; run them in parallel while production continues on the old credential.
- Test Connection + lightweight full pipeline run in non-prod prior to production change.
- Use environment-level credential pointers (an environment variable containing the credential name/ID that jobs reference) to switch all jobs atomically by updating one variable.
- Add monitoring/alerts on job failures so any regression is caught quickly.

Automation and scale
- Script rotation: use cloud provider APIs to create new credentials, and use Matillion orchestration jobs (or Matillion’s REST API if available) to update credentials and trigger canaries.
- Bake into CI/CD: deploy credential changes in a pipeline that runs automated verification and only then promotes the change.
- Keep secrets in external secret managers and fetch at runtime where possible. That centralizes rotation and reduces number of places to update.

Rollback and safeguards
- Keep old credential active and available until verification window passes.
- Implement automated rollback steps in your orchestration if canaries fail (e.g., switch environment pointer back to old credential).
- Log and audit every change—who rotated what and when.

Notes and caveats
- For some infrastructure-level changes (e.g., changing an EC2 instance profile), a restart or instance update may be required; plan windows for those.
- Matillion stores credentials encrypted. Changing credentials in the UI is immediate for subsequent job runs; however, connection pools/cached sessions (rare) could require restarting a job or clearing a session.
- Always test rotations in a staging environment that mirrors production to validate edge cases (scopes, privileges, network ACLs).

Summary checklist
- Inventory -> create new secret -> add/edit credential in Matillion -> Test Connection -> run canaries -> switch -> monitor -> revoke old secret -> log/automate.

[Top](#top)

## How do you validate compliance requirements (HIPAA/PCI/GDPR) and configure logging, masking, and retention accordingly?
Approach summary (how I validate requirements and implement controls in a Matillion pipeline)
1. Interpret the regulation into technical controls
   - Translate HIPAA/PCI/GDPR articles into concrete requirements: encryption in transit/at rest, access control & RBAC, logging/audit retention, masking/pseudonymisation, right-to-be-forgotten / data retention and deletion, breach detection/notification.
   - Produce an itemized control matrix mapping each regulatory requirement to where it is enforced (Matillion, cloud provider, target warehouse, external tokenization/DLP).

2. Data mapping & classification
   - Inventory sources, flows, transformation jobs and targets in Matillion Projects.
   - Tag/annotate sensitive fields (PII, PHI, PAN) in a catalog. Use Matillion metadata and job documentation to maintain the mapping.
   - Decide where sensitive data must be transformed (in-flight in Matillion or in the target DB using native features).

3. Implement controls (Matillion + cloud + warehouse)
   - Access & identity
     - Use SSO/SAML for Matillion UI access, role-based access via Matillion roles and restrict project/job access.
     - Use least-privilege IAM roles for cloud resources (S3, GCS, Azure Blob, Warehouse) and for Matillion instance role/profile.
     - Store credentials in Matillion’s secure credentials manager (encrypted storage). Restrict who can view credentials in UI.
   - Network & instance hardening
     - Run Matillion inside VPC/subnet, use security groups, private endpoints, and Bastion or AWS PrivateLink / Azure Private Link where available.
     - Enforce TLS for UI and all data movement.
   - Encryption
     - Ensure cloud storage buckets and warehouse use encryption at rest (CMEK/KMS) and TLS in transit.
     - Use cloud KMS with rotation policies; limit KMS access via IAM.
   - Logging & auditability
     - Capture Matillion job run history and component logs (store them centrally). Configure Matillion instance to ship OS/job logs to CloudWatch / Azure Monitor / GCP Logging or to an S3/GCS/Azure container.
     - Enable cloud audit logs: AWS CloudTrail, Azure Activity Logs, GCP Audit Logs for API access and S3/GCS access.
     - Enable/collect database audit logs (Snowflake ACCESS_HISTORY, Redshift audit logs, BigQuery audit logs).
     - Retention: ensure logs are retained per policy (Cloud storage lifecycle or dedicated logging retention settings); keep immutable copies if required (S3 Object Lock).
   - Masking / pseudonymisation / tokenization
     - Implement masking prior to downstream exposure:
       - For simple cases, perform deterministic hashing or redaction in Matillion transformations (SQL component or Python/Script).
       - For stronger guarantees, call a tokenization service or DLP API (e.g., AWS Macie+Dynamo/Token service) from Matillion to replace PAN/PII with tokens.
       - Where available, use target-DB native masking (Snowflake Dynamic Data Masking / Masking Policies, BigQuery DLP, column-level security).
     - Example pseudocode (BigQuery-style) for deterministic pseudonymisation:
         TO_HEX(SHA256(CONCAT(@salt, email))) AS email_pseudo
       - Keep salts/secrets in KMS / secret manager; do not hardcode in jobs.
   - Retention & deletion
     - Implement lifecycle policies for cloud storage (S3/GCS/Azure Blob) to archive / delete per retention schedule; use Object Lock when immutability is required.
     - Build Matillion scheduled jobs to locate and purge records in data warehouse per retention policy (and record the deletion in an audit log).
     - For GDPR “right to be forgotten”, implement an orchestrated workflow: identify records, anonymize or delete, verify removal from backups/replicas where applicable, and log the action.
   - Secrets & key management
     - Use cloud-native secret stores (AWS Secrets Manager/Azure Key Vault/GCP Secret Manager) for secret rotation. Limit Matillion access to secrets via IAM roles.
   - Change control & provenance
     - Use Git integration for Matillion projects; store pipeline definitions in version control; require code review for changes to jobs that touch sensitive data.

4. Validation, testing, evidence
   - Configuration validation
     - Automated checks: jobs that query configuration endpoints and validate encryption, IAM roles, and S3 bucket policies against expected values.
     - Periodic drift detection: compare runtime configs to baseline.
   - Functional testing
     - Test masking/pseudonymisation jobs on sample datasets; verify original data isn’t present in outputs or logs.
     - Test “right to be forgotten” workflow end-to-end and verify that audit logs capture the deletion and that downstream copies are addressed.
   - Logging/audit tests
     - Generate test events and validate logs are recorded in Cloud Audit Logs/CloudTrail, shipped to central logging, and retained per policy.
   - Penetration and compliance scans
     - Run vulnerability scans, config audits, and provide artifacts/reports to auditors.
   - Evidence pack
     - Export run logs, job definitions, IAM role policies, KMS key configs, bucket lifecycle settings, and audit log extracts for compliance audits.

Operational examples and concise recipes
- Centralize Matillion logs
  - Configure Matillion instance log shipping (cloud agent or OS-level agent) to forward /var/log and Matillion job logs to CloudWatch/Stackdriver/Azure Monitor, or periodically copy Matillion job logs to an encrypted S3/GCS/Azure container for retention.
- Masking in Matillion transform (generic)
  - Add a transformation step (SQL or Python) that replaces sensitive column with pseudonym:
      hashed_id = HASH_SHA256(CONCAT(salt, pii_col))
    Store salt in KMS or secret manager; never log the raw value.
- Retention & deletion job pattern
  - Scheduled Matillion orchestration:
    1) Query or lookup records older than retention period
    2) Move to archival storage (if required) with encryption
    3) Delete from primary warehouse tables (DELETE/EXTENT or TRUNCATE partition)
    4) Log the delete action to an immutable audit store and emit an event to the compliance queue
- Tokenization integration
  - Use a Python Script component or REST component in Matillion to call a tokenization microservice (or third-party token vault). Replace PII columns with tokens and log token IDs (not raw values).

Shared responsibility model (short)
- Matillion provides orchestration, transformation execution and local logging; the remainder of security is implemented in cloud infra and data warehouse. Validate and document who is responsible for each control (encryption keys, KMS, bucket policies, database masking policies, backup retention).

How I demonstrate compliance to an auditor
- Present the control matrix mapping regulation -> technical control -> implementation location (Matillion/job/DB/cloud).
- Provide configuration snapshots: S3 lifecycle policies, KMS key policy, Matillion job definitions, Git commit history, centralized logs with timestamps, and evidence of test runs showing masking/purging.
- Provide runbooks and SOPs for incident response, data subject requests, and periodic verification jobs.

Key practical rules I follow
- Principle of least privilege everywhere (Matillion, cloud, DB).
- Don’t rely on Matillion logs alone — use cloud audit logs and DB auditing as the primary evidence store.
- Keep secrets in a vault; use deterministic tokenization/hashing only when required and store salts securely.
- Automate validation and produce auditable artifacts for every sensitive-data operation.



[Top](#top)

## How do you set up guardrails and budgets to cap spend per environment and prevent runaway jobs?
High-level approach: apply layered guardrails — prevent overspend where possible, detect spend/long runs quickly, and enforce automatic reactions. Use Matillion controls + target-platform controls + cloud-provider budgets and automation. Example checklist and concrete implementations below.

1) Preventive controls (stop runaway compute before it starts)
- Separate environments and capacity:
  - Put dev/test/qa/prod in separate Matillion Environments (separate VMs or instances) and use smaller instance sizes for non-prod.
  - Tag every environment (env=dev/test/prod) for cost scoping.
- Limit permissions and change control:
  - Use Matillion RBAC / SSO to restrict who can change environment size, alter schedules, start ad-hoc jobs, or run heavy transformations.
  - Use cloud IAM to restrict the ability to resize or reconfigure the Matillion instance or underlying cloud resources.
- Constrain target-platform compute:
  - Snowflake: assign dedicated warehouses per environment sized appropriately; set AUTO_SUSPEND low (eg 60s); disable or limit multi-cluster/concurrency scaling; create Snowflake Resource Monitors to cap credits and automatically suspend warehouses at thresholds.
  - Redshift/BigQuery/Azure Synapse: set cluster/warehouse sizing, concurrency limits, pause schedules, autoscaling caps or quotas as available.
- Job design best-practices:
  - Add timeouts and defensive checks at the top of orchestration jobs (check for existing running jobs, use a lock mechanism).
  - Avoid uncontrolled loops or unbounded retries; use exponential backoff with backstop limits.
  - For heavy transforms, stage and sample in dev before scaling to prod.

2) Detection & alerting
- Cloud provider budgets & alerts:
  - Create per-environment budgets (AWS Budgets / GCP Billing Budgets / Azure Cost Management) scoped by tags or linked accounts; set multiple thresholds (50%, 75%, 90%) to send SNS/email/Cloud PubSub notifications.
- Platform monitoring:
  - Snowflake: monitor credit usage and warehouse suspension events; use Resource Monitor alerts.
  - Matillion: export job execution logs/metrics to CloudWatch/Stackdriver/Azure Monitor and alert on long-running jobs, high concurrency or sustained high API call rates.
- Metrics to watch:
  - Matillion job runtimes, number of concurrent jobs, Matillion VM CPU/memory, target-warehouse credits per hour, sudden spikes vs baseline.

3) Automated reactions (cut spend when thresholds hit)
- Budget-triggered automation:
  - Budget alert -> SNS/PubSub -> Lambda/Cloud Function that runs automated actions:
    - Stop or scale down Matillion VM for non-prod environments.
    - Suspend target warehouses or scale them down (use Snowflake API or cloud SDK).
    - Disable or pause Matillion schedules via Matillion REST API (update job schedule or disable execution).
- Snowflake-specific enforcement:
  - Use Resource Monitors to automatically suspend or prevent warehouses from using more credits beyond a set limit.
- Job cancellation:
  - Use Matillion REST API to query running jobs and cancel/abort long-running jobs programmatically from a remediation function triggered by budget alert or monitoring rule.
- Fail-safe policies:
  - For critical workloads, implement a “soft cap” (alert + throttling) and a “hard cap” (automated suspension or cancellation) with appropriate approval processes.

4) Operational controls you should implement in Matillion
- Use Matillion REST API to build:
  - Pre-flight checks (do not start if environment is already at X concurrent jobs or a specific job is running).
  - Watchdogs that cancel jobs exceeding configured runtime and record the action in execution history.
- Job properties and orchestration patterns:
  - Implement a wrapper orchestration that checks elapsed/start timestamp, calls REST API to abort on overrun, and sends a notification.
  - Disable or block concurrent runs for jobs that must be singletons (implement a lock file/DB flag or API check before launching).
- Scheduling & auto-stop:
  - Stop non-prod Matillion VMs outside working hours (use cloud scheduler + start/stop scripts) to eliminate idle costs and reduce risk of ad-hoc runaway runs.

5) Governance and reporting
- Tagging and chargeback:
  - Enforce tags on Matillion instances and target-platform resources; use those tags to build per-environment budgets and reports.
- Regular reviews and runbooks:
  - Monthly review of job runtimes, cost drivers, and exceptions.
  - Runbook detailing who gets notified when a budget threshold triggers and who can override an automated stop.

Example enforcement workflow (AWS + Snowflake + Matillion)
- Tag Matillion EC2 and Snowflake warehouses with env=dev.
- Create AWS Budget scoped to that tag with 80% and 100% thresholds sending SNS.
- SNS -> Lambda:
  - At 80%: send Slack/email alerts, call Matillion REST API to pause non-critical schedules.
  - At 100%: run Lambda that calls Snowflake API to suspend specified warehouses and calls Matillion REST API to abort running jobs or stop the Matillion EC2 (non-prod).
- Snowflake Resource Monitor set to suspend warehouses at 95% of a monthly credit limit (independent hard enforcement).

Summary
- Use a layered approach: prevent via small/non-prod sizing, RBAC and job timeouts; detect via per-environment budgets, platform monitoring and alerts; react via automation (cloud functions that call Matillion & target-platform APIs) and platform-native guards (Snowflake Resource Monitors). Tagging, separation of environments, and strict permissions are key to making budgets and automation reliable.

[Top](#top)

## How do you control who can create/edit/run jobs and who can modify environments and credentials?
Matillion uses role‑based access control (RBAC) plus optional SSO/LDAP group mapping to control who can create/edit/run jobs and who can manage environments and credentials. Control is applied at the built‑in role level or via custom roles with granular permissions.

How it works (high level)
- Roles and permissions: In Matillion’s Admin (Manage Users / Roles or Permissions Manager) you assign permissions to roles. Permissions cover job operations (Create, Edit, Delete, Run, Schedule), project operations, environment operations, and credential management.
- Assign users to roles (or map SSO/LDAP groups to Matillion roles): Users inherit the permissions of their assigned role(s).
- Environment permissions: You can restrict who can view, use, edit, create or delete specific environments (so a user may run jobs against an environment but not modify it).
- Credential permissions: Credential management is gated by permissions; you can allow users to use stored credentials (for running jobs) without giving them ability to view or edit the credential definitions, and separately allow certain roles to create/modify/delete credentials.

Typical built‑in roles (defaults)
- Admin: full rights across projects, jobs, environments and credentials.
- Developer: can create/edit/delete jobs and projects and usually can run them; typically not allowed to manage environments or credentials unless explicitly granted.
- Operator: can run and schedule jobs and use environments/credentials for execution, but cannot change job logic or environment/credential definitions.
- Viewer (Read‑only): can view jobs/projects but cannot edit or run.

How to implement your policy (step‑by‑step)
1. Define role responsibilities (e.g., Devs = create/edit/run jobs; Ops = manage environments/credentials and run jobs only).
2. In Matillion Admin > Roles/Permissions, create or edit roles and enable only the job create/edit/run permissions for your Developer role. Do not enable Manage Environments or Manage Credentials for that role.
3. Create an Operator/EnvAdmin role that has permissions to Manage Environments and Manage Credentials, plus run/schedule permissions, but not job design permissions if you want to prevent edits.
4. Assign users directly to roles, or map your identity provider (SAML/Okta/Azure AD/LDAP) groups to Matillion roles so group membership controls access.
5. For further restriction, set environment‑level permissions so only the Ops/EnvAdmin role can modify particular environments; allow Developers to “use” the environment for execution if required.
6. Test with representative accounts to confirm Developers can edit and run jobs but cannot change environment definitions or credentials, and Ops can manage environments/credentials but cannot change job logic (if desired).

Notes and gotchas
- “Use” vs “Manage” permissions are different: giving someone the ability to run jobs using an environment/credential does not automatically allow them to edit those environment/credential objects.
- Mapping SSO groups reduces administrative overhead and keeps central identity policies authoritative.
- Built‑in roles can be a good starting point, but use custom roles for strict separation of duties.

This configuration enforces who can create/edit/run jobs separately from who can modify environments and credentials.

[Top](#top)

## How do you audit changes to jobs, variables, and credentials and integrate with SIEM solutions?
Short answer
- Use Matillion’s built‑in audit/job history + Git integration + centralized secret stores, then forward logs (Matillion instance/app logs, cloud secret access logs, Git/webhook events, job history) into your SIEM using cloud logging agents or the Matillion REST API. Combine those sources to get user, timestamp, action, object, before/after and run context.

What to capture (minimum fields)
- User identity (SSO/SAML username when possible)
- Action type (create/update/delete/run/credential-access)
- Object type and name (job, task, variable, credential, environment)
- Timestamp and source IP / session id
- Job run id / commit id / before-and-after values (where safe)
- Result/status and error codes

Where the data comes from
- Matillion audit / job history (UI and backend history for job edits and runs). Expose via Matillion UI exports or REST API programmatically.
- Git repository history (commits/branches): author, timestamp, commit diff for job design changes when you use Matillion’s Git integration.
- Matillion instance and application logs (system logs, API logs, matillion-server logs).
- Secret manager audit logs if you store secrets in cloud secret stores (AWS Secrets Manager / Cloud Secret Manager / Azure Key Vault) instead of Matillion’s internal secrets.
- Identity provider logs (SAML/Okta/Azure AD) for authentication events.

Best practice implementation steps
1. Enforce Git-backed development
   - Put all projects into Git (Bitbucket/GitHub/GitLab).
   - Require commits for changes and use branch/PR workflows.
   - Feed Git commit/webhook events into SIEM for a canonical change record (author, timestamp, diff).
2. Use centralized secrets
   - Store credentials in AWS Secrets Manager / GCP Secret Manager / Azure Key Vault and reference them from Matillion.
   - Cloud secret managers produce auditable events (GetSecretValue/PutSecretValue) that you can forward to SIEM.
3. Enable Matillion audit/job history and export
   - Use Matillion’s job/task history and audit endpoints (or UI exports) to pull change and run records regularly into your logging pipeline.
   - If needed, poll Matillion REST API to ingest history into SIEM.
4. Forward instance/app logs to cloud logging then SIEM
   - On AWS: push Matillion logs to CloudWatch Logs (or use an agent) and set up subscriptions (Kinesis/Lambda) to forward to Splunk/ELK/QRadar.
   - On GCP: push to Cloud Logging and export to Pub/Sub/BigQuery or third‑party sinks.
   - On Azure: push to Azure Monitor/Log Analytics and export to SIEM.
5. Correlate with identity and infrastructure logs
   - Pull IdP (SAML) logs, cloud IAM events (CloudTrail/Azure Activity Logs), and Git events into the same SIEM for full context.
6. Retention, immutability, and access control
   - Ensure audit logs are immutable or append‑only and retained per policy. Limit access to audit data.

Practical SIEM integration patterns
- Log collector agents on the Matillion VM/EC2 (Fluentd/CloudWatch agent/Splunk forwarder) to stream logs to a central logging layer.
- Cloud log exports → forwarding Lambda/Cloud Function or native connectors to SIEM.
- Periodic job: a connector pulls Matillion REST API job/audit history and pushes JSON to SIEM.
- Webhook-based: Git webhooks + CI events push real‑time change events.

Example detections/alerts to configure
- Credential change or creation for production environment
- Job or variable change committed outside standard branch/PR process
- Sudden run of production jobs outside business hours or by unusual user
- Repeated failed login attempts or new IP access for admin accounts
- Deletion of jobs/environments or disabling of logging

Notes on credential auditing
- Matillion’s internal encrypted credential store may not provide an exhaustive access trail; for strongest auditing, use a cloud secrets manager so secret access is logged by the cloud provider.
- Avoid logging plaintext secrets. Capture metadata (who/when/object) rather than secret values.

Example event normalization (send to SIEM)
- EventType: JOB_EDIT / CREDENTIAL_CHANGE / JOB_RUN
- User: alice@example.com
- Source: Matillion UI / REST API / Git
- Object: project:finance.job:load_transactions
- Action: UPDATE (diff id/commit sha)
- Timestamp: 2025-08-29T12:34:56Z
- Result: SUCCESS / FAILED
- Context: job_run_id, commit_sha, environment, source_ip

Summary
- Use Git for design-level auditing, Matillion job/audit history and REST API for operational changes, cloud secret managers for credential auditability, forward instance and cloud logs into your SIEM, and correlate with IdP and cloud IAM events to get complete visibility and alerting.

[Top](#top)

## How do you integrate Matillion with ticketing/ITSM for change approvals and incident tracking?
Short answer
Use Matillion’s orchestration components (HTTP Query, Python Script, Run Command) and the Matillion REST API to (A) create/update tickets on failures or change requests, (B) poll a ticket for an approval state, or (C) accept a webhook/API call from the ITSM tool to start/advance jobs. Mediate with serverless functions or an iPaaS if you need complex auth, mapping, retries or orchestration outside Matillion.

How it typically looks (patterns)
- Outbound incident/ticket creation (Matillion → ITSM)
  - On job error (On Failure or a Try/Catch pattern) call the ITSM REST API (ServiceNow, Jira, Zendesk, etc.) to create an incident/change request and include job name, environment, error details and a correlation ID.
- Approval gating (Matillion waits for change approval)
  - Option A: Matillion creates a change request and polls the ticket API until state == Approved (with timeout/backoff).
  - Option B: Matillion pauses and the ITSM automation calls Matillion’s REST API/webhook to resume the job once approved (preferred for non-blocking flows).
- Inbound trigger (ITSM → Matillion)
  - Configure ticket workflow automation or webhook in the ITSM tool to call Matillion REST API to start a job, passing variables (change ID, schedule, user).
- Incident tracking/updates
  - Update the ticket as steps complete/fail with HTTP calls from Matillion, including links to Matillion logs and the correlation ID for traceability.

Matillion components to use
- HTTP Query component — call REST APIs (create/update tickets, poll status).
- Python Script component (or Run Command) — for SDKs, complex payloads, or advanced error handling.
- Run Command — curl or CLI as alternative for simple calls.
- On Success / On Failure / Try-Catch patterns — to trigger ticket creation on error or update on success.
- Environment/Project variables & Secrets — store credentials, ticket IDs, and correlation IDs securely.
- Matillion REST API — to trigger jobs from the ITSM tool or to advance paused orchestration steps.

Example flows and snippets (conceptual)
- Create a ServiceNow incident when job fails (HTTP Query)
  - POST https://<servicenow>/api/now/table/incident
  - Body: {"short_description":"Matillion job <JOB> failed","description":"<error details>", "u_correlation_id":"<ID>"}
  - Use stored credentials (Basic/OAuth) from Matillion variables or cloud secret manager.

- Poll for approval (pseudo)
  - Create change request → save change_id in variable.
  - Loop: GET https://<servicenow>/api/now/table/change_request/<change_id> every N seconds
  - If state == Approved → continue job
  - If timeout → set failure path / create escalation ticket

- ITSM triggers Matillion job (webhook or automation)
  - ITSM calls Matillion REST API to start job:
    - POST https://<matillion-host>/rest/v1/... (use Matillion REST API)
    - Body: { "jobName":"DeployX", "variables": {"change_id":"CHG123"} }
  - Matillion receives variables and runs appropriate orchestration job.

Middleware / iPaaS patterns
- Use AWS Lambda / Azure Function / Google Cloud Function or an iPaaS (Workato, Mulesoft, Zapier) to:
  - Translate between ITSM and Matillion API formats.
  - Handle OAuth token exchange, retries and rate limits.
  - Persist state and correlation IDs outside Matillion if needed.

Security & operational best practices
- Store credentials in Matillion environment variables or cloud secret manager (AWS Secrets Manager, Azure Key Vault, GCP Secret Manager).
- Use service accounts with least privilege for ITSM and Matillion APIs.
- Add correlation IDs (ticket number) to Matillion logs and ticket payloads for traceability.
- Implement retries, exponential backoff, and idempotency for API calls.
- Don’t block resources indefinitely; prefer webhook-driven resume over long polling when possible.
- Log every ticket interaction and update ticket with links to Matillion job run and logs.

Monitoring & audit
- Link Matillion job run URLs and logs in the ticket.
- Update ticket status on each orchestration milestone.
- Use Matillion job history and audit logs to investigate incidents and changes.

Summary checklist to implement
1. Decide pattern: Matillion-initiated ticket vs ITSM-initiated job vs hybrid.
2. Store credentials and ticket variables securely.
3. Implement HTTP Query / Python Script calls to ITSM APIs for create/update/poll.
4. Expose Matillion REST endpoints (or use middleware) to accept calls from ITSM for resume/trigger.
5. Add correlation ID to all messages and logs.
6. Implement error handling, retries and timeout/escallation logic.
7. Test end-to-end with a staging ITSM instance and validate auditability.

No further suggestions.

[Top](#top)

## How do you design multi-region or multi-account deployments and promote artifacts programmatically?
High-level approach
- Treat each region/account as a separate Matillion instance (or small pool of instances) and manage them as immutable infrastructure created by IaC. Promote artifacts between instances using either GitOps (preferred) or API-driven project import/export from a CI/CD pipeline.
- Keep environment-specific configuration (connections, credentials, variables, endpoints) out of the project payload and move them into environment variables, secret stores, or Matillion’s instance-level configuration so the same artifact runs unchanged across envs.

Design patterns and components
1) Infrastructure
- Provision Matillion instances with IaC (Terraform/CloudFormation/ARM/Bicep). Template should define AMI/VM, instance profile, VPC/subnet/security groups, IAM roles, and user-data bootstrap. Keep artifacts like license info and bootstrap scripts parameterized for region/account.
- Use separate VPCs/subnets per region/account and handle connectivity to target data warehouses via VPC peering/Transit Gateway/PrivateLink/VPN as needed.

2) Artifact storage and CI/CD
- Store project sources in Git (GitHub/GitLab/Bitbucket). Use Matillion’s Git integration so developers work with branches/PRs and Matillion instances can check out the correct branch.
- Build a CI pipeline (Jenkins/Azure DevOps/GitHub Actions/etc.) that:
  - Validates changes (lint/tests).
  - Exports a project artifact (zip) or uses Git as the single source of truth.
  - Uploads artifacts to a central artifact store (S3, blob storage) if you use artifact-driven deploys.
  - Triggers deployment steps for target environment instances.

3) Promotion options
- GitOps (recommended):
  - Map environments to branches/tags (feature/dev/test/master/production).
  - Each Matillion instance runs on a branch appropriate to that instance. Promote by merging branch -> CI triggers instance to pull/checkout the new branch (via Matillion UI/REST or by remote Git operations).
  - Advantages: traceable history, smaller payloads, simpler merges.
- Project export/import via API:
  - CI exports project zip from dev and posts it to QA/prod Matillion instances via Matillion REST API (import endpoint) or via Matillion UI automation.
  - Useful when instances aren’t directly connected to the shared Git repo or for one-off migrations.
- Hybrid:
  - Use Git for everyday development, but use export/import for major releases or backups.

4) Environment configuration
- Use:
  - Matillion Project/Environment variables for runtime values that change by environment.
  - Cloud secret stores (AWS Secrets Manager, Azure Key Vault, GCP Secret Manager) for credentials and let Matillion retrieve them via IAM roles or instance profiles.
  - Service accounts/roles per environment; don’t hardcode credentials in jobs.
- Keep connection definitions per instance (connection pointing at the environment’s Snowflake/Redshift/BigQuery instance). Use consistent connection names across instances.

5) Networking and data residency
- Ensure Matillion instances have network routes to the target data warehouse in each region/account (private connectivity is usually required for production).
- For multi-region replication of intermediate artifacts (S3), either have per-region buckets (preferred for latency/residency) or cross-region replication and appropriate roles to access them.

6) Zero-downtime / Blue-Green
- Blue/Green pattern: provision new Matillion instance with new project, smoke-test pipelines, then switch over DNS or workflow triggers. Keeps downtime minimal.
- Keep idempotent deploy scripts and backups to roll back by importing previous project zip.

Automation example (CI-driven, artifact import)
- Steps:
  1. Developer merges to release branch in Git.
  2. CI creates a project export (zip) or packages the repo.
  3. Upload artifact to S3 (or pipeline artifact store).
  4. CI calls Matillion import API on target instance to import artifact and optionally start smoke-run.
  5. Run automated smoke tests and gate promotion to next env.
- Example curl pattern (conceptual):
  - Export (from source Matillion or from CI artifact): produce project.zip
  - Import:
    curl -u USER:PASS -X POST "https://<matillion-host>/rest/v1/import" -F "file=@project.zip"
  - Use secure service accounts and rotate credentials. Use signed URLs for artifact transfer if possible.

Operational considerations
- Permissions: use least-privilege IAM roles and cross-account assume-role for promotion pipelines that need access to S3 or to create infra in other accounts.
- Secrets: never store secrets in project artifacts. Use secrets manager and variables injected at runtime.
- Licensing: Matillion licensing is per-instance; automation must account for license provisioning in each region/account.
- Auditing: record CI/CD actions (who promoted what, when). Keep artifact checksum and Git commit id associated with every import.
- Testing: include smoke tests and data validation after import before marking promotion complete.
- Rollback: keep previous project artifacts and a documented rollback path (re-import previous zip or revert branch).

Summary checklist
- IaC for instances and network per region/account.
- Git as source of truth + Matillion Git integration where possible.
- CI pipeline that exports or references Git artifacts and imports to target Matillion via API.
- Use environment variables and secret stores for configuration.
- Secure networking, role-based permissions, traceability, and rollback processes.

[Top](#top)

## How do you share common connectors and credentials across projects while isolating secrets?
Goal: share connector definitions and logic but keep credentials separated and secure. Pattern: share templates (jobs/components/connection metadata) and inject secrets at runtime from per-project environments or an external secret store.

How to implement

1) Make reusable connector definitions without embedded secrets
- Build connection templates (Orchestration jobs or components) in a central library project or as Shared Jobs.
- In every connection template, replace any secret fields with variables (for example DB_USER, DB_PASS, S3_KEY). Do not hard-code passwords, keys or tokens.

2) Put secrets in project/environment scope only
- Create Environment-level or Project-level variables for secret values in each project’s Environment.
- Configure the connection properties to reference those variables (e.g. ${DB_USER}, ${DB_PASS}). At runtime Matillion will resolve the values from the Environment attached to that project.
- Because variables live in each project’s Environment, secrets are isolated per project even though the connection template is shared.

3) Use an external secret manager where possible
- Integrate AWS Secrets Manager, Azure Key Vault, or GCP Secret Manager and have your Environment variables populated from those external stores (Matillion supports calling those services or you can use an init Orchestration job to pull secrets).
- Prefer cloud-native auth (IAM role, managed identity, service account) for cloud storage instead of storing long-lived keys.

4) Share the connector logic
- Distribute the non-secret connection jobs/components via:
  - Shared Jobs / Project Library, or
  - Export/import of jobs, or
  - Git-based project sharing (push library project to a repo, pull into other projects).
- When imported, the jobs reference the same variable names; each project supplies its own secret values in its Environment.

5) Access control and operational hygiene
- Limit who can access Environments or change Environment variables via Matillion RBAC.
- Rotate secrets in the external vault and update Environment values accordingly.
- Prefer instance/role-based credentials for cloud services to avoid secrets in Matillion entirely.

Concise example
- Central job defines a DB connection with user=${DB_USER} and password=${DB_PASS}.
- Deploy that job to other projects via Shared Jobs or Git.
- In Project A Environment set DB_USER_A/DB_PASS_A (or populate DB_USER/DB_PASS from its secret store).
- In Project B Environment set DB_USER_B/DB_PASS_B.
- Same connection template, different secret values isolated per project.

Result: connector definitions and reusable jobs are shared; credentials remain isolated and managed per project or via a secure vault.

[Top](#top)

## How do you manage library dependencies for Python components and ensure reproducibility across environments?
Short answer
- Pin exact package versions in a requirements file and ensure the Matillion execution environment is provisioned with those same packages. For production-grade reproducibility, bake dependencies into the runtime (custom AMI/container) or run Python code in a containerized/external compute that you control.

How I handle it in practice (concrete patterns)
1) Lock dependencies
- Maintain requirements.txt (or poetry/poetry.lock, Pipfile.lock). Pin versions (package==x.y.z) and ideally use lockfiles with hashes (--require-hashes) so installs are identical.

2) Bake the runtime (recommended for prod)
- Create a custom Matillion instance image or container that has the exact Python interpreter and pip packages preinstalled.
- Use that image/AMI for dev/test/prod so every environment has identical libraries.
- Automate the build (Packer/CI/CD) so changes to requirements provoke a new image build and promotion.

3) Install centrally on the Matillion instance
- Use Matillion’s admin capability to install Python packages on the instance (or run pip on the instance shell) and ensure you install pinned versions. Capture pip freeze to record the exact set.
- Automate the same install during environment provisioning (bootstrap scripts/Ansible/Terraform) so other instances receive the same packages.

4) Ephemeral per-job installs (useful for dev or small teams)
- Have a job-level step that pip installs packages from a requirements file (hosted in Git or S3). Example: python -m pip install -r /path/requirements.txt
- Pros: reproducible for that run; cons: slower startup and risk of network/availability differences unless you use a private PyPI or wheel cache.

5) Containerize or externalize execution
- Put Python logic into a Docker image (with pinned deps) and run it via ECS/Fargate, Kubernetes, lambda container, or a Matillion "Run Command/External" pattern. This gives full control of interpreter + libs and strong reproducibility.

6) CI/CD and promotion
- Keep requirements.txt and any environment build scripts in Git with the Matillion job definitions.
- As part of your deployment pipeline, rebuild images or rerun provisioning scripts and run smoke tests that validate package versions.

7) Additional best practices
- Record the Python interpreter version as part of the manifest.
- Use a private artifact repository (Artifactory/AWS CodeArtifact) to avoid transient upstream changes.
- Use pip-tools/poetry for deterministic dependency resolution and to avoid implicit dependency drift.
- Store pip freeze / lockfiles with job release metadata so you can roll back to exact environment states.

Common pitfalls
- Installing packages manually on an instance without automation causes drift between environments.
- Using unpinned versions leads to non-deterministic behavior across runs.
- Relying on per-job pip installs without caching can slow jobs and fail under network issues.

Summary recommendation
Pin versions in lockfiles, automate environment provisioning (or bake images/containers) with those pinned packages, and promote those images across environments via CI/CD so Matillion jobs run against identical Python environments.

[Top](#top)

## How do you integrate Matillion with message queues (SQS, Pub/Sub, Service Bus) and exactly-once downstream effects?
Short answer: Matillion does not magically provide distributed exactly-once messaging guarantees — you integrate with queues using standard SDKs or HTTP components (or external triggers) and implement exactly‑once semantics using well‑known patterns: acknowledge only after a successful, idempotent commit; persist message IDs or use DB-level uniqueness/merge; use provider features (FIFO / deduplication IDs / ordering keys / sessions); and use dead‑letter queues for poison messages.

Detailed approaches and concrete patterns

1) How to connect Matillion to a queue
- Use Matillion orchestration jobs (recommended entry point).
  - Python Script component (most flexible): import boto3 / google‑cloud‑pubsub / azure‑servicebus, pull messages, process or stage, ack/delete.
  - Bash/Run Command component: call CLI tools (aws cli, gcloud pubsub cli, az cli).
  - HTTP Query component: use Pub/Sub push -> Matillion REST endpoint or call third‑party APIs.
  - Use Cloud Functions / Lambda / Logic Apps to push messages to Matillion via the Matillion API or to stage payloads in object storage (S3/GCS/Blob) and trigger Matillion.
- Typical flow: receive message → write raw payload to durable staging (S3/GCS/Blob or staging table) → call Matillion transform (or child job) to load/merge into target → acknowledge/delete message only after success.

2) Per‑provider specifics (common implementation patterns)

- AWS SQS
  - Poll from Matillion Python Script via boto3: ReceiveMessage (use VisibilityTimeout) and process N messages per batch.
  - For FIFO: supply MessageGroupId and MessageDeduplicationId at send; consumer preserves ordering per group.
  - Ack/delete only after full success: delete_message with ReceiptHandle.
  - If processing may take longer than VisibilityTimeout, call change_message_visibility to extend.
  - Deduplication strategies: store MessageId / deduplication id in DB (or use SQS FIFO dedupe on sender side) and perform idempotent upsert/MERGE in target (Redshift/Snowflake/DB).
  - Poison messages → configure DLQ.

- Google Pub/Sub
  - Use Subscriber pull inside Python Script (google-cloud-pubsub). Pull returns ack_id; do not ack until commit completes.
  - For long processing, modify ack deadline (modify_ack_deadline) or use lease extension.
  - Ordering: publish with ordering keys and use ordered subscription or process per key single‑threaded.
  - Dedup: use message attributes (messageId / custom id) and perform idempotent writes; BigQuery supports insertId for dedupe on streaming inserts; otherwise MERGE on unique key.
  - Push model: configure Pub/Sub push -> HTTP endpoint that launches Matillion job (via Matillion API) that then reads payload from request body or staging area.

- Azure Service Bus
  - Use azure-servicebus SDK: receive messages in peek‑lock mode, process, then complete() (or abandon/defer) on failure.
  - For sessions/order: use sessions to preserve ordering or session-aware processing.
  - Configure duplicate detection on the queue if messages originate from the same system.
  - Exactly-once: same pattern — persist message id and use idempotent merge/upsert before complete().

3) Exactly‑once (practical) — key patterns (Matillion-specific guidance)
- Do not rely on queue semantics alone — implement idempotency/deduping at landing/target:
  - Persist messages immediately to durable staging (S3/GCS/Blob or a staging table) before attempting to acknowledge the queue.
  - Use a processed_message table with unique constraint on message_id (or dedupe id). Use MERGE/UPSERT logic (Snowflake MERGE, Redshift MERGE, BigQuery MERGE, Synapse) keyed on message_id or natural business key.
  - Acknowledge (delete/ack/complete) the message only after the final commit to target/storage is durable and you have recorded the message as processed.
  - For very small transactions or cross‑system side effects, use an outbox pattern: write the intent to DB in the same transaction as your business state, then have a reliable dispatcher publish/outbound the message using idempotency keys.
- Idempotency tokens: if downstream external APIs accept idempotency keys, send one derived from message_id so retries are no‑ops.
- Visibility/lease management: always extend visibility/ack deadline if processing could exceed initial timeout so the same message is not delivered to another worker mid‑processing.
- Atomic swap pattern: load into staging table, then in single SQL transaction run dedupe/merge into final table; only after transaction success acknowledge.
- Handling retries and poison messages: put a retry counter or use queue redrive policies; route to DLQ for manual inspection after X failures.

4) Matillion job design and scaling tips
- Orchestration job master loop:
  - Poll queue for a batch.
  - Write raw messages to cloud storage (S3/GCS/Blob) and log message ids to staging table.
  - Trigger transformation job that loads the staged files to the target and runs MERGE using message_id dedupe.
  - On transformation success, delete/ack messages using stored receipt handles/ack_ids.
- Concurrency:
  - If ordering matters per key, partition by key and process each partition sequentially (e.g., use group/session or single-thread per key).
  - For high throughput, process in batches and run multiple Matillion workers, but ensure dedupe is in place to avoid duplicates across workers.
- Error handling: capture failures per-message, abandon or extend visibility, increment retry count, and push to DLQ after max retries.

5) Example pseudocode (Python inside Matillion orchestration job)
- SQS (pseudo):
  - receive = sqs.receive_messages(MaxNumberOfMessages=10)
  - for m in receive: persist to S3 and insert (message_id, receipt_handle, payload_meta) into staging table
  - call transformation job to MERGE staging into target
  - if transform success: for each message delete_message(ReceiptHandle)
  - else: extend visibility or leave for retry

- Pub/Sub (pseudo pull):
  - response = subscriber.pull(subscription, max_messages=10)
  - for msg in response: write payload to GCS, record ack_id and message_id in staging
  - run transform to load and dedupe
  - if transform success: subscriber.acknowledge(ack_ids)
  - else: subscriber.modify_ack_deadline(ack_ids, new_deadline)

6) Downstream external side-effects (APIs, billing, etc.)
- Use idempotency keys or outbox:
  - Prefer writing to DB an “outgoing actions” table within the same DB transaction that corresponds to the data change, then a separate reliable worker publishes/executed actions and records delivery status.
  - If Matillion must call external APIs directly, ensure the external API accepts idempotency tokens; only mark message processed if external call returned success and was durable.

7) Summary: practical guarantees
- You can achieve effectively exactly‑once end‑state by combining:
  - Acknowledge/complete only after durable commit.
  - Idempotent writes (MERGE/UPSERT/unique constraints).
  - Message id tracking table for dedupe or use provider FIFO/dedup features.
  - Proper lease/visibility management and DLQ strategy.
- Matillion’s role is to host the orchestration/processing logic (Python/Bash/HTTP components, staging to object storage, and transformations). Exactly‑once requires designing the pipeline around idempotent commits and careful ack semantics — Matillion provides the orchestration primitives to implement those patterns.

If you want specific code snippets for SQS / Pub/Sub / Service Bus that fit into a Matillion Python component or a sample job layout for Redshift/Snowflake/BigQuery MERGE, say which target and I’ll show it.

[Top](#top)

## How do you build a central parameter store or configuration database that Matillion jobs consult at runtime?
Short answer
Store configuration centrally (database table, object store JSON, or cloud Parameter/Secrets store) and have Matillion jobs read that store at job start — either (A) join/look up config inside transformations, or (B) load config into Matillion variables at runtime via a small “Load Config” orchestration. Use secrets managers for credentials.

Options with pros/cons
- Config table in your cloud data warehouse (Snowflake/Redshift/BigQuery)
  - Pros: easy SQL access, fast joins/lookups, single place for history and environments.
  - Cons: requires proper access control; secrets should still be in a secrets manager.
- JSON/YAML file in S3/GCS/Azure Blob
  - Pros: good for complex hierarchical config, versionable.
  - Cons: extra parsing step; eventual consistency.
- Cloud Parameter Store / Secrets Manager (AWS SSM / Secrets Manager, Azure Key Vault, GCP Secret Manager)
  - Pros: built for secrets, encryption, fine-grained access, rotation.
  - Cons: not ideal for large sets of non-secret config values.
- Dedicated configuration DB (RDS etc.)
  - Pros: central for multi-platform use.
  - Cons: extra infra overhead.

Common pattern (recommended)
1) Create a central config table (recommended for operational parameters and feature flags)
   - Example schema:
     - config_key (varchar)
     - config_value (varchar or json)
     - datatype (varchar) optional
     - environment (varchar) — dev/test/prod
     - service (varchar) — optional, to scope to a Matillion project/job
     - effective_from / effective_to — optional versioning
     - description

2) Decide how jobs will consume config
   - Inline lookup (preferred for transformations): join or lookup config table in your SQL transformation. This avoids extra Matillion variable work and leverages the DW performance.
   - Runtime variables (preferred for orchestration control/branching): have a small “Load_Config” orchestration job that reads config for an environment/service and populates Matillion variables (or a grid variable) which downstream orchestration/transformation jobs reference.

3) Implement the “Load_Config” orchestration job
   - Inputs: environment name (project or environment variable) and service/job name (optional).
   - Step A — Query config table (SQL component) using the env/service filters.
   - Step B — Convert results to Matillion variables:
     - If number of keys is fixed and small: use multiple Set Variable components (map key → Set Variable).
     - If keys are dynamic: implement a dynamic loader (two common approaches):
       - Use a short Python Script component (runs inside Matillion) that reads the query result CSV/JSON and sets grid variables or calls Matillion REST API to set project/job variables programmatically.
       - Or write the query result to a JSON file in object storage and have downstream jobs read/parse that JSON into variables via a Python Script or a JSON Parse component.
   - Call Load_Config at the start of any orchestration that needs the config.

Example SQL for fetch
SELECT config_key, config_value
FROM config_table
WHERE environment = :ENV AND (service = :SERVICE OR service IS NULL);

How to use config in transformations
- SQL join:
  SELECT t.*, c.config_value
  FROM staging_table t
  LEFT JOIN config_table c
    ON c.config_key = 'SOME_KEY' AND c.environment = 'prod'
- Variable usage:
  - After Load_Config sets project/job variables, use ${Your_Variable} in components (for file paths, threshold values, conditional branches).

Secrets handling
- Put secrets (DB passwords, API keys) in platform secret managers (AWS Secrets Manager, Azure Key Vault, GCP Secret Manager).
- Fetch them at runtime (Matillion has connectors/components for secrets or use a Python/REST component). Do not store secrets in plain config tables.

Performance and reliability tips
- Cache config per job run: load once at job start; avoid per-row remote calls.
- Keep config lookups efficient (use indexed keys if using RDS, clustering/partitioning in DW).
- Provide sensible defaults and fallback behavior when config is missing.
- Use explicit environment column and/or separate config sets per environment.
- Audit and version changes (effective_from, change log table, or source control for JSON files).
- Secure access: least privilege on config table and storage; use IAM roles/service accounts.

Governance and operational considerations
- Naming convention: service.environment.key
- Validation: validate config types/allowed values early in Load_Config and fail fast.
- Testing: include a ci/cd step or a test harness to validate config changes before promoting to prod.
- Monitoring: alert on missing/invalid config or failed loads.

Recommended baseline
- Non-secret runtime parameters and feature flags: central config table in the DW and either SQL lookups inside transformations or a Load_Config orchestration to populate Matillion variables.
- Secrets/credentials: cloud secrets manager.
- Use a small reusable “Load_Config” job (or shared component) to centralize the loading and mapping logic.

[Top](#top)

## How do you export job definitions as JSON and analyze them to build lineage and impact analysis tools?
Ways to get Matillion job definitions as JSON
- UI export: In the Matillion client you can export single jobs or whole projects to JSON (Project → Export / right‑click job → Export Job). That yields self‑contained JSON job definitions and environment metadata.
- Git integration: Enable Matillion project Git and pull the repo; jobs are stored as JSON there and you can use Git history for diffs.
- Programmatic export: Use Matillion’s API or automation endpoints (project export endpoints / REST automation depending on your Matillion version) to dump job JSONs. Use automation or scheduled scripts to fetch job JSON periodically.

What’s in the JSON you need
- Component list: each component (type, id, name).
- Component configuration/properties: SQL text, table names, file paths, connection names, downstream target info, run‑job references, variable references.
- Links/flow info: connectors between components or explicit child nodes that define the directed flow.
- Job inputs/outputs and variables: job parameters and environment variable placeholders.

High‑level approach to build lineage & impact analysis
1. Export JSONs (initial snapshot or continual via Git/API).
2. Parse JSON to extract components, properties and links.
   - Identify producer components: table create, copy, insert, unload/export, tables mapped in output properties.
   - Identify consumer components: table read, query components, load components that reference external tables.
   - Detect inter‑job edges: components that run other jobs (Run Orchestration, Call Job).
   - Capture variable usage: ${ENV_VAR}, job parameters — you must resolve these to concrete names for accurate lineage.
3. Build a graph model
   - Nodes: datasets/tables (schema.table), jobs, components, columns (optional).
   - Edges: component → dataset (writes), dataset → component (reads), component → component (flow), job → job (run).
   - Use a graph store (Neo4j) or graph lib (networkx) for in‑memory operations.
4. Column‑level lineage (optional, higher fidelity)
   - Parse SQL in Query components to detect SELECT sources → map columns to outputs.
   - Use SQL parsers (sqlglot, sqlparse, Apache Calcite, ANTLR grammars) to extract sources and projection expressions.
   - For complex SQL or UDFs, consider executing on the warehouse (EXPLAIN or query parsing facilities) or fallback to table‑level lineage.
5. Resolve variables and environments
   - Pull environment definitions (from exported environment JSON or API) and substitute variables to turn parameterized names into concrete dataset identifiers.
   - For cases where runtime values depend on orchestration, store unresolved placeholders and treat them as possible pattern matches (wildcards) in lineage queries.
6. Handle multi‑job and nested workflows
   - Follow Run Job component references and link the downstream job’s producers/consumers into the graph.
   - Maintain job boundaries but allow traversal between jobs for full impact analysis.
7. Build impact / downstream/upstream analysis
   - For impact: BFS/DFS upstream from a dataset to find producers; downstream traversal to find consumers.
   - Provide depth limits, filter by component type, and consider transitive closure across jobs.
8. Incremental updates and change tracking
   - Use Git diffs or API timestamps to re‑parse only changed job JSONs.
   - Maintain lineage change events and version history for temporal impact analysis.
9. Store/export to standards
   - Normalize results into OpenLineage/Marquez or your internal catalog schema to integrate with other tools.

Implementation details & tools
- Parsing and graph: Python + networkx for PoC, Neo4j for production graph queries, or store in relational tables for smaller deployments.
- SQL parsing: sqlglot (handles many dialects), Apache Calcite, or commercial SQL parsers for robust column lineage.
- Resolve runtime metadata by querying the target warehouse (e.g., DESCRIBE TABLE, query INFORMATION_SCHEMA) when SQL parsing is insufficient.
- Incremental pipeline: watch Git repo (webhook), reparse changed job JSON, update graph DB.
- UI: D3.js, Cytoscape, or Neo4j Bloom for visualization; support search by dataset/job and show upstream/downstream trees.

Edge cases and gotchas
- Parameterized names: must resolve variables from environments or treat as patterns.
- SQL complexity: dynamic SQL, UDFs, stored procedures and Python/R scripts inside components are hard for column lineage. Treat as black boxes or add custom parsers.
- Encrypted/hidden credentials: job JSON may mask secrets — you’ll still have table names but might not have connection credentials (you don’t need creds for static lineage).
- Multiple environments: the same job can produce different datasets per environment; model environment as a dimension in the graph.
- Performance: huge projects require incremental updates and batching; avoid reparsing everything each run.

Example pseudocode (conceptual)
- Load job JSON
- For each component:
  - node = {id, type, job}
  - if component has SQL: extract table reads and writes via SQL parser → add dataset nodes and edges
  - if component has explicit output table property: add write edge
  - if component calls other job: add job→job edge
  - add component→component edges using connector/links
- Persist nodes/edges in graph DB
- For impact: query graph DB for upstream/downstream traversals

Validation and QA
- Compare parsed lineage against a gold set (manual spot checks).
- Execute sample jobs and verify producers/consumers are observed.
- Use warehouse metadata (query logs, lineage from query history) to validate inferred lineage.

Summary (concise)
- Export jobs via UI, Git, or API.
- Parse job JSON to extract components, SQL, outputs, and links.
- Resolve variables/environments and follow Run‑Job calls.
- Build a graph (dataset/component/job nodes + directed edges).
- Use SQL parsers or warehouse metadata for column lineage where needed.
- Store in a graph DB and implement BFS/DFS queries for impact analysis; keep the process incremental via Git/webhooks.

[Top](#top)

## How do you compare Matillion’s Designer pipelines (DPC) with classic ETL jobs for team onboarding and governance?
Short answer
- Designer pipelines (DPC) are built for modular, declarative, low-code pipeline design and self-service; they emphasize reusability, discoverability, and visual flow.  
- Classic Matillion ETL jobs are the original job canvas with fine-grained procedural control and are often used for complex transformations or where fine control of execution is required.  
- For team onboarding and governance, DPC typically reduces time-to-productivity and enforces more consistent structure; classic jobs give power and flexibility but increase training and governance overhead.

Onboarding — practical differences
- Learning curve
  - DPC: gentler for non-engineers because of cataloged components, templates, and predictable patterns.
  - Classic: steeper for new hires; more “how this team does it” variance.
- Discoverability & reuse
  - DPC: component libraries, templates and a more catalog-driven UX make it easy to find existing pipeline pieces.
  - Classic: reuse exists but is more ad-hoc (copy/paste jobs, custom components).
- Speed to build
  - DPC: faster for standard patterns and pipelines due to pre-built components and param-driven templates.
  - Classic: faster for one-off, specialized logic where you need precise control.
- Training & onboarding artifacts
  - DPC: you can provide a smaller set of patterns and templates to teach; documentation maps to components.
  - Classic: needs more detailed runbooks, coding-style docs and examples.

Governance — practical differences
- Standardization & enforceability
  - DPC: easier to enforce standards via shared component libraries, templates and constrained parameterization.
  - Classic: governance relies on conventions, code reviews and stricter process enforcement.
- Version control & promotion
  - Both support Git and environment promotion, but DPC’s modular pipelines often make branching and merging cleaner because changes are smaller and more isolated.
- Auditing, lineage & metadata
  - DPC: metadata and lineage are clearer when pipelines follow standard componentized flows; easier for automated lineage extraction.
  - Classic: still auditable, but lineage may be harder to infer if jobs are custom and varied.
- Testing & CI/CD
  - DPC: smaller components => easier unit-style tests and predictable integration tests.
  - Classic: requires more bespoke testing approach; CI/CD still possible but tests may be more complex.
- Access control & separation of duties
  - Both support role-based controls at project/environment level; DPC’s componentization reduces surface area that needs privileged access.
- Operational visibility & debugging
  - DPC: more consistent logs and run patterns; easier for on-call and support to triage.
  - Classic: debug paths vary; experienced engineers often needed to interpret custom logic.

When to prefer each (governance-minded)
- Prefer DPC when:
  - You aim for rapid team onboarding and a self-service model.
  - You want strong reuse, predictable patterns and easier lineage.
  - You have many similar pipelines and need to scale developer headcount.
- Prefer Classic jobs when:
  - You have highly custom, complex transformation logic not easily expressed via canned components.
  - You need very fine-grained control over execution sequencing or custom scripting.
- Hybrid approach
  - Common: start new development in DPC for standard flows; keep legacy or highly bespoke jobs as classic. Migrate common patterns from classic to DPC over time.

Concrete governance checklist for either model
- Define a component/job naming convention and folder/project structure.
- Build a shared component library and templates (DPC: catalog; Classic: job templates or snippets).
- Enforce Git branching strategy and protected branches + PR/code-review process.
- Centralize environment variables and secrets; restrict who can change production vars.
- Create CI/CD pipelines to promote between dev/test/prod with automated smoke/integration tests.
- Capture lineage and publish metadata to a metastore or data catalog.
- Require runbooks and SLAs for production pipelines; standardize logging and alerting.
- Periodic audit of jobs/pipelines for deprecated patterns and technical debt.
- Onboard with a few canonical exercises: add a pipeline/component, submit PR, run tests, promote.

Migration & operational notes
- Break migration into small pieces: convert high-value, repetitive jobs first to maximize reuse and governance benefits.
- Preserve job history and run logs during migration for traceability.
- Expect an initial investment in building template libraries, CI/CD and documentation — payoff is faster onboarding and easier audits.

Summary
DPC improves onboarding, consistency and governance through modularity and templates; classic jobs provide power and flexibility for bespoke needs. Use DPC as the default for new and repeatable pipelines, retain classic for edge cases, and back both with the same Git, CI/CD and governance practices.

[Top](#top)

## How do you migrate from Matillion ETL (VM) to the Data Productivity Cloud and preserve pipelines and schedules?
Short answer
- Export projects (or use Git), recreate instance-level settings in Data Productivity Cloud, import projects, then migrate and remap schedules (using the Matillion REST API or by recreating them). You must recreate instance-level credentials, environments and secrets on the new instance because secure values are not exported.

Detailed, step-by-step process

1) Inventory and plan
- List projects, jobs, environments, variables, cloud credentials, custom components, external scripts, and all schedules (cron, recurrence, time zone).
- Note integrations (Git, SSO/IdP), network requirements (VPC, subnets, security groups), and IAM roles the VM used.
- Note any hard-coded IDs (job UUIDs), because import will change them.

2) Prepare the target Data Productivity Cloud (DPC) environment
- Provision the DPC instance and configure networking and IAM/roles to allow access to target data stores.
- Create users/SSO integration and permissions consistent with the source.
- Create instance-level Cloud Credentials (AWS/GCP/Azure), S3/GCS buckets, any external APIs required.

3) Move project code
Two common approaches:
- Git-backed projects: push your repository from the VM (or central Git) and connect the DPC instance to the same repo. This is the cleanest way to preserve history and avoid re-exporting jobs.
- Project export/import: In the VM Matillion UI use Project → Export Project (JSON) for each project, then in DPC use Project → Import Project. This transfers job definitions, transformations, environments (non-secure parts), variables, and custom components that are part of the project.

Notes:
- Secure values (passwords, secret credentials) are not included in project exports. Re-enter them in the DPC instance.
- Custom Python scripts, external files or any components stored outside the project must be copied (S3/GCS or Git).

4) Recreate instance-level items that are not exported
- Cloud Credentials (instance-level)
- Instance-wide environment variables and secrets
- Shared components and image assets
- Any dependent infrastructure (service accounts, IAM policies, network endpoints)

5) Migrate schedules (preserve timings and job links)
Schedules are instance-level and reference job IDs. Project import changes job UUIDs, so schedules must be remapped. Two options:

Option A — Automated (recommended for many schedules)
- Use the Matillion REST API to export schedules from the source and import into the DPC instance programmatically.
  - Steps:
    1. Extract job definitions from source (job name → job ID mapping).
    2. Export schedules as JSON from the source (schedule metadata includes job IDs, cron/interval, timezone, enabled flag).
    3. Import projects into DPC instance, extract new job name → new job ID mapping.
    4. Remap each schedule JSON to replace old job IDs with new job IDs (match by job name).
    5. POST the remapped schedule objects into the DPC instance API to create schedules (preserve enabled state).
  - Practical notes:
    - Schedules often include additional metadata (user who created it, next-run times). Only the actionable fields (job target, recurrence, timezone, enabled) need to be recreated.
    - Ensure your API client authenticates properly to both source and target instances (user with admin privileges).
    - Test on one or two representative jobs first.

Option B — Manual recreation (recommended for small number of schedules)
- Open each job in the DPC instance and recreate its schedule via the UI: set recurrence, cron expression, timezone and enable/disable state.

6) Validate
- Run a subset of jobs manually to confirm behavior and credentials.
- Trigger scheduled jobs and confirm they start and complete as expected.
- Verify environment variables, secrets, and external integrations work.
- Validate logging/monitoring and alerting are configured.

7) Cut-over and decommission
- Freeze changes on the VM instance (no new job edits) during migration cutover.
- After validation, change any upstream/downstream triggers (external schedulers or orchestrators) to point to the DPC instance.
- Decommission the VM instance according to your policies.

Key caveats and tips
- Secure values are never exported; plan for secure input of credentials in DPC.
- Schedules reference job UUIDs, so an automated remap based on job names is the most reliable way to preserve schedules.
- Git workflow reduces friction: connecting DPC to the same repo keeps job definitions identical and avoids some ID-mapping work (you still must recreate instance-level schedules).
- For complex migrations, script the extraction and import with the Matillion REST API and maintain a mapping table (old project/job ID → new project/job ID).
- Preserve timezone and cron expressions exactly; different instances may be configured with different default timezones.

Summary checklist
- Inventory everything (projects, schedules, credentials).
- Provision DPC and configure infra and permissions.
- Transfer code via Git or project export/import.
- Recreate instance-level credentials and environments.
- Export schedules, remap job IDs, and import schedules (or recreate manually).
- Validate runs and monitoring, then cut over.

[Top](#top)

## How do you compare Matillion Data Loader (batch) and Matillion CDC for ongoing ingestion needs?
Short answer
- Matillion CDC = continuous, log‑based capture for low‑latency, row‑level change replication (inserts/updates/deletes) with minimal source load — choose for transactional tables and near‑real‑time needs.
- Matillion Data Loader (batch) = scheduled/extracts or incremental loads (watermarks, API/page pulls) suited to periodic reporting, SaaS connectors, initial/full loads, simpler setup and lower operational overhead.

Detailed comparison (by concern)

1) Latency and semantics
- CDC: near‑real‑time (seconds → minutes), preserves event order and transaction semantics (depends on source), supports deletes/updates natively.
- Data Loader: batch latency determined by schedule (minutes → hours). Incremental via watermark fields or timestamp columns; no transaction‑log ordering guarantees.

2) Change capture method and source impact
- CDC: log‑based (reads DB transaction logs) so low CPU/IO on source and efficient for high‑change workloads.
- Data Loader: query/API based; full table scans or timestamp filters can add significant load for large tables or frequent runs.

3) Supported sources
- CDC: built for transactional DBs and major engines (MySQL, PostgreSQL, SQL Server, Oracle, etc.) and cloud variants — requires access to DB logs and appropriate privileges; not ideal for many SaaS APIs.
- Data Loader: broad set of connectors (databases, SaaS apps, files, APIs). Better for connectors where transaction logs are not available.

4) Setup, operations and complexity
- CDC: more initial setup (agents/permissions, log configuration, offset management) and operational monitoring (lag, offsets, schema drift handling). Higher operational skill required.
- Data Loader: simpler GUI scheduling, easy to onboard for non‑DBA users; simpler job maintenance.

5) Schema changes
- CDC: log‑based CDC typically handles common schema changes (e.g., new columns) more gracefully, but complex schema migrations may still need intervention.
- Data Loader: schema changes generally require job edits and mapping updates.

6) Transformations and pipeline flow
- CDC: typically lands change events into raw staging (change tables) and relies on downstream ELT jobs to apply/upsert and transform.
- Data Loader: can do simple in‑job transformations and loads directly to target tables; better for straightforward EL loads without a separate ELT layer.

7) Throughput and scale
- CDC: ideal for high‑velocity small changes; designed to scale for sustained change streams.
- Data Loader: handles bulk loads well but frequent incremental loads at scale can be inefficient.

8) Cost/licensing
- CDC is typically a separate product/feature with different licensing/pricing compared with Data Loader; CDC can be costlier depending on sources and volume. Factor licensing, agent overhead, and operational cost.

9) Monitoring and recovery
- CDC: provides change stream monitoring, offsets, replay and catch‑up behavior; good for continuous pipelines.
- Data Loader: job run logs and retry scheduling; simpler but less granular streaming diagnostics.

When to choose which (rules of thumb)
- Choose Matillion CDC when:
  - Low latency (near‑real‑time) is required.
  - You need accurate row‑level capture including updates and deletes.
  - Source is a transactional DB with access to logs and high change volume.
  - You need to minimize load on the source system.

- Choose Matillion Data Loader when:
  - Ingestion can be periodic (hourly/daily) and eventual consistency is acceptable.
  - Source is a SaaS API, file, or a system without transaction logs.
  - You need quick, low‑touch setup and basic transformations.
  - You’re doing one‑time/full loads or simpler incremental pulls.

Common hybrid pattern
- Use Data Loader for initial/full loads and for SaaS connectors; use CDC for ongoing delta capture on core OLTP tables. CDC keeps the production tables in sync; ETL/ELT applies business logic and consolidates SaaS data loaded by Data Loader.

Evaluation checklist before deciding
- Required latency (seconds/minutes vs. hours)?
- Need to capture updates and deletes atomically?
- Change rate and expected throughput?
- Source type (DB with transaction logs vs SaaS/API)?
- Allowed impact on source resources?
- Tolerance for operational complexity and agent installation?
- Budget/licensing constraints?
- Need for schema change automation and ordering guarantees?

Example recommendations
- Real‑time analytics/dashboarding on orders/payments: CDC for the core tables, Data Loader for daily SaaS enrichments.
- Monthly/weekly reporting from multiple SaaS apps: Data Loader.
- Large initial migration of on‑prem DB to cloud DW: Data Loader for full extracts, then switch on CDC for deltas.

No pleasantries. No further suggestions.

[Top](#top)

## How do you validate Data Loader pipelines, monitor run status, and integrate failure alerts into your NOC processes?
Validation, monitoring and NOC integration for Matillion Data Loader pipelines is a combination of design-time checks, runtime instrumentation, centralized observability, and incident management. Below is a practical, interview-style breakdown you can implement.

1) Pipeline validation (design-time and pre-production)
- Environment separation and CI/CD
  - Keep dev/test/staging/prod instances; run full pipeline tests in staging before promotion.
  - Store Matillion job definitions in Git and use CI (Jenkins/GitHub Actions) to deploy to a test environment and run validation suites via Matillion REST API.
- Unit and integration tests
  - Create small, focused “test” jobs that validate each component: source extract, transform logic, incremental logic, load. Use synthetic input datasets to assert expected outputs.
  - Use Matillion Query / Python Script / Calculator components to implement assertions (row counts, hash totals, key uniqueness).
- Data quality checks
  - Implement automated checks at end of pipelines: row counts, min/max/timestamp freshness, null thresholds, uniqueness/PK checks, referential integrity, distribution checks (e.g., % change vs baseline).
  - Store baseline metrics in an audit table or metadata store; compare each run to expected baselines and fail job if thresholds exceeded.
- Schema and contract validation
  - Validate source schema before loading (presence of expected columns, types). Fail fast and notify upstream owners on contract drift.
  - Use schema-on-write checks and database constraints where possible to provide a second line of defense.
- Test data and rollback validation
  - Use representative test datasets for regression tests. Validate idempotency of incremental loads.
  - For complex changes, run parallel compares (copy to temporary table) and compare outputs before swapping into production tables.

2) Run-time monitoring (how to monitor Matillion runs)
- Built-in job history and logs
  - Use Matillion’s job run history and per-job logs for direct troubleshooting. Capture run_id, start/end timestamps, job status, step-level logs.
- Export run metadata
  - Use Matillion REST API to export run events and metadata programmatically. Persist run_id, status, duration, row counts, error messages to a central monitoring DB or metrics system.
- Metrics and instrumentation
  - Emit metrics for: job status (success/fail), run duration, processed row count, delta from baseline, data-quality failure counts.
  - Push metrics to Datadog/Prometheus/CloudWatch/Stackdriver via small collector (Lambda/Cloud Function, or Matillion orchestration job that posts metrics).
- Dashboards and SLOs
  - Build dashboards showing job health, recent failures, SLA breaches, throughput. Define SLIs (e.g., pipeline freshness < X minutes) and SLOs.
- Synthetic and heartbeat checks
  - Schedule a lightweight “heartbeat” job that runs frequently, producing a known artifact; alert if heartbeat misses.

3) Alerting and integrating failures into NOC processes
- Alert categories and severity
  - P1 (page): pipeline failures that block downstream production or SLA breaches (e.g., ETL fails, data not refreshed by X minutes).
  - P2 (notify): data-quality thresholds exceeded but partial data arrives; or single-run non-critical failures.
  - P3 (ticket): non-urgent warnings, minor deviations, informational.
- Alert delivery paths
  - Use webhooks, Matillion Notification components, or REST API to post to:
    - Alerting/incident systems: PagerDuty, Opsgenie (for paging/escalation).
    - Chatops: Slack/MS Teams (with run_id, job name, environment, quick link).
    - Ticketing: create ServiceNow/JIRA incident automatically for P2/P3.
- Alert payload and content (what NOC needs)
  - Include: job name, run_id, environment, start/end time, error message/excerpt, failed step, row counts, link to Matillion job run URL, remediation steps and runbook link, last successful run, SLA breach status.
  - Provide actionable info to reduce time-to-resolution.
- Automated remediation and retry policies
  - Implement safe auto-retries with exponential backoff for transient errors; cap attempts and escalate if still failing.
  - Circuit-breaker logic to stop downstream jobs on repeated upstream failures.
  - Optionally run compensation/recovery jobs automatically if safe (e.g., re-run incremental load).
- Escalation and runbooks
  - Maintain per-pipeline runbooks with known failure modes and remediation steps, included in the alert payload.
  - Define escalation policy in PagerDuty/ops tool: who gets paged at what times and conditions.
- Centralized logging and correlation
  - Forward Matillion logs and job metadata to centralized log store (ELK/Cloud Logging). Ensure log entries contain run_id/job_id for correlation with other systems.
  - Correlate pipeline events with downstream consumer alerts (data consumers, BI dashboards) so NOC has context.

4) Implementation pattern (practical architecture)
- Matillion -> REST API -> Lambda/Cloud Function -> Metrics & Alerting
  - Use scheduled Lambda to poll Matillion run status or subscribe to webhooks if available. Push metrics to CloudWatch/Datadog and events to PagerDuty/Slack via integrations.
- Matillion job-level webhooks/notifications
  - On job failure, call an orchestration “Notification” step that posts to a webhook endpoint carrying structured JSON for NOC ingestion.
- Central “monitoring” job
  - A Matillion orchestration job runs every N minutes to collect audit metrics, run validations, and emit metrics or create incidents when thresholds are hit.

5) Example thresholds and alerting rules
- Immediate P1 page:
  - Job failure for a critical pipeline OR SLA missed (run not completed X minutes after expected completion).
  - >3 consecutive failures in a row for the same job.
- P2 notify (create ticket + Slack):
  - Data-quality metric exceeds threshold (e.g., nulls > 5%, row count delta > 50%).
  - Non-critical pipeline failure that does not immediately impact downstream processes.
- P3 log/ticket:
  - Single non-critical warning or transient error auto-resolved by retry.

6) Operational best practices
- Always include run_id and direct Matillion link in alerts.
- Keep audit tables with per-run metadata and data-quality metrics for trend analysis and SLA reporting.
- Test alerts and escalation periodically (playbooks/drills).
- Version control jobs and track changes; tie deployment to release notes so NOC knows what changed.
- Keep runbooks current in the same repo or linked to alerts.

7) Example alert JSON (payload NOC can ingest)
{
  "pipeline": "daily_orders_load",
  "environment": "prod",
  "run_id": "123456",
  "status": "FAILED",
  "start_time": "2025-08-29T02:00:00Z",
  "end_time": "2025-08-29T02:12:03Z",
  "failed_step": "load_to_dw",
  "error_message": "Unique constraint violation on orders.id",
  "row_count_expected": 100000,
  "row_count_loaded": 0,
  "sla_breach": true,
  "matillion_url": "https://matillion.example/jobs/run/123456",
  "runbook_url": "https://confluence.example/runbooks/daily_orders_load",
  "severity": "P1"
}

8) Recovery & post-incident
- Capture RCA metadata automatically (who acknowledged, time to acknowledge, time to resolve).
- Post-incident: add tests or modify thresholds to prevent recurrence; update runbooks; if root cause is environmental (e.g., DB down), add upstream alerts to detect earlier.

Summary checklist
- Validate in CI via test jobs and sample datasets.
- Emit structured metrics and logs from Matillion to centralized monitoring.
- Create clear alerting rules with severity mapping to NOC incident flows (PagerDuty, Slack, ServiceNow).
- Include run_id, job link, error context, and runbook in every alert.
- Implement auto-retry, circuit breakers, and documented runbooks for the NOC.

This approach ensures Matillion pipelines are validated before release, operations can detect and diagnose failures quickly, and NOC processes receive actionable alerts with defined escalation.

[Top](#top)

## How do you implement cross-cutting concerns like PII scanning, schema validation, and DQ in reusable shared jobs?
High level pattern: implement metadata-driven, parameterized shared jobs (orchestration + transformation) that accept table/schema/column/rule-set as variables and run a repeatable loop (Table Iterator / SQL) to produce audit records, enforce thresholds, and optionally remediate (mask, stop, alert). Centralize rules and expected schema in control tables and call the shared job from per-source jobs via Run Orchestration/Transformation Job components.

How this maps in Matillion (concrete components and flows)

1) Shared-job design and reuse
- Build a small number of shared jobs (Orchestration jobs for control/flow, Transformation jobs for data checks). Mark them as reusable by designing them to be driven by Project/Job/Environment variables (schema, table, column, rule_id, sample_size, run_mode, threshold, control_table_name).
- Call shared jobs from other jobs using Run Orchestration Job / Run Transformation Job and pass variables via the component’s “Job Variables” mapping.
- Store rule definitions, thresholds, expected schemas, and PII patterns in control tables in the warehouse (a control schema). This avoids hard-coding and makes the shared job generic.
- Use Git for version control of reusable jobs and use naming/versioning conventions for shared jobs.

2) PII scanning (detection + classification)
- Metadata-driven approach:
  - Control table holds which tables/columns to scan and which pattern(s) to apply (regex, data-type-based, or external type).
  - Use Table Iterator (or a simple SQL that returns the set of columns) to loop.
- Detection techniques:
  - SQL-based regex scans: use SQL components to run REGEXP_LIKE / RLIKE queries (Snowflake, Redshift, BigQuery have equivalents) for patterns (emails, SSNs, credit cards).
  - Sample scanning: run on a random sample (LIMIT or TABLESAMPLE) to reduce cost.
  - Use Python Script component or REST call to integrate enterprise DLP (AWS Macie, Google DLP) for deeper detection; call API via REST Query component or Python requests.
- Actions:
  - Write detection results to control/results table with job_run_id, table, column, pattern, hit_count, sample_size, probability_score.
  - If threshold exceeded, branch with If Condition: call a Masking job, create masked view, or escalate to ops via Email/REST Slack component.
- Masking/remediation:
  - Prefer native warehouse masking where available (Snowflake masking policies): use SQL component to create policies and APPLY.
  - Or use deterministic hashing/HMAC or tokenization in a Transformation job to produce masked copies or masked views. Parameterize algorithm/keys via Environment variables and use Python or SQL components to apply consistently.

3) Schema validation (schema drift detection)
- Store expected schema (column name, data type, nullable, partitioning/PK info) in control table.
- For each target table:
  - Query INFORMATION_SCHEMA (or relevant metadata view) using a SQL component to get actual schema.
  - Compare expected vs actual in a transformation or Python component:
    - New columns, missing columns, type mismatches, nullability changes, extra columns.
  - Insert differences into schema_audit table with severity.
- Behavior:
  - If differences are breaking (e.g., missing columns), fail the job (use If Condition -> Stop Task) or route to a remediation workflow.
  - For non-breaking additions, optionally update metadata or signal downstream teams.
- Automation: run schema checks as a pre-step (Orchestration job) before transformation jobs run to prevent silent failures.

4) Data Quality (DQ) checks
- Represent DQ rules in a control table:
  - rule_id, table, column, rule_type (null_check, unique_check, range_check, regex, referential_integrity), SQL_template, threshold, severity, remediation_job.
- Shared DQ job flow:
  - Table/Rule Iterator -> For each rule, render SQL from SQL_template (use Job Variables for table/column) -> run Query component (count, count distinct, min/max, percent null) -> write metric to dq_results table.
  - Post-loop aggregation: compute pass/fail per rule and overall quality score for the table.
  - If failure thresholds exceeded: branch to remediation (re-run upstream load, load to quarantine tables, create tickets, or raise alerts).
- Common checks:
  - Null rate per column, distinct counts and uniqueness checks, referential integrity (count of orphans via left join), value ranges, distribution change (compare historical percentiles).
- Notification & enforcement: use If Condition + Email / REST components to raise alerts; set job to fail to stop downstream jobs if enforcement is required.

5) Logging, auditing and observability
- Every shared job writes a run-level record and per-rule/per-table results with:
  - job_run_id, start_ts, end_ts, rows_scanned, rows_matched, metric_value, threshold, status, remediation_action.
- Use a centralized dashboard (BI) driven by the results tables for SLAs and trending.
- Emit structured events (JSON) to external monitoring via REST if required.

6) Error handling and control flow
- Use If Condition / Stop Task to enforce fail/pass behavior.
- Provide run_mode variable for “report-only” vs “enforce” so the same shared job can be used for continuous monitoring or blocking enforcement.
- Use try/catch patterns with separate branches to capture errors and write error details to an audit table.

7) Security and operational concerns
- Keep masking keys and DLP credentials in Environment variables or external secret store; never hard-code.
- Minimize full-table scans by sampling and by narrowing columns by type in metadata-driven scans.
- Test shared jobs with a variety of input metadata and include a dry-run mode.

Example minimal implementation outline (pseudo-flow)
- Control tables: pii_rules, dq_rules, expected_schema
- Shared Orchestration Job: PII_Scan_Controller(job variables: schema, table, run_mode)
  - Query component: select columns from control.pii_rules for given table
  - Table Iterator over columns -> Run Transformation Job (PII_Scan_Transform) passing column and pattern
- Shared Transformation Job: PII_Scan_Transform (variables: schema, table, column, pattern, sample_size)
  - SQL component: SELECT COUNT(*) AS hits FROM schema.table WHERE REGEXP_LIKE(column, :pattern) [LIMIT sample_size]
  - Insert result into control.pii_results
  - If hits > threshold AND run_mode='enforce' -> Run Job Masking or Fail

Why this approach works
- Everything is metadata-driven and parameterized so the same shared job scales across many tables and rules.
- Centralized results provide auditability and trend analysis.
- Separation of detection, validation, and remediation keeps shared jobs small, testable and reusable.
- Using Matillion orchestration components (Run Job, Iterator, If Condition) and transformation SQL/Python keeps the logic inside the ETL tooling and leverages the target warehouse for heavy lifting.

[Top](#top)

## How do you structure a medallion architecture in Matillion and enforce contract tests between layers?
High level approach
- Implement classic medallion layers: Bronze (raw landing), Silver (cleaned/enriched), Gold (aggregated/business-ready). Physically separate them by schema/dataset/table prefix and by Matillion job folders to enforce boundaries.
- Use Matillion orchestration jobs to orchestrate loads and tests, transformation jobs to produce layer outputs. Treat each layer transition (Bronze→Silver, Silver→Gold) as a controlled pipeline with pre/post checks (contracts).
- Enforce contracts by running automated SQL/logic checks in Matillion after writing to a staging/temp table and before swapping it into production. Fail the job (or stop swap) on contract violations.

Pattern and job structure
1. Namespaces and jobs
   - Schemas/tables: raw.bronze_*, curated.silver_*, analytics.gold_* (or dataset prefixes).
   - Matillion project structure: folders per layer; reusable sub-jobs for common tasks (load S3/GCS, column mapping, test runner).
   - Use environment variables (connection, schema names) and job variables (run_id, contract_version, batch_ts) so jobs are parameter-driven.

2. Write-to-temp-then-promote
   - Transformations write to a staging/temp table (silver_tmp).
   - Run contract tests against silver_tmp.
   - If tests pass, perform an atomic swap/rename to silver (or MERGE into production table), update metadata; if fail, do not swap and mark failure.

3. Test execution and failure handling
   - Implement tests in orchestration job immediately after the transformation finishes.
   - Use Database Query / SQL Script components to run checks; set job variables from result and use If components to branch.
   - On failure: Stop component / Raise Error, send alerts, and preserve staging for investigation. On success: swap/merge and update contract metadata table.

Types of contract tests (examples)
- Schema contract: expected column names, data types, nullability, column order if required.
  Example check (Snowflake/Redshift style):
    SELECT COUNT(*) FROM INFORMATION_SCHEMA.COLUMNS
     WHERE table_schema='CURATED' AND table_name='SILVER_TMP'
       AND column_name='expected_col' AND data_type='VARCHAR';
  Fail if count <> 1 for any expected column.

- Row count / minimum volume:
    SELECT COUNT(*) AS row_cnt FROM curated.silver_tmp;
  Compare row_cnt >= expected_min; fail if below.

- Uniqueness / primary-key check:
    SELECT (COUNT(*) - COUNT(DISTINCT pk)) AS dup_count FROM curated.silver_tmp;
  Fail if dup_count > 0.

- Referential integrity / foreign keys:
    SELECT COUNT(*) FROM curated.silver_tmp s
      LEFT JOIN curated.dim_ref r ON s.ref_id = r.id
      WHERE r.id IS NULL;
  Fail if > 0 (or handle via soft-degrade if acceptable).

- Business-value thresholds (null rate, outliers):
    SELECT SUM(CASE WHEN important_col IS NULL THEN 1 ELSE 0 END) / COUNT(*) AS null_pct FROM curated.silver_tmp;
  Fail if null_pct > allowed_pct.

- Row-level checks / checksum comparisons:
    - Compare checksums or row counts between source and bronze to ensure completeness.
    - Use HASH functions over key columns to detect unexpected changes.

Implementing tests in Matillion
- Use Database Query / Execute SQL components to run test queries. Capture results into Matillion variables using the Query component’s “Set Variable” option.
- Use an If component to check variables. On failure path, use Stop or Raise Error components (or throw non-zero exit) to fail the orchestration job.
- For multiple tests, aggregate results into a single boolean variable (e.g., tests_passed) and use one conditional branch.
- Use a metadata/test-results table (e.g., ops.contract_tests) to insert each test run result (timestamp, layer_from, layer_to, test_name, status, details). Insert via SQL component so you have historical records and dashboards.

Atomic promotion pattern
- Write to silver_tmp.
- Run contract tests on silver_tmp.
- If pass:
   - For Snowflake: use table rename/replace pattern (e.g., silver_temp -> silver_new; then rename silver to silver_old and silver_new to silver). Or do MERGE to production.
   - For BigQuery: use table copy/replace or load to partition/table and then swap alias pointer (if using views).
- If fail: keep silver_tmp (or write to quarantine schema) and do not replace production.

Metadata-driven contract registry
- Maintain a contracts table that describes expected schema and test parameters:
  contracts (layer_from, layer_to, table_name, contract_version, tests JSON)
- Matillion reads contract definitions and dynamically constructs SQL checks (or iterates tests via a loop sub-job), enabling centralized contract updates without changing many jobs.

Integration with Great Expectations / external test frameworks
- Run Great Expectations suites from Matillion via:
  - Python Script component (Matillion supports running Python in the orchestration context) pointing at a container/virtualenv with GE and DB credentials; or
  - SSH/Run Command to a CI runner that executes tests and returns pass/fail.
- Parse GE results in Matillion and fail the job if expectations fail.
- Advantages: expressive assertions, human-readable docs, versioned expectation suites that can live with code.

CI/CD and enforcement
- Keep Matillion jobs in Git (Matillion has Git integration). Require contract tests run in pipeline prior to deploy/merge.
- In CI pipeline, use the warehouse SQL connection or Matillion’s API to execute a "dry-run" or test job verifying schema and sample data — block deployments on contract failures.
- Use contract_version in code and in the contract registry to prevent blind contract changes.

Monitoring and observability
- Log all test runs to a central table with timestamps, failure messages, and run_id.
- Expose dashboards for SLA/failure rates.
- Send alerts for contract failures with details and links to staging tables.

Concrete SQL examples
- Schema check (example, Snowflake):
  WITH expected AS (
    SELECT column_name, data_type FROM VALUES
      ('id','NUMBER'),('name','VARCHAR'),('ts','TIMESTAMP')
    AS t(column_name, data_type)
  )
  SELECT e.column_name, e.data_type,
     CASE WHEN EXISTS (
       SELECT 1 FROM INFORMATION_SCHEMA.COLUMNS c
        WHERE c.table_schema='CURATED' AND c.table_name='SILVER_TMP'
          AND c.column_name = e.column_name
          AND c.data_type ILIKE e.data_type
     ) THEN 1 ELSE 0 END AS exists_flag
  FROM expected e;
  -- In Matillion, fail if any exists_flag = 0.

- Uniqueness:
  SELECT CASE WHEN SUM(dup_count) = 0 THEN 'PASS' ELSE 'FAIL' END AS pk_unique
  FROM (
    SELECT COUNT(*) - COUNT(DISTINCT id) AS dup_count FROM curated.silver_tmp
  );

Operational best practices
- Keep contracts small and focused (schema + essential integrity + volume thresholds). Let downstream business tests live in Gold.
- Version contracts and change them via PRs with automated tests and a deprecation window for producers.
- Keep staging tables for troubleshooting; archive failing batches for replay.
- Centralize test logic as reusable Matillion sub-jobs so changes to testing behavior propagate consistently.

Summary (concise)
- Structure Bronze→Silver→Gold by schema and Matillion folder/jobs.
- Write transforms to temp tables, run contract tests in Matillion orchestration, and only promote on success.
- Implement schema, row-count, uniqueness, referential, and business-rule tests using SQL components, variables, and If/Stop branching.
- Store contract definitions and test results in metadata tables; integrate external tools (Great Expectations) where useful.
- Gate deploys in CI using contract tests and keep observability/alerting for failures.

[Top](#top)

## How do you surface dataset readiness signals (success flags, watermarks) to downstream consumers reliably?
Short answer
- Emit an explicit "dataset ready" signal at the end of the Matillion orchestration/transform job rather than hoping consumers infer readiness from data presence.
- Implement the signal as one or more of: a control table row (status + watermark + metadata), a manifest/marker file in object storage, and/or an event (SNS/SQS/Kafka/webhook). Use Matillion orchestration components to write those signals atomically only after all load + quality checks succeed.
- Make signals idempotent, monotonic (watermark/sequence), and include run_id, checksums/row_count, and partition info so downstream consumers can verify and handle backfills/out‑of‑order runs.

Concrete approach (recommended pattern)
1) Control table for dataset state (primary source of truth)
   - Create a control table in the target warehouse (Snowflake/Redshift/BigQuery) with columns like:
     dataset_name, partition_key, run_id, status (IN_PROGRESS/FAILED/SUCCESS), watermark_ts, start_ts, end_ts, row_count, checksum, manifest_path, details
   - At job start: INSERT a row with status=IN_PROGRESS and the run_id + watermark.
   - On success: UPDATE the same row to status=SUCCESS and populate end_ts, row_count, checksum, manifest_path.
   - On failure: UPDATE to status=FAILED with error details.
   - Use Matillion's Execute SQL components (or the job-run API) to do these inserts/updates as the last step.

2) Atomically-published manifest/marker file (for S3/GCS)
   - Emit a small JSON manifest or zero-byte _SUCCESS file after successful load listing files + checksums + watermark + run_id.
   - Write the manifest only after all data files are uploaded and quality checks pass. Prefer publishing to a final path (or write to temp then “move” to final). Marker + manifest are easy for non-warehouse consumers to see.
   - Example manifest:
     {"dataset":"orders","partition":"2025-08-28","run_id":"r-20250828-001","status":"SUCCESS","watermark":"2025-08-28T00:00:00Z","row_count":123456,"files":["s3://bucket/path/part-0000.parquet"], "checksum":"..."}
   - Use Matillion S3 components or Python/HTTP components to write these files.

3) Event notification for push-based consumers
   - After updating the control table and/or manifest, push an event with the run_id and pointer to metadata (control row id or manifest path). Use SNS/SQS, Kafka, webhook, or Matillion's HTTP/Python components to call an API or Lambda.
   - Consumers subscribe and trigger ingestion when they receive a SUCCESS event pointing to the proven run_id.

4) Enforcement via pre-commit/quality checks before marking success
   - Run row counts, null/uniqueness checks, schema validation, checksum verification, partition verification and only then move to SUCCESS.
   - Keep a deterministic set of checks and surface the check results in the control row and manifest.

5) Partition-level readiness for large/partitioned datasets
   - Maintain per-partition control rows and per-partition manifests. Downstream consumers operate on partition-level state (e.g., partition=2025-08-28 status=SUCCESS).
   - Avoid a single dataset-wide flag when partitions are loaded independently.

Reliability details (common fail cases and mitigations)
- Atomicity: Do not create a marker file before all files and checks are fully written. Publish marker only after final commit/rename or via a control-table transaction.
- Idempotency: Include run_id and let consumers ignore repeated or older run_ids. Implement upsert semantics on the control table.
- Ordering/backfills: Use monotonic watermarks or sequence numbers. Consumers should compare watermark/run_id and accept only newest or explicitly requested historical runs.
- Partial writes and visibility: Use staging tables and atomic swap where supported (COPY into staging, then atomic rename or swap). Update control table only after swap.
- Failures and retries: On retry, update the same run_id row (status=RETRY or keep attempt_count). Record attempt metadata so consumers can distinguish a retried run from a new run.
- Verification: include row_count and checksums in signals so consumers can validate data before processing further.
- Security & permissions: Restrict who can write control rows or marker files to avoid spoofing and ensure producers are authenticated (Matillion credentials and IAM roles).
- Timezones & ISO format: store watermarks/timestamps in UTC ISO 8601.

How Matillion fits in
- Use Orchestration jobs to coordinate: create events, run transformations, run quality checks, and execute final signal emission.
- Use Execute SQL components to write to the control table; use S3/GCS components or Python Script components to write manifest files; use HTTP Query or Python to send webhooks or push to message queues.
- Optionally use Matillion job variables to carry run_id, watermark, row_count between components and ensure the same run_id is used in all emitted signals.
- Use Matillion job failure steps/On Failure actions to update control table with FAILED if the job dies unexpectedly.

Consumer patterns (how downstreams read signals)
- Poll the control table: SELECT where dataset/partition and status=SUCCESS and watermark >= needed.
- Watch object storage for manifest/marker files (or subscribe to storage events).
- Subscribe to event bus (SNS/SQS/Kafka/webhook) for push notifications.
- Validate signal contents (run_id, row_count, checksum) before processing; track last processed run_id/watermark.

Example minimal workflow in Matillion
1) Start orchestration job — generate run_id and set variable watermark.
2) INSERT control row status=IN_PROGRESS via Execute SQL.
3) Run data load + transforms.
4) Run data quality tests.
5) On success:
   - write manifest to S3 (S3 Put or Python),
   - UPDATE control row to status=SUCCESS with row_count/checksum,
   - POST event via HTTP or invoke Lambda to notify consumers.
6) On failure: UPDATE control row to status=FAILED with error details.

Schema examples
- Control table columns:
  dataset_name, partition_key, run_id, status, watermark_ts, start_ts, end_ts, row_count, checksum, manifest_uri, attempt, error_text

- Manifest (JSON, stored in S3/GCS):
  {dataset, partition, run_id, status, watermark, row_count, files:[{path, size, checksum}], produced_by:"matillion-job-id", end_ts}

Summary checklist for reliable readiness signals
- Use a canonical control table + per-partition rows.
- Publish manifest/marker files after final commit.
- Push events for low-latency consumers.
- Always include run_id, watermark, row_count/checksum.
- Make signals atomic, idempotent, and monotonic.
- Enforce quality checks before signaling success.
- Record attempts and failures for observability.



[Top](#top)

## How do you design table-by-table SLAs and prioritize pipelines accordingly in scheduling and resource allocation?
Approach in steps, with practical Matillion-specific controls and operational rules.

1) Define measurable SLAs per table
- SLA metrics: freshness (max age), availability (success rate %), latency (time from source event to table ready), completeness (row counts or high-water mark), and RTO (time-to-recover/backfill).
- Express SLAs concretely: e.g., orders.dim -> freshness ≤ 15 min, success ≥ 99.9%, completeness within 10k rows of expected daily delta; reporting.fact_sales -> freshness ≤ 2 hours, success ≥ 99%, RTO 4 hours.
- Add windows and exceptions (e.g., maintenance windows, irregular sources).

2) Classify tables into tiers and assign priorities
- Typical tiers: Gold (real-time/BI-critical), Silver (daily reporting), Bronze (archival/experimental).
- Map each table to a priority score (numeric or weight) determined by business impact, consumer dependency, SLA strictness, and data volume.
- Example: Gold=priority 100, Silver=50, Bronze=10.

3) Map tables to pipelines and establish ownership
- Inventory: which Matillion Orchestration/Transformation jobs write each table.
- Ensure single canonical pipeline per table where possible; document owner and downstream consumers.
- Tag Matillion jobs with table names and SLA tier (use job variables or naming conventions).

4) Scheduling and prioritization rules
- Scheduling types: event-driven (CDC, file arrival) for Gold; frequent batch (15m/1h) for Silver; nightly for Bronze.
- Enforce priority ordering in orchestration flows: use controller jobs that schedule high-priority pipeline runs first (Run Orchestration components or "Run transformations" with dependencies).
- Use separate worker queues or environment instances for heavy/low-priority workloads when possible.
- Time windows: reserve peak windows for Gold jobs; schedule heavy extract/transform for Bronze in off-peak.

5) Resource allocation and compute controls
- Split compute concerns: Matillion orchestration engine vs data warehouse compute (Snowflake warehouse, Redshift cluster, BigQuery slot).
- For the warehouse: use auto-scaling warehouses or dynamically resize for high-priority loads; create dedicated warehouses for Gold workloads to avoid noisy neighbors.
- For Matillion runtime: control concurrency by environment/instance sizing and job concurrency settings. Limit concurrent runs of heavy jobs via job-level checks (variables, database locks, or control tables).
- Use separate Matillion environments or instances for resource isolation if necessary.

6) Implement dependency and backpressure controls
- Use “Wait for file”, metadata checks, or CDC checkpoints to avoid unnecessary runs.
- Implement job-level pre-checks: if upstream table not ready, abort or postpone downstream jobs with defined retries and exponential backoff.
- For bulk loads, use partitioned/parallel loads to reduce runtime; mark partial success and re-run specific partitions for recovery.

7) SLA enforcement & escalation
- Instrument jobs with metrics: start/end times, rows processed, success/failure, high-water mark. Store in a central SLA table.
- Integrate alerts: Matillion notifications + CloudWatch/Stackdriver/Prometheus to send thresholds breaches to PagerDuty/Slack.
- Automated actions: on SLA breach, (a) escalate alert, (b) auto-scale warehouse, (c) pause low-priority jobs or re-prioritize queue, (d) trigger backfill jobs with expedited resources.
- Define runbook: who owns fix, expected remediation timeline, rollback/backfill steps.

8) Monitoring, observability and reporting
- Build SLA dashboard showing per-table freshness, run-time, failure rate, and expected vs actual. Leverage Matillion job history, warehouse query logs and a metrics store.
- Implement synthetic queries to validate data quality and freshness automatically.

9) Continuous tuning
- Review SLA compliance periodically, reclassify tables based on consumer needs, tune batch sizes, change CDC vs full extracts, and adjust compute sizing.
- Post-incident reviews to update priorities, scheduling windows, and retries.

Practical Matillion techniques to implement above
- Use Orchestration jobs to coordinate table-level pipelines and enforce ordering and retries.
- Pass SLA tier as a job variable to downstream transformation jobs and use it to decide whether to proceed or to throttle/parallelize.
- Use conditional components (If, Wait, Group) to implement pre-checks and backpressure.
- Log metrics to a centralized table via “Write to Database” or API components for SLA tracking.
- For heavy transforms, use Matillion’s native pushdown to the data warehouse where possible to reduce Matillion compute and leverage warehouse scaling.

Example policy (concise)
- Gold tables: run event-driven or every 15m, dedicated warehouse w/ auto-scale, concurrency limit 3, alert on >3 mins delay, automatic warehouse scale-up and cancellation of Bronze jobs if breached.
- Silver tables: run hourly, shared mid-size warehouse, concurrency limit 6, alert on >30 mins delay, backfill window 4 hours.
- Bronze tables: run nightly, low-priority queue, concurrency unlimited but preemptible by higher tiers.

Outcome goals
- Predictable SLA compliance for critical datasets.
- Isolation of noisy or heavy jobs.
- Clear escalation and automated mitigations.
- Measurable, auditable metrics per table to guide continuous improvement.

[Top](#top)

## How do you ensure reproducibility of transformations by pinning Matillion release, warehouse versions, and SQL patterns?
Short answer: treat reproducibility as three coordinated artifacts you must pin and record — the Matillion runtime image/version, the target warehouse engine + drivers/config, and the exact SQL/transform code (and its templates). Use immutable images/AMI/VM images + Git for Matillion projects + DDL/SQL migration scripts + CI/CD to deploy a known combination. Below are concrete steps and patterns.

1) Pin Matillion release
- Deploy from an explicit image/AMI/VM image reference (not “latest” or image family). For AWS use the specific AMI ID; for GCP use the exact image name; for Azure use the exact VM image URN. Put that value into IaC (CloudFormation/Terraform) so you always launch the same Matillion build.
- Disable automatic in-place upgrades or automate upgrades via controlled image replacement. Never rely on implicit UI upgrades when you need reproducibility.
- Version your Matillion project exports (Matillion jobs are JSON) and store them in Git. Tag the repo with the Matillion instance/image ID that was used for validation.
- Capture and store Matillion instance-level metadata (release version string, AMI/image ID, build timestamp) in a run manifest that travels with each deployment/run.

2) Pin the warehouse engine and drivers
- Where possible pin the warehouse engine version:
  - Redshift: choose and lock the cluster engine version and maintenance window; capture cluster version in the manifest.
  - Snowflake: you cannot pin Snowflake “version” (continuous delivery), so control behavior via session parameters, feature toggles, and by avoiding use of newly released features. Record the Snowflake account identifier and current feature settings at test time.
  - BigQuery: serverless, so you can’t pin an engine version — rely on stable SQL patterns and comprehensive tests.
- Pin JDBC/ODBC driver versions used by Matillion. Install and record explicit driver versions on the Matillion instance. Put driver installers into your IaC or bootstrap scripts.
- If your transforms depend on specific warehouse configuration (sorting, distribution keys, WLM settings, virtual warehouse size in Snowflake), treat these as configuration artifacts and apply them via IaC or DB migrations.

3) Pin SQL patterns and transformation code
- Keep all SQL (ad-hoc SQL components, SQL scripts, transformation queries) in Git — not just inside the Matillion UI. Export Matillion jobs (JSON) into the repo or store canonical SQL files referenced by Matillion.
- Create reusable, versioned SQL templates / stored procedures and reference them from Matillion components. Use Matillion component templates or shared jobs and version them in Git.
- Manage schema and object changes via a migration tool (Flyway, Liquibase, or SQL migration scripts) and include these scripts in the same repo. Apply migrations as part of CI/CD before running transformations.
- Parameterize environment-specific bits (schemas, credentials, temp tables) through Matillion Environment Variables; never hard-code environment-specific SQL in jobs. Version the variable definitions and include them in the project export.

4) CI/CD, deployment and run reproducibility
- Use Git-based deployment: Matillion’s built-in VCS or export/import combined with Git tagging. Tag the project commit you validated, and use that tag in deployment pipelines.
- Automate deployment of a known Matillion image + project commit + DB migrations via a pipeline (Terraform/CloudFormation for infra, then REST API or Matillion’s CLI to import project and run jobs).
- Include a run manifest produced by CI that contains: Matillion image ID & version, Matillion project commit hash & tag, warehouse engine ID/version (or account + active feature list), JDBC driver versions, migration script version, and seed data snapshot hash.
- Run automated data tests (row counts, checksums, key business validations) after deployment to guarantee transformations behave the same.

5) Test data and deterministic runs
- To prove reproducibility, use deterministic, versioned seed data sets (S3/gcs snapshots or fixtures) for unit/acceptance tests. Snapshot any upstream feeds used during validation.
- Capture execution metadata (job id, Matillion instance version, SQL executed, warehouse query ids) and store it alongside results so you can reproduce a failing run exactly.

6) Example manifest (what to record)
- matillion_image: ami-0123456789abcdef
- matillion_version: 1.57.3
- project_git: repo@commitsha
- jdbc_driver: snowflake-jdbc-3.12.8.jar
- warehouse: redshift-cluster-prod / engine_version 1.0.1243
- migrations: flyway v6 / migrations@tag
- seed_data: s3://bucket/seed/v2025-06-01.zip
- run_tests: passed|failed + checksum

7) Practical notes / gotchas
- For Snowflake/BigQuery you cannot truly freeze vendor server version — rely on strict SQL patterns, session parameters, and tests.
- Matillion components sometimes generate SQL automatically; ensure generated SQL is exported and reviewed. Prefer SQL components you control when precise reproducibility is required.
- Upgrading Matillion or drivers can change SQL generation and connector behavior — test upgrades in isolated staging with the same manifest before promoting.

Bottom line: combine pinned Matillion images, pinned drivers and warehouse configs where possible, version-controlled SQL/migrations, and automated CI/CD that records a manifest of the exact combination used. That combination gives you reproducible transformations and an auditable path to recreate any run.

[Top](#top)

## How do you manage long-running or heavy merges and minimize lock contention in the warehouse?
Short answer: avoid doing a single, huge in-place MERGE. Instead stage changes, reduce the MERGE’s scope, or swap an already-built table atomically — all orchestrated from Matillion — and use partitioning/clustering and warehouse scaling to shorten the time any DML holds locks.

Recommended patterns (Matillion-centric)

- Staging + targeted MERGE
  - Load raw data into a staging table using Matillion’s bulk load/COPY components.
  - Identify only the changed keys (CDC or timestamp/checksum) and MERGE only those rows: MERGE ... WHEN MATCHED/NOT MATCHED WHERE target.key IN (changed_keys). Keeps the merge small and short-lived.

- Batch the work (micro-batches)
  - Break the large change set into many smaller MERGE/UPDATE batches (e.g., by key ranges or time partitions) and run sequentially or in limited parallel. Smaller transactions reduce contention and likelihood of blocking.

- Build new table and atomic swap
  - Create a new target table (CTAS / CREATE OR REPLACE / CREATE TABLE AS SELECT) that contains the fully reconciled data, then atomically swap via rename or use CREATE OR REPLACE if supported.
  - This avoids long-running locks on the production table; Matillion can orchestrate the CTAS and the final rename/drop steps.
  - Caveats: swapping can lose GRANTS/constraints/statistics; preserve them explicitly if needed.

- Use partition/cluster aware updates
  - Use partitioned or clustered tables and limit DML to affected partitions. In BigQuery, update/replace single partitions; in Redshift use DISTKEY/SORTKEY to localize changes; in Snowflake design for micro-partition pruning.
  - In Matillion, orchestrate per-partition jobs (Run multiple transformation jobs for different partitions) to parallelize safely.

- Use CDC/warehouse-native streaming
  - For Snowflake: use Streams + Tasks to apply incremental changes asynchronously, avoiding big ad-hoc MERGEs.
  - For other warehouses, use change tables or incremental flags so Matillion jobs only apply deltas.

- Scale the warehouse temporarily
  - Increase compute size (Snowflake warehouse size, Redshift concurrency/cluster nodes, BigQuery slots) to shorten merge runtime and reduce lock duration. Matillion can trigger scaling before a heavy job and scale back after.

- Small transaction commits and locking behavior
  - Avoid huge single transactions. Commit periodically for large deletes/updates (if your warehouse supports it). Use staging deletes + inserts for small deltas rather than huge multi-million-row UPDATEs.
  - Use MERGE only where it’s efficient; sometimes DELETE+INSERT or CTAS is faster.

- Orchestrate concurrency from Matillion
  - Use orchestration jobs to sequence or throttle parallel merges, include Wait/Retry logic for transient lock waits, and run partitioned transformations in parallel when safe.
  - Use the Matillion “Execute Transformation/Orchestration” pattern to fan-out per-partition loads and fan-in a final swap.

Cloud-specific notes
- Snowflake
  - Preferred: stage loads, then MERGE only on changed rows, or CREATE OR REPLACE TABLE (atomic) for full rebuilds. Use Streams + Tasks for CDC. Scale warehouse to shorten DML.
- Redshift
  - Use staging + CTAS + swap to avoid long-running updates. Ensure good DISTKEY/SORTKEY design and run VACUUM/ANALYZE as maintenance.
- BigQuery
  - Use partition-replace or MERGE limited to partitions; copying/replacing partitions is effectively atomic. Minimize slot contention by partitioned jobs.
- Synapse/Dedicated SQL pool
  - Use partition switching (ALTER TABLE ... SWITCH) to swap partitions quickly, or CTAS + swap.

Operational & monitoring tips
- Identify changed rows with checksums/timestamps to minimize affected set.
- Profile query plans and execution time (Matillion job history + warehouse query history).
- Add retry/backoff logic for transient lock waits in Matillion orchestration.
- Test on a copy of the table to estimate run-time and resource needs before production runs.

Example patterns
- Incremental MERGE:
  1) Load staging (COPY).
  2) Compute changed_keys = SELECT key FROM staging JOIN target WHERE staging.hash <> target.hash.
  3) MERGE target USING staging ON target.key = staging.key AND target.key IN (changed_keys).

- CTAS + swap:
  1) CREATE TABLE target_new AS SELECT ... FROM target JOIN staging ...;
  2) GRANT/ANALYZE/restore metadata on target_new if needed.
  3) BEGIN TRANSACTION (if required); RENAME target TO target_old; RENAME target_new TO target; COMMIT; DROP target_old.

Use the right pattern depending on size of change, isolation/locking semantics of your warehouse, and whether you can accept temporary loss of things like grants/constraints during swaps.

[Top](#top)

## How do you handle partition swaps or zero-downtime publish patterns for serving tables?
High-level pattern: build the new dataset in a staging object, validate it, then atomically switch the pointer that serving/consuming queries use so there’s no (or minimal) downtime. In Matillion you implement this as an orchestration job that loads/validates the new table and then executes a targeted DB-level swap step (SQL Run/Script). Common approaches and implementation details:

1) Pointer swap via view replacement (recommended portable pattern)
- Pattern: Load new data into a staging table (schema.my_table_new). Do full validation and checksums. When ready, execute CREATE OR REPLACE VIEW prod.my_table_view AS SELECT * FROM schema.my_table_new.
- Why: CREATE OR REPLACE VIEW is an atomic metadata operation in most DWs, so consumers that query the view switch instantly to the new data. No need to touch underlying production table.
- Matillion specifics: Use an Orchestration job to run the SQL components: load job → validation SQL → Run SQL (CREATE OR REPLACE VIEW). Use Environment variables for target view/table names so you can swap names cleanly.

2) Table rename swap (fast metadata swap)
- Pattern: Load into a new physical table (my_table_new), then rename old → backup and new → production using metadata-only renames.
- Example sequence (metdata renames):
  - ALTER TABLE prod.my_table RENAME TO prod.my_table_bak;
  - ALTER TABLE prod.my_table_new RENAME TO prod.my_table;
  - DROP TABLE prod.my_table_bak (after verification)
- Caveats: DDLs are usually very fast, but not all systems support multi-statement transactional DDL. There can be a tiny window between renames; verify behavior for long-lived queries. GRANTS/OWNERSHIP might need reapplying.
- Matillion specifics: Run the rename steps in a single Orchestration job using Run SQL components. Use Try/Catch or If components to verify counts before doing renames, and a rollback rename path if verification fails.

3) Partition exchange / ALTER TABLE SWITCH (zero-copy partition-level publish)
- Pattern: Build new partition(s) in a staging table that matches production partitioning, then use a partition-exchange command to atomically move the partition into the serving table.
- Where available: SQL Server / Azure Synapse dedicated pools support ALTER TABLE ... SWITCH PARTITION; some MPP engines/Hive variants support EXCHANGE PARTITION semantics. This yields true atomic partition swaps with no row movement.
- Matillion specifics: Orchestration job does partition load → validation → Run SQL with the SWITCH/EXCHANGE statement. Ensure indexes/cluster keys and partitioning schemes are identical.

4) CREATE OR REPLACE TABLE / CTAS replace
- Pattern: CREATE OR REPLACE TABLE prod.my_table AS SELECT * FROM staging.my_table_new
- Pros/cons: Often atomic but may change grants, statistics, or table properties. Use when you can accept reapplying permissions or can script the reapplication in Matillion.
- Matillion specifics: Use Run Query component to execute CTAS; follow with GRANT/ANALYZE steps if needed.

Implementation checklist (Matillion-focused)
- Build a dedicated Orchestration job: Load → Transform (in DB as Transform components / SQL) → Validate (row counts, checksums, pk uniqueness) → Publish (Run SQL swap)
- Use Environment variables for tmp/prod names and timestamped staging names to allow retries and parallel runs.
- Use conditional logic (If component) to gate the swap on validation results.
- Capture pre/post row counts and checksums to enable automated rollback if mismatch.
- Reapply grants/indexes/statistics after swap if your method discards them (CREATE OR REPLACE/CTAS).
- Avoid long-running transactions around the swap. Prefer metadata-only rename/switch operations.
- Implement brief maintenance locking if necessary for downstream DDL changes; but prefer view or partition exchange to avoid locks.
- Smoke tests after swap: simple SELECTs, data freshness checks; implement in Matillion as SQL components with failure propagation.

Target-specific notes
- Snowflake: metadata renames and CREATE OR REPLACE VIEW are fast. CREATE OR REPLACE TABLE is atomic but will reset grants. Recommended: view swap or rename pattern and reapply grants if needed.
- Redshift: Renames are fast; Redshift doesn’t have a general partition-exchange, so view-swap or rename patterns are common. Be mindful of vacuum/analyze requirements.
- BigQuery: Best-practice is to use views to point to the current table, or use table-copy + table rename via the API. Table replacement semantics can affect ACLs—reapply IAM as needed.
- Azure Synapse / SQL Server: Use ALTER TABLE ... SWITCH PARTITION where supported for true zero-downtime partition moves. Otherwise use view or rename strategies.

Rollback and safety
- Always keep a short-lived backup name (prod_bak) during swap to allow immediate revert.
- Run validations before commit; if anything fails, abort swap and keep staging or drop it after manual inspection.
- Implement logging and alerts in Matillion for swap steps so failures trigger automated rollback and paging.

Summary
- Preferred portable approach: load into staging, validate, then atomically swap the pointer (CREATE OR REPLACE VIEW or metadata table rename) from an orchestration job in Matillion. Where supported and necessary, use partition-exchange for true zero-downtime at partition granularity. Ensure you script grants, statistics, smoke tests, and rollback steps in the Matillion workflow.

[Top](#top)

## How do you implement snapshotting strategies and slowly-changing snapshots for audit and reproducibility?
Goal: keep immutable, queryable point-in-time state and a reproducible audit trail while minimizing storage and load. Common patterns: full snapshots, append-only snapshot tables with batch IDs, and SCD Type 2 (slowly-changing dimensions) implemented with change detection (hashes) and MERGE/UPSERT. In Matillion you implement these inside orchestration and transformation jobs combined with audit metadata, object versioning (Git), and staged source artifacts.

Key design elements
- Snapshot identifier: batch_id or snapshot_ts (timestamp) to identify a run.
- Immutable rows: never update in-place for historical rows — insert new versions and mark previous rows closed.
- Change detection: use a deterministic row hash (MD5/SHA) of business columns to detect actual changes.
- Surrogate keys + business key: business_key identifies entity; surrogate_id is unique per version.
- Effective window columns: valid_from, valid_to (or valid_to = '9999-12-31' for open-ended) and is_current flag.
- Audit metadata: job_id/run_id, git_commit_id, source_file_path, source_checksum, row_count, duration, row_hash, schema_hash.
- Storage/retention: retain history in warehouse or offload full snapshots to S3/GCS for long-term reproducibility.

Implementation pattern in Matillion

1) Capture source artifacts and metadata (Orchestration job)
- Stage raw files (S3/GCS/Azure) or capture source table export into a staging schema/table.
- Compute and store source metadata: file path, size, checksum, row_count, extracted_at. Use Matillion components: S3/GCS Unload/Upload, "Run Command" or "Python Script" to compute checksums, or use DB queries on staged loads.
- Assign batch_id = job_run_id or timestamp parameter. Persist these into an audit table (etl_audit.source_files).

2) Produce a change hash per row (Transformation job)
- In a transformation SQL step, compute a hash over business columns:
  SELECT business_key, MD5(CONCAT(col1,'|',col2,'|',...)) as src_hash, ...
- Store this in a staged table along with batch_id, source metadata.

3) Apply SCD Type 2 via MERGE/UPSERT (Transformation job)
- Keep a history table with: surrogate_id, business_key, src_hash, valid_from, valid_to, is_current, batch_id, inserted_at, job_run_id, source_file.
- Use MERGE (Snowflake/Redshift/BigQuery equivalent) to:
  - Close prior current record when src_hash differs (set valid_to = batch_ts, is_current = false).
  - Insert new row for changed records with valid_from = batch_ts, valid_to = '9999-12-31', is_current = true.
  - Insert initial rows for new business keys.
- Example MERGE (SQL pseudocode):
  MERGE INTO dim_entity hist
  USING (SELECT business_key, src_hash, batch_id, batch_ts FROM stage_src) src
    ON hist.business_key = src.business_key AND hist.is_current = true
  WHEN MATCHED AND hist.src_hash <> src.src_hash THEN
    UPDATE SET hist.valid_to = src.batch_ts, hist.is_current = false
  WHEN NOT MATCHED THEN
    INSERT (surrogate_id, business_key, src_hash, valid_from, valid_to, is_current, batch_id, inserted_at)
    VALUES (GENERATE_UUID(), src.business_key, src.src_hash, src.batch_ts, '9999-12-31', true, src.batch_id, CURRENT_TIMESTAMP());

- For warehouses without MERGE, use staged updates in transactions: update old rows to close, then insert new rows.

4) Full point-in-time snapshots (table-per-run or partitioned snapshot)
- For auditing or reproducibility where you need the entire table state at a time, either:
  - Write an append-only snapshot table with batch_id and snapshot_ts containing the full state (small tables).
  - Or produce an exported extract: write staged CSV/Parquet to S3 with batch_id and checksum — maintain etl_audit.manifest entries for exact file set and schema version.
- Use Matillion components to unload to cloud storage (S3/GCS) with naming convention including batch_id and job_run_id.

5) Audit & reproducibility metadata (required)
Maintain these tables (or one combined):
- etl_audit.jobs: job_run_id, job_name, git_commit_id, start_ts, end_ts, status, parameters.
- etl_audit.sources: batch_id, file_path, file_checksum, row_count, extracted_at.
- etl_audit.row_counts: table_name, batch_id, before_count, after_count, inserted, updated, deleted.
- etl_audit.schema_versions: object, schema_hash, created_at, git_commit_id.

Populate via Matillion:
- Use built-in job/run metadata (Matillion exposes job run id and you can use variables).
- Push job_run_id, $JobId, or custom uuids into audit tables as the first step and update status at end.
- Include Git commit id via Matillion Git integration to tag job versions.

6) Reproducibility & restore
- To reconstruct table state as of T: query SCD2 history table where valid_from <= T and valid_to > T and is_current accordingly.
- To fully reproduce upstream data files: reference etl_audit.sources manifest and retrieve files from S3/GCS using stored checksums and file paths.
- To replay pipeline: use job_run parameters + git_commit_id and run Matillion jobs at that commit (Matillion supports repository branch/commit checkout).

7) Change-detection optimizations
- Use column-level hashes or full-row hash (MD5/SHA) to reduce comparison cost.
- Use warehouse-native features if available: Snowflake Streams + Tasks, BigQuery incremental partitions, or Redshift Change Data Capture approaches to capture deltas.
- Partition/hot tables for current-state queries and separate history tables for long-term retention.

8) Operational patterns in Matillion
- Orchestration job:
  - Step 1: create batch_id (UUID or timestamp).
  - Step 2: Stage raw data, compute file checksums, insert into etl_audit.sources.
  - Step 3: Trigger Transformation job with batch_id parameter.
  - Step 4: On completion, update etl_audit.jobs with status and metrics.
- Transformation job:
  - Step 1: build row-level hash and staging table.
  - Step 2: run MERGE/SCD2 logic.
  - Step 3: write snapshot files if needed and record artifact manifest.
  - Step 4: write detailed row_counts and validation results to etl_audit.row_counts.

9) Validation & data quality
- Add jobs to validate row counts, nullability, referential integrity, and to compare previous snapshot vs current snapshot (hash comparisons).
- Fail the orchestration if thresholds exceeded and record error details in audit.

10) Retention and compliance
- Retain SCD2 history per policy; archive older snapshots to object store and store manifest with checksums and schema version.
- Encrypt and protect manifests for compliance; use immutability features (S3 Object Lock) for strict reproducibility.

Quick example table DDL (concept)
- history_dim_entity (
    surrogate_id VARCHAR PRIMARY KEY,
    business_key VARCHAR,
    src_hash VARCHAR,
    valid_from TIMESTAMP,
    valid_to TIMESTAMP,
    is_current BOOLEAN,
    batch_id VARCHAR,
    job_run_id VARCHAR,
    source_file VARCHAR,
    inserted_at TIMESTAMP
  )

Audit entries captured each run
- job_run_id, batch_id, job_name, git_commit_id, start_ts, end_ts, status
- source_file, source_checksum, rows_extracted
- rows_inserted, rows_updated, rows_closed, rows_unchanged
- errors (if any), schema_hash

Notes on tradeoffs
- SCD2 keeps full history but increases storage and can slow queries; mitigate with current-state materialized view or partitioning.
- Full-table snapshot is simpler to reason about for reproducibility but expensive; prefer for small tables or when regulatory requirements demand complete file-level provenance.
- Hash-based change detection avoids noisy updates (ordering of columns) — ensure deterministic concatenation and null handling.

This approach gives auditability (who ran what, which files, file checksums), reproducibility (ability to reconstruct a table at batch_ts or re-run jobs at a specific git commit), and a robust slowly-changing snapshot (SCD2) that preserves history while keeping current-state fast to query.

[Top](#top)

## How do you coordinate Matillion with warehouse-native features like Snowflake Tasks, BigQuery Scheduled Queries, or Redshift MVs?
Short answer: pick one of three patterns — orchestrator-first (Matillion drives warehouse-native features), warehouse-first (Tasks/Scheduled Queries trigger Matillion), or event-driven/hybrid (lightweight in-warehouse SQL + messages to kick off Matillion). Implement with control tables or cloud messaging for decoupling; use Matillion’s API/REST, Execute SQL components, or cloud functions as the glue. Below are concrete approaches, examples, and operational best practices.

Patterns and tradeoffs
- Orchestrator‑first (Matillion schedules and calls warehouse features)
  - Matillion orchestrates everything: runs SQL to REFRESH materialized views, ALTER TASK to manage Snowflake Tasks, executes BigQuery jobs via API, etc.
  - Pros: single source of truth, centralized retries/logging/alerts, easier dependency handling across systems.
  - Cons: Matillion must be able to reach the warehouse control plane (network/permissions); some very data‑local features lose their latency advantage.

- Warehouse‑first (Tasks/Scheduled Queries trigger Matillion)
  - Keep time- or data-sensitive logic inside the warehouse and notify Matillion when downstream orchestration is needed.
  - Pros: in-warehouse operations can run with minimal orchestration overhead; lower latency to trigger immediate downstream work.
  - Cons: harder to manage cross-system dependencies and centralized error handling.

- Event‑driven/hybrid
  - Let the warehouse run in-warehouse transforms (e.g., incremental tables, MV refreshes) and push a message or write to a control table that Matillion consumes to continue downstream processing.
  - Pros: clear separation of responsibilities, resilient and scalable, fits cloud-native patterns.
  - Cons: extra components (Pub/Sub, SQS, Lambdas) and operational surface area.

Concrete integration options

Snowflake
- Orchestrator‑first:
  - Use Matillion’s Execute SQL components to run SQL that controls Tasks or refreshes objects (e.g., DDL to REFRESH MVs or to ALTER TASK <name> RESUME/SUSPEND).
  - Use Matillion’s Snowflake connection and rely on Streams/Tasks SQL as part of orchestration.
- Warehouse‑first:
  - Snowflake Tasks cannot make HTTP calls directly; implement an external function or Snowflake external API integration: Task writes a trigger row to a control table or a staging table that a small cloud function (scheduled poll or triggered by Snowflake job execution logs) reads and calls Matillion’s REST API to start a job.
  - Alternative: Task emits a message to an external service via Snowflake External Functions (API Gateway → Lambda) that calls Matillion’s job start endpoint.
- Typical flow (warehouse-first): Snowflake Task completes → INSERT into control table OR call external function → API Gateway/Lambda forwards to Matillion API with job name/params.

BigQuery
- Orchestrator‑first:
  - Matillion can call BigQuery jobs via Google APIs (use Matillion Python/Script components or the GCP connectors) to trigger on‑demand queries or load jobs; use Execute SQL to run query jobs if Matillion has GCP permissions.
- Warehouse‑first:
  - BigQuery Scheduled Queries finish and write to a table; use Cloud Logging export for job completion to trigger a Cloud Function that calls Matillion’s REST API; or have the scheduled query write a “done” row to a control table that Matillion polls.
  - You can also export BigQuery job logs to Pub/Sub via Cloud Logging and use that event to trigger Matillion downstream work.
- Typical flow: BigQuery Scheduled Query completes → Cloud Logging / destination table / Pub/Sub event → Cloud Function → Matillion start job.

Redshift (including Materialized Views)
- Orchestrator‑first:
  - Matillion’s Redshift connection runs REFRESH MATERIALIZED VIEW or other SQL as part of orchestration (Execute SQL component). Use Matillion orchestration to ensure ordering, retries, and downstream tasks.
- Warehouse‑first:
  - Redshift lacks direct outbound HTTP calls. Common pattern: after in-cluster work completes, write a trigger row to a control table that Matillion polls, or use UNLOAD to S3 and S3 event → Lambda → Matillion API.
- Typical flow: Matillion calls REFRESH MATERIALIZED VIEW inside a job; for Redshift-driven triggers, use S3/Lambda or control table polling.

Implementation details and best practices
- Decouple via control table or messaging
  - Use a lightweight control table or Pub/Sub/SQS message to represent “ready” events; Matillion can poll or subscribe. This avoids fragile direct triggers and provides an audit trail.
- Use Matillion REST API for starting jobs
  - Start jobs with job name and parameters, track run_id for status polling. Authenticate via API tokens and lock them in secrets manager.
- Idempotency and deduplication
  - Make triggers idempotent (unique run IDs, dedupe on control table) so retries or duplicate events don’t re-run heavy jobs.
- Network & security
  - Ensure Matillion can reach warehouses (private endpoints, VPC peering, IP allowlists) and that cloud functions used to bridge have least privilege to call Matillion API and the warehouse.
- Observability and SLAs
  - Centralize logs into your monitoring/alerting stack. Emit run metadata from both Matillion and warehouse tasks to correlate runs.
- Error handling & retries
  - Prefer central retry policies in Matillion for downstream orchestrations; for warehouse-first triggers, make sure the bridge (Lambda/Cloud Function) can retry and report failures back into the control table/alerting.
- Cost and resource management
  - Be mindful of compute costs for frequent full refreshes. Use in-warehouse features (MV, partition pruning, clustering) for data locality and Matillion for orchestration and cross-system joins or movement.
- Governance and ownership
  - Define clear ownership: which team maintains in-warehouse logic vs Matillion flows. Keep naming conventions to map Tasks/MVs to Matillion jobs.
- Testing and deployment
  - Test both the SQL side and the orchestration triggers. Validate permission boundaries and run integration tests in lower environments.

When to choose which model
- Use Matillion as the single orchestrator when workflows span multiple systems (cloud storage, APIs, multiple warehouses) or need centralized retries and monitoring.
- Use warehouse-native scheduling/Tasks when work is pure in-warehouse SQL and low latency is critical; still emit a trigger/event for downstream Matillion steps.
- Use event-driven hybrid when you want durability and loose coupling: warehouse updates → message/control table → Matillion continues.

Example short flows
- Snowflake Task triggers Matillion:
  - Snowflake Task writes to control_table (schema: event_id, status, payload).
  - AWS Lambda polls or query change (e.g., Task writes row and Lambda reads via Snowflake connector) → Lambda calls Matillion REST /v1/jobs/run with payload.
- Matillion triggers BigQuery job:
  - Matillion uses a Python component with Google client libs to call bigquery.jobs.insert, waits for completion, then runs downstream transform jobs.

Summary
- Architect around one coordination pattern per workflow: orchestrator-first for cross-system complexity, warehouse-first for pure in-warehouse work, or hybrid for scalable decoupling.
- Implement triggers through control tables or cloud messaging, glue with cloud functions or Matillion’s SQL/REST capability, and enforce idempotency, security, observability, and clear ownership.

[Top](#top)

## How do you expose pipeline health and data freshness to product/BI teams in a self-serve dashboard?
Short answer: build a small, canonical monitoring dataset (job runs + dataset freshness rows) inside your warehouse, populate it from Matillion (job-level instrumentation + periodic API pulls), then surface that dataset with parameterized dashboards and drill-through links so product/BI teams can self-serve. Below are practical patterns, metrics, implementation steps, sample schemas/SQL, visualization ideas and operational notes tailored to Matillion.

What teams care about (metrics to expose)
- Pipeline health (per job / per pipeline)
  - Latest status (SUCCESS/FAIL/RUNNING)
  - SLA state (on-time / late / missed)
  - Run start/end times and duration
  - Recent failure rate (last 7 / 30 days)
  - Error message / failure link / run_id for drill-down
- Data freshness (per table / dataset / BI model)
  - Last_load_time (when table was last written)
  - Source_max_event_time (last event timestamp ingested)
  - Freshness lag = last_load_time - source_max_event_time or now() - source_max_event_time
  - Row counts, row-count delta, % change vs expected
  - Basic data-quality signals: null% on key columns, cardinality changes, checksum/row-hash mismatches
- Observability/trend metrics
  - Run duration trends, count of retries, SLA heatmap by pipeline
  - Anomalies: huge row-count drops or spikes, schema changes detected

How to capture the data (Matillion patterns)
- Instrument jobs directly
  - Add a small “monitoring” sub-job or components at start/end of each orchestration/transformation job that writes a row to a monitoring table with job_name, run_id, start_time, end_time, status, duration, rows_written, error_text, git_commit, env, run_url, owner, runbook_link.
  - Use job/flow variables to capture counts and metadata; use Table Output or SQL components to insert/merge into the monitoring table.
- Centralized monitoring job
  - Have jobs call a centralized orchestration job (monitor_start, monitor_end) to centralize logic and keep instrumentation consistent.
- Pull Matillion metadata via API
  - Use Matillion REST API to fetch job run history and logs on a schedule and write them into the warehouse. Good for backfilling and independent verification.
- Capture dataset freshness from targets
  - At the end of each transformation, run a SQL query that computes max(event_time), row_count, checksum and upserts into a dataset_freshness table.
  - Alternatively run a periodic freshness job that queries each target table for max(event_time), last_modified, row_count and writes results.
- Optional: integrate external observability tools
  - If using Monte Carlo/Bigeye/Great Expectations, either forward Matillion logs to them or mirror their outputs into the same monitoring schema.

Recommended monitoring table schemas (examples)
- job_runs (one row per job run)
  - job_name, job_id, run_id, environment, start_time, end_time, status, duration_seconds, rows_processed, error_message, git_commit, executed_by, run_url, runbook_link
- dataset_freshness (one row per dataset per run)
  - dataset_name, schema, table_name, load_time, source_max_event_time, freshness_seconds, row_count, checksum, job_run_id, environment

Sample DDL (concise)
- job_runs: job_name varchar, run_id varchar primary key, start_time timestamp, end_time timestamp, status varchar, duration_seconds int, rows_processed bigint, error_message varchar, run_url varchar
- dataset_freshness: dataset_name varchar, table_name varchar, load_time timestamp, source_max_event_time timestamp, freshness_seconds int, row_count bigint, job_run_id varchar

Example SQL for freshness metric
- freshness_seconds = EXTRACT(epoch FROM (load_time - source_max_event_time))
- Latest freshness per table:
  SELECT dataset_name, table_name, MAX(load_time) AS last_load_time,
         MAX(source_max_event_time) AS source_max_event_time,
         EXTRACT(epoch FROM (MAX(load_time) - MAX(source_max_event_time))) AS freshness_seconds
  FROM dataset_freshness
  GROUP BY dataset_name, table_name;

Operational patterns and SLAs
- Define SLAs per dataset (e.g., batch tables must be < 1 hour; nearline < 5 minutes). Compute SLA_state = CASE WHEN freshness_seconds <= SLA_threshold THEN 'OK' WHEN <= 2*SLA_threshold THEN 'WARN' ELSE 'BREACH' END.
- Use retention and aggregates: keep raw job run history for N days and aggregate into daily summaries for long-term trending.
- Store runbook_link and escalation owner in job metadata so dashboards show the exact runbook when a job fails.

Dashboard design for self-serve teams
- Overview page (team-level)
  - SLA heatmap by dataset/pipeline (green/yellow/red)
  - List of recent failures with run_id and one-click links to Matillion and runbook
  - Top stale datasets, sorted by freshness lag
- Dataset detail page
  - Freshness over time (last 7/30 days)
  - Recent row-count trend and % change
  - Last successful run details and link to job run logs
  - DQ checks for key columns (null%, cardinality)
- Job-run debugging page
  - Recent runs, durations, error messages, execution environment, commit hash
  - Link from run_id to Matillion UI or stored logs
- Parameterization and self-serve
  - Filters for team, environment, dataset, SLA severity, time window
  - Saved views for product/BI teams showing only their datasets
  - Expose underlying monitoring tables or SQL query examples so analysts can build additional cards

Automation and alerting
- Primary alerts: configure Matillion notifications (Slack/email/PagerDuty) for immediate failures; also fire aggregated alerts from warehouse SQL (e.g., if key dataset freshness breaches SLA).
- Secondary alerts: BI tool alerts or scheduled queries that check the monitoring table and notify downstream owners.
- On-call playbooks: include runbook links, common fixes, and rollback steps in monitoring metadata.

Security, governance and self-serve controls
- Use column/table-level permissions in the warehouse to allow teams to read monitoring data but restrict write access to the monitoring ingestion job.
- Tag datasets with owner, team, and priority to power team-specific screens.
- Maintain a registry (simple table) that maps BI datasets/models to physical tables/views so freshness in dashboard maps to actual models.

Implementation checklist (step-by-step)
1. Create monitoring schema/tables in your warehouse.
2. Build a small reusable Matillion orchestration sub-job to upsert a job_run row at job start (start_time, status=RUNNING).
3. At job end (success/fail), call the same sub-job to update end_time, status, duration, rows_processed, error_message and run_url.
4. For each output table, add a small SQL step to compute max(event_time), row_count, checksum and upsert into dataset_freshness with job_run_id.
5. Schedule a separate Matillion job that calls the Matillion REST API nightly/continuous to pull job_run metadata for cross-checks and backfill.
6. Build dashboard templates (Looker/LookML, Tableau workbook, Power BI or Metabase) and ship one canonical dashboard per team with filters.
7. Add alerts (Matillion notifications + warehouse-driven alerts) and link runbook/owner metadata.
8. Iterate: add additional DQ checks or integrate a third-party observability product if you need advanced anomaly detection.

Notes, trade-offs and tips
- Instrumentation vs. API polling: instrumenting jobs gives real-time, rich context (rows_processed, event timestamps) but requires changing jobs. API polling is non-invasive but may lack row-level metrics.
- Keep monitoring writes small and idempotent (use upserts keyed by run_id).
- Include run_url/guid so BI users can directly open the Matillion run for debugging.
- Start with a minimal set of metrics (status, last_load_time, freshness) and expand to DQ checks as teams adopt the dashboard.

Quick example: minimal flow for a transformation job
- At job start: call monitor_upsert(run_id, job_name, start_time, status='RUNNING')
- Main work: run transformation SQL -> capture rows_written and max(event_time) into variables
- At job end: call monitor_upsert(run_id, job_name, end_time, status='SUCCESS', rows_written, source_max_event_time)
- Dashboard computes freshness from the dataset_freshness table and flags SLA breaches.

That's the pattern: consistent instrumentation, canonical monitoring tables inside the warehouse, parameterized dashboards with drill-through links, and automated alerts/runbooks so product/BI teams can self-serve visibility and act on issues.

[Top](#top)

## How do you archive unused jobs/artifacts and clean up obsolete variables, connections, and tables?
High-level approach: export/archive artifacts so they can be restored, then identify unused items by searching the project (or exported JSON) and remove them with controlled steps (rename/disable → delete). Automate cleanup where possible and maintain audit/retention rules.

1) Archiving jobs/artifacts
- Export the project or individual jobs:
  - Use Project → Export Project to get a JSON file containing everything.
  - Use job right‑click → Export Job (JSON) to export single jobs.
  - Use Git integration (GitHub/Bitbucket/GitLab): commit an “archive” branch/folder or tag. Git is the recommended long‑term archive because it preserves history and diffs.
- Alternative archive strategies:
  - Create a separate Matillion project called “Archive” and import archived jobs there (Import Project).
  - Export JSONs to an object store (S3, Blob) with date and version metadata.
- Best practice: before deleting, move to an “archive” folder/branch, or export JSON + note dependency/context in a README.

2) Identifying unused variables
- Manual quick checks:
  - Use the UI Project → Manage Variables to list variables.
  - Use Project → Find (or global search) to search for ${VariableName} usage across the project.
- Scripted/robust approach:
  - Export the project JSON and scan for variable references. Example shell commands:
    - List referenced variables: grep -oP '\$\{\K[^}]+' exported_project.json | sort -u
    - Compare to the declared variable list in the JSON to find unused ones.
  - Or use a small Python script: load the JSON, extract declared variables, search all job JSON strings for occurrences of each name, flag zero-occurrence names.
- Safe removal flow:
  - Rename variable (e.g., add _DEPRECATE) or set to a sentinel value.
  - Run dependent jobs in a test environment or run a project search for occurrences again.
  - Remove from Project → Manage Variables once confirmed unused.

3) Identifying and cleaning connections
- Discovery:
  - Project → Manage Connections shows all connections.
  - Search exported project JSON for the connection name or connectionId to find usage: grep -i "connectionName" exported_project.json or search UI.
- Safe removal flow:
  - Repoint suspicious connections to a “dummy”/read‑only test connection or rename to CONNECTION_NAME_DEPRECATED.
  - Validate no jobs fail in a dev/test environment.
  - Delete from Project → Manage Connections.
- Backup: export/record connection definitions and credentials securely before deleting. Use secrets manager or an encrypted store for credentials.

4) Cleaning up obsolete tables (staging/tmp)
- Identify candidate tables:
  - Use naming conventions/prefixes for staging/temp tables (e.g., tmp_, stg_, jobname__tmp) and query your warehouse’s information_schema or catalog to find old ones.
  - Example Snowflake: 
    SELECT table_schema, table_name, created, last_altered
    FROM information_schema.tables
    WHERE table_name ILIKE 'tmp_%' AND created < DATEADD(day, -30, CURRENT_DATE());
  - Example BigQuery:
    SELECT table_catalog, table_schema, table_name, TIMESTAMP_MILLIS(creation_time) AS created
    FROM `project.dataset.INFORMATION_SCHEMA.TABLES`
    WHERE table_name LIKE 'tmp_%' AND TIMESTAMP_MILLIS(creation_time) < TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 30 DAY);
- Deletion flow:
  - Move older tables to an archive schema/database when you need retention (CREATE TABLE archive.schema.table AS SELECT * FROM staging.table).
  - Or drop via scheduled Matillion job using an Execute SQL component with parameterized DROP TABLE statements.
  - Always run SELECT COUNT(*) and/or REVIEW data before DROP, and log drops to an audit table.
- Automate cleanup:
  - Build a Matillion orchestration job that (1) queries the warehouse for candidate tables, (2) optionally moves/archive, (3) drops them, and (4) writes an audit row to a cleanup_log table.
  - Schedule the job with approvals if destructive.

5) Practical automation scripts/examples
- Find referenced variables (shell):
  - exported_project.json is the Export Project file.
  - Referenced list: grep -oP '\$\{\K[^}]+' exported_project.json | sort -u
  - Declared list (Python or parse JSON) → diff declared vs referenced.
- Python sketch to detect unused variables:
  - Load exported_project.json, get declared vars: project["variables"]
  - Dump full JSON as a string and for each var check if var in json_string (or use regex for ${var}).
  - Output unused variable names for review.

6) Deletion safety and governance
- Always backup (export project, export job JSON, backup connection details) before destructive changes.
- Implement soft‑delete: rename/disable first, then delete after a retention/validation window.
- Keep a change log or audit table of deletions (what was removed, by whom, when).
- Use environment separation: perform deletes in dev/test first, then promote to prod cleanup once validated.

Summary checklist
- Export project/job or commit to Git for archive.
- Search project (UI or exported JSON) to find usage of variables and connections.
- Rename/disable, test, then delete unused variables/connections via UI.
- Identify stale tables via warehouse metadata queries, archive or drop with an automated Matillion job that logs actions.
- Maintain backups, audit logging, naming conventions and a retention policy.

[Top](#top)

## How do you prevent accidental runs in production during testing by using run permissions and safe defaults?
Short answer: isolate and lock down the Production environment’s Run permission, make non‑prod the default, and add a programmatic guard in jobs that refuses to proceed unless an explicit production-run flag or privileged role is present.

How to implement (concrete, interview-style steps):

1) Restrict Run permission on the Production environment
- Use roles to control environment-level Run access: Admin → Manage Roles (or Manage Users/Roles). Create a “prod‑runner” role that has Run permission on the Production environment. Remove Run permission for all other roles on that environment (leave them View only).
- Assign only trusted users or an automation/service account to the prod‑runner role.
- Result: users can view jobs in prod but cannot start them.

2) Lock job/folder level execution where needed
- Use folder/job permissions to further restrict who can execute specific production orchestration jobs. Set Edit/View/Run at folder or job level so only intended users can run them.
- Combine with role restrictions for defense in depth.

3) Make safe defaults in the project and environments
- Default environment: set your project’s default environment to a non‑prod (Dev or Test) environment so interactive runs default to non‑prod.
- Keep production credentials and connections only defined inside the Production environment. Users without access to that environment cannot run jobs end‑to‑end against prod systems.

4) Add a guard at the top of production jobs (programmatic safety)
- Create an environment or project variable like ENV_NAME (DEV/QA/PROD) and a confirmation flag CONFIRM_PROD_RUN (default = false).
- At the top of any orchestration that can touch prod, add an If / Switch that checks:
  - If ENV_NAME == 'PROD' AND CONFIRM_PROD_RUN != 'true' → Stop or raise Failure
  - Else → continue.
- This forces an explicit deliberate action (set CONFIRM_PROD_RUN=true) or prevents accidental runs started from the wrong environment/UI.

5) Operational controls & process
- Use separate Matillion instances for prod & non‑prod when possible (strong isolation + separate credentials).
- Require deployments to production via a promotion pipeline (git branch protection / CI) and limit who can merge/promote to the prod branch.
- Schedule production jobs rather than allowing ad‑hoc runs; restrict who can create/trigger schedules.

6) Harden automation and API access
- Use service accounts with limited privileges for scheduled/automated prod runs; do not reuse developer accounts.
- Restrict API tokens and SSH/instance access for non‑production users.

Quick checklist (apply across UI and processes)
- [ ] Remove Run permission on Production environment for general roles.
- [ ] Create dedicated prod‑runner role and assign minimal trusted users.
- [ ] Default project environment = Dev/Test.
- [ ] Store prod credentials only in Production environment.
- [ ] Add top‑level guard that aborts unless explicit CONFIRM_PROD_RUN set.
- [ ] Use promotion pipelines or separate instances for production.

These steps combine Matillion permission controls with safe default configuration and an in‑job safety net to prevent accidental production runs.

[Top](#top)

## How do you manage API quotas and backoffs for high-volume third-party connectors without breaching SLAs?
Short answer: treat the connector as a first-class rate‑limited client — centralize throttling and quota tracking, use batching/incremental loads and exponential backoffs with jitter, enforce concurrency limits from Matillion orchestration, surface real‑time metrics/alerts, and design SLA-aware fallbacks so essential SLAs never wait on batch retries.

How I implement that in a Matillion environment

1. Centralized quota management
- Don’t let every orchestration/transform job independently hammer the API. Use a central “throttle manager” pattern (an orchestration job or lightweight service) that meters tokens for callers.
- Implement token-bucket or leaky-bucket logic (can be in Redis, a small database table, or a cloud function) that releases request tokens at the provider’s allowed rate. Worker jobs request a token before making a call.

2. Concurrency controls inside Matillion
- Control parallelism by limiting number of concurrent child jobs and threads in orchestration. Use variables and job dependencies to serialize or pace calls.
- Use orchestration patterns: fan-out with small, controlled fan-in; queue worker jobs rather than firing unlimited parallel components.

3. Backoff and retry strategy
- Use exponential backoff with randomized jitter to avoid thundering herd on retries.
- Respect provider headers (Retry-After, X-RateLimit-*) and error codes (429, 503). Make your retry policy adaptive: shorter retries for transient errors, stop/alert for sustained quota exhaustion.
- Cap total retry time so retries don’t violate SLAs — after X retries fall back to a degraded path.

4. Batching, pagination & incremental loads
- Batch requests where the API supports it. Reduce frequency by increasing page size within provider limits.
- Shift to incremental/pinpointed pulls (changed-since, delta tokens) rather than full reloads.
- Use caching/conditional GETs (ETag/If-Modified-Since) to avoid unnecessary calls.

5. SLA-aware prioritization and graceful degradation
- Classify load into SLA tiers. Always prioritize high‑SLA data pipelines and throttle low-priority loads during quota pressure.
- Provide a degraded mode: return last-known-good data to downstream consumers if live fetches are blocked.

6. Circuit breaker & failure containment
- Implement a circuit-breaker: if repeated failures/429s occur, open the circuit to stop calls, alert operators, and retry with backoff. Prevents exhausting retries and violating SLA windows.
- Make API calls idempotent or checkpoint progress so retries are safe.

7. Observability and automated reaction
- Emit metrics for request rate, errors, quota usage, retry count, and latency to CloudWatch/Datadog/Prometheus.
- Alert on quota exhaustion and rising 429/5xx rates. Automate scaled responses: slow down workers, pause low-priority jobs, or spin up alternate ingestion paths.
- Use Matillion job history and logs to trace failing runs and backoff behavior.

8. Operational patterns and scaling
- If provider allows multiple API keys/app clients, distribute load across keys while respecting per‑key quotas and terms of service.
- Offload high-frequency ingestion to a streaming layer (Pub/Sub, Kinesis) that then applies controlled outbound calls from managed workers.
- Load-test against expected peak patterns and run chaos scenarios (simulate 429s/Retry-After) to validate SLA behavior.

Example implementation sketch
- Orchestration job A receives work items and pushes them to a queue (or table).
- Throttle service (Redis token bucket) controls global rate R. Worker jobs poll the queue and request a token before calling the third-party API.
- Worker performs calls with exponential backoff + jitter; honors Retry-After headers; updates a checkpoint on success.
- Priority queueing ensures SLA-critical items are dequeued first. Monitoring dashboards and alerts trigger auto-reduce of non‑essential jobs when error rates rise.

Checklist to avoid SLA breaches
- Centralize throttling and track consumption in real time.
- Enforce concurrency limits in Matillion orchestration.
- Use exponential backoff with jitter and honor provider headers.
- Prefer incremental/conditional requests and batching.
- Prioritize SLA-critical flows and have graceful-degradation pathways.
- Monitor quotas and automate reactions (pause/lower concurrency) when limits near.

This combination keeps throughput high under normal conditions, protects against bursts and 429 storms, and ensures SLAs aren’t violated during outages or quota exhaustion.

[Top](#top)

## How do you safely process personally identifiable data and prove minimization and masking across the pipeline?
High-level approach: enforce minimization up front, isolate and stage raw PII only where strictly necessary, pseudonymize/mask/encrypt immediately, enforce least privilege, and build automated validations + auditable evidence at every pipeline stage.

Concrete Matillion pipeline pattern
1) Ingest (isolate)
   - Use Matillion extract components (S3/GCS/Azure Blob connectors, API/DB connectors) to land raw files into a tightly controlled staging area (separate bucket/container and staging schema).
   - Restrict network and IAM so only the Matillion runtime and required service accounts can access this staging area.

2) Immediately pseudonymize/mask/encrypt in the staging job
   - Prefer in-warehouse transformations (SQL components) so raw values never leave the warehouse engine.
   - Use a SQL Script or Transformation job to:
     - Replace cleartext PII with reversible tokens (FPE or envelope encryption) only if re-identification is allowed and audited.
     - Otherwise apply irreversible pseudonymization: HMAC_SHA256(secret, value) or SHA-256 with salt for linkage without revealing PII.
     - Apply masking for display fields: CONCAT(REPEAT('*', LENGTH(col)-n), RIGHT(col,n)) or regex-based redact.
   - Example (generic SQL pseudocode):
     - SELECT HASH_SHA256(CONCAT(email, :salt)) AS email_hash,
              CONCAT(SUBSTR(name,1,1), REPEAT('*', LENGTH(name)-1)) AS name_mask
       FROM stage_table;
   - If you need stronger controls, call a Python Script component to use a KMS-backed FPE library or call an external tokenization service.

3) Load into protected schema and remove raw
   - Load masked/pseudonymized records into production tables that have column-level metadata (tagged as PII masked).
   - Immediately DROP/DELETE the raw staging table and purge staging files (use lifecycle rules and explicit delete).
   - Ensure S3/GCS/Azure buckets use encryption at rest and server-side encryption keys are managed via KMS.

4) Apply warehouse-native controls
   - Enforce column-level security, row-level security, dynamic data masking (if supported) in the target DW (Snowflake, BigQuery, Redshift).
   - Use separate roles/users for analysts vs. privileged re-identification roles.

Key management and secrets
- Never embed keys in job code. Use Matillion secure variables and integrate with cloud Key Management Services (AWS KMS, Google KMS, Azure Key Vault) or Secrets Manager.
- Use envelope encryption: data encrypted with data key; data key encrypted with KMS master key.
- Rotate keys per policy and record key usage from KMS logs for audits.

Proof, validation and evidence
- Automated assertions in the job:
  - Add validation components (SQL or Python) that scan for unmasked PII patterns (email regex, SSN pattern) and fail the job if any found.
  - Record counts: rows processed, rows masked, rows failed.
- Audit trail and provenance:
  - Enable Matillion job run logs and push logs to an immutable store (S3/Cloud Storage/CloudWatch) with retention policy.
  - Commit job definitions to Git (Matillion Git integration) — Git commit ID + environment gives code provenance.
  - Store run metadata: job id, timestamp, component outputs, salt/key version, and a hash (e.g., HMAC) of the job definition in an audit table.
- Lineage and catalog:
  - Export or push lineage metadata (source -> staging -> masked table) into your data catalog (Alation/Collibra/Glue). Tag columns as PII/masked.
- Evidence artifacts to produce for auditors:
  - Job run logs showing staging -> mask -> load -> drop actions.
  - Validation reports showing zero unmasked values and row counts.
  - KMS key usage logs proving who/when keys were used for re-identification or encryption.
  - Git commits and job configuration showing masking logic and secure variables referenced (not the keys).
  - Data catalog entries and IAM policies showing access controls.

Re-identification controls
- Implement a strict, auditable re-id process:
  - Store reversible tokens only if necessary; keep keys in KMS; require a separate, privileged Matillion environment/job or a secure microservice to perform re-id.
  - Log every re-id attempt (who, why, when) and require managerial approval via an automated workflow.

Environment & lifecycle controls
- No production PII in dev/test: use masked or synthetic datasets for lower environments.
- Use separate Matillion environments for dev/test/prod and limit credentials/permissions.
- Implement retention and deletion policies; automate purging of raw and intermediate artifacts.

Tests and CI/CD
- Integrate automated tests into CI:
  - Unit tests to verify masking functions.
  - End-to-end test runs that assert no PII in downstream dev/test environments.
  - Pre-deploy checks that verify secure variables and KMS references are configured.

Example minimal checks you should implement in Matillion jobs
- After masking step run:
  - SELECT COUNT(*) FROM prod_table WHERE email LIKE '%@%' OR ssn_regex_match(ssn) > 0; — must be 0.
  - SELECT COUNT(*) FROM prod_table WHERE email_hash IS NULL; — expected result vs baseline.
- Save these check outputs to an audit table with job_run_id and commit_id.

Operational controls
- Enforce least privilege for Matillion users and service roles.
- Use VPC, private endpoints, and network controls so data paths are restricted.
- Enable TLS for data in transit and at-rest encryption.
- Monitor for anomalies — integrate with SIEM and alerting.

Quick summary for auditors
- Policy: ingest-only-in-staging, immediate pseudonymize/mask, purge raw.
- Controls: KMS for keys, secure variables, role-based access, environment separation.
- Proof: Matillion job logs + Git commits + validation reports + KMS logs + data catalog lineage + audit table entries showing zero unmasked PII and key usage records.

[Top](#top)

## How do you design for tenant isolation so that one tenant’s pipelines cannot read or impact another’s data?
High-level approach: force isolation at the data-plane and control-plane boundaries Matillion uses. Matillion itself is just the runner that issues queries and moves data, so the essential rule is: give each tenant only the credentials, network access, and workspace they need — and prefer physical separation where regulatory risk is high.

Recommended architectures (trade-offs)
- Strong (per-tenant instance)
  - One Matillion instance (VM/container) per tenant, deployed in separate VPC/accounts.
  - Warehouse/storage credentials per tenant, separate cloud accounts or databases/schemas.
  - Pros: near-complete isolation, easiest to reason about security/regulatory compliance.
  - Cons: higher cost and operational overhead.
- Moderate (single instance, per-tenant project + environments)
  - Single Matillion instance, create one Project per tenant; within each project create tenant-specific Environments and Credentials.
  - Lock project membership and restrict ability to export/import projects.
  - Enforce warehouse-level separation (each tenant has its own DB/schema or least-privilege role).
  - Pros: balanced cost and isolation; typical enterprise approach.
  - Cons: still shared control plane; needs strict permissions and governance.
- Lightweight (single project, row-level security)
  - One project handling multiple tenants, rely on target-warehouse RLS/column masking and source access controls.
  - Pros: low cost and simple orchestration.
  - Cons: high risk — a mistake in jobs/components can leak data; not recommended for sensitive data.

Concrete Matillion controls and patterns
- Projects and Environments
  - Use one Project per tenant (preferred) or at least dedicated Environments per tenant.
  - Only grant project membership to that tenant’s users and operations staff.
  - Disable or tightly control project export/import and Git access to prevent copying credentials into other projects.
- Credentials and Secrets
  - Create separate Credentials for each tenant (data warehouse, cloud storage, third-party systems).
  - Mark credentials as secure and limit which roles/users can view or modify them.
  - Never hard-code tenant secrets in components; use Environment Variables or Matillion Credentials.
  - Where possible, prefer short-lived tokens or assume-role patterns instead of long-lived keys.
- Least-privilege access in the data stores
  - The Matillion jobs execute using the configured credentials — ensure those credentials are limited to tenant-specific schemas/tables or an appropriately scoped role.
  - Use separate databases/schemas per tenant or separate cloud accounts/projects when feasible.
  - Enforce row-level security, column masking, and grants at the warehouse level if multi-tenant objects are unavoidable.
- Cloud/Network isolation
  - Run Matillion in private subnets, use security groups and VPC firewall rules so Matillion can only reach tenant-specific endpoints.
  - For cross-account access to storage (S3/GCS), use per-tenant buckets and bucket policies or cross-account roles with External IDs.
  - Consider PrivateLink / VPC endpoints and no public internet exposure.
- Identity and Access Management
  - Use SSO (SAML/OIDC) and role-based access in Matillion; map users to least-privileged roles.
  - Limit who can create/modify Environments, Credentials, and Admin settings.
  - Use separate service accounts for orchestration vs interactive users.
- Operational hardening
  - Audit logging: enable Matillion logs + cloud provider logs + warehouse query logs; centralize logs for monitoring.
  - Audit who exports or downloads Projects, and restrict that capability.
  - Use Git repositories per tenant or per-project branches with protected settings.
  - Lock down API tokens; issue per-tenant tokens with limited scope.
- Data in transit / at rest protection
  - Ensure TLS for all connections and use customer-managed keys (CMKs) per tenant where required.
  - Enforce encryption-at-rest on storage/warehouse and per-tenant keying if compliance demands.
- Runtime safeguards and guardrails
  - Prevent cross-tenant object references in components via code review and CI checks.
  - Use parameterized, tenant-scoped Environment Variables; do not use global shared variables for tenant specifics.
  - Implement automated tests that run on a staging copy of each tenant's environment to catch misconfigurations.
- Backup and disaster separation
  - Store backups per tenant or tag them clearly; ensure restore procedures do not mix tenants.
- Monitoring and detection
  - Alert on unusual cross-tenant queries or access patterns in warehouse logs.
  - Periodically run automated checks to validate that credentials used by Matillion jobs cannot access other tenants’ schemas/tables.

Practical deployment checklist
1. Decide isolation level (per-tenant instance vs per-tenant project vs RLS).
2. For chosen model, create per-tenant credentials and environments in Matillion.
3. Apply IAM least-privilege roles and SSO mapping; disable project export for non-admins.
4. Configure warehouse schemas/roles so each credential only reaches its tenant’s data.
5. Lock down network pathways (VPC, endpoints, bucket policies).
6. Enable logging/auditing (Matillion + cloud + warehouse) and create alerts for cross-tenant access attempts.
7. Perform penetration tests and cross-tenant access validation before go-live.

Primary risk to emphasize: Matillion itself does not enforce data-layer isolation beyond credentials/permissions you give it. The ultimate isolation is enforced in the data stores and network. Choose instance-level separation when you cannot fully rely on correct credential scoping or when compliance requires physical separation.

[Top](#top)

## How do you compare Matillion to building ingestion with Airflow + dbt + custom code for your organization’s skill set and roadmap?
Short answer
- Use Matillion when you want fast, low-maintenance ELT/ingest with a GUI, your team is heavier on SQL/analytics skills than platform engineering, and your roadmap emphasizes quick time-to-value and fewer infrastructure/ops responsibilities.
- Use Airflow + dbt + custom code when you need maximal flexibility, strong software-engineering workflows (CI/CD, testing, modular code), complex/custom connectors or orchestration patterns, or you plan to scale a data-platform team that owns platform engineering.

Detailed comparison by axis

1) Speed to value / ramp time
- Matillion: Much faster to stand up pipelines and onboard non-engineers. GUI components and prebuilt connectors reduce initial development time.
- Airflow+dbt+custom: Longer ramp (Airflow infra + orchestration DAG design + custom connectors). dbt gives fast modeling once dbt skills exist, but full ingestion stack takes longer.

2) Team skills & hiring
- Matillion: Best if team strengths are SQL, BI, and analytics engineering; less need for Python/infra expertise.
- Airflow+dbt+custom: Requires Python engineers, DevOps for Airflow, and analytics engineers skilled in dbt + SQL. Easier to hire for generic engineering roles, more control over coding standards.

3) Maintainability & operational overhead
- Matillion: Vendor-managed pieces reduce maintenance; upgrades and many runtime concerns are handled by Matillion. Less operational toil, but you rely on vendor for stability/features.
- Airflow+dbt+custom: Higher ops burden (Airflow scheduler/workers, scaling, monitoring). But you control upgrades, plugin choices, and incident remedies.

4) Flexibility & extensibility
- Matillion: Strong for typical cloud data sources and ELT flows. Less flexible for exotic connectors, event/streaming patterns, or highly custom logic — though you can embed scripts/custom components.
- Airflow+dbt+custom: Highly flexible. Can integrate any API/stream, complex branching, custom retry logic, custom resource handling, and tie into broader infra/workflows.

5) Transformations, testing & engineering practices
- Matillion: Supports transformations and some testing, but dbt provides industry-standard model testing, documentation, lineage, and modular engineering practices.
- Airflow+dbt+custom: dbt brings strong testing, modular SQL, docs, and CI workflows. Airflow orchestrates dbt runs cleanly. Stronger for engineering best practices.

6) Observability & lineage
- Matillion: Provides built-in monitoring, logging, and some lineage/metadata. Ease of use is good for analysts.
- Airflow+dbt+custom: You can assemble best-of-breed observability (Prometheus, OpenLineage, Data Observability tools), and dbt gives lineage at the model level. Requires work to integrate.

7) Cost & licensing
- Matillion: Commercial licensing; faster delivery but recurring fees. Total Cost of Ownership (TCO) includes license + cloud runtime.
- Airflow+dbt+custom: Lower licensing (open-source Airflow, dbt Core free) but higher engineering and infra costs. Enterprise dbt or managed Airflow add cost.

8) Vendor lock-in & portability
- Matillion: Some lock-in to Matillion’s job definitions and components; migrating off can be non-trivial.
- Airflow+dbt+custom: More portable because code and orchestration are open; easier to move infra or replace components.

9) Scaling & performance
- Matillion: Scales for many typical ELT workloads; relies on cloud data warehouse for heavy transformations. Good parallel execution in many cases.
- Airflow+dbt+custom: Scalability depends on how you design workers/execution and where transformations run (dbt/warehouse or Spark). Offers more control for extreme scale or custom compute.

10) Security & compliance
- Matillion: Runs in your cloud account/ VPC (Matillion Cloud architecture varies); supports enterprise security features. Vendor SaaS model means you need to validate compliance.
- Airflow+dbt+custom: Full control over security posture, network, and data residency. More work but greater control.

How this maps to common roadmaps
- Roadmap: quick analytics enablement, limited platform team, SLA-lite production needs → Matillion accelerates delivery and keeps ops light.
- Roadmap: build a centralized data platform, invest in reproducible engineering, heavy automation/CI, many custom sources, or plan for multi-tool ecosystem → Airflow+dbt+custom is a better long-term fit.

Hybrid options
- Use Matillion for ingestion and lightweight ELT, and dbt for complex modeling/testing. Or run Matillion for quick wins while building an Airflow+dbt platform in parallel, migrating workloads incrementally.

Decision checklist (practical)
- Do you have strong Python/DevOps skills and want full control? Choose Airflow+dbt+custom.
- Do you need to get analysts productive fast and reduce maintenance overhead? Choose Matillion.
- Need dbt-style testing/engineering but want low-code ingestion? Consider Matillion + dbt hybrid.

Conclude with the trade-off
- Matillion trades flexibility and portability for speed and reduced ops. Airflow+dbt+custom trades higher upfront effort and ongoing maintenance for maximal flexibility, reproducibility, and platform ownership. Choose based on whether your roadmap prioritizes fast delivery and limited ops vs. long-term platform control and engineering standards.

[Top](#top)

## How do you present TCO and ROI for Matillion, including licenses, cloud compute, storage, and operational overhead?
Approach overview (how I present TCO/ROI)
- Start with an executive summary: total investment (year 1 and 3-year), annual run-rate, expected annual savings, payback period, and 3-year ROI/NPV.
- Follow with a detailed cost breakdown, quantified benefits, assumptions, sensitivity scenarios (conservative/base/aggressive), and risks/mitigations.
- Use simple financial metrics: Payback Period, ROI % = (Net Benefit / Investment), and NPV over a chosen horizon.

TCO components to include (what to calculate)
1. License/subscription
  - Matillion license cost (marketplace hourly or annual subscription). Include both baseline and reserved/enterprise pricing options if available.
  - Any third-party connectors or add-ons.
2. Cloud compute
  - ETL/ELT worker instance costs (type, vCPU, memory, hourly rate).
  - Runtime hours per job and frequency (sum of instance-hours = sum over jobs of instance_count * job_duration * runs_per_period).
  - Auto-stop/scale assumptions to reduce idle time.
  - Orchestration server cost (if separate).
3. Data warehouse compute
  - Transformation pushdown or ELT compute in Snowflake/Redshift/BigQuery: cost per credit/cluster-hour used by transformations.
  - Estimate based on current transformation patterns and expected reduction due to Matillion optimizations (or increase if enabling more transformations).
4. Storage
  - Staging storage (S3/GCS/Azure Blob) – GB * retention months * $/GB-month.
  - Data warehouse storage costs for retained data.
  - Snapshot/backups and long-term archive.
5. Network and I/O
  - Data transfer costs between cloud services, cross-region egress, API call charges.
6. Operational overhead (people & processes)
  - ETL developer FTE costs (salary + overhead) for development, maintenance, and support.
  - DevOps/system administration for infrastructure management (patching, backups).
  - Monitoring, incident response, and on-call.
  - Training, onboarding, documentation, and change management.
7. One-time/migration costs
  - Professional services, consultants, proof-of-concept, migration engineering, and testing.
  - Data validation and reconciliation costs.
8. Ongoing licensing/contracts and managed services
  - Support contracts, premium support tiers, and software upgrade management.

Quantifiable benefits to include (how you justify ROI)
- Developer productivity gains (estimate % reduction in dev hours because of GUI, templates, components).
- Faster time-to-insight -> business value (e.g., revenue improvement or cost avoidance from faster analytics).
- Reduced maintenance (fewer bespoke scripts, fewer incidents, lower MTTR).
- Consolidation benefits (retire legacy ETL tools/licenses/infrastructure).
- Lower infra costs from ELT pushdown (less separate transformation compute).
- Automation reducing manual runs and manual interventions.
- Improved data quality reducing rework and support costs.

Data you must gather from the customer
- Current ETL tool(s), license costs, and renewal terms.
- Job inventory: number of jobs, average run time, scheduled runs per day/week, concurrency.
- Current ETL server instance types and hours, usage patterns (idle vs active).
- Data volumes (daily ingest, processed TB/month), retention policies.
- Current warehouse compute consumption (credits/hours).
- Number of ETL devs, average loaded labor cost, support FTEs, incident rates and average MTTR.
- Expected growth (data volume, jobs/year).
- Migration effort estimate (FTE-months or consultant days).

How to calculate (formulas and example)
- Annual license cost = Matillion subscription (annual or projection from hourly marketplace usage).
- Annual compute cost = sum(instance_hourly_rate * used_hours) + warehouse_compute_costs.
- Annual storage cost = staging_GB * $/GB-month * 12 * retention factor.
- Annual operational labor cost = number_of_FTEs * loaded_salary.
- Year 1 TCO = license + compute + storage + network + ops labor + migration amortized (or one-time listed separately).
- Net annual benefit = (costs avoided + labor savings + incremental revenue) - incremental ongoing costs.
- ROI% = Net benefit / Investment. Payback months = (one-time investment) / (annual net cash inflow).
- NPV = sum_{t=1..T} (NetBenefit_t / (1+r)^t) - InitialInvestment.

Illustrative numeric example (concise)
Assumptions (example):
- Matillion license = $120,000/year
- Matillion worker compute = $30,000/year
- Staging storage = $10,000/year
- Warehouse compute (net change) = -$20,000/year (savings from pushdown)
- Migration & training (one-time) = $100,000
- Ops labor today = 3 FTEs ($180,000 each loaded) -> $540,000/year
- Expected 25% reduction in ETL FTE effort after Matillion = 0.75 FTE freed -> annual labor savings = $135,000

Year 1:
- Costs: license 120k + compute 30k + storage 10k + ops labor remaining (540k - 135k = 405k) + migration 100k = 665k
- Benefit (costs avoided + other gains): labor savings 135k + warehouse compute savings 20k = 155k
- Net Year1 cash flow = - (665k - 155k) = -510k (negative in year 1 because of migration)
Year 2 onward (no migration):
- Annual costs = 120k + 30k + 10k + 405k = 565k
- Annual benefits = 155k
- Net annual = -410k (in this simplified example net is still negative because license+ops remain higher than identified savings; but you would include additional productivity/revenue gains)
Payback and ROI:
- If additional quantified benefits (e.g., faster time-to-insight generating $600k/year revenue or cost avoidance), adjust net cash flows and compute Payback and NPV accordingly.

Sensitivity analysis
- Vary developer productivity savings (10%/25%/40%).
- Vary runtime hours (optimize auto-stop could reduce compute by 30-70%).
- Vary migration cost and discount rate.
- Present best/base/worst-case scenarios for payback months and 3-year ROI.

Risks and mitigations to present
- Underestimated migration complexity -> include buffer and phased rollout.
- Higher-than-expected warehouse cost if pushdown not leveraged -> training and templates.
- Idle Matillion compute -> implement autoscale/auto-stop policies and guardrails.

Presentation structure (recommended slide order)
1. Executive summary (1 slide)
2. Current state snapshot & pain points
3. Proposed Matillion solution & licensing model
4. Detailed TCO (year 1 + ongoing)
5. Quantified benefits and assumptions
6. Financial metrics: Payback, ROI, NPV (3-year)
7. Sensitivity scenarios (3 cases)
8. Migration plan, timeline, and risk mitigation
9. Recommendation and decision points

Key messages to leadership
- TCO is more than license: include cloud compute, warehouse impact, storage, network, operational labor, and migration.
- ROI depends heavily on measurable productivity gains and proper operational controls (autoscale, template reuse, pushdown).
- Provide scenario-based outcomes so stakeholders can see best/base/worst financial results and recommended guardrails.

Final note
- Build the model in a spreadsheet so stakeholders can change key inputs (dev savings %, run-hours, data growth) and instantly see updated TCO/ROI numbers.

[Top](#top)

## How do you train new engineers on Matillion best practices and enforce code reviews and standards?
High-level approach: combine a structured onboarding program, concise standards and templates, automated validations and CI gates, and a disciplined PR/review workflow with ongoing coaching and metrics. Steps I use in practice:

1) Onboarding & training curriculum
- Week 1: classroom + demos
  - Matillion architecture, environments, Git integration, job types (Orchestration vs Transformation).
  - Walkthrough of our standard pipelines and a “good” vs “bad” job.
- Hands-on labs
  - Sandbox tasks: build a small ETL pipeline using our naming conventions, parameterization, and logging.
  - Guided failure scenarios: force errors, validate retries and alerts.
- Certification & checkpoints
  - Complete Matillion Academy modules and an internal quiz.
  - Sign off by a mentor after pair-programming a real task.
- Continuous learning
  - Brown-bag sessions, recorded walkthroughs, component-library demos.

2) Concrete best-practices docs & templates
- One-page style guide: naming conventions, variable naming, folder structure, component-level rules (e.g., avoid global variables unless necessary).
- Reusable templates: starter Orchestration and Transformation jobs with logging, error handling, and parameter blocks.
- Shared component library: pre-built API calls, S3 copy components, database load patterns, versioned in Git.
- Standards cover:
  - Parameterization and environment variables (no hard-coded credentials).
  - Modularity: small jobs, single responsibility, reusable components.
  - Idempotency and retries.
  - Logging, metrics emission, and structured error handling.
  - Resource usage and concurrency constraints.

3) Git/branching and CI/CD
- Use Matillion’s Git integration (push projects to Git provider) and enforce:
  - Branch strategy: feature/* branch per task, pull requests into develop, protected main/release branches.
  - Protected branches and required status checks before merge.
- CI pipeline (Jenkins/GitHub Actions/GitLab CI):
  - On PR: export Matillion project JSON and run automated checks (naming, secrets detection, required metadata).
  - Run smoke tests: deploy to ephemeral sandbox or QA environment and execute key jobs.
  - Run SQL validation and unit tests for SQL components (or run dbt tests if dbt is in use).
  - Publish artifact and deployment plan when checks pass.
- Deployment pipeline:
  - Promote artifacts between environments using automated jobs and approvals (no manual file edits in production).

4) Code review process and standards enforcement
- PR requirements:
  - Small PRs (recommended < 300 lines of JSON/job changes) and a clear description + test plan.
  - Linked ticket/owner and target environment.
- Review checklist (used as PR template):
  - Naming conventions followed?
  - Parameterization / no hard-coded secrets?
  - Proper error handling and retry logic?
  - Logging and metrics present?
  - Reusable components used where applicable?
  - Side-effects (table truncates, DDL) documented and scoped?
  - Performance considerations addressed (pushdown, parallelism)?
- Reviewer assignment & SLAs:
  - Two reviewers for critical or production-impacting changes; one for minor.
  - 24–48 hour review SLA for business hours.
- Use inline comments in the PR; require thumbs-up from designated approvers for production merges.

5) Automation & static checks
- Export Matillion job and run automated validators:
  - Custom scripts that parse job JSON to catch anti-patterns (hard-coded connections, missing audit components, oversized jobs).
  - Use REST API to validate job definitions and run health checks post-deploy.
- Secrets scanning:
  - Prevent commits of credentials with pre-commit hooks or CI scans.
- Enforce via protected branches and required CI status; block merges if checks fail.

6) Access control and environment separation
- Role-based access in Matillion:
  - Developers have sandbox/QA access; only a release engineer or CI role can deploy to production.
- Separate projects for shared components vs team-specific projects.
- Audit logging enabled and periodic review of who changed what.

7) Reinforcement, measurement and feedback loop
- Weekly rotation for reviewers to spread knowledge and avoid bottlenecks.
- Monthly retrospectives on production incidents tied to code quality and update standards.
- Metrics dashboards:
  - PR size, time-to-merge, CI pass/fail rates, number of rollbacks.
- Continuous improvement: update templates and rules when recurring issues appear.

8) Practical enforcement examples
- Example automated check: export project JSON -> linter script checks for any component with a literal password field or credential reference outside allowed variables -> fail CI with clear error message.
- Example CI smoke test: after deploying feature branch to sandbox, run a small upstream->downstream flow and compare row counts and hash checksums to baseline.
- Example PR policy: any PR that modifies a production job or schema requires at least one approver from the Data Platform team and a successful run of the smoke tests.

9) Quick starter checklist for new hires
- Complete Matillion Academy modules.
- Run 3 sandbox labs and submit PRs using templates.
- Pair with a mentor to review first 3 PRs.
- Pass a short practical test (build and deploy a parameterized pipeline and demonstrate rollback).

This approach balances teaching engineers the right patterns with automated gates and a disciplined review workflow so standards are enforced consistently without being purely manual.

[Top](#top)

## How do you build a center-of-excellence library of shared components, connectors, and job templates?
Goal: create a maintainable, discoverable, secure CoE library (components, connectors, job templates) that teams can reuse and evolve with confidence.

High-level approach (phases)
1. Plan & scope: define what belongs in the library (connectors, transformation patterns, orchestration patterns, utility components, templates). Assign owners and SLA for support and deprecation.
2. Build canonical artifacts: implement components/connectors/templates according to agreed design patterns and naming conventions.
3. Version & publish: store artifacts in Git + Matillion project exports/component exports and publish a catalog with docs and usage examples.
4. Test & release: automated tests + manual QA, CI/CD promotion across envs.
5. Govern & maintain: code reviews, release cadence, metrics, and lifecycle rules.

Concrete implementation details for Matillion

Repository and storage
- Git as single source of truth. Structure repo like:
  - connectors/
  - components/
  - job_templates/
  - docs/
  - tests/
  - releases/
- Keep Matillion exports (project JSONs) and component JSONs checked in as release artifacts. Use branch model (main/master = production-ready, develop = integration, feature/*).

Where artifacts live inside Matillion
- Create a “CoE Templates” Matillion Project or a read-only “Shared Library” project that contains canonical job templates, shared components, global variables examples, and orchestration jobs.
- Use Matillion’s “Create Component” (user components) feature for encapsulated reusable components; export/import component JSON for distribution.

Naming, metadata, and template conventions
- Adopt semantic versioning: MAJOR.MINOR.PATCH (e.g., connector-salesforce-1.2.0).
- Naming examples:
  - Components: COE_Component_<purpose>_vX.Y (e.g., COE_Component_PersistToS3_v1.0.0)
  - Connectors: COE_Connector_<system>_vX.Y (COE_Connector_SFDC_v1.0.0)
  - Job templates: TEMPLATE_Load_DimCustomer_v1.0.0
- Include metadata inside README and component description: purpose, inputs/outputs, variables, dependencies, sample usage, tests, owner, changelog.

Design patterns & coding standards
- Small focused components: single responsibility (e.g., “API paging fetch” separate from “upsert into target”).
- Parameterize everything: connections, schemas, batch sizes, retry counts, timeouts.
- No hard-coded credentials: use Matillion Environment variables or external secrets manager (AWS Secrets Manager / GCP Secret Manager / Azure Key Vault).
- Explicit inputs/outputs and error codes. Return status variables and standard error messages for orchestrations to pick up.
- Logging and observability: set job variables or use Matillion logging conventions; include timing metrics for performance baseline.

Building connectors
- Prefer building connectors as parametrized reusable Matillion components (API Query + Paging pattern or Python3 component for complex auth).
- Implement standard auth patterns using environment-level connection objects or tokens pulled from secure store.
- Provide a “connector wrapper” orchestration job that demonstrates full end-to-end use (auth, incremental watermark, staging, load).
- Export connector component JSONs and example orchestration job as a template.

Job templates
- Create full jobs that represent common ETL patterns: incremental staging, SCD2 load, dimension rebuild, CDC apply.
- Template jobs include:
  - Well-documented variables
  - Deploy-time hooks for environment substitution
  - Test data paths or sample run options
- Keep templates generic: no hard-coded schema names; use variables for table names and partitions.

Distribution & deployment
- For manual consumption: users import component JSON into their project or copy jobs from the shared project.
- For automated distribution:
  - Use Git for code; use Matillion REST API to import project JSONs or to deploy jobs to target projects as part of a pipeline.
  - CI/CD pipeline example: build artifact (component JSON/project export) → run automated tests against a staging Matillion instance → on success, deploy to shared Matillion “Templates” project and tag release in Git.
- Release artifacts stored under releases/ with changelogs.

Testing strategy
- Unit tests: implement small test jobs that assert outputs for specific input cases.
- Integration tests: run full connector flows against sandbox accounts (or mocked endpoints).
- Smoke/perf tests: validate performance and resource usage; capture baseline metrics.
- Automate these tests in CI (use Matillion API or orchestrate Matillion jobs from CI runner).

Governance & lifecycle
- Establish PR and code review process for library changes.
- Require one or more approvers before publishing new versions.
- Maintain an owner for each artifact and a lifecycle policy (supported, deprecated, removed) with timelines.
- Use semantic versioning and require backwards-compatible changes for MINOR releases, breaking changes only in MAJOR.

Documentation & catalog
- Maintain a searchable catalog (Confluence, internal docs site, or GitHub READMEs) that lists:
  - Artifact name, version, purpose, owner
  - Quick-start example
  - Full API (inputs, outputs, variables)
  - Test cases and known limitations
- Include “how to import/use” step-by-step and a sample job to copy into user projects.

Security & access control
- Restrict who can edit the shared CoE project in Matillion using Matillion roles.
- Keep credentials out of components: use Environment variables and cloud secret manager integration.
- Scan and review external connector code (Python) for risks before accepting into the library.

Operationalize & measure adoption
- Track usage (who copies what jobs or which templates are used), incident reports, and performance regressions.
- Onboard teams with a small set of pilot templates and collect feedback.
- Run quarterly reviews to add new artifacts and deprecate unused ones.

Practical rollout roadmap (example)
1. Set up CoE project and Git repo; create templates folder and docs.
2. Implement 3 pilot artifacts: one connector (API), one transformation component (SCD2), one orchestration template (incremental load).
3. Publish pilot, onboard 1–2 teams for feedback.
4. Implement CI pipeline to validate and publish releases.
5. Formalize governance, expand library.

This approach balances Matillion-native capabilities (user components, project exports, environment variables, Matillion REST API) with standard software-engineering practices (Git, CI, semantic versioning, tests, docs, owners) so teams can reliably reuse, evolve, and govern shared ETL assets.

[Top](#top)

## How do you validate and document operational SLOs and define escalation paths for pipeline breaches?
High-level approach: convert business expectations into measurable SLOs (with SLIs and error budgets), implement automated measurement and alerts in the Matillion ecosystem, validate via tests and historical analysis, document in a single-source runbook with owners and playbooks, and map breaches to a tiered escalation matrix with clear time-to-ack/resolve and communications templates.

1) Define SLOs (what to measure)
- Identify business-relevant metrics per pipeline: data freshness, job success rate, end-to-end latency, throughput, and completeness/row-count accuracy.
- For each SLO capture:
  - SLI definition (precise metric and how it’s calculated).
  - Target (e.g., 99% of daily tables available within 2 hours of scheduled run).
  - Measurement window and aggregation (rolling 28d, calendar month).
  - Error budget (e.g., 1% allowable failures per month).
  - Owner and on-call rotation.

2) Implement SLIs and measurement
- Instrument Matillion jobs:
  - Emit completion timestamps, success/failure status, row counts via job components, API calls, or third-party checks.
  - Push metrics to monitoring (CloudWatch/Prometheus/GCP Monitoring/Azure Monitor) or to a metrics pipeline.
- Build dashboards showing SLIs and error budget burn (Grafana/Cloud console).
- Create automated checks (synthetic runs or SQL probes) that validate data freshness and completeness after job end.

3) Validate SLOs
- Baseline with historical data: compute current SLI performance, set realistic targets from historical percentiles.
- Run controlled tests:
  - Canary runs/synthetic upstream delays to ensure monitoring alerts and metrics behave as expected.
  - Chaos tests (simulate worker failure, slow source) for detection and auto-remediation validation.
  - Load/stress tests for throughput and latency SLOs.
- Perform tabletop exercises with on-call, platform, and data owners to walk through breaches and runbooks.

4) Document SLOs and runbooks
- Single-source documentation (Confluence/Git repo) per pipeline including:
  - SLO summary table (SLI, target, window, owner, error budget).
  - Measurement details and where metrics/dashboards live.
  - Runbook with step-by-step actions for common failures (how to check Matillion job logs, environment health, DB load, upstream availability).
  - Links: Matillion job links, job history, logs, dashboards, PagerDuty/Slack channels, escalation matrix.
  - Communication templates for incidents (status updates, severity, impact, remediation steps).
- Version the runbook with the pipeline repo so changes track with pipeline updates.

5) Escalation paths and severity mapping
- Define severity levels and triggers (examples):
  - P0/P1 (critical): Major SLA breach, >50% of downstream consumers affected, or data missing for production reporting window.
    - Time-to-ack: 5–15 minutes. Immediate PagerDuty page to primary on-call and platform lead.
    - Actions: Auto-retry, failover to backup source, escalate to engineering SRE/Platform, open incident bridge.
  - P2 (high): Partial degradation (1–2 critical tables late).
    - Time-to-ack: 30–60 minutes. Notify on-call via Slack, email.
    - Actions: Check Matillion job logs, retry job, check upstream connector, escalate to data owner if needed.
  - P3 (medium): Non-urgent failures, next-day reporting unaffected.
    - Time-to-ack: next business hour. Ticket to backlog and assign owner.
- Escalation matrix (who to call, when):
  - Tier 1 — Pipeline Owner/Primary On-call: initial triage and immediate remediation steps.
  - Tier 2 — Platform/Matillion Admins: environment, compute, job scheduler, job configuration issues.
  - Tier 3 — Data Engineering / SRE: code fixes, schema issues, database scaling.
  - Business/Stakeholder notification for P1/P0 after incident declared.
- Implement escalation automation via PagerDuty (escalation policies, schedules) and Slack channels with pinned runbooks.

6) Runbook actions (example workflow for a late ingestion)
- Detect: monitoring alerts when SLI > threshold.
- Triage: on-call checks Matillion job history and logs, checks job instance for errors and stack traces.
- Remediate:
  - If transient: restart Matillion job or task (document exact commands/API endpoints).
  - If source-down: contact source owner, switch to fallback source if available.
  - If resource issue: scale compute or re-schedule non-critical jobs.
- Escalate: if not resolved within defined time-to-escalate, follow escalation matrix and open incident with bridge and stakeholders.
- Post-incident: run postmortem, update SLO if needed, revise runbook and dashboards.

7) Matillion-specific practices
- Use Matillion job notifications and API to emit status to monitoring.
- Keep idempotent orchestration patterns and built-in retry logic.
- Tag Matillion jobs with owner/contact metadata to populate runbooks automatically.
- Store job logs centrally (S3/Cloud storage) with links in dashboards for quick access.
- Use transformation tests (SQL checks, Great Expectations) as part of Matillion orchestration to fail fast and surface meaningful errors.

8) Continuous improvement
- Weekly SLO reporting and monthly SLO review meetings.
- Use postmortems to adjust SLO targets, update error budgets, and refine escalation steps.
- Track trends in error budget burn to decide when to prioritize reliability work vs feature work.

Example SLO snippet (concise)
- Name: Daily Orders Ingestion Freshness
  - SLI: time from schedule-completion to data available in target table.
  - Target: 99% of daily runs < 2 hours latency (rolling 28 days).
  - Owner: Orders Pipeline Owner, Primary On-call.
  - Alert: 1 table late -> P2 (ack within 60 min); >=3 tables late -> P1 (ack within 15 min, PagerDuty).
  - Runbook: check Matillion job, retry job, check source API, escalate to platform if job fails on infrastructure.

This establishes measurable SLOs, automated validation, documented runbooks, and a clear, automated escalation path tied into Matillion monitoring and organizational on-call processes.

[Top](#top)

## How do you plan and execute a large-scale migration of legacy ETL (Informatica/Talend/SSIS) into Matillion with minimal downtime?
High-level approach: treat this as a phased “assess → design → migrate → validate → cutover → operate” program with wave-based migration, automated testing and reconciliation, CDC-enabled parallel runs, and a clear rollback plan. Key goals: correctness, performance, repeatability, observability and minimal downtime.

1) Discovery & assessment (2–6 weeks)
- Inventory: extract all ETL jobs, workflows, schedules, dependencies, data sources/targets, connectors, custom scripts, stored procedures, and SLAs.
- Classify jobs by complexity/risk: trivial (simple extracts/loads), SQL-heavy (pushdown candidates), transformation-heavy (row-by-row logic, custom code), and mission-critical (tight SLAs).
- Extract metadata: mappings, source-to-target lineage, transformation logic, parameterization, error handling. Use vendor metadata APIs, repository exports or SQL parsing to automate where possible.
- Identify data volumes, window sizes, historical retention, and peak concurrency.
- Identify CDC capabilities of sources (log-based, timestamp-based, triggers) and feasibility of using CDC for minimal-downtime cutover.
- Define non-functional requirements: RTO/RPO, security/compliance, cost targets.

2) Target architecture & design (2–4 weeks)
- Choose target DWH and patterns: ELT pushdown (Snowflake/BigQuery/Redshift) vs Matillion orchestration for heavier transformations. Design staging layer (cloud object store), raw zone, curated zone.
- Define job design standards: use Matillion Orchestration for orchestration & extracts, Transformation jobs for in-warehouse SQL, variables & environments, reusable components, parameters, and Git integration.
- Decide migration strategy per job class:
  - Rehost (wrap existing SQL) — quick wins.
  - Refactor to ELT pushdown — preferred for SQL-heavy jobs.
  - Rebuild in Matillion for complex workflows (use Python/Ruby components if needed).
- Plan CDC/incremental approach: prefer log-based CDC (Debezium/GG/DMS) for minimal downtime. For sources without CDC, design timestamp/high-watermark strategies.
- Security: IAM roles, VPC, private endpoints, secrets management (AWS Secrets Manager/Azure Key Vault/GCP Secret Manager), encryption in transit/at rest, audit logging.
- Operational: monitoring, alerting (Matillion job notifications, CloudWatch/Stackdriver/Log Analytics), runbooks, rollback procedures.
- Define acceptance criteria, data validation rules, performance targets.

3) Proof of Concept (PoC) (2–6 weeks)
- Pick representative high-value jobs: one trivial, one SQL-heavy, one complex transformation, one large-volume streaming/CDC example.
- Implement end-to-end flow in Matillion: ingest, transform, load into target DWH, orchestrate, schedule, and monitor.
- Validate: functional correctness, reconciliation tests (row counts, column-level aggregates, checksums), performance, and operational procedures.
- Iterate design decisions: pushdown vs in-Matillion transforms, resource sizing, partitioning/cluster keys.

4) Automation and conversion tooling
- Build automation to accelerate migration:
  - Metadata-driven templates to generate Matillion jobs from mapping metadata.
  - Reusable components for common patterns (staging load, merge/upsert, error handling).
  - Scripts to translate SQL dialect differences (source SQL → target DWH dialect).
- Use Matillion’s REST API and Git integration to deploy jobs programmatically and manage CI/CD.
- Create test harnesses to run reconciliation and regression tests automatically.

5) Wave-based migration and parallel run
- Plan waves by risk/business domain rather than by vendor. Start with low-risk/simple jobs to build confidence.
- For each wave:
  - Develop Matillion jobs in dev/staging, run unit tests and automated reconciliation.
  - Deploy to production environment(s) but run in parallel with legacy ETL (dual-run), writing to new schema/warehouse while legacy continues to serve consumers.
  - Use CDC/incremental loads to keep target up-to-date; for large full loads, use bulk load to stage and then incremental deltas.
- Monitor for functional parity and performance. Run statistical and business rule reconciliations.
- Tune resource sizing, SQL push-down, and concurrency as needed.

6) Cutover strategy to minimize downtime
- Use continuous parallel runs with CDC to reduce delta size before cutover.
- Cutover flow:
  - Freeze schema changes on source or set agreed quiesce window as needed.
  - Final delta capture: capture changes since last parallel run (CDC/log-based is ideal).
  - Apply final deltas to Matillion/target in a single final batch or streaming sync.
  - Validate reconciliation (row counts, checksums, key lookups, business metrics).
  - Switch consumers: repoint BI connections/ETL downstream to the new warehouse endpoint or change DNS/connection strings or feature flags.
  - Monitor closely for SLA violations.
- Keep legacy ETL available and documented for a rollback window. Define the exact steps to reverse the cutover (e.g., repoint back, re-enable legacy schedules).

7) Testing & validation (continuous)
- Unit tests per job, integration tests per pipeline.
- Reconciliation tests:
  - Row counts per table.
  - Column-level checksums/hashes.
  - Sampling-based record comparisons for complex transformations.
  - Business-key based reconciliation and referential integrity checks.
- Performance/load tests in production-like environment.
- SLA/latency verification for critical jobs.

8) Monitoring, alerting & operationalization
- Implement Matillion job monitoring + cloud-native monitoring (CloudWatch/Stackdriver/Azure Monitor) and log aggregation.
- Define alert thresholds and escalation paths; enable job-level retries, error notifications and automated remediation where safe.
- Build dashboards: job success rates, latency, throughput, data drift, reconciliation failures.
- Maintain runbooks and playbooks for common failures and for rollback.

9) Governance, security & compliance
- Ensure IAM least-privilege for Matillion instances and compute.
- Maintain encryption, key management, and data residency controls.
- Implement audit logging and change management (Matillion Git integration, code reviews).
- Data masking and PII handling policies during migration and in target.

10) Cutover acceptance & decommissioning
- Establish acceptance sign-off criteria and retention period before decommissioning legacy ETL.
- After a predefined stabilization period, decommission legacy components in phases; keep backups and metadata exports for compliance.

11) Rollback plan
- Keep legacy ETL runnable with known state; preserve source high-watermarks.
- Document exact steps to repoint consumers and resume legacy pipelines.
- Maintain incremental data capture to reconcile and avoid data loss on rollback.

Resourcing, timeline and KPIs
- Typical small program: 6–12 weeks (assessment → PoC → a few waves).
- Large-scale enterprise migration: 3–12+ months depending on volume, complexity and parallelization.
- Core team: solution architect, Matillion developer(s), data engineers, QA, DBA/DWH expert, network/security, business SME per domain.
- KPIs: % jobs migrated, reconciliation pass rate, cutover RTO/RPO, job SLA adherence, cost delta.

Risks & mitigations
- Data drift/semantic mismatch — mitigate via thorough lineage, business-validation suites.
- Performance regressions — use pushdown, proper partitioning/indexing, and scale compute during testing.
- Long-running final delta — use CDC and delta window minimization, schedule maintenance windows if unavoidable.
- Operational unfamiliarity — provide runbooks, training, and initial shadow-run support.

Tools & patterns commonly used
- CDC: Debezium, AWS DMS, Oracle GoldenGate, vendor log-based replication.
- Staging: S3/GCS/Azure Blob + Matillion Bulk Load components.
- Reconciliation: checksum utilities, custom Python scripts in Matillion or external validation jobs.
- CI/CD: Git integration, Matillion API, Terraform for infra provisioning.
- Secrets: Cloud secret managers integrated with Matillion.

Outcome focus
- Preserve data correctness and lineage, achieve parity and performance, minimize service interruption via parallel runs and CDC, automate repeatable migration steps, and hand over a maintainable, governed Matillion-based platform with observability and rollback controls.

[Top](#top)
