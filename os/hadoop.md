# Hadoop Ecosystem

## Introduction

- Hadoop or Hadoop Ecosystem contains a collection of open-source softwares managed through the Apache Software Foundation
- These softwares are designated to work on a distributed system for handling big data.
- Natively written in Java
- A distributed system is consisted of computer clusters
  - It offers the following two functionality:
    - Distributed Storage
    - Distributed Processing
- History
  - The distributed system is originated from the Google's papers in 2003-2004.
    - Google File System(GFS) enables distributed storage
    - MapReduce enables distributed processing
  - `Yahoo!` started to build search engine based on the distributed concept at the same time.
  - The Co-founder, Doug Cutting, who was working at `Yahoo!` at the time, named it after his son's toy elephant

## Components

#### Hadoop Distributed Filesystem (HDFS)

- The Hadopp version of `GFS`.
- It allows hard drives across the computer clusters works as one filesystem.
- It retains redundent copys of data across hard drives.
- It devides large files into 128 MB blocks.
  - One block for anything smaller than 128 MB
  - The blocks can be ready for parallel processing
- Data is stored across multiple data nodes.
- Name node records the location of all the blocks.
- Name node keep a record of changes made to all blocks in an edit log.
- Client side is the client node that will access name node every time before read and write.
- When client node write block to name node. Name node communicate with other name nodes to duplicate files for redundancy,and send acknowledgment to client node after. Client node will inform name node the process is completed
- Name node can't be the single point of failure, there are serveral solutions:
  - Write to local storage and backup metadata, It will have downtime
  - Secondary Namenode - Maintain a merged copy of edit log, It will have downtime
  - Running two name node, a stand by name node and the active name node will share a common edit log in an external storage
    - Zookeeper tracks and determines the active name node
    - It is important to make sure only one name node is active at a time.
- HDFS Federation allows multiple name node to be responsible for a specific namespace volume. This will split or expand one name node into a group of name nodes.
- There are several ways to use to the HDFS:
  - UI Consoles(Ambari)
  - Command Line Interface
    - `ssh` connection to the hadoop server and use `hadoop fs` command
      - Run `hadoop fs` to list all the commands available
  - HTTP/HDFS Proxies
  - Java Interface
  - NFS Gateway

#### MapReduce

- It is a programming model that will process data in one of the two ways:
  - Mappers - Transform data in parallel for distribution across computer clusters
    - Mappers find the valuable data for a certain task then map them into a dictionary of key and value pairs.
    - It will then group all values with the same key and sort the key automatically(merge sort across running instances).
  - Reducers - Aggregate data together
    - It will run once for each key provided by the Mapper and provide the designated output
      - The keys are not necessarily from the same instance since it has been sorted across all instances.
- It runs on worker nodes that managed by the node manager.
  - One node can run one or more map/reduce tasks.
  - All of these tasks acquire data from HDFS.
- There is one node that is called MapReduce Application Manager, it managers all other nodes and receive task from YARN
  - This node also has a node manager
  - It can relocate or restarted failed worker nodes.
  - When Application Manager fails, YARN will restart it.
- Natively jobs can be written in Java
- It supports other language using shell steaming with `stdin` and `stdout`.
  - For `python` job for example, use:
    - `python job.py <data>` to test the job locally.
    - `python job.py -r hadoop <data>` to run the job using hadoop.
      - `<data>` should be an HDFS path like `hdfs://<path>.`
      - if using local file it will be copied to HDFS for processing.
      - `--hadoop-streaming-jar` needs to be specified for some platform.

#### Yet Another Resource Negotiator (YARN)

- It manages computer cluster resources
- It runs on HDFS
- It will assign tasks to the node that is closet to the data source.
- It can restart fails clusters.
- A hot standby resources manager can be created and monitored by zookeeper, in case the YARN fails.

#### MESOS

- It is a resource negotiator that can be an alternative for `YARN`
- It runs on HDFS
- It can even work with YARN

#### Spark

- It runs on `YARN` or `MESOS`
- It is much faster than `MapReduce`
- It supports `Scala`, `Python` and `Java`
  - `Scala` is the recommanded language for Spark
- It supports SQL queries, machine learning, and realtime streaming data.

#### TEZ

- It is similar to `Spark`
- It runs on `YARN`
- It is another alternative to `MapReduce`

#### Pig

- It runs on MapReduce.
- It allows queries using SQL-like scripting language called Pig Latin.
- It can runs on TEZ and complete MapRuduce jobs faster.
- Pig Latin enables user defined functions.
- Grunt is a Pig command line tool that can run script one line at a time.
  - It can also run an entire script file.

#### Hive

- It allows queries using SQL language.
- It runs on `MapReduce` or `TEZ`
  - It works faster with `TEZ`

#### HBASE

- It adds the functionality of a NoSQL database to the existing clusters.
- It allows other transactional platform to access data in the NoSQL manner.
- It runs directly on the Filesystem.

### Add-ons Tools

#### Apache Storm

- It is used to process streaming data.

#### oozie

- It manages schedule tasks.

#### Zookeeper

- It monitors clusters and services.

#### Sqoop

- It is a data ingestion tool that connects the Hadoop Filesystem with external SQL database.

#### Flume

- It is a data ingestion tool that transports web logs into the Hadoop Filesystem
- Realtime log data can then be processed by Spark Streaming or Apache Storm.

#### Kafka

- It is a general purpose data ingestion tool that collects data from other clusters.

#### Apache Drill

- It allows queries on both SQL and NoSQL database at the same time.

#### Apache Phoenix

- It is similar to Apache Drill.
- It provides ACID guarantees and supports OLTP for NoSQL database, hence minimize the performance difference between SQL and NoSQL data.

#### Presto

- A query tool which is similar to Apache Drill.

#### Apache Zeppelin

- A query tool which is similar to Apache Drill.
- It provices a notebook style UI.

#### Hue

- A query tool that work well with Hive and HBase.

#### Apache Ambari

- It is a high level frontend console that controls every through a webpage.
  - It is used by Hadoop distributions like `Hortonworks`
- Accessed by using `127.0.0.1:8080` in browser
- It can install services using the left panel.
- It can change services config using UI and even the config files.
- There are sevaral tab on the Navi bar
  - Services - Same as the left panel in Dashboard.
  - Host - It enables the admin to start/stop services running on each host.
  - Alert - controls alerts and email notifications.
- Admin account enables the control of cluster's services
  - To enable admin account `ssh` to the hosting server and run `ambari-admin-password-rest`
- The Grid Icon provide access to views:
  - File View is for browsering the HDFS.
  - Hive View is for executing SQL querries through Hive.
  - Pig View is for executing and managing Pig scripts.

## Installation

- Cloudera is one of the vendor who provides installation packages for the hadoop ecosystem.
- The Hortonworks Sandbox version can be installed on a personal computer for practise and learning purpose. It has:
  - They are image files for `VMWARE`, `Docker` or `VirtualBox`.
  - The Hortonworks HDP which include the Apache Hadoop, Apache Spark, Apache Hive, Apache HBase, Druid and Data Analytics Studio (DAS). [Click here](https://www.cloudera.com/downloads/hortonworks-sandbox/hdp.html) to download.
  - The Cloudera DataFlow (Ambari) - formerly known as Hortonworks DataFlow, which includes Apache NiFi, Apache Kafka, Apache Storm, and Streaming Analytics Manager (SAM). [Click here](https://www.cloudera.com/downloads/hortonworks-sandbox/hdf.html) to download.
  - The VM that is hosted using the downloaded image will have a running hadoop ecosystem. For local host machine to access.
