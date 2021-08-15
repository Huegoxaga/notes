# Hadoop

## Introduction

* Hadoop or Hadoop Ecosystem contains a collection of open-source softwares managed through the Apache Software Foundation
* These softwares are designated to work on a distributed system for handling big data.
* Natively written in Java
* A distributed system is consisted of computer clusters
  * It offers the following two functionality:
    * Distributed Storage
    * Distributed Processing
* History
  * The distributed system is originated from the Google's papers in 2003-2004.
    * Google File System\(GFS\) enables distributed storage
    * MapReduce enables distributed processing
  * `Yahoo!` started to build search engine based on the distributed concept at the same time.
  * The Co-founder, Doug Cutting, who was working at `Yahoo!` at the time, named it after his son's toy elephant

## Components

#### Hadoop Distributed Filesystem \(HDFS\)

* The Hadopp version of `GFS`.
* It allows hard drives across the computer clusters works as one filesystem.
* It retains redundent copys of data across hard drives.
* It devides large files into 128 MB blocks.
  * One block for anything smaller than 128 MB
  * The blocks can be ready for parallel processing
* Data is stored across multiple data nodes.
* Name node records the location of all the blocks.
* Name node keep a record of changes made to all blocks in an edit log.
* Client side is the client node that will access name node every time before read and write.
* When client node write block to name node. Name node communicate with other name nodes to duplicate files for redundancy,and send acknowledgment to client node after. Client node will inform name node the process is completed
* Name node can't be the single point of failure, there are serveral solutions:
  * Write to local storage and backup metadata, It will have downtime
  * Secondary Namenode - Maintain a merged copy of edit log, It will have downtime
  * Running two name node, a stand by name node and the active name node will share a common edit log in an external storage
    * Zookeeper tracks and determines the active name node
    * It is important to make sure only one name node is active at a time.
* HDFS Federation allows multiple name node to be responsible for a specific namespace volume. This will split or expand one name node into a group of name nodes.
* There are several ways to use to the HDFS:
  * UI Consoles\(Ambari\)
  * Command Line Interface
    * `ssh` connection to the hadoop server and use `hadoop fs` command
      * Run `hadoop fs` to list all the commands available
  * HTTP/HDFS Proxies
  * Java Interface
  * NFS Gateway

#### MapReduce

* It is a programming model that will process data in one of the two ways:
  * Mappers - Transform data in parallel for distribution across computer clusters
    * Mappers find the valuable data for a certain task then map them into a dictionary of key and value pairs.
    * It will then group all values with the same key and sort the key automatically\(merge sort across running instances\).
  * Reducers - Aggregate data together
    * It will run once for each key provided by the Mapper and provide the designated output
      * The keys are not necessarily from the same instance since it has been sorted across all instances.
* It runs on worker nodes that managed by the node manager.
  * One node can run one or more map/reduce tasks.
  * All of these tasks acquire data from HDFS.
* There is one node that is called MapReduce Application Manager, it managers all other nodes and receive task from YARN
  * This node also has a node manager
  * It can relocate or restarted failed worker nodes.
  * When Application Manager fails, YARN will restart it.
* Natively jobs can be written in Java
* It supports other language using shell steaming with `stdin` and `stdout`.
  * For `python` job for example, use:
    * `python job.py <data>` to test the job locally.
    * `python job.py -r hadoop <data>` to run the job using hadoop.
      * `<data>` should be an HDFS path like `hdfs://<path>.`
      * if using local file it will be copied to HDFS for processing.
      * `--hadoop-streaming-jar` needs to be specified for some platform.
* Example code for MapReduce job in Python using `mrjob` library

  ```python
  from mrjob.job import MRJob
  from mrjob.step import MRStep
  class RatingsBreakdown(MRJob):
      def steps(self):
          return [
              MRStep(mapper=self.mapper_get_ratings,
                    reducer=self.reducer_count_ratings)
          ]
      def mapper_get_ratings(self, _, line):
          (userID, movieID, rating, timestamp) = line.split('\t')
          yield rating, 1
      def reducer_count_ratings(self, key, values):
          yield key, sum(values)
  if __name__ == '__main__':
      RatingsBreakdown.run()
  ```

#### Yet Another Resource Negotiator \(YARN\)

* It manages computer cluster resources
* It runs on HDFS
* It will assign tasks to the node that is closet to the data source.
* It can restart fails clusters.
* A hot standby resources manager can be created and monitored by zookeeper, in case the YARN fails.

#### MESOS

* It is a resource negotiator that can be an alternative for `YARN`
* It runs on HDFS
* It can even work with YARN

#### Spark

* It provides a memory based solution that can run tasks on RAM.
* It uses \(directed acyclic graph\) DAG
  * Each task is defined first, when it get started it will determine the best path to find and solve the task first, in order to increase the speed.
* The spark core is a driver program to generate spark context
  * Spark context is used to create RDD object
  * It transform data into a Resilient Distributed Dataset \(RDD\) object for fast manipulation.
  * The driver can be used to retrive data from `Program Variables`, `Local files`, `HDFS`, `HIVE context`, `External database through JDBC`, `Hbase` etc.
* Spark 2.0 uses Dataset which is based on RDD
* Spark 2.0 is enpowered by some libaries built on top of Spart Core
  * Sparking Streaming - It supports real time processing instead of batch processing
  * Spark SQL - It supports SQL queries for Spark
  * MLLib - Data mining and ML models.
  * GraphX - Analysis data using graph theory.
* It runs on `YARN` or `MESOS`, or it can use its own cluster manaer.
* It is much faster than `MapReduce`
* It supports `Scala`, `Python` and `Java`
  * Spark is written in Scala
  * `Scala` is the recommanded language for Spark, it is faster and it saves resources.
* It supports SQL queries, machine learning, and realtime streaming data.
* RDD object methods example in Python:

  ```python
  rdd.map(lambda x: x*x) # Iterate through all elements of the dataset and apply the lambda
  rdd.flatmap(fucntion) # return dataset with combined or splited elements.
  rdd.filter(function) # filter
  rdd.distinct() # return distinct values
  rdd.sample()
  rdd1.union(rdd2) # combine elements
  rdd1.intersection(rdd2)
  rdd1.substract(rdd2)
  rdd1.cartesian(rdd2)
  rdd.collect() # Return dataset as python object
  rdd.count() # Count the elements in the dataset
  rdd.countByValue(value) # Count the occurance of a certain value
  rdd.take(n) # Get n elements from the dataset
  rdd.top(n) # Get n elements from the dataset
  rdd.reduce(function) # take a function to process dataset
  ```

#### TEZ

* It is similar to `Spark`
* It runs on `YARN`
* It is another alternative to `MapReduce`
* It uses \(directed acyclic graph\) DAG to speed up the jobs

#### Pig

* It runs on MapReduce.
* It can runs faster on TEZ.
* It allows queries using SQL-like scripting language called Pig Latin.
* It can translate SQL script into query jobs. Ex, Codes for MapReduce jobs if it runs on MapReduce.
* Pig Latin enables user defined functions\(UDF's\).
* Grunt is a Pig command line tool that can run script one line at a time.
  * It can also run an entire script file.
* Pig scrpits can be executed in the Ambari console, click run on TEZ option will make the query much faster.
* Data needs to be loaded to create a relationship, the schema is only created during loading.

  ```sql
  ratings = LOAD '/user/maria_dev/ml-100k/u.data' AS (userID:int, movieID:int, rating:int, ratingTime:int);
  metadata = LOAD '/user/maria_dev/ml-100k/u.item' USING PigStorage('|')
    AS (movieID:int, movieTitle:chararray, releaseDate:chararray, videoRealese:chararray, imdblink:chararray);
  nameLookup = FOREACH metadata GENERATE movieID, movieTitle,
    ToUnixTime(ToDate(releaseDate, 'dd-MMM-yyyy')) AS releaseTime;
  ratingsByMovie = GROUP ratings BY movieID;
  avgRatings = FOREACH ratingsByMovie GENERATE group as movieID, AVG(ratings.rating) as avgRating;
  fiveStarMovies = FILTER avgRatings BY avgRating > 4.0;
  fiveStarsWithData = JOIN fiveStarMovies BY movieID, nameLookup BY movieID;
  oldestFiveStarMovies = ORDER fiveStarsWithData BY nameLookup::releaseTime;
  DUMP oldestFiveStarMovies;
  ```

  * `DUMP` will print out the data.
  * `DESCRIBE` will show the relationship for a certain data.

#### Hive

* It allows user to query data stored in HDFS using SQL language.
* It runs on `MapReduce` or `TEZ`
  * It works faster with `TEZ`
* It uses `HiveQL` to query data
  * A SQL language that is similar to `MySQL`
* It supports `JDBC` or `ODBC` driver for connection
* It supports Thrift server
* It supports user defined functions
* It is good for `OLAP` for analytics, not good for `OLTP` for transcation due to high latency
* It does not support record level inserts, updates and deletes
* It utilize the concept called schema on read, the schema is defined and used when reading data
  * Traditional SQL database uses schema on write - The schema is defined before inserting data to the database
* A view in `HiveQL` is a logical contruct that stores the relationship of the queried data without storing a copy of the data anywhere
  * Once a view is created. It can then be queried as a newly created table
* Login to `Ambari` and select Hive View to start to query
  * Firstly, start with `Upload Table` from `HDFS`
* It also works with CLI

#### HBASE

* It adds the functionality of a NoSQL database to the existing clusters.
* It allows other transactional platform to access data in a NoSQL manner.
* It runs directly on the Filesystem.
* It is built based a the Google's paper about BigTable
* It provides an API for `CRUD` queries
* It generates multple `Region Server`s as a result of auto sharding
  * Each server contains data for a range of keys
  * As the data grows, it will re-adapt or partiioning the keys into different servers.
  * Client servers will connect to `Region Server` for data
* `HMaster` server is responsible for auto-sharding, and storing schema
* `ZooKeeper` is used to moniter the `HBase` master server
* HBase Data Model
  * Each record of data is stored in a row, with an unique key
  * Each intersection of column and row is a cell
    * Versioning can be enabled to each cell using timestamp
    * cell value can be null and it consumes zero storage
  * Each row can contain a small number of column families
    * Column families can contain arbitary number of columns
* Access HBase
  * HBase Shell - CLI tool
  * Java API - `HBase` is written in Java
    * API wrappers written for Python, Scala
  * connect to Spark, Hive, Pig
  * Built-in RESTful API
  * Thrift Serive
  * Avro Service

### Add-ons Tools

#### Apache Storm

* It is used to process streaming data.

#### oozie

* It manages schedule tasks.

#### Zookeeper

* It monitors clusters and services.

#### Sqoop

* It is a data ingestion tool that connects the Hadoop Filesystem with external SQL database.

#### Flume

* It is a data ingestion tool that transports web logs into the Hadoop Filesystem
* Realtime log data can then be processed by Spark Streaming or Apache Storm.

#### Kafka

* It is a general purpose data ingestion tool that collects data from other clusters.

#### Apache Drill

* It allows queries on both SQL and NoSQL database at the same time.

#### Apache Phoenix

* It is similar to Apache Drill.
* It provides ACID guarantees and supports OLTP for NoSQL database, hence minimize the performance difference between SQL and NoSQL data.

#### Presto

* A query tool which is similar to Apache Drill.

#### Apache Zeppelin

* A query tool which is similar to Apache Drill.
* It provices a notebook style UI.

#### Hue

* A query tool that work well with Hive and HBase.

#### Apache Ambari

* It is a high level frontend console that controls every through a webpage.
  * It is used by Hadoop distributions like `Hortonworks`
* Accessed by using `127.0.0.1:8080` in browser
* It can install services using the left panel.
* It can change services config using UI and even the config files.
* There are sevaral tab on the Navi bar
  * Services - Same as the left panel in Dashboard.
  * Host - It enables the admin to start/stop services running on each host.
  * Alert - controls alerts and email notifications.
* Admin account enables the control of cluster's services
  * To enable admin account `ssh` to the hosting server and run `ambari-admin-password-rest`
* The Grid Icon provide access to views:
  * File View is for browsering the HDFS.
  * Hive View is for executing SQL querries through Hive.
  * Pig View is for executing and managing Pig scripts.

## Installation

* Cloudera is one of the vendor who provides installation packages for the hadoop ecosystem.
* The Hortonworks Sandbox version can be installed on a personal computer for practise and learning purpose. It has:
  * They are image files for `VMWARE`, `Docker` or `VirtualBox`.
  * The Hortonworks HDP which include the Apache Hadoop, Apache Spark, Apache Hive, Apache HBase, Druid and Data Analytics Studio \(DAS\). [Click here](https://www.cloudera.com/downloads/hortonworks-sandbox/hdp.html) to download.
  * The Cloudera DataFlow \(Ambari\) - formerly known as Hortonworks DataFlow, which includes Apache NiFi, Apache Kafka, Apache Storm, and Streaming Analytics Manager \(SAM\). [Click here](https://www.cloudera.com/downloads/hortonworks-sandbox/hdf.html) to download.
  * The VM that is hosted using the downloaded image will have a running hadoop ecosystem. For local host machine to access.

