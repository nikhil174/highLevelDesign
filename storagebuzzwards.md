<!-- Reference: Key Storage Buzzwords -->

**Relational Database**: A database structured to recognize relations among stored items of information, using tables with rows and columns.
    - Example: MySQL, PostgreSQL
    - Benefit: Enforces data integrity and supports complex queries with SQL.
    - Shortcoming: Can be less flexible and harder to scale horizontally.

**Non-relational Database**: A database that stores data in formats other than tables, such as documents, key-value pairs, or graphs.
    - Example: MongoDB, Cassandra
    - Benefit: Flexible schema, scales easily for large or unstructured data.
    - Shortcoming: May lack strong consistency and complex query support.

**SQL vs NoSQL**:
    - **SQL**: Uses structured query language for defining and manipulating data in relational databases.
        - Example: SELECT * FROM users WHERE age > 18;
        - Benefit: Strong consistency, ACID compliance, complex queries.
        - Shortcoming: Rigid schema, scaling can be challenging.
    - **NoSQL**: Refers to non-relational databases, often optimized for specific data models and access patterns.
        - Example: Storing JSON documents in MongoDB.
        - Benefit: High scalability, flexible schema, handles big data and real-time web apps.
        - Shortcoming: Weaker consistency guarantees, limited complex queries.

**Object Storage**: A storage architecture that manages data as objects, rather than files or blocks.
    - Example: Amazon S3, Google Cloud Storage
    - Benefit: Ideal for storing large amounts of unstructured data, like media files and backups.
    - Shortcoming: Not suitable for transactional data or frequent updates.

**Cache**: A high-speed data storage layer that stores frequently accessed data for quick retrieval.
    - Example: Redis, Memcached
    - Benefit: Reduces database load and improves application performance.
    - Shortcoming: Stale data if not updated properly, limited storage size.

**CDN (Content Delivery Network)**: A distributed network of servers that delivers content to users based on their geographic location.
    - Example: Cloudflare, Akamai
    - Benefit: Speeds up content delivery and reduces latency for global users.
    - Shortcoming: Extra cost and possible cache invalidation issues.