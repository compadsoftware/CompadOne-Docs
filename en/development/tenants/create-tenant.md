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


## 🔗 Related information API
- [create tenant](api/tenant-create.md)
- [update tenant](api/tenant-update.md)
- [delete tenant](api/tenant-delete.md)
- [switch tenant](api/tenant-switch.md)
- [get tenant](api/tenant-get.md)


## 🔗 Related information
- [general](index.md)
- [switch tenant](switch-tenant.md)

