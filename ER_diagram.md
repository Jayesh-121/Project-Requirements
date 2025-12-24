``` mermaid
erDiagram
    USER {
        int id PK
        string username
        string email
        string password
        string bio
        string profile_image
        datetime created_at
    }

    TWEET {
        int id PK
        int user_id FK
        string content
        datetime created_at
        int parent_tweet_id
        int quoted_tweet_id
        boolean is_retweet
    }

    FOLLOW {
        int id PK
        int follower_id FK
        int following_id FK
        datetime created_at
    }

    LIKE {
        int id PK
        int user_id FK
        int tweet_id FK
        datetime created_at
    }

    NOTIFICATION {
        int id PK
        int sender_id FK
        int receiver_id FK
        int tweet_id FK
        string type
        boolean is_read
        datetime created_at
    }

    USER ||--o{ TWEET : creates
    USER ||--o{ FOLLOW : follows
    USER ||--o{ LIKE : likes
    USER ||--o{ NOTIFICATION : receives
    TWEET ||--o{ LIKE : has
    TWEET ||--o{ NOTIFICATION : triggers
    TWEET ||--o{ TWEET : replies_to
    TWEET ||--o{ TWEET : quotes


```
