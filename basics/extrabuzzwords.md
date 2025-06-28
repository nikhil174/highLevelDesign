**Cloud Computing**
- Definition: Delivery of computing services (servers, storage, databases, networking, software) over the internet (the cloud).
- Benefits:
  - Scalability: Easily scale resources up or down as needed.
  - Cost Efficiency: Pay only for what you use, no need for heavy upfront investment.
  - Accessibility: Access services and data from anywhere.
  - Reliability: High availability and disaster recovery options.
  - Maintenance: Cloud provider handles updates and infrastructure management.

**Logging & Monitoring**
- Logging: Recording events, errors, and information about system operations for troubleshooting and auditing.
- Monitoring: Continuously tracking system performance, health, and usage to detect issues and ensure reliability.
- Why important: Helps identify problems, optimize performance, and maintain security.

**Hashing & Consistent Hashing**
- Hashing: Converts data into a fixed-size numeric code (hash) for fast lookup and storage.
  - Analogy: Like assigning a code to each book in a library for quick shelving and retrieval.
- Consistent Hashing: A technique to distribute data across multiple servers so that minimal data is moved when servers are added or removed.
  - Benefit: Improves scalability and fault tolerance in distributed systems.
  - Example: Used in distributed caches and databases to evenly distribute keys.

**CAP Theorem**

Ideally, you would want your system to be both consistent and available.

Let's say an accident happens that creates a partition in our system.

How will you tolerate the partition?

The CAP theorem says that either you can make your system available or you can make it consistent. You can’t have both at the same time.

Example:

Consider there is a social media company ‘SweetBook’. They have servers all around the world.

At 3pm, an accident happens and the connection between their New York and San Francisco servers is lost. They have a partition now.

At 3:30pm, your friend in New York posts something on social media.

Now there could be two scenarios:

- If SweetBook prioritizes availability, the site remains accessible, but you won't see the new post from your friend in New York—only posts from local San Francisco users.
- If SweetBook prioritizes consistency, you might see a message like "Website not available" when you try to access it from San Francisco.

You cannot have both at the same time.




