# Amazon DynamoDB
**Amazon DynamoDB**: is AWS as NoSQL database as a service. It is a schema-less, high scalable and durable database system. Each writes to servers in multiple availability zones. It also provides high speed extremely low latency performance. 

The following are the basic DynamoDB components:
  - Tables – Similar to other database systems, DynamoDB stores data in tables. A table is a collection of data. For example, see the example table called People that you could use to store personal contact information about friends, family, or anyone else of interest. You could also have a Cars table to store information about vehicles that people drive.

  - Items – Each table contains zero or more items. An item is a group of attributes that is uniquely identifiable among all of the other items. In a People table, each item represents a person. For a Cars table, each item represents one vehicle. Items in DynamoDB are similar in many ways to rows, records, or tuples in other database systems. In DynamoDB, there is no limit to the number of items you can store in a table.
  
  - Attributes – Each item is composed of one or more attributes. An attribute is a fundamental data element, something that does not need to be broken down any further. For example, an item in a People table contains attributes called PersonID, LastName, FirstName, and so on. For a Department table, an item might have attributes such as DepartmentID, Name,Manager, and so on. Attributes in DynamoDB are similar in many ways to fields or columns in other database systems.

In Amazon DynamoDB, a database is a collection of tables. An table is a collection of items and each item is a collection of attributes. DynamoDB is a simple NoSQL database, not a relational database. So, It does not support joins. If you want to perform join operations it needs to be done with an external application outside of DynamoDB. Amazon DynamoDB is integrated with **Apache Hive**, a data warehousing application that runs on **Amazon EMR**. Hive can read and write data in DynamoDB tables, allowing you to:  

- Query live DynamoDB data using a SQL-like language (HiveQL).  
- Copy data from a DynamoDB table to an Amazon S3 bucket, and vice-versa.  
- Copy data from a DynamoDB table into Hadoop Distributed File System (HDFS), and vice-versa. Perform join operations on DynamoDB tables.

Amazon DynamoDB supports the following data types:  
1. Scalar types – Number, String, Binary, Boolean, and Null.
2. Multi-valued types – String Set, Number Set, and Binary Set.
3. Document types – List and Map.
 
DynamoDB uses eventually consistent reads, unless you specify otherwise. Read operations (such as GetItem, Query, and Scan) provide a ConsistentRead parameter. If you set this parameter to true, DynamoDB uses strongly consistent reads during the operation.

## Working with DynamoDB

Every global secondary index must have a partition key, and can have an optional sort key. The index key schema can be different from the base table schema; you could have a table with a simple primary key (partition key), and create a global secondary index with a composite primary key (partition key and sort key) — or vice-versa.

DynamoDB supports types that represent sets of Number, String, or Binary values. All of the elements within a set must be of the same type. For example, an attribute of type Number Set can only contain numbers; String Set can only contain strings; and so on.  

There is no limit on the number of values in a set, as long as the item containing the values fits within the DynamoDB item size limit (400 KB).

Each value within a set must be unique. The order of the values within a set is not preserved; therefore, your applications must not rely on any particular order of elements within the set. Finally, DynamoDB does not support empty sets.

The Query operation finds items based on primary key values. A Scan operation reads every item in a table or a secondary index. By default, a Scan operation returns all of the data attributes for every item in the table or index.

By default, the DynamoDB write operations (PutItem, UpdateItem, DeleteItem) are unconditional: each of these operations will overwrite an existing item that has the specified primary key.
DynamoDB optionally supports conditional writes for these operations. A conditional write will succeed only if the item attributes meet one or more expected conditions. Otherwise, it returns an error. Conditional writes are helpful in many situations. For example, you might want a PutItem operation to succeed only if there is not already an item with the same primary key. Or you could prevent an UpdateItem operation from modifying an item if one of its attributes has a certain value. Conditional writes are helpful in cases where multiple users attempt to modify the same item.

One read capacity unit represents one strongly consistent read per second, or two eventually consistent reads per second, for an item up to 4 KB in size. If you need to read an item that is larger than 4 KB, DynamoDB will need to consume additional read capacity units. The total number of read capacity units required depends on the item size, and whether you want an eventually consistent or strongly consistent read.

One write capacity unit represents one write per second for an item up to 1 KB in size. If you need to write an item that is larger than 1 KB, DynamoDB will need to consume additional write capacity units. The total number of write capacity units required depends on the item size.

If your DynamoDB items are 5 KB and you want to read 80 items per second from your table, then you need to provision **160** read capacity units for strong consistency.

If your DynamoDB items are 5 KB and you want to read 80 items per second from your table, then you need to provision **80** read capacity units for eventual consistency.


If your DynamoDB items are 3.5 KB and you want to do 20 writes per second, then you would need to provision **80** write capacity units.

For table and secondary index names, allowed characters are a-z, A-Z, 0-9, '_' (underscore), '-' (dash), and '.' (dot). Names can be between 3 and 255 characters long.


The DynamoDB capacity units consumed by an operation depends on the following:
- Item size
- Read consistency (in case of a read operation)

The optimal usage of a DynamoDB table's provisioned throughput depends on these factors:
1. Database schema
2. The primary key selection.
3. The workload patterns on individual items
