# Password recovery request

Send a password recovery request token to the user

**URL** : `/api/*version*/authentication/recovery/request/`

**Method** : `POST`

**Auth required** : NO

**Data constraints**

```json
{
    "username": "[valid email address]",
}
```

**Data example**

```json
{
    "username": "esmeijer@compad.nl",
}
```

## Success Response

**Code** : `200 OK`

**Content example**





> **Password recovery request** 
>
> After the password recovery request an email is send to the user. When the user clicks on the confirmation link
> the user is redirect to the password recovery page or the user can enter the request code into an password recovery confirmation
> form
>



## Error Response

**Condition** : If 'username' is not found

**Code** : `401 NOT FOUND

**Content** :

```json
{
    "username": [
        "no username found."
    ]
}
```
