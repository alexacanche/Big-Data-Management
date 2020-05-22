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

### 2. When would you use a serialization frameworks?
When writing raw data and prevent bugs such as data corruption. When using you get errors at the time of writing the data—giving you full context as to how and why the data became invalid. In addition, the error prevents the program from corrupting the master dataset
by writing that data. However, serialization frameworks are limited when it comes to achieving a fully rigorous schema.

### 3. With your words what are properties in Thrift?
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

### 1. Think of a data system and give and example for the following concepts:
(answers may vary)
- **Database**: Facebook.
- **Information**: Mutual friends.
- **Data**: Friends changes
- **Queries**: How many friends does Tommy have?
- **Views**: Number of friends.
