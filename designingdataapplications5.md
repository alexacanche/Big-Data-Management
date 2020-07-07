# Designing Data-Intensive Applications
 
## Chapter 5: Replication

### 1. What are some reasons to replicate your data?
- To keep data geographically close to your users (and thus reduce latency).
- To allow the system to continue working even if some of its parts have failed (and thus increase availability).
- To scale out the number of machines that can serve read queries (and thus increase read throughput).

### 2. Make a comparison of Synchronous vs. Asynchronous Replication
![comparison](img/39.png)

### 3. Summarize the process of setting up a follower
- Take a consistent snapshot of the leader’s database at some point in time—if possible, without taking a lock on the entire database. 
- Copy the snapshot to the new follower node.
- The follower connects to the leader and requests all the data changes that have happened since the snapshot was taken. This requires that the snapshot is associated with an exact position in the leader’s replication log.
- When the follower has processed the backlog of data changes since the snapshot, we say it has caught up. It can now continue to process data changes from the leader as they happen.

### 4. What is failover?
After the failure of a leader, one of the followers needs to be promoted to be the new leader, clients need to be reconfigured to send their writes to the new leader, and the other followers need to start consuming data changes from the new leader.

### 5.Write a brief description about the different replication logs methods
- **Statement-based replication**: the leader logs every write request (statement) that it executes and sends that statement log to its followers.
- **Write-ahead log (WAL) shipping**: the log is an append-only sequence of bytes containing all writes to the database. We can use the exact same log to build a replica on another node: besides writing the log to disk, the leader also sends it across the network to its followers.
- **Logical (row-based) log replication**: use different log formats for replication and for the storage engine, which allows the replication log to be decoupled from the  storage engine internals.
- **Trigger-based replication**: A trigger lets you register custom application code that is automatically executed when a data change (write transaction) occurs in a database system. The trigger hasthe opportunity to log this change into a separate table, from which it can be read by an external process.

### 6. How can you implement read-after-write consistency in a system with leader-based replication?
- When reading something that the user may have modified, read it from the leader; otherwise, read it from a follower.
- If most things in the application are potentially editable by the user, that approach won’t be effective, as most things would have to be read from the leader (negating the benefit of read scaling).
- The client can remember the timestamp of its most recent write—then the system can ensure that the replica serving any reads for that user reflects updates at least until that timestamp.
- If your replicas are distributed across multiple datacenters, any request that needs to be served by the leader must be routed to the datacenter that contains the leader.

### 7. How can you achive achieving monotonic reads?
Making sure that each user always makes their reads from the same replica (different users can read from different replicas).

### 8. How does the replication lag anomalies with violation of causality works?
![comparison](img/40.png)

### 9. Why isn't useful to use multi-leader setup within a single datacenter?
Because the benefits rarely outweigh the added complexity. However, there are some situations in which this configuration is reasonable.

### 10. The biggest disadvantage of multi-leader replication is the writing conflics, how can you solve them?
- One master per session If session writes do not interfere (e.g., data are only stored per user), this will avoid issues altogether.
- Converge to consistent state Apply a last-write-wins policy, ordering writes by timestamp (may loose data) or report conflict to the application and let it resolve it (same as git or Google docs)
- Use version vectors Modelled after version clocks, they encode happens before relationships at an object level.

### 11. What are three example topologies in which multi-leader replication can be set up?
![topo](img/41.png)

### 12. What are two mechanisms used in Dynamo-style datastores?
- **Read repair**: when a client makes a read from several nodes in parallel, it can detect any stale responses.
- **Anti-entropy process**: some datastores have a background process that constantly looks for differences in the data between replicas and copies any missing data from one replica to another.

### 13. If a write succeeded on some replicas but failed on others (for example because the disks on some nodes are full), and overall succeeded on fewer than w replicas, it is not rolled back on the replicas where it succeeded, what happens?
This means that if a write was reported as failed, subsequent reads may or may not return the value from that write.

### 14. What is hinted handoff?
Once the network interruption is fixed, any writes that one node temporarily accepted on behalf of another node are sent to the appropriate “home” nodes.

### 15. Define version vector
Version vectors are sent from the database replicas to clients when values are read, and need to be sent back to the database when a value is subsequently written. (Riak encodes the version vector as a string that it calls causal context.) The version vector allows the database to distinguish between overwrites and concurrent writes.

### References
- https://www.slideshare.net/HBaseCon/synchronous-replication-for-hbase
- https://gousios.org/courses/bigdata/dist-databases.html
 
