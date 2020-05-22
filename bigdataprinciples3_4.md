# Big Data Principles and Best Practices of Scalable Real-Time Data Systems
 
## Chapter 3: Data Model for Big Data: Illustration

### 1. Give an example of data corruption 
(answers may vary)
**Some examples:**
- Aging, damaged or faulty computer or network components; loose or improperly installed cards, connectors, terminators; bent pins, etc.
- Failing or degraded storage media.
- Power fluctuations, spikes, surges, interruptions or outages.
- Malicious software (malware).
- Operating system or program bugs (software issues) (including third-party programs), or faulty network card drivers (older releases of manufacturer drivers), etc.
- Interference from other software programs running.

### 2. When would you use a serialization framework?
When writing raw data and prevent bugs such as data corruption. When using you get errors at the time of writing the data—giving you full context as to how and why the data became invalid. In addition, the error prevents the program from corrupting the master dataset
by writing that data. However, serialization frameworks are limited when it comes to achieving a fully rigorous schema.

### 3. With your own words, what are properties in Thrift?
(answers may vary)
A combination of nodes (Unions) and edges (structs).

### 4. What is an union data type?
A single value that may have any of several representations. 

### 5. Write an example of node using Thrift (different from the book)
(answers may vary)
union PersonID { 1: i64 user_id;}

### 6. What is an essential property while using schemas?  
That they can evolve over time.

### 7. Why you shouldn't reuse a field ID while changing schemas in Thrift?
Thrift would try to deserialize that old data into the new field, which will lead to either invalid or incorrect data. 

### 8. What are the two approaches you can chose to help you with the limitations of serialization frameworks?
- Wrap your generated code in additional code that checks the additional properties you care about, like ages being non-negative. 
- Check the extra properties at the very  beginning of your batch-processing workflow.

### 9. What are other popular serialization frameworks? (Write at least three)
- Boost Framework
- Protocol Buffer
- Avro
- Message Pack

### 10. After your reading of the chapter, what are some advantages of using serialization frameworks?
- It is easy to use and can be customized.
- The serialized stream can be encrypted, authenticated and compressed.
- Serialized classes can support coherent versioning and are flexible enough to allow gradual evolution of your application's object.

## Chapter 4: Data Storage in the batch layer

### 1. What are the three requirements for the master dataset?
- **Read**: Support for parallel processing.
- **Write**: Efficient appends of new data and scalable storage.
- **Both**: Tunable storage and processing costs and enforceable immutability.

### 2. According to the text what are the disadvantages of using key/value store for the master dataset?
- There’s no natural key in the data model, nor is one necessary because the data is meant to be consumed in bulk.
- Key/value stores need fine-grained access to key/value pairs to do random reads and writes, you can’t compress multiple key/value pairs together.
- They are meant to be used  as mutable stores, which is a problem if enforcing immutability is so crucial for the  master dataset.
- It has a lot of things you don’t need: random reads, random writes, and all the machinery behind making those work.

### 3. What are the advantages of using distributed filesystems?
- You have full control over the bytes of a file.
- You have the full freedom to compress them however you want. 
- It doesn't limits your ability to  tune storage cost versus processing cost.
- They implement fine-grained permissions systems, which are perfect for enforcing immutability.

### 4. Write 5 examples of distributed filesystem tools.
(answers may vary)
- DCE Distributed File System (DCE/DFS)
- Sun Microsystems' Network File System (NFS)
- Novell NetWare
- Microsoft's Distributed File System
- IBM/Transarc's DFS

### 5. How does nodes work in Hadoop Distributed File System?
In an HDFS cluster, there are two types of nodes: a single namenode and multiple datanodes. All (typically large) files are broken
into blocks, usually 64 to 256 MB. These blocks are replicated (typically with 3 copies) among the HDFS servers (datanodes).The namenode provides a lookup service for clients accessing the data and ensures the blocks are correctly replicated across the cluster.

### 6. Create a situation when you would use vertical partitioning
(answers may vary)
You have a computation that only requires information collected during the past two weeks. The batch storage should allow you to partition your data so that a function only accesses data relevant to its computation.

### 7. How do you do vertical partitioning?
Vertically partitioning data on a distributed filesystem can be done by sorting your data into separate folders.

### 8. Why using distributed filesystems API's is considerated low-level?
While trying to append a folder of data into your master dataset if the master dataset folder contains any files of the same name, then the mv operation will fail and also if the files in the folder are of a different format than teh master dataset the mv operation won’t work at all.
