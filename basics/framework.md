# Design Framework

A clear and structured approach to system design. Use the phrase: **"RACE AND PLAN"** to remember the steps.

- **R**equirements
    - Functional: What should the system do?
        - Example: Users can upload and share photos.
    - Non-functional: Performance, reliability, scalability, etc.
        - Example: The system should handle 1,000 uploads per minute with 99.9% uptime.
- **A**ssess Capacity
    - Estimate Monthly/ Daily Active Users (MAU/DAU)
        - Example: Expecting 100,000 MAU and 10,000 DAU.
    - Throughput: Requests per second
        - Example: 200 API requests per second during peak hours.
    - Storage/Memory: Data size and memory needs
        - Example: 1TB of images stored per month.
    - Network Bandwidth: Data transfer requirements
        - Example: 500GB data transfer per day.
- **C**reate APIs
    - Define endpoints, request/response formats, and error handling
        - Example: POST /upload-photo with JSON response and error codes.
- **E**stablish High-Level Design
    - Identify main components and their interactions
        - Example: Web server, application server, database, object storage.
- **AND**
- **PLAN** Deep Dive
    - Detail each component: data models, algorithms, scaling, bottlenecks
        - Example: Photo metadata schema, image compression algorithm, sharding database for scale, CDN for fast delivery.

**Phrase to remember:**
> "RACE AND PLAN your system design!"

This framework ensures you cover all critical aspects from requirements to detailed design.