# Login User Account

CompadOne uses central user and tenant management, allowing users to access different applications with a single user account. An user can login to a specific tenant or a specific application. 
During the login process, the user account is checked for the following:

- user activated
- user not disabled
- user not blocked due to too many incorrect login attempts
- user access to requested tenant
- user access to requested application

## Screen design

[<img src="/en/images/log-in.jpg" width="250"/>](login.png)

## Registration process

**Process**
```mermaid
flowchart TD
    start([start login])
    lookupemail[[lookup email]]
    start --> lookupemail
    checkemailexist{email exists}
    lookupemail --> checkemailexist
    checkemailexist --> |exist|checkpassword
    checkemailexist --> |not exist|loginfailed
    checkpassword{"`check password`"}
    checkpassword --> |correct|checkactivated
    checkpassword --> |invalid|failedattempt
    checkactivated{"`user activated`"}
    checkactivated --> |not activated|sendvalidationemail
    checkactivated --> |activated|checkblocked
    sendvalidationemail[[send validation email]]
    sendvalidationemail --> loginfailed
    failedattempt[[failed attempt]]
    failedattempt --> failedattemptcountermax
    failedattemptcountermax{max. failed attempts}
    failedattemptcountermax --> |limit failed attempts|blockaccount
    failedattemptcountermax --> |no limit failed attempts|loginfailed
    checkblocked{is account is block}
    checkblocked --> |current block|loginfailed
    checkblocked --> |current not block anymore|resetfailedattempt
    resetfailedattempt[[unlock account and reset failed attempt]]
    resetfailedattempt --> checkdisabled
    checkdisabled{check account is disabled}
    blockaccount[[block user account and send notivation email]]
    checkdisabled --> |disabled|loginfailed
    checkdisabled --> |enabled|checkproductline
    checkproductline{user access to productline}
    checkproductline --> |yes|checkappright
    checkproductline --> |no|loginfailed
    checkappright{user access to app}
    checkappright --> |yes|checktenant
    checkappright --> |no|loginfailed
    checktenant{tenant is requested}
    checktenant --> |tenant is given|checktenantaccess
    checktenant --> loginwithouttenant
    checktenantaccess{user access to tenant}
    checktenantaccess --> |yes|login
    checktenantaccess --> |no|loginfailed
    loginwithouttenant[login without tenant]
    login[login with tenant]
    loginfailed --> endlogin
    endlogin([end login])

```


## 🔗 Related information
- [login](login.md)
- [logout](logout.md)
- [forgot password](password-recovery-request.md)
- [email validate](user-confirmed.md)
- [inovate](user-inovate.md)


