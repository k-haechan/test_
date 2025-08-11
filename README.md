## 🏛️ 아키텍처

```mermaid
graph TD
    subgraph "Client"
        A[User's Browser / Mobile App]
    end

    subgraph "AWS Cloud"
        B[CloudFront CDN]
        C[S3 Bucket for Media]
    end

    subgraph "Backend Infrastructure"
        D[API Gateway / Load Balancer]
        subgraph "SNS Server (Spring Boot)"
            E[Controller Layer <br> (REST & WebSocket)]
            F[Service Layer <br> (Business Logic)]
            G[Repository Layer <br> (Data Access)]
        end
        subgraph "Databases"
            H[MySQL <br> (Users, Posts, etc.)]
            I[Redis <br> (Cache, Pub/Sub)]
            J[MongoDB <br> (Chat History)]
        end
    end

    A --> D
    D --> E
    E --> F
    F --> G
    G --> H
    G --> I
    G --> J

    F --> B
    B --> C
```