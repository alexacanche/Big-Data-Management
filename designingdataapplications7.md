# Designing Data-Intensive Applications
 
## Chapter 7: Transactions

### 1. Dscribe what is transactions and why is it necessary
A transaction is a way for an application to group several reads and writes together into a logical unit. Transactions are not a law of nature; they were cre‐
ated with a purpose, namely to simplify the programming model for applications accessing a database. By using transactions, the application is free to ignore certain potential error scenarios and concurrency issues, because the database takes care ofthem instead (we call these safety guarantees).
 
### 2. Describe each concept of ACID
![acid](img/45.png)

### 3.  Investigate about the benefits of ACID
- **Absolute Data Integrity and Safety**: Avoiding lost updates, dirty reads, stale reads, and enforcing app-specific integrity constraints are critical concerns for app developers. Solving these concerns directly at the database layer using the consistency provided by ACID transactions is a much simpler approach.
- **Simplified Concurrency Control**: Concurrent access to shared resources such as retail inventory, bank balance, and gaming leaderboards is unavoidable. Isolation in ACID transactions come to the rescue of app developers. E.g. when a database guarantees transactions with serializable isolation, developers can treat each transaction as if it were executed sequentially, even though it may actually be executed concurrently.
- **Intuitive Data Access Logic**: ACID compliant databases usually allow complex schema modeling and native support for multi-step data manipulation operations such as consistent secondary indexes. Business logic can be now represented more directly in the application code.
- **Future-Proofing Database Needs**: Durability is rarely up for debate in databases where stable persistence is a must-have. Hence our view is that “in-memory” only systems should not be even considered databases! However, there is always an urge on part of developers to trade-off either Atomicity or Consistency or Isolation or some combination of them in return for higher performance in distributed databases. 

### 4.

## References
- https://blog.yugabyte.com/a-primer-on-acid-transactions/
