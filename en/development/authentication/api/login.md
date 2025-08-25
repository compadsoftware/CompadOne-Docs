
# Login user
User login 


## Endpoints

**URL** : `/api/authentication/`

**Method** : `POST`

**Auth required** : NO

**Permissions required** : None

**Data constraints**

```json
{  "productCode": "[1 to 100 chars]",
    "applicationCode": "[1 to 100 chars]"
    "emailAddress": "[email address]",
    "password": "[1 to 100 chars]",
    "tenantId": "[1 to 100 chars, optional]",
}
```


**Data examples**

```json
{   
    "productCode": "CompadOne",
    "applicationCode": "pos",
    "emailAddress": "esmeijer@compad.nl",
    "password": "12345",
    "tenantId": "0000-0000-0000-0000"
}
```
> [!IMPORTANT]  
> The registration process should be as simple as possible. Therefore, it is not necessary to confirm the email address ? immediately, but within 24 hours. Every time the user attempts to log in with an email address that has not yet been confirmed, a confirmation email will be sent.



### Success Responses

**Condition** :  If everything is OK 

**Code** : `200 OK`

**Content example** : Response will reflect back the user information. A
User with `id` of '00000-00000-00000-00000' sets their last login date/time` header of :

```json
{
    "user" : {
        "id": "0000-0000-0000-0000",
        "email": "esemeijer@compad.nl",
        "firstName": "Carol",
        "lastName": "Esmeijer"        
    },
    "token" : "93144b288eb1fdccbe46d6fc0f241a51766ecd3d":
}
```
#### Note

* If the account is not activated/confirmed resend the confirmation email (again)
* If the account is not activated/confirmed in 24 hours, the login will failed
* To activate an account, the user receives a validation email. By clicking on the activation link in the validation email, the account is activated
* Created accounts are external accounts and can fully manage new tenants and already created tenants independently
