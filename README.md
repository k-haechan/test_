## 🏛️ 아키텍처

```mermaid
graph TD
    subgraph Client
        A["User's Browser / Mobile App"]
    end

    subgraph "AWS Cloud"
        B["CloudFront CDN"]
        C["S3 Bucket for Media"]
    end

    subgraph "Backend Infrastructure"
        D["API Gateway / Load Balancer"]
        subgraph "SNS Server (Spring Boot)"
            E["Controller (REST & WebSocket)"]
            F["Service (Business Logic)"]
            G["Repository (Data Access)"]
        end
        subgraph Databases
            H["MySQL (Users, Posts, etc.)"]
            I["Redis (Cache, Pub/Sub)"]
            J["MongoDB (Chat History)"]
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