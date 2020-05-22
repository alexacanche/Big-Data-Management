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

### 3. Write an example of node using Thrift.
Is a merge of all of its propierties and better, such as handle very large amounts of data and parallelize large-scale batch computations on very large amounts of data.

### 4. Difference between information and data (write how can you achive data and its relation to data systems).
Data is the purest information, where nothing else is derived from. You find data by asking questions and when you get to where it's derived from anything you'll find data. Since data systems ask those question by looking through the entire dataset the more general definition is of a data system would be: query = function(all data)

### 5. Desired properties for a big data system (add a short description for each one)
- **Robustness and fault tolerance**: Work no matter the issues with the machines and human mistakes.
- **Low latency reads and updates**: Real-time access and updates.
- **Scalability**: Handle huge amounts of data.
- **Generalization**: Must work with a variety of different applications.
- **Extensibility**: Open to changes without big losses. 
- **Ad hoc queries**: Mine a dataset arbitrarily.
- **Minimal maintenance**: Less work required to keep a system running smoothly.
- **Debuggability**: Show precisely the mistakes if done any.

### 6. Give an exmaple of fully incremental architecture (different from the book).
Open question. (Example: the rating of movies for a certain page, saves the average of ratign fro movies until more people rate and the rate is incremented or decreased)

### 7. Describe some problems of the fully incremental architecture
- **Operational complexity**: When space is unsed a proccess called compaction is done to reclaim this space, unfortunately it lower the performance od the machine. 
- **Extreme complexity of achieving eventual consistency**: Being available for updates inpresence any failure.
- **Lack of human-fault tolerance**: A data system with human-fault tolerance is vital since they are unavoidable.

### 8. Give a brief and concise description of each layer of the lambda achitecture. 
- **Batch Layer**: Stores an immutable, constantly growing master dataset, and compute arbitrary
functions on that dataset.
- **Serving Layer**: When new batch views are available, the serving layer automatically swaps those in so that more up-to-date results are available.
- **Speed Layer**: Similar to batch layer, the only difference is that the speed layer only looks at recent data.

### 9. Write some 5 other examples of elastic clouds.
(answers may vary)
- Google cloud.
- Azure.
- Softlayer.
- Vmware.
- AlertLogic.

### 10. What is HDFS?
Is a distributed, fault-tolerant storage system that can scale to petabytes of data. MapReduce is a horizontally scalable computation framework that integrates with HDFS


## Chapter 2: Data model for Big Data

### 1. Think of a data system and give and example for the following concepts:
(answers may vary)
- **Database**: Facebook.
- **Information**: Mutual friends.
- **Data**: Friends changes
- **Queries**: How many friends does Tommy have?
- **Views**: Number of friends.
