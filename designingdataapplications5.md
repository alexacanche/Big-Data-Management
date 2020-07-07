# Designing Data-Intensive Applications
 
## Chapter 5: Replication

### 1. What are some reasons to replicate your data?
- To keep data geographically close to your users (and thus reduce latency).
- To allow the system to continue working even if some of its parts have failed (and thus increase availability).
- To scale out the number of machines that can serve read queries (and thus increase read throughput).

### 2. Make a comparision of Synchronous vs. Asynchronous Replication
