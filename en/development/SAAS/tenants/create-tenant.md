![][~concept]

[~concept]: https://img.shields.io/badge/-concept-ff0000.svg

# Create tenant

After the user had register an `UserAccount` he/she can create one or more tenants. Only user with the role `tenant administrator` can create new tenants and **external** users who are 
invited by another user can create a new tenant for his own business

**Creating tenant process**
```mermaid
sequenceDiagram
    User->>CompadOne: Create a new tenant
    User->>CompadOne: Purchase a plan for an App?
    CompadOne-->>Affliate: Send notification email
    CompadOne-->>Publisher: Send notification email
    CompadOne-->>All tenant-administrators: Send notification email
```

## Screen design

[<img src="/en/images/log-in.jpg" width="250"/>](login.png)

## Tenant creating process

Who can create an tenant?
- **external** users who where invited by another user, they can create a tenant for there own business
- users with an user role 'tenant administrators'

**Process**

```mermaid
flowchart TD
    start([start creating tenant])
    lookupuser[[lookup email]]
    start --> lookupuser
    lookupuser --> checkrights
    checkrights{check the rights}
    checkrights --> |no|creatingfailed
    checkrights --> |yes|checktenantunique
    checktenantunique{Tenant exists?}
    checktenantunique --> |not exist|createinstance
    checktenantunique --> |exists|creatingfailed
    createinstance --> createdatabase
    createdatabase --> createtenant
    createinstance[[create a application instance]]
    createdatabase[[create a application database]]
    createtenant[[create a tenant]]
    createtenant --> sendnotification
    sendnotification[[send notificationt]]
    sendnotification --> endcreating
    creatingfailed --> endcreating
    creatingfailed[[creating tenant failed]]
    endcreating([end creating])

```
> [!NOTE]  
> All administrative and financial processing for new tenants, including invoicing of subscriptions for these tenants and payments, is handled by CompadOne. We will use CompadOne for the invoicing itself.

## ERD Diagram




```mermaid
erDiagram
    User {
        guid id PK 
        string firstname
        string lastname        
        string emailaddress FK "Unique email address"
        string password
    }
    User ||--o{ UserTenantRole : has
    UserTenantRole {
        guid id PK 
        user user FK
        tenant tenant FK
        productline productline
        app application
    }
    UserTenantRole }|--o| ProductLine : has
    ProductLine {
        guid id PK 
        string code
        string name
    }
    ProductLine }|--o| App : has
    App {
        guid id PK 
        string code
        string name
    }
    UserTenantRole }|--o| App : has
    UserTenantRole }|--o| Tenant : has
    Tenant {
        guid id PK 
        string companyname
        string tradename
        string emailaddress
        string address
        string postalcode
        string city
        string region
        country country
        string bankaccount
        string phonenumber
        string website
        string taxnumber
    }
    UserTenantRole }o--|{ Role :has
    Role {
        guid id PK
        string name FK
    }
    Role }o--o{ Permission : has
    Permission {
        Guid id PK
        string name FK
    }

```


## 🔗 Related information API
- [create tenant](api/post.md)
- [update tenant](api/put.md)
- [delete tenant](api/delete.md)
- [switch tenant](api/switch.md)
- [get tenant](api/get.md)
- [get tenant](api/get-list.md)


## 🔗 Related information
- [general](index.md)
- [switch tenant](switch-tenant.md)

