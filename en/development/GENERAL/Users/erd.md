## Users ERD Diagram


```mermaid
erDiagram
    User {
        guid id PK 
        string firstname
        string lastname
        boolean disabled       
        guid userAccount
        string pincode
    }
    User ||--o{ userAccount : has
    User ||--o{ UserRole : has
    UserRole {
        guid id PK 
        user user FK
        role role FK
    }
    UserRole }o--|{ Role :has
    Role {
        guid id PK
        string name FK
    }
    Role }o--o{ Permission : has
    Permission {
        Guid id PK
        string name FK
    }
