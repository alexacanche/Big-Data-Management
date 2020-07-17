# Designing Data-Intensive Applications
 
## Chapter 6: Partitioning

### 1. Why is convenient to use partitions?
The main reason for wanting to partition data is scalability. Different partitions can be placed on different nodes in a shared-nothing cluster. Thus, a large dataset can be distributed across many disks, and the query load can be distributed across many processors.

### 2. How does work combining replication and partitioning?
Each node acts as leader for some partitions and follower for other partitions.
![combining](img/42.png)

### 3.
