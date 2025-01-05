CDC :: Change Data Capture

CDC is the process that enables us to capture everything from the database (Data lakes using Hudi also come up with this features) and the changes made to that data after the initial capture.

## CDC is of 2 types.
- Query-based 
- Log-based

### Query based CDC.
 Fetch the changes based upon a timestamp column (Any column which has the property of increasing monotonically whenever the record is modified, you can also use an serial/increment key. Timestamp is usually preferred because it's easy to implement and understand and also gives a meaningful information which is the time).

- Example: SELECT * FROM <table_name> where <ts_column> > <last_read_column>

### Log Based CDC.
 Every Operation we perform on a database will be logged into the log file(Which is in binary format most of the times), so we read the log file and track the operations that have happened on the database.

 This gives us and massive advantage of also capturing delete operations which would not be possible while doing the Query based CDC.
 Every mutation of the record is explicitly logged into the log and hence the change tracking of the record is also present
