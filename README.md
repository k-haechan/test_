## 🏛️ 아키텍처

```mermaid
graph TD
    subgraph Client
        ClientApp["User's Browser / Mobile App"]
    end

    subgraph Backend
        direction LR
        subgraph "SNS Server (Spring Boot)"
            Controller["Controller"]
            Service["Service"]
            Repository["Repository"]
        end
        subgraph "Databases"
            MySQL["MySQL"]
            Redis["Redis"]
            MongoDB["MongoDB"]
        end
    end


    subgraph "AWS Storage"
        CloudFront["CloudFront CDN"]
        S3["S3 Bucket"]
    end

    %% Flows
    ClientApp -- "1. API Calls" --> Controller
    Controller -- "2. Business Logic" --> Service
    Service -- "3. Data Access" --> Repository
    Repository -- "4. CRUD" --> MySQL & Redis & MongoDB

    ClientApp -- "6. Upload/Download Media" --> CloudFront
    CloudFront --> S3

    Service -- "5. Generates & returns Pre-signed URL" -.-> ClientApp
```
