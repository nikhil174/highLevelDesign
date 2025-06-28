<!-- Reference: Key System Design Terms -->

**client**: A device or application that requests and uses services or resources from a server.
    - Example: A web browser accessing a website.
    - Use: To interact with servers and access resources.
    - Benefit: Enables user access to remote data and services from anywhere.
    - Shortcoming: Limited by server availability and network speed.

**server**: A system or program that provides services or resources to clients over a network.
    - Example: A web server hosting a website.
    - Use: To serve data and resources to multiple clients.
    - Benefit: Centralizes resources and services for many users.
    - Shortcoming: Can become a bottleneck or single point of failure.

**Database**: A structured system for storing, managing, and retrieving data.
    - Example: MySQL, MongoDB.
    - Use: Centralized data storage and querying.
    - Benefit: Enables efficient, organized, and reliable data management.
    - Shortcoming: Can be a performance bottleneck if not scaled.

**Vertical Scaling**: Increasing the resources (CPU, RAM) of a single server.
    - Example: Upgrading a server from 8GB to 32GB RAM.
    - Use: Simple way to improve performance.
    - Benefit: Fastest way to boost performance for small to medium workloads.
    - Shortcoming: Limited by hardware; expensive at scale.

**Horizontal Scaling**: Adding more servers to distribute the load.
    - Example: Adding more web servers behind a load balancer.
    - Use: Handles more traffic and improves reliability.
    - Benefit: Supports high availability and large-scale growth.
    - Shortcoming: More complex to manage and synchronize.

**Load Balancer**: Distributes incoming traffic across multiple servers.
    - Example: NGINX, AWS ELB.
    - Use: Prevents any one server from being overwhelmed.
    - Benefit: Ensures even traffic distribution and improves system reliability.
    - Shortcoming: Can be a single point of failure if not redundant.

**Database Sharding**: Splitting a database into smaller, more manageable pieces (shards).
    - Example: User data split by region.
    - Use: Improves performance and scalability.
    - Benefit: Allows handling of very large datasets and high traffic.
    - Shortcoming: Increases complexity and risk of uneven data distribution.

**Database Replication**: Copying data from one database server to others.
    - Example: Master-slave replication in MySQL.
    - Use: Improves availability and read performance.
    - Benefit: Provides redundancy and disaster recovery.
    - Shortcoming: Data consistency issues and replication lag.

**Cache**: Temporary storage for frequently accessed data.
    - Example: Redis, Memcached.
    - Use: Reduces database load and speeds up responses.
    - Benefit: Greatly improves response time for users.
    - Shortcoming: Stale data if not updated properly.

**CDN (Content Delivery Network)**: Distributes content to servers closer to users.
    - Example: Cloudflare, Akamai.
    - Use: Faster content delivery and reduced latency.
    - Benefit: Improves user experience globally and reduces server load.
    - Shortcoming: Extra cost and possible cache invalidation issues.

**Monolith**: All components in a single codebase/application.
    - Example: Traditional web app with frontend, backend, and database together.
    - Use: Simple to develop and deploy initially.
    - Benefit: Easier to start and manage for small teams or projects.
    - Shortcoming: Hard to scale and maintain as it grows.

**Microservice**: Application split into small, independent services.
    - Example: Separate services for user, payment, and notification.
    - Use: Easier to scale and maintain; independent deployments.
    - Benefit: Enables independent scaling, deployment, and development.
    - Shortcoming: More complex communication and deployment.

**Message Queue**: System for asynchronous communication between services.
    - Example: RabbitMQ, Kafka.
    - Use: Decouples services and smooths out traffic spikes.
    - Benefit: Handles bursty workloads and improves system resilience.
    - Shortcoming: Adds latency and complexity; risk of message loss.

**API Gateway**: Entry point that routes requests to appropriate services.
    - Example: AWS API Gateway, Kong.
    - Use: Centralizes authentication, logging, and routing.
    - Benefit: Simplifies client interaction and centralizes cross-cutting concerns.
    - Shortcoming: Can become a bottleneck or single point of failure.