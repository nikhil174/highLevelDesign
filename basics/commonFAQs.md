<!-- Reference: Common Database Indexing FAQs -->

**Database Indexing**
- **What is it?**
  - An index is a data structure (like a B-tree or hash) that improves the speed of data retrieval operations on a database table at the cost of additional space and slower writes.
- **How do we create indexes?**
  - Indexes are created using SQL commands such as `CREATE INDEX index_name ON table_name(column_name);` or automatically by the database for primary keys.
- **Does the DB automatically create indexes?**
  - Most databases automatically create indexes for primary keys and unique constraints. Other indexes must be created manually as needed.
- **Is it used every time? Why?**
  - Indexes are used by the database query optimizer when they help speed up data retrieval. However, for some queries (like those that scan most of the table), the optimizer may choose not to use an index.
- **Benefits:**
  - Faster query performance for lookups, joins, and sorting.
- **Shortcomings:**
  - Slower inserts, updates, and deletes; increased storage usage; may require maintenance.

**Why should we do capacity estimation?**
- To determine the number of servers and databases needed for expected load.
- For cost management and budgeting.
- To decide device type and specifications for all hardware.
- To identify if the system is read-heavy or write-heavy, which influences design choices.
- To ensure scalability and avoid performance bottlenecks as usage grows.

**Apache Kafka & Event Streaming**
- **Event Streaming:**
  - The practice of collecting, storing, processing, and analyzing streams of events (data points) in real time or for future analysis.
  - Example: User activity logs, financial transactions, IoT sensor data.
  - Why: Enables real-time analytics, monitoring, and responsive applications.
- **Apache Kafka:**
  - A distributed event streaming platform used to build real-time data pipelines and streaming applications.
  - Features: High throughput, fault tolerance, scalability, and durability.
  - Use Cases: Log aggregation, real-time analytics, data integration, messaging, and event sourcing.