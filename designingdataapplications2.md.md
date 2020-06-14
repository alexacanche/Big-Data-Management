# Designing Data-Intensive Applications
 
## Chapter 2: Data Models and Query Languages

### 1.  What do you consider that even though there were new data store approaches, the relational model dominate them?
The use of business data processing, which was performed on mainframe computers in the 1960s and ’70s. Other databases at that time forced application developers to think a lot about the internal representation of the data in the database. The goal of the relational model was to hide that implementation detail behind a cleaner interface.

### 2. What were the necessities that drove the creation of NoSQL databases?
- A need for greater scalability than relational databases can easily achieve, including
very large datasets or very high write throughput.
- A widespread preference for free and open source software over commercial
database products.
- Specialized query operations that are not well supported by the relational model.
- Frustration with the restrictiveness of relational schemas, and a desire for a more
dynamic and expressive data model.

### 3. Mention five Object-relational mapping (ORM) frameworks (different from the book).
(answers may vary)
- Apache Cayenne (Java implementation of Active record pattern, inspired by Ruby on Rails).
- DataNucleus (open-source JDO and JPA implementation, formerly known as JPOX).
- Ebean (open-source).
- EclipseLink (Eclipse persistence platform).
- Enterprise JavaBeans (EJB).

### 4. Imagine you are creating a relational database and you are now creating a table for shipping orders, using the many-to-many relationships how would you create your table?
