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


