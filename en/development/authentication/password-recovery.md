# Register User Account

Users have one single user account forall the CompadOne applications. When the user forgot his password, he/she can start a password recovery procedure, by press on the 'forgotten password'.

**Validation process**
```mermaid
sequenceDiagram
    User->>CompadOne: Start password recovery (forgot password)?
    CompadOne-->>User: Send password recovery notification with link
    User->>CompadOne: Confirm password recovery
    CompadOne -->> User: Send notification email changing password
```

## Screen design

[<img src="/en/images/log-in.jpg" width="250"/>](login.png)

## Password recovery process

The password recovery procedure has three step. The first step generate an unique `password recovery request token' and send it by email to the user. In the second step the user can enter the request token or press on the link in the email.
When the combination 'username' and 'password recovery request token' match, the user can set an new password. There are the API available for password recovery.

- password-recovery-request
- password-recovery
- password

**Fase 1 - Password recovery request**

```mermaid
flowchart TD
    start([start register])
    lookupemail[[lookup email]]
    start --> lookupemail
    checkemailexist{email exists}
    lookupemail --> checkemailexist
    checkemailexist --> |exist|sendPasswordRecoveryEmail
    checkemailexist --> |not exists|passwordRecoveryFailed
    sendPasswordRecoveryEmail[[send password recovery email]]
    passwordRecoveryFailed[[password recovery failed]]
    sendPasswordRecoveryEmail --> endrecovery
    passwordRecoveryFailed --> endrecovery
    endrecovery([end password recovery])

```

**Fase 2 - Password recovery check**

```mermaid
flowchart TD
    start([start register])
    lookupemail[[lookup email]]
    start --> lookupemail
    checkemailexist{email exists}
    lookupemail --> checkemailexist
    checkemailexist --> |exist|checkPasswordRecoveryTokenCheck
    checkemailexist --> |not exists|passwordRecoveryFailed
    checkPasswordRecoveryTokenCheck{"`password recovery
      token match`"}
    checkPasswordRecoveryTokenCheck --> |yes|passwordRecovery
    checkPasswordRecoveryTokenCheck --> |no|passwordRecoveryFailed
    passwordRecovery[[password recovery is ok]]
    passwordRecoveryFailed[[password recovery failed]]
    passwordRecovery --> endrecovery
    passwordRecoveryFailed --> endrecovery
    endrecovery([end password recovery])

```

**Fase 3 - Change password**

```mermaid
flowchart TD
    start([start register])
    lookupemail[[lookup email]]
    start --> lookupemail
    checkemailexist{email exists}
    lookupemail --> checkemailexist
    checkemailexist --> |exist|checkPasswordRecoveryTokenSet
    checkemailexist --> |not exists|changepasswordfailed
    checkPasswordRecoveryTokenSet{"`password recovery
      request token or
      old password?`"}
    checkPasswordRecoveryTokenSet-->|password recovery request token|checkPasswordRecoveryToken
    checkPasswordRecoveryTokenSet-->|old password|checkOldPassword
    checkPasswordRecoveryToken{"`password
      recovery
      request token match`"}
    checkPasswordRecoveryToken --> |correct|changepassword
    checkPasswordRecoveryToken --> |not correct|changepasswordfailed
    checkOldPassword{"`old password
      match`"}
    checkOldPassword --> |valid password|changepassword
    checkOldPassword --> |invalid password|changepasswordfailed
    changepassword[[password changed]]
    changepassword --> endrecovery
    changepasswordfailed --> endrecovery
    changepasswordfailed[[password recovery failed]]
    endrecovery([end password recovery])

```

## 🔗 Related information API
- [password-recovery request](/api/password-recovery-request.md)
- [password-recovery](api/password-recovery.md)
- [change password](/api/password.md)


  ## 🔗 Related information
- [login](login.md)
- [logout](logout.md)
- [register](register.md)
- [invite](user-invite.md)

