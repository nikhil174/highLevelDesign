<!-- Reference: Caching Deep Dive -->

**Read Caching Strategies**
- **Cache-Aside (Lazy Loading)**: Data is loaded into the cache only when requested.

  Pros:
  - Simple
  - Reduces cache pollution
  - Only hot data cached

  Cons:
  - First read is slow (cache miss)
  - Possible cache stampede

- **Read-Through**: Cache sits in front of the database and loads data automatically on cache miss.

  Pros:
  - Transparent to application
  - Consistent cache population

  Cons:
  - More complex
  - May add latency on miss

**Write Caching Strategies**
- **Write-Aside (Lazy Write)**: Application writes data to the database and then invalidates or updates the cache.

  Pros:
  - Simple
  - Avoids stale cache
  - No risk of data loss in cache

  Cons:
  - Cache may be empty after write
  - Extra logic needed in application

- **Write-Through**: Data is written to both cache and database at the same time.

  Pros:
  - Data consistency
  - Simple recovery

  Cons:
  - Slower writes
  - Higher write amplification

- **Write-Back (Write-Behind)**: Data is written to cache first, then asynchronously to the database.

  Pros:
  - Fast writes
  - Reduces DB load

  Cons:
  - Risk of data loss on cache failure
  - Eventual consistency

