# mermaid2

```mermaid
erDiagram
    GROUP {
        int id PK
        string name "UNIQUE"
        string description
        string photoUrl
        int goalRep "DEFAULT 0"
        string discordWebhookUrl
        string discordInviteUrl
        int likeCount "DEFAULT 0"
        string[] tags
        int owner_id FK "REFERENCES USER(id)"
        string[] badges
        datetime createdAt "DEFAULT NOW()"
        datetime updatedAt "DEFAULT NOW()"
    }

    GROUP_PARTICIPANT {
        int id PK
        int group_id FK "REFERENCES GROUP(id)"
        string user_id "UNIQUE"
        string user_password
        datetime joinedAt "DEFAULT NOW()"
        %% UNIQUE(group_id, user_id) 추가해야 함
    }



    EXERCISE_RECORD {
        int id PK
        int group_id FK "REFERENCES GROUP(id)"
        int user_id FK "REFERENCES USER(id)"
        string[] exerciseType
        string description
        int duration "time"
        float distance "in km"
        string[] photos
        datetime createdAt "DEFAULT NOW()"
    }

    GROUP --o{ GROUP_PARTICIPANT : "has many participants"
    GROUP --o{ EXERCISE_RECORD : "contains"
```
