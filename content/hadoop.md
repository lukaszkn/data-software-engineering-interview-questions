# Hadoop
Hadoop

* [What are the main components of a Hadoop Application?](#What-are-the-main-components-of-a-Hadoop-Application)
* [What is the core concept behind Apache Hadoop framework?](#What-is-the-core-concept-behind-Apache-Hadoop-framework)
* [What is Hadoop Streaming?](#What-is-Hadoop-Streaming)
* [What is the difference between Nodes in HDFS?](#What-is-the-difference-between-Nodes-in-HDFS)
* [What is the optimum hardware configuration to run Apache Hadoop?](#What-is-the-optimum-hardware-configuration-to-run-Apache-Hadoop)
* [What do you know about Block and Block scanner in HDFS?](#What-do-you-know-about-Block-and-Block-scanner-in-HDFS)
* [What are the default port numbers on which Nodes run in Hadoop?](#What-are-the-default-port-numbers-on-which-Nodes-run-in-Hadoop)
* [How will you disable a Block Scanner on HDFS DataNode?](#How-will-you-disable-a-Block-Scanner-on-HDFS-DataNode)
* [How will you get the distance between two nodes in Apache Hadoop?](#How-will-you-get-the-distance-between-two-nodes-in-Apache-Hadoop)
* [Why do we use commodity hardware in Hadoop?](#Why-do-we-use-commodity-hardware-in-Hadoop)
* [How does inter cluster data copying works in Hadoop?](#How-does-inter-cluster-data-copying-works-in-Hadoop)
* [How can we update a file at an arbitrary location in HDFS?](#How-can-we-update-a-file-at-an-arbitrary-location-in-HDFS)
* [What is Replication factor in HDFS?](#What-is-Replication-factor-in-HDFS)
* [What is the difference between NAS and DAS in Hadoop cluster?](#What-is-the-difference-between-NAS-and-DAS-in-Hadoop-cluster)
* [What are the two messages that NameNode receives from DataNode?](#What-are-the-two-messages-that-NameNode-receives-from-DataNode)
* [How does indexing work in Hadoop?](#How-does-indexing-work-in-Hadoop)
* [What data is stored in a HDFS NameNode?](#What-data-is-stored-in-a-HDFS-NameNode)
* [What would happen if NameNode crashes in a HDFS cluster?](#What-would-happen-if-NameNode-crashes-in-a-HDFS-cluster)
* [What are the main functions of Secondary NameNode?](#What-are-the-main-functions-of-Secondary-NameNode)
* [What happens if HDFS file is set with replication factor of 1 and DataNode crashes?](#What-happens-if-HDFS-file-is-set-with-replication-factor-of-1-and-DataNode-crashes)
* [What is the meaning of Rack Awareness in Hadoop?](#What-is-the-meaning-of-Rack-Awareness-in-Hadoop)
* [How will you check if a file exists in HDFS?](#How-will-you-check-if-a-file-exists-in-HDFS)
* [Why do we use fsck command in HDFS?](#Why-do-we-use-fsck-command-in-HDFS)
* [What will happen when NameNode is down and a user submits a new job?](#What-will-happen-when-NameNode-is-down-and-a-user-submits-a-new-job)
* [What are the core methods of a Reducer in Hadoop?](#What-are-the-core-methods-of-a-Reducer-in-Hadoop)
* [What are the primary phases of a Reducer in Hadoop?](#What-are-the-primary-phases-of-a-Reducer-in-Hadoop)
* [What is the use of Context object in Hadoop?](#What-is-the-use-of-Context-object-in-Hadoop)
* [How does partitioning work in Hadoop?](#How-does-partitioning-work-in-Hadoop)
* [What is a Combiner in Hadoop?](#What-is-a-Combiner-in-Hadoop)
* [What is the default replication factor in HDFS?](#What-is-the-default-replication-factor-in-HDFS)
* [How much storage is allocated by HDFS for storing a file of 25 MB size?](#How-much-storage-is-allocated-by-HDFS-for-storing-a-file-of-25-MB-size)
* [Why does HDFS store data in Block structure?](#Why-does-HDFS-store-data-in-Block-structure)
* [How will you create a custom Partitioner in a Hadoop job?](#How-will-you-create-a-custom-Partitioner-in-a-Hadoop-job)
* [What is a Checkpoint node in HDFS?](#What-is-a-Checkpoint-node-in-HDFS)
* [What is a Backup Node in HDFS?](#What-is-a-Backup-Node-in-HDFS)
* [What is the meaning of term Data Locality in Hadoop?](#What-is-the-meaning-of-term-Data-Locality-in-Hadoop)
* [What is a Balancer in HDFS?](#What-is-a-Balancer-in-HDFS)
* [What are the important points a NameNode considers before selecting the DataNode for placing a data block?](#What-are-the-important-points-a-NameNode-considers-before-selecting-the-DataNode-for-placing-a-data-block)
* [How will you replace HDFS data volume before shutting down a DataNode?](#How-will-you-replace-HDFS-data-volume-before-shutting-down-a-DataNode)
* [What are the important configuration files in Hadoop?](#What-are-the-important-configuration-files-in-Hadoop)
* [How will you monitor memory used in a Hadoop cluster?](#How-will-you-monitor-memory-used-in-a-Hadoop-cluster)
* [Why do we need Serialization in Hadoop map reduce methods?](#Why-do-we-need-Serialization-in-Hadoop-map-reduce-methods)
* [What is the use of Distributed Cache in Hadoop?](#What-is-the-use-of-Distributed-Cache-in-Hadoop)
* [How will you synchronize the changes made to a file in Distributed Cache in Hadoop?](#How-will-you-synchronize-the-changes-made-to-a-file-in-Distributed-Cache-in-Hadoop)
* [Can you elaborate about Mapreduce Job](#Can-you-elaborate-about-Mapreduce-Job)
* [Why compute nodes and the storage nodes are the same?](#Why-compute-nodes-and-the-storage-nodes-are-the-same)
* [What is the configuration object importance in Mapreduce?](#What-is-the-configuration-object-importance-in-Mapreduce)
* [Where Mapreduce not recommended?](#Where-Mapreduce-not-recommended)
* [What is Namenode and it’s responsibilities?](#What-is-Namenode-and-it-s-responsibilities)
* [What is Jobtracker’s responsibility?](#What-is-Jobtracker-s-responsibility)
* [What are the Jobtracker and Tasktracker?](#What-are-the-Jobtracker-and-Tasktracker)
* [What is Job scheduling importance in Hadoop Mapreduce?](#What-is-Job-scheduling-importance-in-Hadoop-Mapreduce)
* [When used Reducer?](#When-used-Reducer)
* [Where the Shuffle and Sort process does?](#Where-the-Shuffle-and-Sort-process-does)
* [Java is mandatory to write Mapreduce Jobs?](#Java-is-mandatory-to-write-Mapreduce-Jobs)
* [What methods can controle the Map And Reduce function’s output?](#What-methods-can-controle-the-Map-And-Reduce-function-s-output)
* [What is the main difference between Mapper And Reducer?](#What-is-the-main-difference-between-Mapper-And-Reducer)
* [Why compute Nodes and the Storage Nodes are same?](#Why-compute-Nodes-and-the-Storage-Nodes-are-same)
* [What is difference between mapside join and reduce side join?](#What-is-difference-between-mapside-join-and-reduce-side-join)
* [What happen if number of Reducer is 0?](#What-happen-if-number-of-Reducer-is-0)
* [When we are goes to Combiner? Why it is Recommendable?](#When-we-are-goes-to-Combiner-Why-it-is-Recommendable)
* [What is the main difference between Mapreduce Combiner and Reducer?](#What-is-the-main-difference-between-Mapreduce-Combiner-and-Reducer)
* [What Is Partition?](#What-Is-Partition)
* [When we goes to Partition?](#When-we-goes-to-Partition)
* [What are the important steps when you are partitioning table?](#What-are-the-important-steps-when-you-are-partitioning-table)
* [Can you elaborate Mapreduce Job architecture?](#Can-you-elaborate-Mapreduce-Job-architecture)
* [Why task Tracker launch child Jvm?](#Why-task-Tracker-launch-child-Jvm)
* [Why JobClient and Job Tracker submits job resources to file system?](#Why-JobClient-and-Job-Tracker-submits-job-resources-to-file-system)
* [How many Mappers and Reducers can run?](#How-many-Mappers-and-Reducers-can-run)
* [What is InputSplit?](#What-is-InputSplit)
* [How to configure the split value?](#How-to-configure-the-split-value)
* [How much ram required to process 64mb data?](#How-much-ram-required-to-process-64mb-data)
* [What is difference between block And split?](#What-is-difference-between-block-And-split)
* [Why Hadoop Framework reads a file parallel why not sequential?](#Why-Hadoop-Framework-reads-a-file-parallel-why-not-sequential)
* [If I am change block size from 64 to 128?](#If-I-am-change-block-size-from-64-to-128)
* [What is IsSplitable()?](#What-is-IsSplitable)
* [How much Hadoop allows maximum block size and minimum block size?](#How-much-Hadoop-allows-maximum-block-size-and-minimum-block-size)
* [What are the Job Resource files?](#What-are-the-Job-Resource-files)
* [What’s the Mapreduce Job consists?](#What-s-the-Mapreduce-Job-consists)
* [What is the data locality?](#What-is-the-data-locality)
* [What is speculative execution?](#What-is-speculative-execution)
* [What is chain Mapper?](#What-is-chain-Mapper)
* [How to do value level comparison?](#How-to-do-value-level-comparison)
* [What is setup and clean up methods?](#What-is-setup-and-clean-up-methods)
* [How many slots allocate for each task?](#How-many-slots-allocate-for-each-task)
* [Why TaskTracker launch child Jvm to do a task? Why not use Existent Jvm?](#Why-TaskTracker-launch-child-Jvm-to-do-a-task-Why-not-use-Existent-Jvm)
* [What main configuration parameters are specified in Mapreduce?](#What-main-configuration-parameters-are-specified-in-Mapreduce)
* [What is identity Mapper?](#What-is-identity-Mapper)
* [What is RecordReader in a MapReduce?](#What-is-RecordReader-in-a-MapReduce)
* [What is OutputCommitter?](#What-is-OutputCommitter)
* [What are the parameters of Mappers and Reducers?](#What-are-the-parameters-of-Mappers-and-Reducers)
* [Explain JobConf in Mapreduce?](#Explain-JobConf-in-Mapreduce)
* [Explain Job scheduling through Jobtracker?](#Explain-Job-scheduling-through-Jobtracker)
* [What is SequenceFileInputFormat?](#What-is-SequenceFileInputFormat)
* [Explain how input and output data format of the Hadoop Framework?](#Explain-how-input-and-output-data-format-of-the-Hadoop-Framework)
* [What are the restriction to the Key and Value Class ?](#What-are-the-restriction-to-the-Key-and-Value-Class)
* [Explain the wordcount implementation via Hadoop Framework?](#Explain-the-wordcount-implementation-via-Hadoop-Framework)
* [How Mapper is instantiated in a running Job?](#How-Mapper-is-instantiated-in-a-running-Job)
* [Which are the methods in the Mapper Interface?](#Which-are-the-methods-in-the-Mapper-Interface)
* [What happens if You don't Override the Mapper methods and keep them as it is?](#What-happens-if-You-don-t-Override-the-Mapper-methods-and-keep-them-as-it-is)
* [What is the use of context Object?](#What-is-the-use-of-context-Object)
* [How can you Add the arbitrary Key-value pairs in your Mapper?](#How-can-you-Add-the-arbitrary-Key-value-pairs-in-your-Mapper)
* [How Does Mapper's Run() Method Works?](#How-Does-Mapper-s-Run-Method-Works)
* [Which Object can be used to get the progress of a particular Job?](#Which-Object-can-be-used-to-get-the-progress-of-a-particular-Job)
* [What is next step after Mapper Or Maptask?](#What-is-next-step-after-Mapper-Or-Maptask)
* [How can we control particular Key should go in a specific Reducer?](#How-can-we-control-particular-Key-should-go-in-a-specific-Reducer)
* [What is the use of Combiner?](#What-is-the-use-of-Combiner)
* [How many Maps are there in a particular Job?](#How-many-Maps-are-there-in-a-particular-Job)
* [What is the Reducer used for?](#What-is-the-Reducer-used-for)
* [Explain the core methods of the Reducer?](#Explain-the-core-methods-of-the-Reducer)
* [What are the primary phases of the Reducer?](#What-are-the-primary-phases-of-the-Reducer)
* [Explain the Shuffle?](#Explain-the-Shuffle)
* [Explain the Reducer's sort phase?](#Explain-the-Reducer-s-sort-phase)
* [Explain the Reducer's reduce phase?](#Explain-the-Reducer-s-reduce-phase)
* [How many Reducers should be configured?](#How-many-Reducers-should-be-configured)
* [It can be possible that a Job has 0 Reducers?](#It-can-be-possible-that-a-Job-has-0-Reducers)
* [What happens if number of Reducers are 0?](#What-happens-if-number-of-Reducers-are-0)
* [How many instances of Jobtracker can run on a Hadoop Cluster?](#How-many-instances-of-Jobtracker-can-run-on-a-Hadoop-Cluster)
* [What is the Jobtracker and what it performs in a Hadoop Cluster?](#What-is-the-Jobtracker-and-what-it-performs-in-a-Hadoop-Cluster)
* [How a task is scheduled by a Jobtracker?](#How-a-task-is-scheduled-by-a-Jobtracker)
* [How many instances of Tasktracker run on a Hadoop Cluster?](#How-many-instances-of-Tasktracker-run-on-a-Hadoop-Cluster)
* [How many maximum Jvm can run on a Slave Node?](#How-many-maximum-Jvm-can-run-on-a-Slave-Node)
* [What is Nas?](#What-is-Nas)
* [How Hdfs differs with Nfs?](#How-Hdfs-differs-with-Nfs)
* [How does a NameNode handle the failure of the Data Nodes?](#How-does-a-NameNode-handle-the-failure-of-the-Data-Nodes)
* [Can Reducer talk with each other?](#Can-Reducer-talk-with-each-other)
* [Where the Mapper's intermediate data will be stored?](#Where-the-Mapper-s-intermediate-data-will-be-stored)
* [What is the Hadoop Mapreduce api contract for a Key and Value Class?](#What-is-the-Hadoop-Mapreduce-api-contract-for-a-Key-and-Value-Class)
* [What is a IdentityMapper and IdentityReducer in Mapreduce?](#What-is-a-IdentityMapper-and-IdentityReducer-in-Mapreduce)
* [What is the meaning of Speculative Execution in Hadoop?](#What-is-the-meaning-of-Speculative-Execution-in-Hadoop)
* [How Hdfs is different from traditional File Systems?](#How-Hdfs-is-different-from-traditional-File-Systems)
* [What is Hdfs block size and how is it different from Traditional File System block size?](#What-is-Hdfs-block-size-and-how-is-it-different-from-Traditional-File-System-block-size)
* [What is a NameNode and how many instances of NameNode run on a Hadoop Cluster?](#What-is-a-NameNode-and-how-many-instances-of-NameNode-run-on-a-Hadoop-Cluster)
* [How the client communicates with Hdfs?](#How-the-client-communicates-with-Hdfs)
* [How the Hdfs blocks are replicated?](#How-the-Hdfs-blocks-are-replicated)
* [Can you give some examples of Big Data?](#Can-you-give-some-examples-of-Big-Data)
* [What is the basic difference between traditional Rdbms and Hadoop?](#What-is-the-basic-difference-between-traditional-Rdbms-and-Hadoop)
* [What is structured and unstructured Data?](#What-is-structured-and-unstructured-Data)
* [Since the data is replicated thrice in Hdfs so does it mean that any calculation done on One Node will also be replicated on the other Two?](#Since-the-data-is-replicated-thrice-in-Hdfs-so-does-it-mean-that-any-calculation-done-on-One-Node-will-also-be-replicated-on-the-other-Two)
* [What is throughput and how does Hdfs get a good throughput?](#What-is-throughput-and-how-does-Hdfs-get-a-good-throughput)
* [What is streaming access?](#What-is-streaming-access)
* [What is a Commodity Hardware so does Commodity Hardware include Ram?](#What-is-a-Commodity-Hardware-so-does-Commodity-Hardware-include-Ram)
* [Is NameNode also a Commodity?](#Is-NameNode-also-a-Commodity)
* [What is a Metadata?](#What-is-a-Metadata)
* [What is a Daemon?](#What-is-a-Daemon)
* [What is a Heartbeat in Hdfs?](#What-is-a-Heartbeat-in-Hdfs)
* [How indexing is done in Hdfs?](#How-indexing-is-done-in-Hdfs)
* [If a Data Node is full how it's identified?](#If-a-Data-Node-is-full-how-it-s-identified)
* [If DataNodes increase then do we need to upgrade NameNode?](#If-DataNodes-increase-then-do-we-need-to-upgrade-NameNode)
* [Are Job Tracker and Task Trackers present in separate machines?](#Are-Job-Tracker-and-Task-Trackers-present-in-separate-machines)
* [On what basis NameNode will decide which DataNode to write on?](#On-what-basis-NameNode-will-decide-which-DataNode-to-write-on)
* [Who is a user in Hdfs?](#Who-is-a-user-in-Hdfs)
* [Is client the end user in Hdfs?](#Is-client-the-end-user-in-Hdfs)
* [What is the Communication Channel between client and NameNode/DataNode?](#What-is-the-Communication-Channel-between-client-and-NameNode-DataNode)
* [What is a Rack?](#What-is-a-Rack)
* [On what basis Data will be stored on a Rack?](#On-what-basis-Data-will-be-stored-on-a-Rack)
* [Do we need to place 2nd and 3rd Data in Rack 2 only?](#Do-we-need-to-place-2nd-and-3rd-Data-in-Rack-2-only)
* [What if Rack 2 and DataNode fails?](#What-if-Rack-2-and-DataNode-fails)
* [What is the difference between Gen1 and Gen2 Hadoop with regards to the NameNode?](#What-is-the-difference-between-Gen1-and-Gen2-Hadoop-with-regards-to-the-NameNode)
* [Do we require two servers for the NameNode and the DataNodes?](#Do-we-require-two-servers-for-the-NameNode-and-the-DataNodes)
* [Why are the number of splits equal to the number of Maps?](#Why-are-the-number-of-splits-equal-to-the-number-of-Maps)
* [Is a Job split into maps?](#Is-a-Job-split-into-maps)
* [Which are the two types of writes in Hdfs?](#Which-are-the-two-types-of-writes-in-Hdfs)
* [Why reading is done in parallel and writing is not in Hdfs?](#Why-reading-is-done-in-parallel-and-writing-is-not-in-Hdfs)
* [Can Hadoop be compared to Nosql Database like Cassandra?](#Can-Hadoop-be-compared-to-Nosql-Database-like-Cassandra)
* [How JobTracker schedules a task?](#How-JobTracker-schedules-a-task)
* [What is a Task Tracker in Hadoop and how many instances of Task Tracker run on a Hadoop Cluster?](#What-is-a-Task-Tracker-in-Hadoop-and-how-many-instances-of-Task-Tracker-run-on-a-Hadoop-Cluster)
* [What is a task instance in Hadoop and where does it run?](#What-is-a-task-instance-in-Hadoop-and-where-does-it-run)
* [What is configuration of a typical Slave Node on Hadoop Cluster and how many Jvms run on a Slave Node?](#What-is-configuration-of-a-typical-Slave-Node-on-Hadoop-Cluster-and-how-many-Jvms-run-on-a-Slave-Node)
* [How NameNode handles DataNode failures?](#How-NameNode-handles-DataNode-failures)
* [Does Mapreduce programming model provide a way for Reducers to communicate with each other and in a Mapreduce Job can a Reducer communicate with another Reducer?](#Does-Mapreduce-programming-model-provide-a-way-for-Reducers-to-communicate-with-each-other-and-in-a-Mapreduce-Job-can-a-Reducer-communicate-with-another-Reducer)
* [Can I set the number of Reducers to Zero?](#Can-I-set-the-number-of-Reducers-to-Zero)
* [Where is the Mapper Output intermediate Kay-value data stored?](#Where-is-the-Mapper-Output-intermediate-Kay-value-data-stored)
* [If Reducers do not start before all Mappers finish then why does the progress on Mapreduce Job shows something like Map 50 percents Reduce 10 percents and why Reducers progress percentage is displayed when Mapper is not Finished yet?](#If-Reducers-do-not-start-before-all-Mappers-finish-then-why-does-the-progress-on-Mapreduce-Job-shows-something-like-Map-50-percents-Reduce-10-percents-and-why-Reducers-progress-percentage-is-displayed-when-Mapper-is-not-Finished-yet)
* [Explain in brief the three Modes in which Hadoop can be run?](#Explain-in-brief-the-three-Modes-in-which-Hadoop-can-be-run)
* [Explain what are the features of Standalone local Mode?](#Explain-what-are-the-features-of-Standalone-local-Mode)
* [What are the features of fully distributed mode?](#What-are-the-features-of-fully-distributed-mode)
* [Explain what are the main features Of pseudo mode?](#Explain-what-are-the-main-features-Of-pseudo-mode)
* [What are the port numbers of NameNode and JobTracker and TaskTracker?](#What-are-the-port-numbers-of-NameNode-and-JobTracker-and-TaskTracker)
* [Tell us what is a spill factor with respect to the ram?](#Tell-us-what-is-a-spill-factor-with-respect-to-the-ram)
* [Is fs.mapr working for a single directory?](#Is-fs-mapr-working-for-a-single-directory)
* [Which are the three main Hdfs-site.xml properties?](#Which-are-the-three-main-Hdfs-site-xml-properties)
* [How can I restart NameNode?](#How-can-I-restart-NameNode)
* [How can we check whether Namenode is working or not?](#How-can-we-check-whether-Namenode-is-working-or-not)
* [At times you get a connection refused Java Exception when you run the file system check command Hadoop fsck?](#At-times-you-get-a-connection-refused-Java-Exception-when-you-run-the-file-system-check-command-Hadoop-fsck)
* [What is the use of the command Mapred.job.tracker?](#What-is-the-use-of-the-command-Mapred-job-tracker)
* [What does etc/init.d do?](#What-does-etc-init-d-do)
* [How can we look for the Namenode in the browser?](#How-can-we-look-for-the-Namenode-in-the-browser)
* [What do masters and slaves consist of?](#What-do-masters-and-slaves-consist-of)
* [What is the function Of Hadoop-env.sh and where is it present?](#What-is-the-function-Of-Hadoop-env-sh-and-where-is-it-present)
* [Can we have multiple entries in the master files?](#Can-we-have-multiple-entries-in-the-master-files)
* [In Hadoop_pid_dir and what does pid stands for?](#In-Hadoop-pid-dir-and-what-does-pid-stands-for)
* [What does Hadoop-metrics and properties file do?](#What-does-Hadoop-metrics-and-properties-file-do)
* [What are the network requirements for hadoop?](#What-are-the-network-requirements-for-hadoop)
* [Why do we need a password-less ssh in fully distributed environment?](#Why-do-we-need-a-password-less-ssh-in-fully-distributed-environment)
* [What will happen if a NameNode has no data?](#What-will-happen-if-a-NameNode-has-no-data)
* [What happens to job tracker when NameNode is down?](#What-happens-to-job-tracker-when-NameNode-is-down)
* [Explain what do you mean by formatting of the Dfs?](#Explain-what-do-you-mean-by-formatting-of-the-Dfs)
* [We use Unix variants for hadoop and can we use Microsoft Windows for the same?](#We-use-Unix-variants-for-hadoop-and-can-we-use-Microsoft-Windows-for-the-same)
* [Which one decides the input split hdfs client or NameNode?](#Which-one-decides-the-input-split-hdfs-client-or-NameNode)
* [Can you tell me if we can create a hadoop cluster from scratch?](#Can-you-tell-me-if-we-can-create-a-hadoop-cluster-from-scratch)
* [Explain the significance of ssh and what is the port on which port does ssh work and why do we need password in ssh local host?](#Explain-the-significance-of-ssh-and-what-is-the-port-on-which-port-does-ssh-work-and-why-do-we-need-password-in-ssh-local-host)
* [What is ssh and explain in detail about ssh communication between masters and the slaves?](#What-is-ssh-and-explain-in-detail-about-ssh-communication-between-masters-and-the-slaves)
* [Can You Tell Is What Will Happen To A NameNode and When Job Tracker Is Not Up And Running?](#Can-You-Tell-Is-What-Will-Happen-To-A-NameNode-and-When-Job-Tracker-Is-Not-Up-And-Running)

## What are the main components of a Hadoop Application?
A Hadoop application consists of three primary components:

*   **HDFS (Hadoop Distributed File System):** This serves as the storage unit of Hadoop, designed to run on commodity hardware and manage large datasets in a distributed manner.
*   **MapReduce:** As the processing unit, MapReduce is a programming model for parallel processing of large datasets across a cluster.
*   **YARN (Yet Another Resource Negotiator):** This component acts as the resource management unit, responsible for overseeing cluster resources and scheduling tasks.

## What is the core concept behind Apache Hadoop framework?
The core concept of the Apache Hadoop framework is to store and process massive datasets in a distributed environment. It is designed to scale from a single server to thousands of machines, with each node providing local computation and storage. This allows for high-throughput data processing and fault tolerance.

## What is Hadoop Streaming?
Hadoop Streaming is a utility that allows users to create and run MapReduce jobs using any executable or script as the mapper and/or reducer. This means you can leverage standard Unix tools like `cat` and `wc` or scripts written in languages like Python or Perl to process data in Hadoop.

## What is the difference between Nodes in HDFS?
In HDFS, there are two main types of nodes:

*   **NameNode:** This is the master node that manages the file system namespace, regulates client access to files, and stores metadata about the files.
*   **DataNode:** These are the slave nodes that store the actual data in the form of blocks. A cluster typically has multiple DataNodes.

## What is the optimum hardware configuration to run Apache Hadoop?
The optimal hardware configuration for a Hadoop cluster depends on the specific workload and data size. However, a typical slave node configuration includes:

*   **Processor:** 2 quad-core CPUs
*   **RAM:** 24-64 GB
*   **Storage:** 12-24 TB of local storage (JBOD)
*   **Network:** 10 Gigabit Ethernet

## What do you know about Block and Block scanner in HDFS?
*   **Block:** In HDFS, files are divided into fixed-size blocks (defaulting to 128 MB), which are then distributed and stored across the DataNodes.
*   **Block Scanner:** This is a process running on each DataNode that periodically verifies the integrity of the blocks. If a corrupt block is detected, it is reported to the NameNode, which then arranges for a new replica to be created on another DataNode.

## What are the default port numbers on which Nodes run in Hadoop?
The default port numbers for various Hadoop nodes are:

*   **NameNode:** 50070 (Web UI), 8020 (client requests)
*   **Secondary NameNode:** 50090 (Web UI)
*   **DataNode:** 50075 (Web UI), 50010 (data transfer), 50020 (IPC)
*   **JobTracker:** 50030 (Web UI), 8021 (client requests)
*   **TaskTracker:** 50060 (Web UI)

## How will you disable a Block Scanner on HDFS DataNode?
To disable the Block Scanner on a DataNode, you need to set the `dfs.datanode.scan.period.hours` property to `0` in the `hdfs-site.xml` configuration file.

## How will you get the distance between two nodes in Apache Hadoop?
The distance between two nodes in Hadoop is determined by their network topology, specifically their rack locations. The distance is calculated as the sum of the distances to their nearest common ancestor. The `NetworkTopology` class can be used to programmatically determine this distance.

## Why do we use commodity hardware in Hadoop?
Hadoop is designed to run on commodity hardware, which is inexpensive and widely available. This approach allows for the construction of large, cost-effective clusters. The framework's fault-tolerant design ensures that the cluster remains operational even if a node fails, as data is replicated across multiple machines.

## How does inter cluster data copying works in Hadoop?
Inter-cluster data copying in Hadoop is typically done using the `distcp` (distributed copy) command. This tool is designed to efficiently copy large amounts of data between Hadoop clusters by running a MapReduce job where the mappers handle the data transfer in parallel.

## How can we update a file at an arbitrary location in HDFS?
HDFS does not support updating files at arbitrary locations. Files in HDFS are write-once, meaning they can be written to, closed, and then reopened for reading. To modify a file, you must either overwrite it completely or append new data to the end.

## What is Replication factor in HDFS?
The replication factor in HDFS is the number of times each block of a file is replicated and stored across the DataNodes. The default replication factor is 3, which ensures high data availability and fault tolerance. If a DataNode fails, the data can still be accessed from one of the other replicas.

## What is the difference between NAS and DAS in Hadoop cluster?
*   **NAS (Network Attached Storage):** This is a file-level storage system that is connected to a network, allowing multiple clients to access the data. It is typically a single, high-end machine.
*   **DAS (Direct Attached Storage):** This refers to storage that is directly connected to a single computer. In a Hadoop cluster, each DataNode has its own DAS, which contributes to the overall distributed storage.

## What are the two messages that NameNode receives from DataNode?
The NameNode receives two primary types of messages from each DataNode:

*   **Heartbeat:** This is a periodic message (sent every 3 seconds by default) that informs the NameNode that the DataNode is alive and functioning correctly.
*   **Block Report:** This is a more detailed message (sent every 6 hours by default) that provides the NameNode with a complete list of all the blocks stored on that DataNode.

## How does indexing work in Hadoop?
Hadoop does not provide a built-in indexing mechanism for data stored in HDFS. However, you can integrate Hadoop with external indexing solutions like Apache Solr or Elasticsearch. These tools can be used to create and manage indexes of the data in HDFS, enabling fast and efficient searching.

## What data is stored in a HDFS NameNode?
The HDFS NameNode stores the metadata for the entire file system. This includes:

*   The file system namespace (directory structure)
*   File-to-block mapping (which blocks make up a file)
*   Block-to-DataNode mapping (which DataNodes store which blocks)
*   File attributes (permissions, modification times, etc.)

## What would happen if NameNode crashes in a HDFS cluster?
If the NameNode crashes, the HDFS cluster becomes inaccessible. The NameNode is a single point of failure, and without it, clients cannot locate their data because the file-to-block mapping is lost. To mitigate this, Hadoop provides a Secondary NameNode, which periodically creates checkpoints of the NameNode's metadata.

## What are the main functions of Secondary NameNode?
The main function of the Secondary NameNode is to periodically merge the `fsimage` (a snapshot of the file system metadata) with the `edits` log (a record of all subsequent changes). This process creates a new, updated `fsimage`, which helps to reduce the startup time of the NameNode and provides a backup of the metadata.

## What happens if HDFS file is set with replication factor of 1 and DataNode crashes?
If a file has a replication factor of 1 and the DataNode storing that file's only replica crashes, the data becomes permanently lost. This is why a replication factor of at least 3 is recommended for production environments to ensure data durability.

## What is the meaning of Rack Awareness in Hadoop?
Rack Awareness is a feature in Hadoop that allows the NameNode to be aware of the cluster's network topology, specifically which DataNodes are on which racks. This information is used to improve data reliability and performance by placing replicas of a block on different racks. This ensures that even if an entire rack fails, the data is still accessible.

## How will you check if a file exists in HDFS?
You can check if a file exists in HDFS using the `hadoop fs -test -e <file_path>` command. This command will return an exit code of `0` if the file exists and `1` otherwise.

## Why do we use fsck command in HDFS?
The `fsck` (file system check) command is used to check the health of the HDFS file system. It can be used to identify missing or corrupt blocks, under-replicated files, and other inconsistencies. This is a valuable tool for diagnosing and troubleshooting issues with HDFS.

## What will happen when NameNode is down and a user submits a new job?
If the NameNode is down, a user cannot submit a new job. The NameNode is responsible for managing the file system, and without it, the JobTracker cannot access the necessary job resources (like the JAR file and input data) that are stored in HDFS.

## What are the core methods of a Reducer in Hadoop?
The core methods of a Reducer are:

*   `setup()`: This method is called once at the beginning of the reduce task.
*   `reduce()`: This method is called for each key, with an iterator for all the values associated with that key.
*   `cleanup()`: This method is called once at the end of the reduce task.

## What are the primary phases of a Reducer in Hadoop?
The primary phases of a Reducer are:

*   **Shuffle:** The Reducer copies the sorted map outputs from each Mapper.
*   **Sort:** The framework merges and sorts the map outputs by key.
*   **Reduce:** The `reduce()` method is called for each key, where the final output is generated.

## What is the use of Context object in Hadoop?
The `Context` object in Hadoop is used to pass information between the framework and the Mapper/Reducer. It provides access to job configuration, allows for the emission of output key-value pairs, and can be used to report progress and set status messages.

## How does partitioning work in Hadoop?
Partitioning in Hadoop is the process of determining which Reducer will receive the intermediate key-value pairs from the Mappers. By default, this is done using a hash function on the key, but you can implement a custom `Partitioner` to control how the data is distributed among the Reducers.

## What is a Combiner in Hadoop?
A Combiner is an optional, local Reducer that runs on the same node as the Mapper. It performs a preliminary aggregation of the map output, which helps to reduce the amount of data that needs to be transferred over the network to the Reducers. This can significantly improve the performance of a MapReduce job.

## What is the default replication factor in HDFS?
The default replication factor in HDFS is 3. This means that for every block of data, there will be three copies stored on different DataNodes across the cluster.

## How much storage is allocated by HDFS for storing a file of 25 MB size?
For a 25 MB file, HDFS will allocate one block. With a default block size of 128 MB, the file will occupy 25 MB of space within that block. However, due to the default replication factor of 3, the total storage allocated across the cluster will be 75 MB (25 MB x 3).

## Why does HDFS store data in Block structure?
HDFS stores data in a block structure for several reasons:

*   **Large File Support:** It allows HDFS to store files that are larger than the storage capacity of any single node.
*   **Simplified Storage Management:** It simplifies the storage subsystem since the block size is fixed.
*   **Fault Tolerance:** Blocks can be easily replicated across multiple DataNodes to ensure data availability.

## How will you create a custom Partitioner in a Hadoop job?
To create a custom Partitioner, you need to:

1.  Write a Java class that extends the `Partitioner` class.
2.  Override the `getPartition()` method, which takes the key, value, and number of reducers as input and returns the partition number.
3.  In the driver code, set the custom Partitioner class using `job.setPartitionerClass()`.

## What is a Checkpoint node in HDFS?
A Checkpoint Node is a node that periodically creates checkpoints of the NameNode's namespace. It fetches the `fsimage` and `edits` log from the NameNode, merges them, and then uploads the new `fsimage` back to the NameNode. This is a more efficient alternative to the Secondary NameNode.

## What is a Backup Node in HDFS?
A Backup Node is similar to a Checkpoint Node, but it also maintains an in-memory, up-to-date copy of the file system namespace. This allows it to be a read-only NameNode and provides a more robust backup solution.

## What is the meaning of term Data Locality in Hadoop?
Data Locality is a key concept in Hadoop that refers to the practice of moving the computation to the data, rather than the other way around. By processing the data on the same node where it is stored, Hadoop minimizes network traffic and improves the overall performance of MapReduce jobs.

## What is a Balancer in HDFS?
A Balancer is a tool in HDFS that is used to redistribute data blocks evenly across the DataNodes in a cluster. This is useful when new DataNodes are added or when data becomes unevenly distributed over time. The Balancer helps to ensure that the cluster's resources are utilized effectively.

## What are the important points a NameNode considers before selecting the DataNode for placing a data block?
When placing a data block, the NameNode considers several factors:

*   **Rack Awareness:** It tries to place replicas on different racks to ensure fault tolerance.
*   **DataNode Capacity:** It considers the available disk space on each DataNode.
*   **Data Locality:** It prioritizes placing a replica on the same node as the client that is writing the data.

## How will you replace HDFS data volume before shutting down a DataNode?
To replace an HDFS data volume on a DataNode, you should first decommission the node using the `hdfs dfsadmin -decommission` command. This will replicate the blocks on that node to other DataNodes. Once the decommissioning is complete, you can shut down the DataNode, replace the volume, and then bring the node back online.

## What are the important configuration files in Hadoop?
The important configuration files in Hadoop are:

*   `core-site.xml`: Contains the core configuration settings for Hadoop.
*   `hdfs-site.xml`: Contains the configuration settings for HDFS.
*   `mapred-site.xml`: Contains the configuration settings for MapReduce.
*   `yarn-site.xml`: Contains the configuration settings for YARN.

## How will you monitor memory used in a Hadoop cluster?
You can monitor memory usage in a Hadoop cluster using several tools:

*   **YARN Web UI:** The YARN ResourceManager provides a web interface that shows memory usage for each application and node.
*   **Ganglia:** This is a popular open-source monitoring tool that can be integrated with Hadoop to provide detailed metrics on memory, CPU, and network usage.
*   **Nagios:** This is another monitoring tool that can be used to track the health and performance of a Hadoop cluster, including memory usage.

## Why do we need Serialization in Hadoop map reduce methods?
Serialization is the process of converting an object into a stream of bytes, which can then be easily transmitted over the network or stored in a file. In Hadoop, serialization is used to efficiently transfer data between the Mappers and Reducers. All keys and values in a MapReduce job must be serializable.

## What is the use of Distributed Cache in Hadoop?
The Distributed Cache is a facility in Hadoop that allows you to distribute read-only files (like text files, JARs, or archives) to the slave nodes at the start of a job. This is useful for sharing common data that is needed by all the tasks in a job, without having to manually copy it to each node.

## How will you synchronize the changes made to a file in Distributed Cache in Hadoop?
You cannot synchronize changes to a file in the Distributed Cache. The files are read-only and are meant to be static for the duration of the job. If you need to share dynamic data, you should consider using a different mechanism, such as a database or a distributed key-value store.

## Can you elaborate about Mapreduce Job
A MapReduce job is a unit of work that consists of the input data, the MapReduce program, and the configuration information. The job is submitted to the JobTracker, which then distributes the work to the TaskTrackers. The job is complete when all the map and reduce tasks have finished.

## Why compute nodes and the storage nodes are the same?
In Hadoop, the compute nodes and storage nodes are the same to leverage the principle of data locality. By processing the data on the same node where it is stored, Hadoop minimizes network I/O and improves performance. This is a fundamental design principle that distinguishes Hadoop from other distributed computing frameworks.

## What is the configuration object importance in Mapreduce?
The `Configuration` object is of central importance in a MapReduce job. It is used to provide the framework with all the necessary information to run the job, including the input and output paths, the Mapper and Reducer classes, the input and output formats, and any other custom parameters.

## Where Mapreduce not recommended?
MapReduce is not recommended for:

*   **Low-latency data processing:** The overhead of starting up a MapReduce job makes it unsuitable for real-time or near-real-time applications.
*   **Iterative algorithms:** The need to write intermediate results to disk after each iteration can make MapReduce inefficient for iterative algorithms.
*   **Complex event processing:** MapReduce is a batch-oriented system and is not well-suited for processing continuous streams of events.

## What is Namenode and it’s responsibilities?
The NameNode is the master node in HDFS. Its responsibilities include:

*   Managing the file system namespace.
*   Storing the metadata for all files and directories.
*   Regulating client access to files.
*   Coordinating the replication of data blocks.

## What is Jobtracker’s responsibility?
The JobTracker is the master node for MapReduce. Its responsibilities include:

*   Accepting job submissions from clients.
*   Breaking a job down into a series of map and reduce tasks.
*   Assigning tasks to the TaskTrackers.
*   Monitoring the progress of the tasks and re-executing failed tasks.

## What are the Jobtracker and Tasktracker?
The JobTracker and TaskTracker are the master and slave nodes in the MapReduce framework, respectively.

*   **JobTracker:** This is the master node that coordinates all the jobs running on the cluster.
*   **TaskTracker:** This is a slave node that runs on each DataNode and is responsible for executing the map and reduce tasks assigned by the JobTracker.

## What is Job scheduling importance in Hadoop Mapreduce?
Job scheduling is important in a multi-user Hadoop cluster to ensure that all users get a fair share of the cluster's resources. Hadoop provides different schedulers, such as the FIFO scheduler, the Fair Scheduler, and the Capacity Scheduler, which can be configured to meet the specific needs of an organization.

## When used Reducer?
A Reducer is used when you need to aggregate or summarize data. It takes the intermediate key-value pairs from the Mappers and processes them to produce the final output. A Reducer is not always necessary; for simple map-only jobs, you can set the number of reducers to zero.

## Where the Shuffle and Sort process does?
The shuffle and sort process takes place between the map and reduce phases. The framework automatically handles this process, which involves:

*   **Shuffle:** Copying the map outputs to the Reducer nodes.
*   **Sort:** Merging and sorting the map outputs by key before they are passed to the `reduce()` method.

## Java is mandatory to write Mapreduce Jobs?
No, Java is not mandatory for writing MapReduce jobs. While the native API is in Java, Hadoop Streaming allows you to use any executable or script as your mapper and/or reducer. This means you can write your MapReduce logic in languages like Python, Perl, or C++.

## What methods can controle the Map And Reduce function’s output?
The output of the map and reduce functions can be controlled by using the `Context` object. The `context.write(key, value)` method is used to emit key-value pairs from both the Mapper and the Reducer. You can also control the output format by setting the `OutputFormat` class in the job configuration.

## What is the main difference between Mapper And Reducer?
The main difference between a Mapper and a Reducer is their role in the MapReduce workflow:

*   **Mapper:** The Mapper processes the input data and generates intermediate key-value pairs.
*   **Reducer:** The Reducer processes the intermediate key-value pairs and generates the final output.

## Why compute Nodes and the Storage Nodes are same?
In Hadoop, the compute nodes and the storage nodes are the same to maximize data locality. By processing the data on the same node where it is stored, Hadoop avoids the need to transfer large amounts of data over the network, which is a major bottleneck in distributed computing.

## What is difference between mapside join and reduce side join?
*   **Map-side join:** This is performed in the map phase and is suitable when one of the datasets is small enough to fit into memory. The smaller dataset is loaded into memory, and the join is performed as the larger dataset is streamed through the mappers.
*   **Reduce-side join:** This is performed in the reduce phase and is suitable for joining large datasets. The mappers tag the data with the source dataset, and the join is performed in the reducers after the data has been shuffled and sorted.

## What happen if number of Reducer is 0?
If the number of reducers is set to zero, the MapReduce job will be a map-only job. The output of the mappers will be written directly to HDFS, and there will be no reduce phase. This is useful for simple data transformation tasks that do not require aggregation.

## When we are goes to Combiner? Why it is Recommendable?
A Combiner is recommended when the operation being performed is both commutative and associative (e.g., sum or max). By performing a local aggregation on the map-side, a Combiner can significantly reduce the amount of data that needs to be shuffled across the network, leading to better performance.

## What is the main difference between Mapreduce Combiner and Reducer?
The main difference between a Combiner and a Reducer is that the Combiner is an optional, local optimization that runs on the same node as the Mapper, while the Reducer is a mandatory part of the MapReduce workflow (unless the number of reducers is set to zero) that runs on a separate node.

## What Is Partition?
A Partition is a logical division of the intermediate data from the Mappers. The Partitioner determines which partition each key-value pair belongs to, and thus which Reducer will process it.

## When we goes to Partition?
You would use a custom Partitioner when you need to control how the data is distributed among the Reducers. For example, you might want to send all the data for a particular key to the same Reducer to ensure that all the related data is processed together.

## What are the important steps when you are partitioning table?
The important steps when partitioning a table are:

1.  **Choose a partition key:** This is the column that will be used to determine the partition.
2.  **Implement a custom Partitioner:** This class will contain the logic for assigning a key to a partition.
3.  **Set the Partitioner in the job configuration:** This will tell the framework to use your custom Partitioner.

## Can you elaborate Mapreduce Job architecture?
The MapReduce job architecture consists of:

*   **Client:** Submits the MapReduce job.
*   **JobTracker:** Coordinates the job and manages the resources.
*   **TaskTrackers:** Execute the map and reduce tasks.
*   **HDFS:** Stores the input and output data.

## Why task Tracker launch child Jvm?
The TaskTracker launches a child JVM for each task to provide isolation. This ensures that any errors or failures in one task do not affect other tasks running on the same node. It also allows for better resource management, as each task runs in its own separate process.

## Why JobClient and Job Tracker submits job resources to file system?
The JobClient and JobTracker submit job resources (like the JAR file and configuration) to the file system so that they can be accessed by the TaskTrackers. This ensures that all the necessary files are available on the slave nodes where the tasks will be executed.

## How many Mappers and Reducers can run?
The number of Mappers is determined by the number of input splits. By default, this is one per HDFS block. The number of Reducers is configured by the user and can be set to any value, including zero.

## What is InputSplit?
An InputSplit is a logical representation of a chunk of the input data that will be processed by a single Mapper. It does not contain the data itself, but rather a reference to it. The size of the InputSplit is determined by the `InputFormat`.

## How to configure the split value?
The split value can be configured using the `mapred.min.split.size` and `mapred.max.split.size` properties in the `mapred-site.xml` file. You can also control the split size programmatically by implementing a custom `InputFormat`.

## How much ram required to process 64mb data?
The amount of RAM required to process 64 MB of data depends on the specific MapReduce job. However, a general rule of thumb is to have at least twice the block size in RAM available for each task. So, for a 64 MB block, you would want at least 128 MB of RAM.

## What is difference between block And split?
*   **Block:** A block is a physical division of the data stored in HDFS.
*   **Split:** A split is a logical division of the data that is processed by a single Mapper. While a split is often the same size as a block, it can be smaller or larger depending on the `InputFormat`.

## Why Hadoop Framework reads a file parallel why not sequential?
Hadoop reads files in parallel to achieve high throughput. By breaking a file into blocks and processing them concurrently on different nodes, Hadoop can process massive datasets much faster than if it were to read the file sequentially from a single node.

## If I am change block size from 64 to 128?
Changing the block size from 64 MB to 128 MB will reduce the number of blocks for a given file. This will, in turn, reduce the amount of metadata that the NameNode needs to store and may improve performance for very large files. However, it may also lead to less parallelism, as there will be fewer blocks to process concurrently.

## What is IsSplitable()?
`isSplitable()` is a method in the `InputFormat` class that determines whether a file can be split. If this method returns `false`, the entire file will be processed by a single Mapper. This is useful for compressed files or other file formats that cannot be arbitrarily split.

## How much Hadoop allows maximum block size and minimum block size?
Hadoop does not have a hard-coded maximum or minimum block size. However, the recommended block size is between 128 MB and 256 MB. A very small block size will increase the amount of metadata on the NameNode, while a very large block size may reduce parallelism.

## What are the Job Resource files?
The job resource files are the files that are needed to run a MapReduce job. This includes the job JAR file, the job configuration file, and any files that have been added to the Distributed Cache.

## What’s the Mapreduce Job consists?
A MapReduce job consists of:

*   The input data.
*   The Mapper class.
*   The Reducer class (optional).
*   The Partitioner class (optional).
*   The Combiner class (optional).
*   The job configuration.

## What is the data locality?
Data locality is the principle of moving the computation to the data, rather than the other way around. By processing the data on the same node where it is stored, Hadoop minimizes network traffic and improves the overall performance of MapReduce jobs.

## What is speculative execution?
Speculative execution is a feature in Hadoop where the JobTracker may run a backup copy of a task that is taking a long time to complete. This helps to avoid situations where a single slow node can delay the entire job. The first copy of the task to complete is used, and the other is killed.

## What is chain Mapper?
A Chain Mapper is a feature that allows you to chain multiple Mappers together in a single MapReduce job. The output of the first Mapper becomes the input of the second Mapper, and so on. This is useful for creating complex data processing pipelines.

## How to do value level comparison?
Value-level comparison can be done by implementing a custom `RawComparator` for the key. This allows you to control how the keys are sorted and grouped during the shuffle and sort phase.

## What is setup and clean up methods?
The `setup()` and `cleanup()` methods are part of the Mapper and Reducer APIs.

*   `setup()`: This method is called once at the beginning of a task.
*   `cleanup()`: This method is called once at the end of a task.

## How many slots allocate for each task?
Each task is allocated a certain number of slots on a TaskTracker. The number of slots is configurable and determines how many tasks can run concurrently on a single node.

## Why TaskTracker launch child Jvm to do a task? Why not use Existent Jvm?
The TaskTracker launches a child JVM for each task to provide isolation and prevent a single task from bringing down the entire TaskTracker. This also allows for better resource management and prevents tasks from interfering with each other.

## What main configuration parameters are specified in Mapreduce?
The main configuration parameters in a MapReduce job are:

*   The input and output paths.
*   The Mapper and Reducer classes.
*   The input and output formats.
*   The number of Reducers.

## What is identity Mapper?
An Identity Mapper is the default Mapper in Hadoop. It simply emits the input key-value pair as the output, without any transformation.

## What is RecordReader in a MapReduce?
A `RecordReader` is responsible for reading the data from an `InputSplit` and converting it into key-value pairs that can be processed by the Mapper.

## What is OutputCommitter?
The `OutputCommitter` is responsible for managing the output of a MapReduce job. It ensures that the output is written to a temporary location during the job and then moved to the final output directory upon successful completion. This provides an atomic commit mechanism for the job's output.

## What are the parameters of Mappers and Reducers?
The parameters for Mappers and Reducers are:

*   **Mapper:** `(KEYIN, VALUEIN, KEYOUT, VALUEOUT)`
*   **Reducer:** `(KEYIN, VALUEIN, KEYOUT, VALUEOUT)`

Where `KEYIN` and `VALUEIN` are the input key-value types, and `KEYOUT` and `VALUEOUT` are the output key-value types.

## Explain JobConf in Mapreduce?
`JobConf` is the primary interface for a user to describe a MapReduce job to the Hadoop framework. It is used to specify the job's configuration, including the Mapper, Reducer, input/output formats, and other parameters.

## Explain Job scheduling through Jobtracker?
The JobTracker schedules jobs by placing them in a queue and then assigning tasks to the TaskTrackers as slots become available. The scheduling policy can be configured using different schedulers, such as FIFO, Fair, or Capacity.

## What is SequenceFileInputFormat?
`SequenceFileInputFormat` is an `InputFormat` for reading sequence files. Sequence files are flat files consisting of binary key-value pairs. They are a good choice for intermediate data in a MapReduce workflow because they are compact and efficient to process.

## Explain how input and output data format of the Hadoop Framework?
The input and output data formats in Hadoop are specified using the `InputFormat` and `OutputFormat` classes. The default format is `TextInputFormat`, which reads and writes text files. However, Hadoop supports a variety of other formats, including `SequenceFileInputFormat` and `AvroInputFormat`.

## What are the restriction to the Key and Value Class ?
The key and value classes in Hadoop must implement the `Writable` interface for serialization and the `WritableComparable` interface for comparison.

## Explain the wordcount implementation via Hadoop Framework?
The WordCount implementation in Hadoop consists of:

*   **Mapper:** Reads the input text, tokenizes it into words, and emits a `(word, 1)` pair for each word.
*   **Reducer:** Receives the `(word, 1)` pairs, sums the counts for each word, and emits a `(word, total_count)` pair.

## How Mapper is instantiated in a running Job?
The Mapper is instantiated by the TaskTracker on a slave node. The TaskTracker creates a new JVM for each map task and then instantiates the Mapper class within that JVM.

## Which are the methods in the Mapper Interface?
The `Mapper` interface has three methods:

*   `setup()`: Called once at the beginning of the task.
*   `map()`: Called for each key-value pair in the input split.
*   `cleanup()`: Called once at the end of the task.

## What happens if You don't Override the Mapper methods and keep them as it is?
If you don't override the Mapper methods, the default `IdentityMapper` will be used. This Mapper simply emits the input key-value pairs as the output, without any transformation.

## What is the use of context Object?
The Context Object is a crucial component in Hadoop MapReduce that allows the Mapper and Reducer to interact with the rest of the Hadoop system. It provides access to configuration details, enables communication of progress, and allows for the emission of output key-value pairs. Essentially, it bridges the gap between the user's code and the Hadoop framework, providing the necessary context for the task to run correctly.

## How can you Add the arbitrary Key-value pairs in your Mapper?
In Hadoop, you can add arbitrary key-value pairs in the Mapper by using the `context.write(key, value)` method. This allows the Mapper to emit custom intermediate data that will be processed by the Reducer. The key and value must be serializable and implement the `WritableComparable` and `Writable` interfaces, respectively, to ensure they can be transmitted across the network and sorted efficiently.

## How Does Mapper's Run() Method Works?
The Mapper's `run()` method is the entry point for the map task. It first calls the `setup()` method for any necessary initializations. Then, it iterates through the input splits, calling the `map()` method for each key-value pair. Finally, it invokes the `cleanup()` method to perform any required cleanup operations, such as closing resources. This lifecycle ensures that the Mapper processes all its assigned data and manages its resources effectively.

## Which Object can be used to get the progress of a particular Job?
To get the progress of a particular job, you can use the `Job` object, which provides methods like `getStatus()` to retrieve the current state of the job. Additionally, the `Context` object within the Mapper and Reducer can be used to report progress and update counters, which can then be monitored through the JobTracker's web UI or command-line tools.

## What is next step after Mapper Or Maptask?
After the Mapper or Maptask completes, the next step is the **Shuffle and Sort** phase. During this stage, the intermediate key-value pairs generated by the Mapper are partitioned, transferred to the Reducers, and sorted by key. This ensures that each Reducer receives all values associated with the same key, preparing the data for the reduce phase.

## How can we control particular Key should go in a specific Reducer?
To control which key goes to a specific Reducer, you can implement a custom `Partitioner`. The Partitioner determines which partition a key-value pair belongs to, and since each partition is processed by a single Reducer, this allows for precise control over data distribution. By default, Hadoop uses a `HashPartitioner`, which distributes keys based on their hash code, but a custom implementation can enforce specific routing rules.

## What is the use of Combiner?
The Combiner is an optional optimization in MapReduce that runs on the Mapper nodes and performs a preliminary reduction of the intermediate data. It helps to reduce the amount of data that needs to be transferred over the network to the Reducers, which can significantly improve job performance. The Combiner's logic is often the same as the Reducer's, as it aggregates values for the same key before they are shuffled.

## How many Maps are there in a particular Job?
The number of maps in a particular job is determined by the number of input splits. Hadoop divides the input data into fixed-size splits, and each split is processed by a single map task. Therefore, the number of maps is equal to the number of splits, which can be configured based on the data size and the desired level of parallelism.

## What is the Reducer used for?
The Reducer is used to process the intermediate key-value pairs generated by the Mapper. It aggregates, summarizes, or transforms the data by processing all values associated with the same key. The Reducer's output is the final result of the MapReduce job, which is then written to the Hadoop Distributed File System (HDFS).

## Explain the core methods of the Reducer?
The core methods of the Reducer are:
1.  **`setup()`**: Called once at the beginning of the task for initialization.
2.  **`reduce()`**: Called for each unique key and its associated list of values.
3.  **`cleanup()`**: Called once at the end of the task for resource cleanup.

## What are the primary phases of the Reducer?
The primary phases of the Reducer are:
1.  **Shuffle**: The Reducer copies the sorted intermediate data from the Mapper nodes.
2.  **Sort**: The framework merges and sorts the data by key.
3.  **Reduce**: The `reduce()` method is called for each key to process its associated values.

## Explain the Shuffle?
The Shuffle phase is the process of transferring the intermediate data from the Mappers to the Reducers. It involves partitioning the data, sorting it by key, and then sending it to the appropriate Reducer. This ensures that all values for a given key are grouped together before the reduce phase begins.

## Explain the Reducer's sort phase?
The Reducer's sort phase occurs after the shuffle phase and involves merging the intermediate data from multiple Mappers and sorting it by key. This ensures that the `reduce()` method receives all values for a single key in a single call, which is essential for correct data aggregation.

## Explain the Reducer's reduce phase?
The Reducer's reduce phase is where the actual data processing occurs. The `reduce()` method is called for each unique key, along with an iterator for all its associated values. The method then performs the desired aggregation or transformation and writes the final output to HDFS.

## How many Reducers should be configured?
The optimal number of Reducers depends on the cluster's capacity and the nature of the job. A common recommendation is to set it to a value slightly less than the number of available Reducer slots in the cluster, such as 0.95 times the total slots. This allows for better load balancing and fault tolerance.

## It can be possible that a Job has 0 Reducers?
Yes, it is possible for a job to have zero Reducers. In this case, the job is a map-only job, and the output of the Mappers is written directly to HDFS without any reduction.

## What happens if number of Reducers are 0?
If the number of Reducers is set to zero, the MapReduce job will not have a reduce phase. The output from the Mappers will be written directly to the output directory in HDFS, with each Mapper producing its own output file. This is useful for tasks like data filtering or transformation that do not require aggregation.

## How many instances of Jobtracker can run on a Hadoop Cluster?
Only one instance of the JobTracker can run on a Hadoop cluster. It acts as the master node for MapReduce jobs, coordinating all the tasks and managing the resources of the cluster.

## What is the Jobtracker and what it performs in a Hadoop Cluster?
The JobTracker is the master daemon for MapReduce jobs in a Hadoop cluster. It is responsible for accepting job submissions from clients, breaking them into tasks, scheduling the tasks on TaskTrackers, and monitoring their progress. It also manages the overall resources of the cluster and ensures fault tolerance by re-scheduling failed tasks.

## How a task is scheduled by a Jobtracker?
A task is scheduled by the JobTracker based on the availability of TaskTracker slots. When a TaskTracker sends a heartbeat to the JobTracker, it indicates its availability. The JobTracker then assigns a task to it from the queue of pending tasks, prioritizing tasks from jobs with higher priority.

## How many instances of Tasktracker run on a Hadoop Cluster?
One instance of the TaskTracker runs on each slave node in a Hadoop cluster. The TaskTracker is responsible for executing the map and reduce tasks assigned to it by the JobTracker and reporting their status back to the master.

## How many maximum Jvm can run on a Slave Node?
The maximum number of JVMs that can run on a slave node is determined by the number of map and reduce slots configured for the TaskTracker. Each task runs in its own JVM, so the total number of JVMs is the sum of the map and reduce slots.

## What is Nas?
NAS stands for Network Attached Storage. It is a dedicated file storage device that can be accessed over a network. In the context of Hadoop, NAS can be used for storing input and output data, but it is generally not recommended for the intermediate data due to its lower performance compared to HDFS.

## How Hdfs differs with Nfs?
HDFS (Hadoop Distributed File System) differs from NFS (Network File System) in several key ways. HDFS is designed for large-scale, distributed data processing and provides high throughput for sequential reads, while NFS is a more general-purpose file system. HDFS also has built-in fault tolerance through data replication, which is not a standard feature of NFS.

## How does a NameNode handle the failure of the Data Nodes?
The NameNode handles the failure of DataNodes by detecting when a DataNode stops sending heartbeats. Once a DataNode is marked as failed, the NameNode initiates the replication of the blocks that were stored on that node to other healthy DataNodes to maintain the desired replication factor.

## Can Reducer talk with each other?
No, Reducers cannot talk to each other. Each Reducer works in isolation on its own partition of the data. This design ensures that the reduce phase can be parallelized, as there are no dependencies between the Reducers.

## Where the Mapper's intermediate data will be stored?
The Mapper's intermediate data is stored on the local disk of the node where the map task is running. This data is temporary and is deleted once the job is complete. Storing it locally avoids the overhead of writing to HDFS and allows for faster access during the shuffle phase.

## What is the Hadoop Mapreduce api contract for a Key and Value Class?
The Hadoop MapReduce API contract for a Key and Value class is that the Key class must implement the `WritableComparable` interface, while the Value class must implement the `Writable` interface. This ensures that the keys can be sorted and compared, and both keys and values can be serialized and deserialized for network transmission.

## What is a IdentityMapper and IdentityReducer in Mapreduce?
IdentityMapper and IdentityReducer are default implementations provided by Hadoop. The IdentityMapper simply emits its input key-value pairs without any transformation. The IdentityReducer writes all the values for a given key to the output. They are useful when you only need to perform a sort or when the default behavior is sufficient for your needs.

## What is the meaning of Speculative Execution in Hadoop?
Speculative Execution is a feature in Hadoop where the JobTracker may schedule a duplicate copy of a slow-running task on another node. Whichever copy of the task finishes first is accepted, and the other is killed. This helps to mitigate the impact of slow nodes or network issues and can improve overall job completion time.

## How Hdfs is different from traditional File Systems?
HDFS is different from traditional file systems in that it is designed for storing and processing very large datasets across a distributed cluster of commodity hardware. It provides high throughput for sequential data access and is fault-tolerant by default through data replication. Traditional file systems, on the other hand, are typically designed for general-purpose use on a single machine.

## What is Hdfs block size and how is it different from Traditional File System block size?
The HDFS block size is typically 128 MB or 256 MB, which is much larger than the block size of traditional file systems (e.g., 4 KB). This large block size allows HDFS to minimize the metadata overhead and reduce the number of disk seeks required to read a file, which improves performance for large files.

## What is a NameNode and how many instances of NameNode run on a Hadoop Cluster?
The NameNode is the master node in an HDFS cluster. It is responsible for managing the file system namespace, maintaining the metadata for all files and directories, and regulating access to files by clients. There is only one active NameNode in a standard Hadoop cluster, although a standby NameNode can be configured for high availability.

## How the client communicates with Hdfs?
The client communicates with HDFS by first contacting the NameNode to get the locations of the data blocks for a file. Once the client has the block locations, it communicates directly with the DataNodes to read or write the data. This design allows for high-performance data access by distributing the load across the cluster.

## How the Hdfs blocks are replicated?
HDFS blocks are replicated across multiple DataNodes to ensure fault tolerance. When a client writes a block, it is first written to one DataNode, which then forwards it to a second DataNode, and so on, until the desired replication factor (typically 3) is reached. This ensures that the data is available even if a DataNode fails.

## Can you give some examples of Big Data?
Examples of Big Data include social media data from platforms like Facebook and Twitter, sensor data from IoT devices, financial trading data, and scientific research data from fields like genomics and astronomy. These datasets are characterized by their large volume, high velocity, and wide variety.

## What is the basic difference between traditional Rdbms and Hadoop?
The basic difference between traditional RDBMS and Hadoop is that RDBMS is designed for structured data and is optimized for online transaction processing (OLTP), while Hadoop is designed for both structured and unstructured data and is optimized for large-scale batch processing and data analysis.

## What is structured and unstructured Data?
Structured data is data that has a well-defined format and schema, such as data in a relational database. Unstructured data, on the other hand, does not have a predefined data model and can include things like text documents, images, and videos. Hadoop is capable of processing both types of data.

## Since the data is replicated thrice in Hdfs so does it mean that any calculation done on One Node will also be replicated on the other Two?
No, the calculation is not replicated. Data replication in HDFS is for fault tolerance and data availability. The computation is performed only on the data that is local to the node where the task is running. This is known as data locality, and it is a key principle of Hadoop that helps to minimize network traffic and improve performance.

## What is throughput and how does Hdfs get a good throughput?
Throughput is the amount of data that can be processed in a given amount of time. HDFS achieves good throughput by allowing for parallel processing of data across multiple nodes in a cluster. Its large block size and focus on sequential reads also contribute to high throughput for large-scale data processing tasks.

## What is streaming access?
Streaming access is a data processing pattern where data is read sequentially from start to finish. HDFS is optimized for this pattern, making it highly efficient for processing large files, as it allows for high throughput of data.

## What is a Commodity Hardware so does Commodity Hardware include Ram?
Commodity hardware refers to inexpensive, widely available, off-the-shelf computer hardware. It is not custom-built or high-end. Yes, it includes standard components like RAM, CPU, and disk drives.

## Is NameNode also a Commodity?
While DataNodes are typically commodity hardware, the NameNode is usually run on higher-grade, more reliable hardware. This is because the NameNode is a single point of failure in a standard Hadoop setup and it holds all the filesystem metadata in memory, requiring more RAM and processing power.

## What is a Metadata?
In the context of HDFS, metadata is data about the data. It includes information like the file system namespace (directory structure), file permissions, and the mapping of files to their constituent blocks and the locations of those blocks on DataNodes.

## What is a Daemon?
A daemon is a background process that is not under the direct control of a user. In Hadoop, daemons are core components that run continuously, such as the NameNode, DataNode, ResourceManager, and NodeManager, which manage the HDFS and YARN frameworks.

## What is a Heartbeat in Hdfs?
A heartbeat is a periodic signal sent from a DataNode to the NameNode (and from a NodeManager to the ResourceManager). It informs the master node that the slave node is alive and functioning correctly. It also carries information about the slave nodes status, such as storage utilization.

## How indexing is done in Hdfs?
HDFS itself does not provide traditional indexing like a relational database. The NameNode stores all the filesystem metadata, including the block locations for every file, in its memory. This allows for very fast lookups of file locations without needing a separate index.

## If a Data Node is full how it's identified?
A DataNode continuously reports its storage capacity, usage, and other health metrics to the NameNode with each heartbeat. If a DataNode is nearing its capacity, the NameNodes scheduler will see this and avoid assigning new data blocks to it for writing.

## If DataNodes increase then do we need to upgrade NameNode?
Yes, as the number of DataNodes, files, and blocks in the cluster increases, the amount of metadata the NameNode must manage also grows. This requires more RAM and CPU resources on the NameNode. Therefore, the NameNode hardware often needs to be upgraded to keep up with cluster growth.

## Are Job Tracker and Task Trackers present in separate machines?
This question refers to Hadoop 1.x. In that architecture, the JobTracker typically ran on the master node (often co-located with the NameNode), while TaskTrackers ran on the slave nodes (co-located with DataNodes). So, they were on separate machines in a multi-node cluster.

## On what basis NameNode will decide which DataNode to write on?
The NameNode uses a rack-aware replica placement policy. The goal is to balance fault tolerance and network bandwidth. By default, it places the first replica on the local node (if the writer is on a DataNode), the second on a different node in the same rack, and the third on a node in a different rack.

## Who is a user in Hdfs?
In HDFS, a user or client is any application or process that interacts with the HDFS cluster to perform file operations like reading, writing, or deleting data. It communicates with the NameNode for metadata and directly with DataNodes for data transfer.

## Is client the end user in Hdfs?
The client is the software component (e.g., a Java application using the HDFS API) that interacts with the HDFS cluster. The end-user is typically a person or another system that uses this client application. So, the client acts as an intermediary for the end-user.

## What is the Communication Channel between client and NameNode/DataNode?
The communication is done over TCP/IP. The client initiates a connection to the NameNode to get metadata (file block locations). After that, the client communicates directly with the DataNodes to read or write the actual file data.

## What is a Rack?
A rack is a physical frame that houses multiple servers (nodes). In the context of Hadoop, nodes within the same rack are connected to the same network switch, meaning communication between them is much faster than communication between nodes in different racks.

## On what basis Data will be stored on a Rack?
Data placement is based on the rack-aware policy. The goal is to ensure that if an entire rack fails (e.g., due to a power outage or switch failure), a copy of the data will still be available on another rack, thus ensuring high availability.

## Do we need to place 2nd and 3rd Data in Rack 2 only?
No. The standard policy is to place the second replica on a *different* node within the *same* rack as the first, and the third replica on a node in a *different* rack. This protects against both node failure and rack failure.

## What if Rack 2 and DataNode fails?
If a DataNode fails, the NameNode detects it via missed heartbeats and re-replicates its blocks. If an entire rack fails, the NameNode detects all DataNodes in that rack have failed and initiates re-replication for all the blocks that had replicas on that rack to maintain the desired replication factor across the remaining racks.

## What is the difference between Gen1 and Gen2 Hadoop with regards to the NameNode?
Hadoop 1 (Gen1) had a single NameNode, which was a single point of failure. Hadoop 2 (Gen2) introduced NameNode High Availability (HA), which allows for an Active/Standby pair of NameNodes. If the Active NameNode fails, the Standby can take over quickly, eliminating the single point of failure.

## Do we require two servers for the NameNode and the DataNodes?
In a production environment, yes. The NameNode (or two for High Availability) runs on a dedicated master server. The DataNodes run on a separate set of slave servers. This separation is crucial for performance and scalability.

## Why are the number of splits equal to the number of Maps?
The number of map tasks is determined by the number of input splits. Each map task processes exactly one split. An input split is a chunk of the input data, and by default, its size is the same as the HDFS block size.

## Is a Job split into maps?
A MapReduce job is not split into maps. Rather, the *input data* for the job is split into chunks called InputSplits. A map task is then created for each of these splits. The job itself is a single unit of work that consists of multiple map and reduce tasks.

## Which are the two types of writes in Hdfs?
HDFS has one primary method for writing files, which follows a write pipeline. The client writes a block to the first DataNode, which then forwards it to the second, which forwards it to the third. An acknowledgment flows back through the pipeline only after all replicas are written.

## Why reading is done in parallel and writing is not in Hdfs?
Reading is parallel because different blocks of a file are stored on different DataNodes. A client can read multiple blocks from multiple DataNodes simultaneously. Writing to a single file is sequential to ensure data consistency; the blocks are written one after another in a pipeline.

## Can Hadoop be compared to Nosql Database like Cassandra?
They are different tools for different purposes. Hadoop is a distributed file system (HDFS) and a batch processing framework (MapReduce/Spark), ideal for analytical queries on massive, static datasets. Cassandra is a NoSQL database designed for high-throughput, low-latency online transaction processing (OLTP) with real-time read/write access.

## How JobTracker schedules a task?
In Hadoop 1.x, the JobTracker receives a job submission. It gets the locations of the input data blocks from the NameNode. It then tries to schedule map tasks on TaskTrackers that are running on the same DataNodes where the data resides (data locality principle) to minimize network traffic.

## What is a Task Tracker in Hadoop and how many instances of Task Tracker run on a Hadoop Cluster?
In Hadoop 1.x, a TaskTracker is a daemon that runs on each slave node in the cluster. It is responsible for running the map and reduce tasks assigned by the JobTracker. There is exactly one TaskTracker process running on each slave node.

## What is a task instance in Hadoop and where does it run?
A task instance is the actual execution of a map or a reduce task. It runs as a separate Java Virtual Machine (JVM) process on one of the slave nodes. This process is launched and managed by the TaskTracker (in Hadoop 1) or the NodeManager (in YARN/Hadoop 2+).

## What is configuration of a typical Slave Node on Hadoop Cluster and how many Jvms run on a Slave Node?
A typical slave node runs a DataNode daemon and a NodeManager daemon. The NodeManager launches application tasks (like mappers and reducers) inside containers. Each container runs in its own JVM. Therefore, multiple JVMs can be running on a slave node simultaneously: one for the DataNode, one for the NodeManager, and one for each active task container.

## How NameNode handles DataNode failures?
The NameNode detects DataNode failures when it stops receiving heartbeats from them. Once a DataNode is marked as dead, the NameNode identifies all the data blocks that were stored on that node and initiates the process of re-replicating them on other healthy DataNodes to maintain the configured replication factor.

## Does Mapreduce programming model provide a way for Reducers to communicate with each other and in a Mapreduce Job can a Reducer communicate with another Reducer?
No, the MapReduce programming model does not allow for communication between reducers. Each reducer works in isolation on its own partition of the intermediate key-value pairs. This design choice ensures that the reduce phase can be parallelized and is not dependent on the state of other reducers.

## Can I set the number of Reducers to Zero?
Yes, you can set the number of reducers to zero. This results in a map-only job. In this case, the output of the map tasks is written directly to the final output location in HDFS, bypassing the sort, shuffle, and reduce phases entirely. This is useful for tasks like data filtering or transformation.

## Where is the Mapper Output intermediate Kay-value data stored?
The intermediate key-value data generated by a mapper is stored on the local disk of the slave node where the map task is running. It is not written to HDFS. This local storage is temporary and is cleaned up after the job is complete.

## If Reducers do not start before all Mappers finish then why does the progress on Mapreduce Job shows something like Map 50 percents Reduce 10 percents and why Reducers progress percentage is displayed when Mapper is not Finished yet?
This is because the Reduce phase has three sub-phases: copy, sort, and reduce. The copy phase, where the reducers start copying the intermediate key-value pairs from the mappers, can begin as soon as the first mapper finishes. The progress bar shows the percentage of map outputs that have been copied. The actual reduce function, however, will not start until all mappers have completed.

## Explain in brief the three Modes in which Hadoop can be run?
Hadoop can be run in three modes:
*   **Standalone (or Local) Mode:** This is the default mode. It runs on a single machine without any daemons and is primarily used for debugging purposes. It uses the local file system.
*   **Pseudo-Distributed Mode:** Hadoop runs on a single machine, but each Hadoop daemon (NameNode, DataNode, JobTracker, TaskTracker) runs in a separate Java process. This mode is used for testing and development.
*   **Fully-Distributed Mode:** Hadoop runs on a cluster of machines. This is the production mode of Hadoop.

## Explain what are the features of Standalone local Mode?
Standalone mode features include:
*   No Hadoop daemons are run.
*   It uses the local file system for input and output.
*   It's the fastest mode for simple tests.
*   It's primarily used for debugging MapReduce applications.
*   No special configuration is needed.

## What are the features of fully distributed mode?
Fully distributed mode features include:
*   Data is distributed and processed across a cluster of machines.
*   It provides high availability and fault tolerance.
*   It's highly scalable, allowing for the addition of more nodes to the cluster.
*   It's the mode used for production environments to handle large datasets.

## Explain what are the main features Of pseudo mode?
Pseudo-distributed mode features include:
*   All Hadoop daemons run on a single node, simulating a multi-node cluster.
*   It uses HDFS for storage.
*   It's useful for development and testing of Hadoop applications before deploying to a full cluster.
*   Configuration files (core-site.xml, hdfs-site.xml, mapred-site.xml) need to be set up.

## What are the port numbers of NameNode and JobTracker and TaskTracker?
In older versions of Hadoop (1.x):
*   **NameNode:** Default port is 50070 (for the web UI) and 8020 or 9000 (for the filesystem metadata operations).
*   **JobTracker:** Default port is 50030 (for the web UI) and 8021 (for RPC).
*   **TaskTracker:** No specific public port, it communicates with the JobTracker.
In Hadoop 2.x (YARN), JobTracker and TaskTracker are replaced by ResourceManager and NodeManager.
*   **ResourceManager:** 8088 (web UI)
*   **NodeManager:** 8042 (web UI)

## Tell us what is a spill factor with respect to the ram?
The spill factor refers to the threshold at which the in-memory buffer used by a mapper for intermediate key-value pairs is written (spilled) to disk. By default, this is controlled by the `io.sort.spill.percent` property, which is set to 0.80 (or 80%). When the buffer reaches this percentage of its capacity, its contents are spilled to a file on the local disk.

## Is fs.mapr working for a single directory?
`fs.mapr.working.dir` is a property specific to the MapR distribution of Hadoop. It specifies the working directory for MapR-FS. It can be set to a single directory. In standard Apache Hadoop, the equivalent property is `fs.defaultFS` or `fs.default.name`.

## Which are the three main Hdfs-site.xml properties?
Three important properties in `hdfs-site.xml` are:
*   `dfs.replication`: Sets the default block replication factor for files stored in HDFS. The default is 3.
*   `dfs.namenode.name.dir`: Specifies the path on the local filesystem where the NameNode stores the namespace and transaction logs.
*   `dfs.datanode.data.dir`: Specifies the path on the local filesystem where the DataNode stores its blocks.

## How can I restart NameNode?
You can restart the NameNode using the scripts provided in the Hadoop `sbin` directory.
*   To stop the NameNode: `./sbin/hadoop-daemon.sh stop namenode`
*   To start the NameNode: `./sbin/hadoop-daemon.sh start namenode`
Alternatively, you can use `./sbin/stop-dfs.sh` and `./sbin/start-dfs.sh` to stop and start all HDFS daemons.

## How can we check whether Namenode is working or not?
You can check the status of the NameNode in a few ways:
*   Use the `jps` command on the NameNode machine. You should see a 'NameNode' process listed.
*   Access the NameNode's web UI by navigating to `http://<namenode-hostname>:50070` in a web browser.
*   Run an HDFS command like `hdfs dfs -ls /`. If it executes successfully, the NameNode is running.

## At times you get a connection refused Java Exception when you run the file system check command Hadoop fsck?
A 'Connection refused' exception when running `hdfs fsck` usually indicates that the NameNode is not running or is not accessible from where you are running the command. Check if the NameNode process is active and that there are no firewall rules blocking the connection to the NameNode's RPC port (default 8020 or 9000). Also, verify the NameNode address in your `core-site.xml`.

## What is the use of the command Mapred.job.tracker?
`mapred.job.tracker` is not a command, but a configuration property in `mapred-site.xml` (in Hadoop 1.x). It specifies the address and port of the JobTracker. MapReduce clients submit their jobs to this address. In YARN (Hadoop 2.x+), this property is deprecated and replaced by `yarn.resourcemanager.address`.

## What does etc/init.d do?
The `/etc/init.d` directory is a standard directory on many Unix-like systems that contains startup scripts for various services or daemons. For Hadoop, you might find scripts here to start and stop Hadoop daemons (like `hadoop-namenode`, `hadoop-datanode`) as system services, allowing them to be managed with commands like `service hadoop-namenode start`.

## How can we look for the Namenode in the browser?
You can access the NameNode's web interface by opening a web browser and navigating to `http://<namenode-hostname>:50070`, where `<namenode-hostname>` is the hostname or IP address of the machine running the NameNode.

## What do masters and slaves consist of?
In a typical Hadoop 1.x cluster:
*   **Masters:** Consist of the NameNode (manages the file system namespace) and the JobTracker (schedules MapReduce jobs). A Secondary NameNode is also usually run on a master node.
*   **Slaves:** Consist of DataNodes (store data blocks) and TaskTrackers (execute MapReduce tasks).
In Hadoop 2.x (YARN):
*   **Masters:** ResourceManager and NameNode.
*   **Slaves:** NodeManager and DataNode.

## What is the function Of Hadoop-env.sh and where is it present?
The `hadoop-env.sh` file is a script that sets up the environment variables for Hadoop. It is located in the `etc/hadoop` or `conf` directory of your Hadoop installation. Its primary function is to specify environment variables like `JAVA_HOME`, heap size options for Hadoop daemons, and other runtime settings.

## Can we have multiple entries in the master files?
The `masters` file is used to specify the Secondary NameNode. It should contain only one hostname. Having multiple entries would be incorrect. The `slaves` file, on the other hand, lists all the slave nodes (DataNodes/NodeManagers) and will contain multiple entries in a multi-node cluster.

## In Hadoop_pid_dir and what does pid stands for?
`PID` stands for **Process ID**. The `HADOOP_PID_DIR` is an environment variable that specifies the directory where Hadoop daemons store their process ID files. These `.pid` files contain the process ID of the running daemon, which is used by the stop scripts to identify and terminate the correct process.

## What does Hadoop-metrics and properties file do?
The `hadoop-metrics.properties` file (in Hadoop 1.x) and `hadoop-metrics2.properties` (in Hadoop 2.x) are used to configure the Hadoop metrics system. This system allows you to collect and report various metrics about the state and performance of Hadoop daemons (e.g., HDFS capacity, memory usage, number of active jobs). You can configure different 'sinks' to send these metrics to, such as files, Ganglia, or other monitoring systems.

## What are the network requirements for hadoop?
Key network requirements for Hadoop include:
*   **Passwordless SSH:** Required for the master nodes to remotely start, stop, and manage the slave daemons.
*   **High Bandwidth:** A high-speed, low-latency network is crucial, especially for the data-intensive shuffle and sort phase between mappers and reducers. A full bisection bandwidth network is ideal.
*   **DNS Resolution:** All nodes in the cluster must be able to resolve each other's hostnames.
*   **Firewall Configuration:** Firewalls must be configured to allow traffic on the ports used by Hadoop daemons.

## Why do we need a password-less ssh in fully distributed environment?
Passwordless SSH is required so that the master node(s) can seamlessly and automatically start, stop, and manage the Hadoop daemons (DataNode, NodeManager) on all the slave nodes without requiring a password for each connection. This is essential for the startup scripts (`start-dfs.sh`, `start-yarn.sh`) and for overall cluster management.

## What will happen if a NameNode has no data?
If a NameNode has no data, it simply means the HDFS cluster is empty. This is the state of a newly formatted HDFS. The cluster is fully functional and ready to store data. It doesn't indicate an error.

## What happens to job tracker when NameNode is down?
If the NameNode is down, the JobTracker (or ResourceManager in YARN) will not be able to function correctly. The JobTracker needs to interact with the NameNode to access job-related files (like JARs, configuration, and split information) stored in HDFS. Any new job submissions will fail, and running jobs that need to access HDFS will also fail. The entire Hadoop cluster becomes non-operational.

## Explain what do you mean by formatting of the Dfs?
Formatting the DFS (Distributed File System), specifically HDFS, is an initialization process. When you run the command `hdfs namenode -format`, it creates a new, empty filesystem. This involves creating the storage directories for the NameNode (specified in `dfs.namenode.name.dir`), generating a new namespace ID for the filesystem, and initializing the metadata structures (the fsimage file). This is a destructive operation that should only be done once, before the cluster is used for the first time.

## We use Unix variants for hadoop and can we use Microsoft Windows for the same?
Yes, Hadoop can be run on Microsoft Windows, but it's not the recommended or most common platform for production environments. While Apache provides Windows binaries, setting it up can be more complex due to differences in shell scripts and file permissions. Linux/Unix variants are the standard and most well-supported platforms for running Hadoop clusters.

## Which one decides the input split hdfs client or NameNode?
The **HDFS client** (specifically, the `InputFormat` class being used by the MapReduce job) decides how to create the input splits. The client queries the NameNode to get information about the file's block locations. Using this information, the `InputFormat` logic computes the splits, trying to align them with block boundaries to achieve data locality. The NameNode provides the data location information, but the client makes the final decision on the splits.

## Can you tell me if we can create a hadoop cluster from scratch?
Yes, absolutely. You can build a Hadoop cluster from scratch by installing the Java runtime on a set of commodity servers, downloading the Apache Hadoop distribution, configuring the Hadoop XML files (`core-site.xml`, `hdfs-site.xml`, `yarn-site.xml`, etc.) to define the master and slave nodes, setting up passwordless SSH between the nodes, formatting the HDFS, and then starting the Hadoop daemons.

## Explain the significance of ssh and what is the port on which port does ssh work and why do we need password in ssh local host?
SSH (Secure Shell) is significant because it provides a secure, encrypted channel for communication and remote command execution between nodes in the cluster. Hadoop's control scripts use SSH to start and stop daemons on slave nodes. SSH works on the standard **port 22**. You need a password (or preferably, a passwordless setup using public/private key pairs) for `ssh localhost` to allow the master daemons (e.g., NameNode) to manage other daemons (e.g., DataNode) even when they are running on the same physical machine, which is the case in a pseudo-distributed setup.

## What is ssh and explain in detail about ssh communication between masters and the slaves?
SSH, or Secure Shell, is a cryptographic network protocol for operating network services securely over an unsecured network. In Hadoop, the master node (running NameNode/ResourceManager) acts as an SSH client to connect to the slave nodes (running DataNode/NodeManager), which act as SSH servers. This communication is used by Hadoop's startup and shutdown scripts (`start-dfs.sh`, `stop-yarn.sh`, etc.). The master iterates through the list of hosts in the `slaves` file and executes remote shell commands (e.g., `hadoop-daemon.sh start datanode`) on each slave to manage its daemons. To make this process automated and non-interactive, passwordless SSH is configured using a public/private key pair. The master's public key is placed in the `authorized_keys` file on each slave, allowing it to connect without a password prompt.

## Can You Tell Is What Will Happen To A NameNode and When Job Tracker Is Not Up And Running?
The NameNode's operation is independent of the JobTracker (or ResourceManager). If the JobTracker is down, the HDFS part of the cluster will remain fully functional. You can still perform all HDFS operations like reading, writing, and deleting files. However, you will not be able to submit or run any MapReduce (or YARN) jobs, as there is no service to manage and schedule them. The NameNode itself will be unaffected.
