# Big Data Principles and Best Practices of Scalable Real-Time Data Systems
 
## Chapter 1: A new paradigm for Big Data

### 1. According to the first example of database, when does data become big data? cite evidence.
The five most important characteristics of big data are: volume, variety, veracity, value and velocity. During the story we can see how he handled the problem as he realized the big amount of information it was being generated, the importance of the data as he had a portion of it unavilable while a machine was down, the rapidity of real-time data as the page become more popular and more people visited the page, the validation of it while a human-fault tolerance was applied and it was impossible to know which data got damaged.
- > " The database can’t keep up with the load, so write requests to increment pageviews are timing out. "
- > " As the application gets more and more popular, you keep having to reshard the database into more shards to keep up with the write load. Each time gets more and more painful because there’s so much more work to coordinate. "
- > " Eventually you have so many shards that it becomes a not-infrequent occurrence for the disk on one of the database machines to go bad. That portion of the data is unavailable while that machine is down. "
- > " While working on the queue/worker code, you accidentally deploy a bug to production that increments the number of pageviews by two, instead of by one, for every URL. You don’t notice until 24 hours later, but by then the damage is done. Your weekly backups don’t help because there’s no way of knowing which data got corrupted. "

### 2. What were some mistakes with the first example and how could've been resolved?
- **Unawere of distribution.** The code needs to undestand its nature, and if the system had been created to know it could help with the shards, replication, and distributed queries and others.
- **Human-fault tolerance.** Since the code was created with this technique errors happened and data was lost. The system must be carefully thought out to limit the damage a human mistake can cause.
- **Immutable data.** Pageview counts were being stored as the core dataset, which was continuously being mutated as new pageviews came in, instead of storing the raw pageview information.

### 3. What is the Lambda Architecture compared to other data systems (Hadoop, Cassandr, Riak, etc.)?.
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
-AlertLogic.

### 10. What is HDFS?
Is a distributed, fault-tolerant storage system that can scale to petabytes of data. MapReduce is a horizontally scalable computation framework that integrates with HDFS


## Chapter 1: Data model for Big Data

### 1. According to the first example of database, when does data become big data? cite evidence.

