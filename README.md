
## System Design

   >Software + Hardware + Network + Processess. eg:A Social Media App (Facebook,Instagram) The Whole App.
  
   > System Design is the process of designing the architecture, components, and interfaces for a system  so that it meets the end-user requirements.

   > ***Scalability*** and ***Reliability***: System design ensures systems can grow and handle increased demand without failure.

   > **Efficient Resource Management**: It helps in optimizing resource allocation, ensuring fast and responsive applications.

The goal is to create a well-organized and efficient structure that meets the intended purpose while considering factors like scalability, maintainability, and performance.

### High-Level Design (HLD)
It lays out the overall architecture of the system — how major components interact, what services or modules will exist, and how data flows among them.

Gives you the big picture: how the system fits together, its core structure, and major decisions.
Done by architects, stakeholders and managers.

### Low-Leve Design (LLD)
Gives developers a clear, actionable blueprint to build each component.
Once a High Level Design is built by stakeholders, it is the job of senior developers and designers to create a low level design.

## Steps for getting started with System Design

  1. Understand the requirements:
     Before you begin designing the system, you need to understand the requirements. This involves talking to stakeholders and users, reviewing existing documentation, and analyzing the business processes that the system will support.

  2. Define the system architecture:
     Once you have a clear understanding of the requirements, you can begin defining the system architecture. This involves identifying the major components of the system and the interfaces between them.
  3. Choose the technology stack:
     Based on the requirements and the system architecture, you can select the technology stack. This includes choosing the programming language, database, frameworks, and libraries that will be used to implement the system.
  4. Design the modules:
     you need to design the modules that will make up the system. This involves defining the functions that each module will perform and the data that it will manipulate.
  5. Plan for scalability:
     As you design the system, you need to consider how it will scale. This involves identifying potential bottlenecks and designing the system to handle increased loads.
  6. Consider security and privacy:
    Security and privacy should be a key consideration in system design. This involves identifying potential security threats and designing the system to mitigate them.
  7. Test and validate:
     Once the system design is complete, you need to test and validate it. This involves creating test cases and scenarios that simulate real-world usage and verifying that the system meets the requirements.

### Examples of Functional and Non-functional Requirements
 

1. Online Banking System

    1. Functional Requirements:
       Users should be able to log in with their username and password.
       Users should be able to check their account balance.
       Users should receive notifications after making a transaction.

    2. Non-functional Requirements:
       The system should respond to user actions in less than 2 seconds.
       All transactions must be encrypted and comply with industry security standards.
       The system should be able to handle 100 million users with minimal downtime.

### Horizontal Vs. Vertical Scaling: Which Should You Choose?

##### What Is Scalability?

 **Scalability** describes a system’s elasticity. While we often use it to refer to a system’s ability to grow.

      Scale Up = Horizontal Scaling
      Scale Out = Vertical Scaling
      Scale Down = Opposite Of This Both
    
Thus, scalability describes your system’s ability to adapt to change and demand. 

#### What Is Horizontal Scaling?

Horizontal scaling ( scaling out) refers to adding additional nodes or machines to your infrastructure to cope with new demands. If you are hosting an application on a server and find that it no longer has the capacity or capabilities to handle traffic, adding a server may be your solution.
[!Horizontal-Scaling](horizontal-scaling.webp)

High costs initially; optimal over time.
Higher Performance.
Faliaure Chances :Low because other machines in the cluster offer backup.
Want **Load Balancer** to Necessary to actively distribute the workload across the multiple nodes.
Not Want DwonTime
Distributed Archtiture.

similar to delegating workload among several employees instead of one.

#### What Is Vertical  Scaling?

Vertical scaling (aka scaling up) describes adding additional resources to a system so that it meets demand. How is this different from horizontal scaling?
While horizontal scaling refers to adding additional nodes, vertical scaling describes adding more power to your current machines. For instance, vertical scaling would mean upgrading the CPUs if your server requires more processing power. You can also vertically scale the memory, storage, or network speed.
[!Vertical-Scaling](vertical-scaling.webp)

Low-cost initially; less cost-effective over time.
Lower Performance.
Faliaure Chances:High since it’s a single source of failure
No Need of Load Balancer.
Any Archtiture.
Want DwonTime.



For example, Google spreads search queries across thousands of servers worldwide, boosting performance and enabling failover if one fails.

### Vertical-Scaling vs Horizontal-Scaling

[!Vertical-Scaling vs Horizontal-Scaling](scaling-type.webp)


### What Is Diagonal Scaling? And How Does It Compare?

Diagonal scaling is a hybrid approach that combines the best of vertical and horizontal scaling.

Instead of choosing one or the other, it starts by scaling vertically — adding CPU, RAM, or storage to a single server — until the system reaches a performance or cost threshold. Then, it shifts to horizontal scaling by cloning the optimized system across additional nodes.

eg:

    Uber started with vertical scaling — running its monolithic app on robust EC2 instances to support local traffic.

    As demand grew, they adopted horizontal scaling — splitting services like trip-matching and pricing across nodes and regions.

    Today, Uber still uses large instances for real-time services such as location tracking, while scaling out globally for reliability and performance.

    This diagonal scaling approach helps Uber stay fast, resilient, and ready for massive traffic.

Choosing between horizontal vs vertical scaling, or a diagonal approach, depends on your setup, budget, and traffic needs.

##### Use vertical scaling when:

        You’re just starting, and traffic is low or unpredictable.
        You need a quick, low-cost way to boost performance.
        Your app isn’t built for distributed systems.
        Downtime for upgrades won’t impact users.
        You’re using internal tools with stable demand.

##### Use horizontal scaling when:

        You need to serve users across locations.
        Uptime is critical and backups are essential.
        You expect rapid or steady growth.
        You’re running containerized or microservice-based apps.
        You want to avoid downtime during updates.

##### Use diagonal scaling when:

        You want to start simple and avoid overbuilding.
        Your app is growing fast, but it’s not yet ready for full horizontal scaling.
        You need high performance but aren’t ready for complex infrastructure.
        You want cost control early, with room to expand later.
        You’re migrating from a monolith to microservices gradually.

### Stateful Vs. Stateless Applications

  Knowing whether your application is stateful or stateless is key when designing your scaling strategy — it directly impacts how well your system can scale.

  #### Stateless applications

    Stateless apps don’t store session or user data on the server. Each request is processed independently.

    Examples: Web APIs, microservices, static content delivery.

  #### Stateful applications

      Stateful apps retain session or transactional data between requests. They require context to function correctly.

      Examples: Databases, authentication servers, real-time messaging.


#### On-Premise Vs. Cloud Scaling

**Cloud Scaling**

Service providers such as Azure and AWS have automatic scaling.
They can increase and decrease resources according to your requirements at any given time. They can scale up or out when traffic to your application is at its peak and scale down when demand is lessened. This provides organizations with more efficient and cost-effective scaling. 


### CAP Theorem

 CAP theorem states that in a distributed system, you can only have two out of three of the following properties:
***Consistency***: All nodes see the same data at the same time. When a write is made to one node, all subsequent reads from any node will return that updated value.
***Availability***: Every request to a non-failing node receives a response, without the guarantee that it contains the most recent version of the data.
***Partition Tolerance***: The system continues to operate despite arbitrary message loss or failure of part of the system (i.e., network partitions between nodes).

imagine you're running a website with two servers - one in the USA and one in Europe. When a user updates their public profile (let's say their display name), here's what happens:
   1. User A connects to their closest server (USA) and updates their name
   2. This update is replicated to the server in Europe
   3. When User B in Europe views User A's profile, they see the updated name.

everything works smoothly until we encounter a network partition - the connection between our USA and Europe servers goes down. Now we have a critical decision to make:
When User B tries to view User A's profile, should we:
   Option A: Return an error because we can't guarantee the data is up-to-date (choosing consistency)
   Option B: Show potentially stale data (choosing availability).

**This is where CAP theorem becomes practical - we must choose between consistency and availability.**

In the case, the answer is rather clear: we would rather show a user in Europe the old name of User A, rather than show an error. Seeing a stale name is better than seeing no name at all.

##### consistency

Some systems absolutely require consistency, even at the cost of availability:
*Ticket Booking Systems*: Imagine if User A booked seat 6A on a flight, but due to a network partition, User B sees the seat as available and books it too. You'd have two people showing up for the same seat!
*E-commerce Inventory*: If Amazon has one toothbrush left and the system shows it as available to multiple users during a network partition, they could oversell their inventory.
*Financial Systems*: Stock trading platforms need to show accurate, up-to-date order books. Showing stale data could lead to trades at incorrect prices.

##### availability Better 

The majority of systems can tolerate some inconsistency and should prioritize availability. In these cases, eventual consistency is fine. Meaning, the system will eventually become consistent, but it may take a few seconds or minutes.
*Social Media*: If User A updates their profile picture, it's perfectly fine if User B sees the old picture for a few minutes.
*Content Platforms (like Netflix)*: If someone updates a movie description, showing the old description temporarily to some users isn't catastrophic.
*Review Sites (like Yelp)*: If a restaurant updates their hours, showing slightly outdated information briefly is better than showing no information at all.
***The key question to ask yourself is: "Would it be catastrophic if users briefly saw inconsistent data?" If the answer is yes, choose consistency. If not, choose availability.***\


### ACID Model in DB

ACID stands for Atomicity, Consistency, Isolation, and Durability. It is a transaction processing model used in databases to ensure that data remains accurate and consistent during a transaction.

**Atomicity**: It ensures that a transaction is treated as a single unit of work, and either all the steps in a transaction must be completed successfully, or none of them must be executed at all. In other words, if a transaction fails, it is rolled back to the original state.

**Consistency**: It ensures that the data is always consistent (correct for all rules ) before and after a transaction. In other words, a transaction cannot leave the database in an inconsistent state.

**Isolation**: It ensures that each transaction is isolated from other concurrent transactions. This means that a transaction sees the state of the database before any concurrent transaction has modified it.

**Durability:** It ensures that the changes made by a transaction are permanent and will not be lost even if the system crashes.


### The BASE Model IN DB

BASE stands for Basically Available, Soft state, Eventually consistent. It is a database model used for distributed systems, which must be able to handle large volumes of data and a high degree of concurrency.

**Basically Available**: It means that the system is always available, even if there is a network partition or a node failure.

**Soft state**: It means that the state of the system can change over time, even without input

**Eventually Consistent**: It means that the system will eventually become consistent, although there may be some inconsistency in the meantime.

### Sharding vs Partitioning: Understanding Database Distribution.

##### Sharding 

Sharding is the process of dividing a database into smaller, more manageable pieces called "shards." Each shard contains a subset of the overall data and functions as an independent database. 

The shards are distributed across multiple servers, enabling the system to handle large datasets and high volumes of traffic. This approach balances the load among servers and allows for tailored optimizations for specific shards based on their data.

[!sharding](sharding.avif)

**Scalability**: Enables horizontal scaling by distributing data across multiple servers.
**Improved performance**: Reduces query load on individual servers due to data being distributed more widely.
**Fault tolerance**: Ensures that failure in one shard doesn’t affect others, increasing system reliability.

##### Partitioning

Partitioning is the process of dividing a large database table into smaller, more manageable segments called partitions—all within the same server and database system. Each partition holds a subset of the data based on a specified rule, such as date ranges, geographic regions, or customer IDs.

Unlike sharding, partitioning doesn’t spread data across multiple machines. Instead, it helps organize data internally to speed up queries and simplify maintenance.

[!partitioning](partitioning.avif)

both techniques aim to optimize database performance and scalability, they operate at different levels and serve distinct purposes.

When to use sharding
Use sharding when your system is hitting the limits of what a single database can handle

When to use partitioning
Use partitioning when your data is growing large, but you're still operating within a single server or database.


### Optimistic Locking vs Pessimistic Locking.

---
When multiple users/programs try to update the same data at the same time, we need a way to prevent conflicts (like overwriting each other’s changes).

#### **Pessimistic Locking**

* Assumes **conflicts are likely**, so it prevents them by **locking data before access**.
* A transaction locks the row/record/table, and no other transaction can modify it until the lock is released.

The system puts a lock on the data when someone starts reading/updating it.
Others who try to update the same data must wait until the lock is released.
Good when conflicts are very likely.

### Example:

* Two users want to update the same bank account balance.
* With pessimistic locking, the first user’s transaction locks the account record.
* The second user must **wait** until the first finishes before making changes.

* Prevents conflicts entirely.
* Good for **high-contention** systems (lots of simultaneous writes).
* Reduces concurrency (others may be blocked).
* Risk of **deadlocks** (two transactions waiting on each other’s locks).

---

####  **Optimistic Locking**

* Assumes **conflicts are rare**, so it lets transactions proceed without locking first.
* When committing, the system checks if the data was modified by someone else during the transaction.
* If a conflict is found → the transaction **fails/retries**.
When updating, the system checks if the data was modified by someone else (often by using a version number or timestamp).

If it was modified, the update fails, and the user must retry.

Good when conflicts are rare.

##### Example:

* Two users read a product price of `$100`.
* User A updates it to `$120`.
* User B tries to update it to `$110`, but the system detects the record was already changed.
* User B’s update **fails** and must retry with the new version.

* High concurrency (no blocking).
* No deadlocks.
* Better for **read-heavy workloads** with fewer conflicts.
* Conflicts cause retries (extra work).
* Bad for **high-contention** systems (lots of simultaneous writes).

---

| Feature       | Pessimistic Locking       | Optimistic Locking           |
| ------------- | ---------------------------- | ------------------------------- |
| Assumption    | Conflicts are **likely**     | Conflicts are **rare**          |
| How it works  | Locks data before access     | Allows access, checks on commit |
| Concurrency   | Low (blocking)               | High (no blocking)              |
| Risk          | Deadlocks                    | Rollbacks/retries               |
| Best use case | Write-heavy, high contention | Read-heavy, low contention      |

---

 In distributed **BASE systems**, optimistic approaches are more common because:

* Locking across many nodes is expensive.
* Eventual consistency works better if systems allow retries rather than blocking.
Pessimistic Locking = "Lock first, work later." (Safe but slow if many users)
Optimistic Locking = "Work first, check later." (Fast but may need retries).

### Strong consistency.

Strong consistency is a property in distributed systems that ensures that all nodes in the system see the same data at the same time, regardless of which node they are accessing.

### Eventual consistency

the system converges towards consistency, but during the transient period, users accessing 
different data centers may observe different versions of the data. This is the characteristic 
behavior of eventual consistency. While the system guarantees that updates will eventually be 
propagated and all nodes will reach a consistent state, there can be temporary discrepancies 
between nodes at any given moment.

[!EventualConsistency](eventualconsistancy.webp)


1. Data Accuracy:
    * Strong Consistency: Ensures that all nodes see the same data at the same time, guaranteeing immediate data accuracy and integrity. Users can always read the most recent write, and there are no stale or conflicting values.
    * Eventual Consistency: Temporarily allows nodes to be inconsistent, which may result in stale data being read until convergence occurs. This introduces the possibility of users seeing outdated values during the convergence process.

2. Performance:
    * Strong Consistency: Achieving strong consistency often involves increased coordination and communication among nodes, leading to higher latency for read and write operations. The system may experience more contention and slower responses due to the need for synchronous updates across replicas.
    * Eventual Consistency: The asynchrony of write propagation and reduced coordination overhead allows for lower latency and higher throughput for read and write operations. The system can scale more easily and handle larger numbers of concurrent requests.

3. Use Cases:
    * Strong Consistency: Best suited for scenarios where data integrity and consistency are critical, such as financial systems, e-commerce platforms, and critical business applications.
    * Eventual Consistency: Well-suited for applications where real-time consistency is not vital and where system availability and scalability are more important, such as social media platforms, content distribution networks, and collaborative systems.


### types of NoSQL Databases

   ##### 1. Document-Based NoSQL Databases 


    document-based NoSQL Databases store data in documents rather than rows and columns. They use JSON, BSON, or XML documents to store the data. The best thing about document-based NoSQL Databases is that businesses can store or retrieve in a form closest to the data objects used in the application.

    Documents are stored with flexible schemas. 
    It is easy to create and maintain documents. 
    There is no direct relationship between two documents, eliminating the need to have a foreign key. 
    Documents are available in JSON, BSON, and XML formats. 

    Popular Document-based NoSQL Databases are MongoDB, CouchDB, and Firebase Firestore. 

   ##### 2. Key-Value Stores 
   
   This is the simplest form of a NoSQL Database that stores each data element in a pair of keys and values. A unique key is allotted to each data element and is used to retrieve data. The values associated with each data element can be anything from strings to numbers to complex objects.

   Caching, real-time leaderboards, cloud-based scalable applications. 

        Popular key-value databases are Redis, Memcached, and Amazon DynamoDB. 

   ##### 3.Column-Oriented Databases

   column-based databases are NoSQL Databases that store data in columns, not rows. Businesses can efficiently run analytics on a few columns without looking at unwanted data. These databases are known for their efficiency in reading and retrieving data. Applications that deal with a large volume of data should go for columnar databases.

   Real-time analytics, IoT applications, large-scale Machine Learning models, applications that require distributed storage. 

        Popular Column-Oriented Databases are HBase, Apache Cassandra, Google Bigtable.

   ##### 4. Graph-Based Databases

   graph-based NoSQL Databases store data as nodes. Their main focus is to identify the relationships between different data elements. The connections between these nodes are called links or relationships. Here, data is simply represented as nodes and edges, and to retrieve relationships, quick graph traversal algorithms are used. 

        Some of the popular graph-based databases are Neo4j, Amazon Neptune, and ArangoDB. 

    
## What Is Caching?

 is a technique that allows computer applications to temporarily store data in a computer's memory for quick retrieval.

 the temporary storage area for this data is known as the cache. Caching frequently accessed data makes applications more efficient. Memory retrieval is much faster than accessing solid-state drives (SSDs), hard disk drives (HDDs), or network resources.

[!CACHING](caching.svg)

Caching is especially efficient when the application exhibits a common pattern of repeatedly accessing data that was previously accessed.

Memory caching works by first setting aside a portion of RAM to be used as the cache. As an application tries to read data, typically from a data storage system like a database, it checks to see if the desired record already exists in the cache. If it does, the application will read the data from the cache, thus eliminating the slower access to the database. If the desired record is not in the cache, the application reads the record from the source instead. It retrieves data and stores it in the cache, allowing the application to quickly access it in the future.

a least-recently-used (LRU) strategy removes the record that has not been accessed for the longest time compared to others in the cache. The underlying assumption is that if a record hasn’t been accessed in a while, it is less likely to be accessed again soon. In other words, recent records will likely be used again soon.

On the other hand, a least-frequently-used (LFU) strategy involves tracking how many times each record in the cache has been accessed. Under this strategy, the record with the fewest accesses is removed. The assumption is that a record used infrequently will unlikely be accessed again soon.

### Types of Caching

1. CPU Cache

    A small amount of memory is built into a computer’s central processing unit (CPU) that stores frequently accessed data and instructions. The CPU cache makes it faster for the CPU to get to data and instructions, so it doesn’t have to go to the slower main memory or storage devices as often.

2. Memory Cache

    Memory caching is a small portion of main memory (RAM) set aside as a temporary storage area for frequently accessed data. It helps to improve application performance by reducing the time it takes to access data from slower storage media like hard disk drives or networks.

3. Disk Cache

    This is a portion of main memory (RAM) used to store data that has recently been read from or written to a disk, such as a hard disk drive or solid-state drive. Disk caching helps reduce the number of read and write operations on the disk, improving the overall system performance.

4. Browser Cache

    A web browser's cache is a temporary storage area for web content, such as HTML pages, images, and other media. When a user visits a webpage, their browser stores a copy of its content in the cache. When the user revisits the same webpage, the browser can load the content from the cache rather than downloading it again, improving the page’s loading time.

5. Distributed Cache

    A distributed cache is a shared resource used by multiple computers within a network, designed to store frequently accessed data across various servers. By reducing the need to retrieve data from multiple servers, distributed caching enhances the performance of distributed systems. Additionally, it improves an application's scalability, as data can be cached in different locations. This setup allows more concurrent users to access the data with fewer requests.


#### What is a data center

A data center is a physical location that stores computing machines and their related hardware equipment. It contains the computing infrastructure that IT systems require, such as servers, data storage drives, and network equipment. It is the physical facility that stores any company’s digital data.

