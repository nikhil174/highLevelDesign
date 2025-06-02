<!-- Reference: Key System Design Buzzwords -->

**Scalability**: The ability of a system to handle increased load by adding resources (hardware or software).
    - Example: Adding more servers to support more users.
    - Why it matters: Ensures your system can grow with demand.

**Availability**: The degree to which a system is operational and accessible when required for use.
    - Example: 99.99% uptime for a web service.
    - Why it matters: High availability means users can rely on your service.

**Consistency**: The guarantee that all users see the same data at the same time.
    - Strong Consistency: All reads return the most recent write.
    - Eventual Consistency: All updates will propagate eventually, but not instantly.
    - Why it matters: Impacts user experience and data correctness.

**Fault Tolerance / No SPOF (Single Point of Failure)**: The ability of a system to continue operating even if some components fail.
    - Example: Using redundant servers so if one fails, others take over.
    - Why it matters: Increases reliability and prevents total outages.

**CAP Theorem**: States that a distributed system can only guarantee two out of three: Consistency, Availability, and Partition Tolerance.
    - Example: In a network partition, you must choose between consistency and availability.
    - Why it matters: Guides design decisions for distributed systems.

**Partition Tolerance**: The ability of a distributed system to continue operating even if network failures or partitions occur, meaning some nodes cannot communicate with others.
    - Example: If a network link between data centers goes down, the system still works in both locations.
    - Why it matters: Real-world networks are unreliable, so systems must handle communication failures gracefully.