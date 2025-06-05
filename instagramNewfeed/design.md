### Requirements

#### Functional Requirements
- **Social Media Post**: can be text, video, images  
- **Follow/unfollow other users**:  
- **News Feed**: feed from users that they follow in reverse chronological Order (Newest to Oldest)  
- **Like and Comment on other people's post**:  
- **User Notification**: user gets notification when another user likes or comments on the post  

#### Non-Functional Requirements
- **Availability**: should be highly available - 99.999% uptime  
- **Consistency**: eventual consistency, if the user posts something, it's okay if it doesn't show up immediately but appears within a few seconds (1 - 2 seconds)  
- **Latency**: if we click on home button newsfeed should load in 1 - 2 seconds  
- **Scalability**: the system should scale through the globe (500M DAU and 2B MAU)  
- **Extensibility**: easier to extend it in the future. If we need to add features like replying to a comment, post recommendations, or ads  
- **Usability**: for newsfeed system rendering should be super fast

---

### Capacity Estimation

#### DAU/MAU
- **DAU**: 500 million
- **MAU**: 2 Billion

#### Throughput
- **Write**
    1. **Creating Post**: 10% users post every day = 50 million / day
    2. **Following**
    3. **Commenting or Liking**
- **Read**
    - **Reading News Feed**: Single user watches 100 posts a day = 50 Billion / day

#### Storage
- **What we are storing**
    - **Posts**
        - Assumptions/day: 
            - Video: 20MB, 20% = 200TB
            - Images: 0.5MB, 60% = 15TB
            - Text Posts: 100KB, 20% = 1TB

#### Network & Bandwidth Estimation
- **Ingress**: (216 TB) / (24 × 60 × 60) ≈ **2.5 GB/second**
- **Egress**: 0.2 × 100 KB + 0.2 × 20 MB + 0.5 × 0.5 MB = **4.32 MB** per user per day
    - (50 billion × 4.32 MB) / (24 × 60 × 60) ≈ **2.5 TB/second**

#### API Design
- **Create a text post**
    - Method: POST
    - Endpoint: `/v1/posts`
    - HTTP Body:
      ```json
      {
        "userId": "abc",
        "description": "Excited for the europe trip",
        "hashtag": ["travel", "fun"]
      }
      ```
- **Create image/video post**
    - Image/video will be uploaded on object storage
    - Method: POST
    - Endpoint: `/v1/posts`
    - HTTP Body:
      ```json
      {
        "userId": "abc",
        "mediaUrl": "s3url", // url from object storage
        "description": "Relaxing",
        "hashtags": ["relax", "chilling"]
      }
      ```
- **Like/Comment on a post**
    - Method: POST
    - Endpoint: `/v1/comments`
    - HTTP Body:
      ```json
      {
        "userId": "abc",
        "postId": "1234",
        "comment": "Beautiful! Great Shot"
      }
      ```
- **Follow/Unfollow another user**
    - Method: POST
    - Endpoint: `/v1/follow`
    - HTTP Body:
      ```json
      {
        "followerId": "abc",
        "followingId": "def"
      }
      ```
- **Read the news feed**
    - Method: GET
    - Endpoint: `/v1/feeds/{userId}`


#### High Level Design

- **Follow/Unfollow another user**
  
  ![High Level Design](in1.png)
  - Graph DB stores follower and followee relationship efficiently.
  - Graph DB is specialized in storing relationship between data.

- **Create a text post**
  - Design is similar to in1.png except DB is not graph DB
  - Flow: client → API gateway → Load balancer → Postwriter Service → Post DB, API gateway → client

- **Read a news feed**
  
  ![News Feed Design](in2.png)
  - NewsFeedReader Service first finds all the users followed, then gets all the posts, then orders in reverse chronological order.

  **Optimizing**
  
  ![Optimized News Feed](in3.png)
  - Prepare news feed in advance
  - Once a post arrives in PostWriter Service, it also adds the {postId, userId} in message queue (MQ) after post is added in Post DB
  - NewsFeedGenerator (NFG) service is responsible for creating newsfeed for all users
  - NFG service pulls the message from MQ
  - NFG gets new post from Post DB, finds all the followers from Follow DB, adds the new feed to all the following users in Feed DB
  - The same info is updated in cache

- **Create an image/video post**
  
  ![Image/Video Upload Flow](in4.png)
  - Client requests a presigned URL to upload the image/video. A presigned URL allows the client to upload content directly to object storage.
  - API gateway routes the request to the presigned URL generator service, which generates the URL and returns it to the client.
  - Client uploads the content directly to object storage; object storage returns the URL of the uploaded content to the client.
  - Client requests for the post feed to the API gateway with the {postId, userId, mediaUrl}. The following steps are similar to the create text post request