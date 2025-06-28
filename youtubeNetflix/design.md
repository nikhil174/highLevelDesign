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

---

## Capacity Estimation
- **Delhi Active Users:** 100 million
- **Monthly Active Users:** 2.5 billion

### Throughput
- **Write Throughput:** 0.4 million users upload videos per day (100 million / 250 = 0.4 million write records)
- **Read Throughput:** 1 billion read requests per day (100 million users × 10 videos each)

### Storage
- Main storage is for video files; metadata is minimal compared to video data.
- Average video size: 600MB
- Daily uploads: 0.4 million × 600MB ≈ 240TB/day
- 10-year storage: 240TB × 365 × 10 ≈ 876PB
- Videos must be stored reliably and be highly available

### Memory
- Cache is used for popular videos and metadata
- 1% of daily storage cached: 1% × 240TB ≈ 2.4TB
- Caching reduces latency and backend load

### Network / Bandwidth Estimation
- **Ingress:** 240TB/day ≈ 2.7GB/sec
- **Egress:** 1B reads/day × 600MB = 600PB/day ≈ 7TB/sec
- Network must support high upload and streaming throughput

---

## API Design

### Upload Content (Resumable Uploads)
- Large videos (10 minutes to 2 hours) cannot be uploaded in a single request.
- The client uploads video data in small chunks using multiple requests.
- **Step 1:** Initiate upload
    - **Method:** POST
    - **Endpoint:** `/v1/videos?uploadType=resumable`
    - **Request Body:** Video metadata (title, format, etc.)
    - **Response:** Server returns a resumable session URL (with an upload ID)
- **Step 2:** Upload video chunks
    - **Method:** PUT
    - **Endpoint:** Resumable session URL (e.g., `/v1/videos?uploadType=resumable&uploadId=123`)
    - **Request Body:** Binary video data (chunk)
- The client repeats Step 2 until the entire video is uploaded.
- This approach allows for reliable, large uploads and recovery from network interruptions.

### Stream Content
- Videos are streamed in chunks rather than as a single large file.
- The server provides a manifest file (playlist) containing the locations of all video chunks.
- **Step 1:** Get manifest file
    - **Method:** GET
    - **Endpoint:** `/v1/watch?v={videoId}`
    - **Response:** Manifest file with chunk URLs
- **Step 2:** Fetch video chunks
    - **Method:** GET
    - **Endpoint:** Chunk URLs (provided in manifest)
    - Video chunks are stored in the CDN, not on the main server.
- **Protocol:** HLS (HTTP Live Streaming)
    - HLS enables adaptive streaming, adjusting video quality based on the client's internet speed for a smooth viewing experience.