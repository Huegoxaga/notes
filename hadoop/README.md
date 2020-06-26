# Hadoop Ecosystem

## Introduction

- Hadoop or Hadoop Ecosystem contains a collection of open-source softwares managed through the Apache Software Foundation
- These softwares are designated to work on a distributed system for handling big data.
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
- It retains redundent copys of hard drives.

#### Yet Another Resource Negotiator (YARN)

- It manages computer cluster resources
- It runs on HDFS

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

#### MapReduce

- It is a programming model that will process data in one of the two ways:
  - Mappers - Transform data in parallel for distribution across computer clusters
  - Reducers - Aggregate data together
- It runs on YARN

#### Pig

- It runs on MapReduce.
- It allows queries using scripts.

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

## Installation

- Cloudera is one of the vendor who provides installation packages for the hadoop ecosystem.
- The Hortonworks Sandbox version can be installed on a personal computer for practise and learning purpose. It has:
  - They are image files for `VMWARE`, `Docker` or `VirtualBox`.
  - The Hortonworks HDP which include the Apache Hadoop, Apache Spark, Apache Hive, Apache HBase, Druid and Data Analytics Studio (DAS). [Click here](https://www.cloudera.com/downloads/hortonworks-sandbox/hdp.html) to download.
  - The Cloudera DataFlow (Ambari) - formerly known as Hortonworks DataFlow, which includes Apache NiFi, Apache Kafka, Apache Storm, and Streaming Analytics Manager (SAM). [Click here](https://www.cloudera.com/downloads/hortonworks-sandbox/hdf.html) to download.
  - The VM that is hosted using the downloaded image will have a running hadoop ecosystem. For local host machine to access.
