# Designing Data-Intensive Applications
 
## Chapter 1: Reliable, Scalable, and Maintainable Applications

### 1.  Exaplain each of the three component software systems must contain: 
- **Reliability:** Performing the correct function at the desired level of performance even in the face of adversity.
- **Scalability:** As the system grows (in data volume, traffic volume, or complexity), there should be reasonable ways of dealing with that growth.
- **Maintainability:** Over time, many different people will work on the system (engineering and operations, both maintaining current behavior and adapting the system to new use
cases), and they should all be able to work on it productively.

### 2. Think of a software example and describe it for each point of the expectations of reliability in software
(answers may vary)
**GITHUB**
- Performs the function that the user expected. (upload a file)
- Tolerates user mistakes or using the software in unexpected ways. (selects files with the same name as the one that are already in the repository)
- Performs good enough under the expected load and data volume. (charges fast even though the file is heavy)
- Prevents any unauthorized access and abuse. (trying to edit the file of someone else without forking)

### 3. Write other three other tools that can help increase the fault-tolerance like the netflix chaos monkey.
(answers may vary)
Gremlin, pumba, chaos toolkit, simian army, powerfulSeal, litmus, etc.

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

### 10. After reading the chapter, what are some advantages of using serialization frameworks?
- It is easy to use and can be customized.
- The serialized stream can be encrypted, authenticated and compressed.
- Serialized classes can support coherent versioning and are flexible enough to allow gradual evolution of your application's object.

