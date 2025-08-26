# Password recovery 

Check if the password recovery procedure was started. It's only an check

**URL** : `/api/v1/authentication/recovery/`

**Method** : `POST`

**Auth required** : NO

**Data constraints**

```json
{
    "username": "[valid email address]",
    "requesttoken": "[valid password recovery request token]",
}
```

**Data example**

```json
{
    "username": "esmeijer@compad.nl",
    "requesttoken": "93144b288eb1fdccbe46d6fc0f241a51766ecd3d",
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
