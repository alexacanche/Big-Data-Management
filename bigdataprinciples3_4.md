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


### 5. Desired properties for a big data system (add a short description for each one)
- **Robustness and fault tolerance**: Work no matter the issues with the machines and human mistakes.
- **Low latency reads and updates**: Real-time access and updates.
- **Scalability**: Handle huge amounts of data.
- **Generalization**: Must work with a variety of different applications.
- **Extensibility**: Open to changes without big losses. 
- **Ad hoc queries**: Mine a dataset arbitrarily.
- **Minimal maintenance**: Less work required to keep a system running smoothly.
- **Debuggability**: Show precisely the mistakes if donestributed, fault-tolerant storage system that can scale to petabytes of data. MapReduce is a horizontally scalable computation framework that integrates with HDFS


## Chapter 2: Data model for Big Data

### 1. Think of a data system and give and example for the following concepts:
(answers may vary)
- **Database**: Facebook.
- **Information**: Mutual friends.
- **Data**: Friends changes
- **Queries**: How many friends does Tommy have?
- **Views**: Number of friends.
