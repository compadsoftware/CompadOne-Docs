# Password update 

Check if the password recovery procedure was started. It's only an check

**URL** : `/api/v1/authentication/password/`

**Method** : `POST`

**Auth required** : NO

**Data constraints**

```json
{
    "username": "[valid email address]",
    "requesttoken": "[optional valid password recovery request token]",
    "oldpassword": "[optional valid old password]",
    "newpassword": "[optional valid new password]"
}
```

**Data example**

```json
{
    "username": "esmeijer@compad.nl",
    "requesttoken": "93144b288eb1fdccbe46d6fc0f241a51766ecd3d",
    "newpassword": "12345new"
}
```


```json
{
    "username": "esmeijer@compad.nl",
    "oldpassword": "12345",
    "newpassword": "12345new"
}
```
## Success Response

**Code** : `200 OK`

**Content example**





> **Password reset** 
>
> After the password reset request an email is send to the user. When the user clicks on the confirmation link
> the user is redirect to the password recovery page
>



## Error Response

**Condition** : If 'username' and 'password' combination is wrong.

**Code** : `401 NOT FOUND

**Content** :

```json
{
    "username": [
        "no username found."
    ]
}
```

## Error Response

**Condition** : If 'username' and 'requesttoken' combination is wrong.

**Code** : `400 BAD REQUEST

**Content** :

```json
{
    "username": [
        "no username found."
    ]
}
```
