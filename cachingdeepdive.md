<!-- Reference: Caching Deep Dive -->

**Read Caching Strategies**
- **Cache-Aside (Lazy Loading)**: Data is loaded into the cache only when requested.

  Pros:
  - increased fault tolerance
  - flexible data models

  Cons:
  - stale data

- **Read-Through**: Cache sits in front of the database and loads data automatically on cache miss.

  Pros:
  - no stale data

  Cons:
  - cache Failure (all request goes through cache)
  - less flexibility (db and cache should have same data)

**Write Caching Strategies**
- **Write-Aside (Lazy Write)**: Application writes data to the database and then invalidates or updates the cache.

  Pros:
  - faster writes
  - cache independence (increased fault tolerance)

  Cons:
  - slower reads
  - stale data

- **Write-Through**: Data is written to both cache and database at the same time.

  Pros:
  - no stale data
  - faster reads

  Cons:
  - Slower writes
  - cache dependency

- **Write-Back (Write-Behind)**: Data is written to cache first, then asynchronously to the database.

  Pros:
  - Faster writes
  - Faster reads

  Cons:
  - Risk of data loss 
  - cache dependency

