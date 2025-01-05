
## What is Hudi?
 - Hudi is a framework built by Uber in 2016 to bring the ACID functionality to Data Lakes essentially making Datalakes __DataLakeHouses__.
 - Hudi integrates with multiple other frameworks. One such framework we use [[spark]] to perform the CRUD operations including    [[CDC]]

## How to install Hudi?
- Use the packages option and use the respective Hudi jar file  Coordinate to install it from the central repository.

## How Hudi works?
 - While storing the dataframe into storages and filesystems unlike the databases, along with the dataframe being stored into regular flat files, we have some metadata about the data also being stored which enables us to leverage the capabilities of CDC.
 - There are many customization options available regarding the table type, storage type, partition and precombine fields which are unavailable in other formats.

## Why Hudi?
- Hudi abbreviating for Hadoop Upserts Deletes Incremental provides options for us to perform an update or delete operation on a specific dataset.
- As the data lakes began to popularize, the process of overwriting data every time has become very expensive and time consuming, Hence was the need fulfilled by Hudi.


## [[Hashing]]

## Issues and Solutions

- [https://github.com/apache/hudi/issues/7991](https://github.com/apache/hudi/issues/7991 "https://github.com/apache/hudi/issues/7991")
		Getting exceptionally high costs for S3 Head objects while using Hudi