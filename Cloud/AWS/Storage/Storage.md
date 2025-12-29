[[AWS]]
## Introduction

Whether on premises or in a cloud environment, you have three primary types of storage: block, file, and object.

### Block Storage

_Block storage_ is raw storage in which the hardware storage device or drive is a disk or volume that is formatted and attached to the compute system for use. The storage is formatted into predefined continuous segments on the storage device. These segments are called blocks. The blocks are the basic fixed storage units used to store data on the device.

This storage type is used by the operating system or an application that has the capabilities to manage block storage directly.

### File Storage

_File storage_ is built on top of block storage, typically serving as a file share or file server.

File storage is created using an operating system that formats and manages the reading and writing of data to the underlying block storage. The name _file storage_ comes from the primary use of storing data as files typically in a directory-tree hierarchy.


### Object Storage

_Object storage_ is built on top of block storage. Object storage is created using an operating system that formats and manages the reading and writing of data to the underlying block storage. The name object storage comes from the primary use of storing the data within a binary object.

## AWS Storage Portfolio

The AWS Storage portfolio consists of the core storage services and other closely associated services that work with the core storage services. Associated services include online and offline data and file-transfer services, edge storage services, hybrid storage services, and data-protection services.

![[AWS Storage Portfolio.png]]
AWS Provides AWS Core storage services which resemble the Core storage services (Block, File, Object)

![[Core Storage Services.png]]

### AWS Block Storage Services

- [[EBS|Amazon EBS]]
- [[FSx for NetApp ONTAP|Amazon FSx for NetApp ONTAP]]

### AWS File Storage Services

- [[EFS|Amazon EFS]]
- [[FSx for Lustre|Amazon FSx for Lustre]]
- [[FSx for Windows File Server|Amazon FSx for Windows File Server]]
- [[FSx for NetApp ONTAP|Amazon FSx for NetApp ONTAP]]
- [[FSx for OpenZFS|Amazon FSx for OpenZFS]]

### AWS Object Storage services
- [[S3|Amazon S3]]

## Hybrid cloud storage services

AWS offers services that are designed to provide hybrid cloud solutions. Hybrid solutions to connect your on-premises infrastructure to storage services in the AWS Cloud. Hybrid services allow you to customize and optimize the integration between your on-premises systems and data, and your services running in the AWS Cloud.

- [[Storage Gateway|AWS Storage Gateway]]
- [[Outposts|AWS Outposts]]
- [[File Cache|Amazon File Cache]]

## Data Protection Services

- [[Backup|AWS Backup]]
- [[Elastic Disaster Recovery|AWS Elastic Disaster Discovery]]