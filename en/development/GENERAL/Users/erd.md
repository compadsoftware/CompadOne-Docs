## Users ERD Diagram


```mermaid
erDiagram
    AppUser {
        guid id PK 
        string firstname
        string lastname
        boolean disabled       
        guid userAccount
        string pincode
    }
    AppUser ||--o{ userAccount : has
    AppUser ||--o{ UserRole : has
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
