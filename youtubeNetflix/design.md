# Requirements

## Functional Requirements
- There are two types of users: **Viewers** and **Creators**.
    - **Viewers** will consume the content.
        - Streaming capability on multiple devices (mobile, laptop, computer, etc.).
    - **Creators** will create and upload content.
        - Should receive a notification upon upload completion.

## Non-Functional Requirements
- **Viewers:**
    - **Low latency:** Viewers should not wait long; low buffering and lag.
    - **Scalability:** Millions of users can watch videos simultaneously.
    - **User Experience:** Good internet = high quality; poor internet = lower quality streams.
    - **Availability:** System should be highly available (99.9999% uptime).
- **Content Creators:**
    - **Scalability:** System should handle many upload requests at the same time.
    - **Security:** Uploaded content must be secure; unauthorized access and piracy must be prevented.
    - **Storage Reliability:** Uploaded videos should not disappear; reliable storage

Capacity Estimation 
    - Delhi Active Users. 100 million. 
    - Monthly active users. 2.5 billion. 

    Throughput. 
        - Write Throughput : We assume that one of 250 people upload the videos. That will be 100 million / 250. That will be 0.4 million users which means 0.4 million write records. 
        - Read throughput : We assume that one user watches 10 videos per day that will be around 10 into 100 million. Equal to one billion read request. 

    Storage
        - Main storage is for video files; metadata is minimal compared to video data.
        - Average video size: 600MB.
        - Daily uploads: 0.4 million × 600MB ≈ 240TB/day.
        - 10-year storage: 240TB × 365 × 10 ≈ 876PB.
        - Videos must be stored reliably and be highly available.

    Memory
        - Cache is used for popular videos and metadata.
        - 1% of daily storage cached: 1% × 240TB ≈ 2.4TB.
        - Caching reduces latency and backend load.

    Network / Bandwidth Estimation
        - Ingress: 240TB/day ≈ 2.7GB/sec.
        - Egress: 1B reads/day × 600MB = 600PB/day ≈ 7TB/sec.
        - Network must support high upload and streaming throughput.

