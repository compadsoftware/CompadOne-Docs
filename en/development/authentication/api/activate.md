# Activate

Used to collect a Token for a registered User.

**URL** : `/api/v1/activate/`

**Method** : `POST`

**Auth required** : NO

**Data constraints**

```json
{
    "username": "[valid email address]",
    "activationCode": "[activation code in plain text]",
    "tenant": "[optional preferred tenant guid in plain text]"
}
```

**Data example**

```json
{
    "username": "esmeijer@compad.nl",
    "activationCode": "336367363",
    "tenant": "00000-00000-00000-00000"
}
```

## Success Response

**Code** : `200 OK`

**Content example**

```json
{
    "token": "93144b288eb1fdccbe46d6fc0f241a51766ecd3d"
}
```

## Error Response

**Condition** : If 'username' and 'activationCode' combination is wrong or empty

**Code** : `400 BAD REQUEST`

**Content** :

```json
{
    "non_field_errors": [
        "Unable to login with provided credentials."
    ]
}
```
