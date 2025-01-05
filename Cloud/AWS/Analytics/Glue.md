[[Analytics]]

> [!Definition]
> AWS Glue is a serverless data integration service that makes it easy for analytics users to discover, prepare, move, and integrate data from multiple sources.

With AWS Glue, data scientists, analysts, and developers can discover, prepare, and combine data for various purposes.

## AWS Glue features

AWS Glue features fall into three major categories:

- Discover and organize data
- Transform, prepare, and clean data for analysis
- Build and monitor data pipelines

All-in-All we know that Glue is an Serverless ETL tool, Glue has numerous in-built abilities as an ETL Tool.
- [[Data Discovery]]: Glue Crawlers
- [[Data Catalog]]: Glue Data Catalog
- Data Quality
- Data Transformation
- Glue Studio
- Glue Streaming
- ETL Jobs
- Orchestration
- Auto Scaling

AWS Glue is built for different groups across an organization to easily build and manage pipelines, It offers visual job creation engine [[Glue Studio]] to build jobs in a no-code format. Glue easily integrates with other analytical and storage services like Amazon S3 data lakes, AWS Redshift, Amazon Athena etc..,

### Serverless ETL jobs run in isolation

AWS Glue is designed to do the following:

- Segregate customer data.
- Protect customer data in transit and at rest.
- Access customer data only as needed in response to customer requests, using temporary, scoped-down credentials, or with a customer's consent to IAM roles in their account.

For each tuple (customer account ID, IAM role, subnet ID, and security group), AWS Glue creates a new environment that is isolated at the network and management level from all other environments inside the AWS Glue service account.



### Glue Data Catalog

The persistent metadata store in AWS Glue. It contains table definitions, job definitions, and other control information to manage your AWS Glue environment.

A table is metadata representation of a collection of structured or semi-structured data stored in sources such as Amazon RDS, Apache Hadoop Distributed File System, Amazon OpenSearch Service, and others. The AWS Glue Data Catalog provides a uniform repository where disparate systems can store and find metadata to keep track of data in data silos.

The Data Catalog, along with CloudTrail and Lake Formation, also provides you with comprehensive audit and governance capabilities, with schema change tracking and data access controls. This helps ensure that data is not inappropriately modified or inadvertently shared.

### Glue crawlers and classifiers

AWS Glue also lets you set up crawlers that can scan data in all kinds of repositories, classify it, extract schema information from it, and store the metadata automatically in the AWS Glue Data Catalog.

### AWS Glue ETL operations

Using the metadata in the Data Catalog, Glue can automatically generate Scala or PySpark scripts with AWS Glue extensions that you can use and modify to perform various ETL operations.

### Streaming ETL in AWS Glue

Glue enables you to perform ETL operations on streaming data using continuously-running jobs. AWS Glue streaming ETL is built on the Apache Spark Structured Streaming engine, and can ingest streams from Amazon Kinesis Data Streams, Apache Kafka, and Amazon Managed Streaming for Apache Kafka (Amazon MSK).