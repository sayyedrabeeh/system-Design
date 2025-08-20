
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