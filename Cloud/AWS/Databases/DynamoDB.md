[[Databases]]

> [!Definition]
> DynamoDB is a full managed key-value or a document database with a milli-second response time at any scale.

## History

Amazon DynamoDB was a solution originally initiated for their biggest customer amazon.com when they hit the scaling requirements for the RDS server, They were not able to scale more due to the infrastructure limits and there came up the need for an NoSQL service in AWS

The DynamoDB paper was released in 2007 and In 2012, DynamoDB was available as a public service to all the AWS Accounts

## Properties of DynamoDB

Data in DynamoDB is stored as tables, These tables comprise different rows called items and an Item is comprised of different attributes. Schema Flexibility of DynamoDB allows us to Store complex and hierarchical data into a single item. 

One of the Attributes is the partition key, the partition key is what that decides the partition where the data will be present in.

Data is stored is a Denormalized fashion, often requiring only a single table


## How DynamoDB works

By Now, we have understood that DynamoDB is a NoSQL database which stores key-value or document based _items_ into a DynamoDB _table_. Let's see how this happens in a deeper context.

The partition key (Hash key) of an Incoming item is hashed by the DynamoDB's internal hash function, the output of the hash is a pointer or memory address, There are some partitions, that are pre-defined by the DynamoDB and these partitions store data for a range of memory addresses. Hence the incoming item is assigned a partition to which it has to be persisted to. The item is stored as is without any distribution of the attributes of the item.

DynamoDB manages the partitions (Let's say N partitions), These partitions are also replicated across different availability zones for high availability and durability. As the data is written to the leader node (One node across different availability zones) this node also replicates the same data into other availability zones

### Capacities in DynamoDB

#### Throughput

- RCU - 4KB on demand, 4KB/sec in provisioned (Half the consumption of RCU for eventually consistent read) or 1 item minimum
- WCU - 1KB on demand, 1KB/sec in provisioned or 1 item minimum
#### Size
 - One item - 400KB

#### Scaling

- Each virtual partition delivers 1000 WCU/sec or 3000 RCU/sec
- As the traffic grows the partitions are split into two and each virtual partition grows can get the max capacity
- partition based on size. if a partition increases more than 10GB, it splits

## Reading data from DynamoDB

There are multiple ways how we can read data from DynamoDB
- GetItem :: Specify the exact value of the primary key, returns exactly 0 or 1 item
- Query :: Specify an exact value of the partition key and optionally a sort key or a condition with the sort key, optionally we can add filters to the output, returns matching items (multiple)
- Scan :: scans the complete table, optionally we can add filter expressions.


## On Demand and Provisioned Mode

We can have the Read Capacity Units (RCU) and the Write Capacity Units (WCU) which perform the read and write operations on the DynamoDB table. These RCUs and WCUs can be consumed either on provisioned basis or on On-Demand basis depending upon the workload type we might be having with the DynamoDB table.

We can use the On-Demand mode more for a spiky usage where the workloads can drop to zero and spike up whenever there is usage and the provisioned capacity for constant traffic.

We can also use Autoscaling for scaling the RCUs and WCUs as within the minimum and maximum limits and scale-up or scale-down as the traffic fluctuates


## Characteristics of DynamoDB

### Serverless
- There are no servers needed to be provisioned, managed and maintain (upgrades and patches)
- Provides Zero-downtime.

### NoSQL
- Improves performance, Scalability and flexibility of schema compared to traditional relational databases

## Capabilities of DynamoDB

### Multi-active replication with global tables

- Global tables provide multi-active replication of your data across your chosen AWS Regions with 99.999% availability.
- There are no complicated or delayed failovers, or database downtime when failing over an application between Regions.
### ACID transactions

Within DynamoDB, we can have ACID Transactions, which allow you do either fully do a set of actions or not do any of them. This bring the ACID support to the DynamoDB

### Change data capture for event-driven architectures

- DynamoDB supports streaming of item-level change data capture (CDC) records in near-real time.
- Two types of streaming models :: DynamoDB Streams and Kinesis Data Streams for DynamoDB

### Secondary Indexes

- DynamoDB lets you create Secondary indexes, Global Secondary Index and Local Secondary Index, we can query the table data with an alternate key.
#### Global Secondary Index
 - Alternate partition and sort key
 - DynamoDB creates a separate table which it internally manages with the new partition and sort key.
#### Local Secondary Index
- The Partition key has to be the same for a local secondary key, but the sort key can change, if we are having a different access pattern which allows us to use the same partition key we can use Local Secondary Index
- It is stored in the same physical partition
- Major fallback is for a partition key, we cannot exceed 10GB with the LSI
#### Table class

DynamoDB supports two table classes which is the standard and In-frequent access, and we can switch between table classes once every 24 hours.

The Infrequent access class reduces the storage
### Service integrations

### Serverless integrations
- API Gateway
- Lambda
- AWS AppSync
- Amazon Kinesis Data Streams

### Importing and exporting data to Amazon S3

- Supports full table and incremental exports to S3

### Backup and Restore

- We can backup the data from the DynamoDB table for compliance or audit purposes. Unlike traditional RDBMS purposes, we need not backup data in order to protect the data from getting lost due to an unforeseen circumstances since the data is resilient to AZ level failures and when we talk about global tables we achieve an SLA of 99.999% availability
- Along with the per second backup we can also have Point In Time Restore (PITR), which will allow us to rollback to any period of time within the past 35 days, to revert any mistakes with the data persisted into the table
- This two can be combined together and also supports integration with [[Backup]]

### Zero-ETL integration

- DynamoDB supports zero-ETL integration with Amazon Redshift. These integrations enable you to run complex analytics on your DynamoDB table data

### NoSQL Workbench

A GUI for data modelling, visualizations and operation builder

### PartiQL

PartiQL is a SQL Interface for DynamoDB, which is helpful for developers coming from a SQL background, we can write SQL like queries for all the CRUD operations we do through the DynamoDB APIs. 

### Caching

- [[#DAX]] - In Memory data caching solution


## DAX

DAX or DynamoDB Accelerator is a fully managed highly available In-Memory read cache Infront of DynamoDB, reduces read latencies from Milli Seconds to Micro Seconds. 

Unlike other caching options we need not modify our applications for including a DAX Cluster, we can just have the same API pointing towards a different endpoint, It also Implements read-through caching mechanism, simplifying the usage of a Cache system. 

## Audit

With DynamoDB we can not only log the Control plane related operations, but also the operations related to the data plane can be logged into [[CloudTrail]]