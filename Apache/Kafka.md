[[Apache]]

### Topics

Topics are analogous to tables which we have in a database
We write the data to the topics and any kind of data can be written to a topic and can have any number of topics as we like.
- A topic is identified by its name
- A sequence of messages are called as an data stream

We cannot directly query a topic, we need to utilize the Kafka consumers and the producers for ingesting and querying the data.

### Partitions

Topics are split into partitions, the data is written to the partitions. The messages sent to a Kafka topic are sent to the partitions

![[kafka.excalidraw|800]]

- Once data is written to a partition, it's immutable, we can't delete the data nor modify it.
- Each message in the partition gets a incremental id called the offset.
- This also implies that all the messages in a partition are ordered.
- Data is retained for a limited time only (1 week by default).
- Order is only guaranteed with in the partition
- Data is randomly assigned to the partitions if no key is defined


### Producers

Producers are the entities which write data into the Kafka topics




