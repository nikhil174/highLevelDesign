<!-- Reference: Key Communication Buzzwords -->

**API (Application Programming Interface)**: A set of rules and protocols for building and interacting with software applications.
    - Why it matters: Enables different software systems to communicate and share data.

**REST (Representational State Transfer)**: An architectural style for designing networked APIs using HTTP methods.
    - Example: GET /users, POST /orders
    - Why it matters: Simple, stateless, and widely adopted for web services.

**GraphQL**: A query language for APIs that allows clients to request exactly the data they need.
    - Example: Querying only specific fields from a user object.
    - Why it matters: Reduces over-fetching and under-fetching of data, flexible for clients.

**gRPC (Google Remote Procedure Call)**: A high-performance, open-source framework for remote procedure calls using HTTP/2 and Protocol Buffers.
    - Example: Microservices communicating with each other in real time.
    - Why it matters: Efficient, supports multiple languages, and enables fast communication between distributed systems.

**MQ (Message Queue)**: A communication method used to send messages between different parts of a system asynchronously.
    - Example: RabbitMQ, Apache Kafka, AWS SQS.
    - Why it matters: Decouples services, smooths out traffic spikes, and enables reliable, scalable communication in distributed systems.