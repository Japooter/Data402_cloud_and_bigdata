# Cloud and Big Data

## Introduction to Big Data

Companies are storing and processing huge amounts of data, but where does this data come from?
- Employee-tied data from employees
- Warehouse information from stock information groups or employees
- Customers shop online, data received from those transactions
- Emergence of tools for information such as "clickstream analysis", ad-sense, cookies, etc.
- "Direct Traffic", "Referral Traffic", "Search Traffic", "Campaign Traffic"
- Data logs
- Social media
- RFID tags and UPC barcodes

We have uses for big data such as sentiment analysis, machine learning, analysing buying patterns. There is also benefits in healthcare research, fraud detection and predicting equipment failure.

### Enablers
- Commodity Hardware - New Big Data tech works with off-the-shelf computers
- Reduced Storage Costs - Disk drives are denser and cheaper than ever
- Open Source - Reduced overheads and new communities and standards
- Web-based Companies - Increased supply and demand of data

### The "Vs" of Big Data
"Value", "Volume", "Variety", "Veracity", "Velocity", "Variability" (?)

Note the following though:
Are the data included truly Big to warrant Big Data? Do they need to be Big? Can the infrastructure handle Big Data? Do you actually need Big Data or just something within NoSQL?

## How do you "solve" Big Data?
Your regular-sized freezer is at capacity, but you need to have more frozen food stored. What are your options?


## Distributed Systems
- Can use commodity hardware, which reduces costs
- Higher chance of system failure, so more things can go wrong
- High programming complexity, luckily there are tools such as Hadoop that are designed to manage the programming complexity and system failure rate management


## Hadoop
- HDFS - Storage layer
- YARN - Data processing layer

Hadoop was created in 2005 by Mike Cafarella and Doug Cutting. The free, open-source software framework (part of Apache, an open source software foundation). Hadoop is used in data discovery, processing unstructured data and handling massive data storage/processing.

### Features of Hadoop
- Scalable (horizontal and vertical scaling, horizontal allowing machines to be added in parallel and vertical scaling replaces machines with bigger machines)
- Flexible (easy to store huge datasets and you can decide how to use them later on)
- Economical (no licensing costs and can use ordinary computers for data processing)
- Reliable (It stores multiple copies of data on different machines and is resistant to hardware failure)

### Hadoop components
- Hadoop Distributed File System (HDFS), provides high-throughput access to application data
- Yet Another Resource Negotiator (YARN), a framework for job scheduling and cluster management
- MapReduce, a YARN-based system for parallel processing of data. Has two parts: Mapping and reducing the data


Apache and Apache Spark, what does it do, where will it fit on the pipeline,

Apache Spark is an open-source processing engine, mainly used with (as is likely expected if being here) Big Data. The structure of Spark is based on Resilient Distributed Datasets (RDDs), which is a read-only collection of data that Spark heavily relies upon for everything it does, even creating data relies on the RDDs to have Spark work efficiently. RDDs can be created from the Haloop Distributed File System and distributed into shards and cached in memory for easy referral. They can even be reconstructed after the potential loss of a partition, using a concept called "Lineage", this helps with the Hadoop feature of reliability in being resistant to hardware failure [1],[2]. For this reason, Spark is likely to be within the Data Storage and Processing Layers. Spark has multiple forms that can be used, including Spark SQL.

Cassandra is a database management system under the "NoSQL" series of database designs (more specifically, wide column store). It is open source and due to the nature of being a NoSQL database design, it is scalable, but also alongside this resistant to faults. It holds structured, unstructured and a hybrid of the two (semi-structured) as data formats, It also supports the ACID principles (Atomicity, Consistency, Isolation and Durability) [3]. It is likely that Cassandra and its "CQL" are found within the Data Query Layer.

Zookeeper is a centralised service for several uses, including, but not limited to, the provision of group services, maintaining configuration information and the provision of distributed synchronisation. Zookeeper is an attempt at making several services have a simple interface to allow various applications to use them effectively under more strenuous time constraints. In short, Zookeeper allows for these services to communicate with each other effectively and provide some coordination. This is done via "Znodes", a series of nodes organised into a hierarchy. These Znodes, like with regular nodes, can be used to store and retrieve data and state information. There are also "elections" that determine which of the nodes is situated at the top of the hierarchy, as well as recovery methods which both allow for failure resistant. This is similar to how replica sets have secondary and primary sets, along with being able to form elections for what becomes the primary. We use Zookeeper in cases where we need coordination services, where there are "race conditions" (two or more systems trying to perform some task) and where deadlocks can occur (two or more operations waiting for each other) [4]. Zookeeper is likely used in the Data Monitoring Layer.


#### Data Storage Layer:
Store the data that has been ingested, allowing it to be saved and recalled for other layers (such as processing)
- S3 - "Simple Storage Service", easy to store and read data with it.
- HDFS - "Hadoop Distributed File System", a storage system that is the primary choice within the Hadoop ecosystem. It allows for fast storage via the transfer of data between nodes. This and its ease of use on commodity hardware is what makes it so popular
- HBase - designed for fast read/write access to Big Data that is random. Hosts very large tables.

#### Data Processing Layer:
Where the data is made queryable from storage and put into a state that analysis can be achieved.
- Batch - A way of having a "batch" of data at a time, rather than processing everything individually
- Real time - The use of streaming technologies to handle the workloads of a state that is constantly changing
- Hybrid - Mixing features of RDBMS with NoSQL, such as high performance data processing in main memory and large storage space.
- Storm - An addition to the Hadoop ecosystem which allows for more real time data processing as opposed to how Hadoop itself does things with batch processing
- MapReduce - Splits data processing into chunks that include compute nodes and storage nodes.
- Spark - Distributed processing system that has several componenets (some covered in detail later)
- Spark Streaming - "enables scalable, high-throughput, fault-tolerant stream processing of live data streams."

#### Data Monitoring Layer:
Where data is kept under check to make sure that there are no clashes in the processes being done
- Zookeeper - Zookeeper allows for services to communicate with each other effectively and provide some coordination. This is done via "Znodes"
- YARN - Comprised of a ResourceManager made up of "per-application" ApplicationMasters and Scheduler. RM responsible for negotiating resources, but the Scheduler simply schedules.

#### Data Security Layer:
- HTTP (HTTP server project, not a part of the Hadoop ecosystem), quote: "secure, efficient and extensible server"

[1] https://nexocode.com/blog/posts/what-is-apache-spark/
[2] https://www.sciencedirect.com/topics/computer-science/resilient-distributed-dataset
[3] https://www.geeksforgeeks.org/introduction-to-apache-cassandra/
[4] https://www.geeksforgeeks.org/what-is-apache-zookeeper/

Feedback from presentation (covered Data Processing, Data Storage, Data Security and Data Monitoring Layers):
Good overall work, but could maybe do a bit less detail on Zookeeper (match everything else in terms of what was covered). 
