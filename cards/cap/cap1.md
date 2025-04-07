
**Flashcards 1-20: Conceptual Understanding**

<!-- Card Start -->

### Front

What is the primary data model used by relational databases?

### Back

Relational databases use a **fixed schema** with structured tables consisting of rows and columns, enforcing relationships via foreign keys. This model is ideal for systems requiring ACID transactions, such as banking applications.

<!-- Card End -->

<!-- Card Start -->

### Front

How do document databases handle schema flexibility?

### Back

Document databases store data as **JSON/BSON documents** with dynamic schemas, allowing for evolving data models. They are well-suited for applications like content management systems (CMS) where schema agility is important.

<!-- Card End -->
<!-- Card Start -->

### Front

Describe the data organization in wide-column databases.

### Back

Wide-column databases organize data into **column families**, where rows can have dynamic columns. Columns are stored separately, enabling efficient compression and querying of sparse data. This structure is beneficial for time-series data in IoT systems.

<!-- Card End --> 
<!-- Card Start -->

### Front

What scalability model do relational databases typically follow?

### Back

Relational databases generally rely on **vertical scaling**, enhancing a single server's capacity. While this ensures transactional integrity, it limits growth potential compared to horizontal scaling methods.

####  **Scalability & Performance**

|Aspect|Relational|Document|Wide-Column|
|---|---|---|---|
|**Scaling**|Vertical|Horizontal|Horizontal[5](https://www.scylladb.com/glossary/wide-column-database/)|
|**Write Throughput**|Moderate|High|Very High[5](https://www.scylladb.com/glossary/wide-column-database/)|
|**Query Complexity**|JOINs, transactions|Simple CRUD|Column-specific|

-


<!-- Card End -->
<!-- Card Start -->

### Front

Explain the CAP theorem in the context of distributed databases.

### Back

The CAP theorem states that a distributed data store can provide only two out of the following three guarantees: **Consistency**, **Availability**, and **Partition Tolerance**. In the event of a network partition, the system must choose between maintaining consistency or availability.

<!-- Card End -->


<!-- Card Start -->

### Front

Which type of database is best suited for applications requiring ACID compliance?

### Back

**Relational databases** are best suited for applications requiring ACID compliance due to their strong consistency and transactional support.

<!-- Card End -->  <!-- Card Start -->

### Front

How do document databases achieve horizontal scaling?

### Back

Document databases achieve horizontal scaling through **sharding**, distributing data across multiple servers to handle large volumes and ensure high availability.

<!-- Card End -->  <!-- Card Start -->

### Front

What is a common trade-off when using wide-column databases?

### Back

Wide-column databases optimize for read/write performance on specific columns but often have **limited transactional support**, making them less suitable for applications requiring complex transactions.

Wide-column databases like Cassandra are optimized for high throughput and scalability, but they often **sacrifice strong consistency and transactional support**.  
However, **Cassandra offers tunable consistency**, allowing developers to balance consistency and availability based on their needs.


<!-- Card End --> 

<!-- Card Start -->

### Front

In the CAP theorem, what does 'Partition Tolerance' mean?

### Back

**Partition Tolerance** means the system continues to operate despite an arbitrary number of messages being dropped or delayed by the network between nodes.

<!-- Card End --> <!-- Card Start -->

### Front

Why might a social media platform choose a document database over a relational database?

### Back

A social media platform might choose a document database for its **schema flexibility** and ability to handle unstructured data, accommodating evolving features and user-generated content more efficiently than a fixed-schema relational database.

<!-- Card End --> 

**Flashcards 21-40: Multiple Choice Questions**

<!-- Card Start -->

### Front

Which of the following is a characteristic of relational databases?

- **A**: Dynamic schemas
    
- **B**: Horizontal scaling by default
    
- **C**: Fixed schemas with structured tables
    
- **D**: Optimized for unstructured data
    

### Back

- **C**: Fixed schemas with structured tables
    

<!-- Card End -->  <!-- Card Start -->

### Front

Document databases are best suited for:

- **A**: Applications with fixed schemas
    
- **B**: Systems requiring complex joins
    
- **C**: Evolving data models with unstructured data
    
- **D**: Applications needing strong ACID compliance
    

### Back

- **C**: Evolving data models with unstructured data
    

<!-- Card End --> 
<!-- Card Start -->

### Front

Which database type uses column families for data organization?

- **A**: Relational databases
    
- **B**: Document databases
    
- **C**: Wide-column databases
    
- **D**: Key-value stores
    

### Back

- **C**: Wide-column databases
    

<!-- Card End --> 
<!-- Card Start -->

### Front

In the context of CAP theorem, if a system prioritizes consistency and partition tolerance, what does it sacrifice?

- **A**: Latency
    
- **B**: Availability
    
- **C**: Scalability
    
- **D**: Durability
    

### Back

- **B**: Availability
    

<!-- Card End --> <!-- Card Start -->

### Front

Which scaling strategy is commonly associated with document databases?

- **A**: Vertical scaling
    
- **B**: Horizontal scaling
    
- **C**: Diagonal scaling
    
- **D**: No scaling needed
    

### Back

- **B**: Horizontal scaling

####  **Scalability & Performance**

| Aspect               | Relational          | Document    | Wide-Column                                                            |
| -------------------- | ------------------- | ----------- | ---------------------------------------------------------------------- |
| **Scaling**          | Vertical            | Horizontal  | Horizontal[5](https://www.scylladb.com/glossary/wide-column-database/) |
| **Write Throughput** | Moderate            | High        | Very High[5](https://www.scylladb.com/glossary/wide-column-database/)  |
| **Query Complexity** | JOINs, transactions | Simple CRUD | Column-specific                                                        |


    

<!-- Card End --> 
<!-- Card Start -->

### Front

A system that requires high write throughput and can tolerate eventual consistency is best suited for which type of database?

- **A**: Relational database
    
- **B**: Document database
    
- **C**: Wide-column database
    
- **D**: Graph database
    

### Back

- **C**: Wide-column database
    

<!-- Card End --> <!-- Card Start -->

### Front

Which of the following is true about ACID transactions?

- **A**: They are commonly associated with NoSQL databases
    
- **B**: Ensure strong consistency and isolation
    
- **C**: Prioritize availability over consistency
    
- **D**: Are not suitable for complex queries
    

### Back

- **B**: Ensure strong consistency and isolation
    

<!-- Card End -->


<!-- Card Start -->

### Front

Why is partition tolerance considered non-negotiable in distributed systems?

### Back

Partition tolerance is essential because **network failures are inevitable** in distributed systems. Without P, a system cannot maintain availability or consistency during partitions, making it unreliable in real-world distributed scenarios.

<!-- Card End --> <!-- Card Start -->

### Front

What trade-off does a high-availability system typically accept according to the CAP theorem?

### Back

High-availability systems typically accept the **Availability + Partition Tolerance (AP)** trade-off, allowing the system to remain responsive by tolerating temporary inconsistencies or stale reads.

<!-- Card End --> <!-- Card Start -->

### Front

What happens in an AP system during a network partition?

### Back

An AP system **continues to operate and serve requests**, potentially returning stale or outdated data rather than failing or delaying responses. This prioritizes uptime and user experience.

<!-- Card End --> <!-- Card Start -->

### Front

Which type of database aligns with the AP trade-off in CAP theorem?

- **A**: PostgreSQL
    
- **B**: MongoDB
    
- **C**: Cassandra
    
- **D**: Both B and C
    

### Back

- **D**: Both B and C  
    Document (MongoDB) and Wide-column (Cassandra) databases often prioritize **Availability and Partition Tolerance**, making them suitable for high-availability systems.
    

<!-- Card End --> <!-- Card Start -->

### Front

What is the key downside of AP systems in terms of data accuracy?

### Back

AP systems accept **eventual consistency**, meaning updates may not be immediately visible across all nodes, which can lead to **temporary stale reads** or conflicts.

<!-- Card End -->


<!-- Card Start -->

### Front

What is a major **benefit** of prioritizing availability over consistency in e-commerce systems?

### Back

It enables **uninterrupted service** during peak loads (e.g., Black Friday), allowing users to browse, add to cart, and checkout even if some data (like inventory levels) is stale.

<!-- Card End --> <!-- Card Start -->

### Front

What is a common **risk** introduced by eventual consistency in product listings?

### Back

**Stale product data** may be shown to users, leading to potential cart abandonment or confusion due to outdated pricing or stock levels.

<!-- Card End --> <!-- Card Start -->

### Front

Which scenario in e-commerce requires **strong consistency** despite performance concerns?

### Back

**Payment processing**—ACID compliance is crucial to avoid double charges or inconsistent transaction states.

<!-- Card End --> <!-- Card Start -->

### Front

How can systems reduce the risk of overselling under eventual consistency?

### Back

By implementing **reserved inventory pools** and syncing stock levels for critical items in near real-time.

<!-- Card End --> <!-- Card Start -->

### Front

Which architectural strategy can help resolve order conflicts in distributed systems?

### Back

Use of **compensating transactions**, such as sagas, to roll back or adjust inconsistent operations post-facto.

<!-- Card End --> <!-- Card Start -->

### Front

Which of the following is an **operational challenge** in eventual consistency models?

- **A**: Schema migrations
    
- **B**: Conflict resolution due to divergent data versions
    
- **C**: Lack of ACID compliance in payment gateways
    
- **D**: Low cache hit ratios
    

### Back

- **B**: Conflict resolution due to divergent data versions
    

<!-- Card End --> <!-- Card Start -->

### Front

In what case is **eventual consistency** typically an acceptable trade-off?

- **A**: Real-time fraud detection
    
- **B**: Distributed payment authorization
    
- **C**: High-traffic shopping cart updates
    
- **D**: Identity verification during login
    

### Back

- **C**: High-traffic shopping cart updates
    

<!-- Card End --> <!-- Card Start -->

### Front

Which of the following systems prioritizes availability and scales horizontally with tunable consistency?

- **A**: MySQL
    
- **B**: Cassandra
    
- **C**: Redis Streams
    
- **D**: MongoDB
    

### Back

- **B**: Cassandra  
    (Cassandra supports AP trade-offs with tunable consistency levels.)
    

<!-- Card End --> <!-- Card Start -->

### Front

Which caching technique can mitigate stale data problems in eventually consistent systems?

- **A**: LRU eviction
    
- **B**: TTL with proactive invalidation
    
- **C**: Lazy writes
    
- **D**: Read-through caching only
    

### Back

- **B**: TTL with proactive invalidation
    

<!-- Card End --> <!-- Card Start -->

### Front

What is a potential **business impact** of weak consistency during a flash sale?

### Back

**Overselling**, which can lead to customer refunds, operational costs, and **damaged brand trust**.

<!-- Card End -->