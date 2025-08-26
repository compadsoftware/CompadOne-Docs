
# Logout user
User logout for specific application 


## Endpoints

**URL** : `/api/*version*/authentication/`

**Method** : `POST`

**Auth required** : NO

**Permissions required** : None

**Data constraints**

```json
{
    "productlineCode": "[1 to 100 chars]",
    "applicationCode": "[1 to 100 chars]"
    "username": "[valid email address (1 to 300 chars)]",
}
```


**Data examples**

```json
{   
    "productlineCode": "CompadOne",
    "applicationCode": "pos",
    "username": "esmeijer@compad.nl",
}
```


### Success Responses

**Condition** :  If everything is OK 

**Code** : `200 OK`

**Content example** : Response will reflect back the user information.

## Error Response

**Condition** : If 'productlineCode', 'applicationCode' or 'username' are empty or 'productlineCode', 'applicationCode' doesn't exists.

**Code** : `401 BAD REQUEST`

**Content** :

```json
{
    "non_field_errors": [
        "Unable to login with provided credentials."
    ]
}
```

## Error Response

**Condition** : If 'username' doesn't exists

**Code** : `401 NOT FOUND

**Content** :

```json
{
    "non_field_errors": [
        "username not found."
    ]
}
```

## Error Response

**Condition** : If 'user' was not logged in

**Code** : `401 UNAUTHORIZED

**Content** :

```json
{
    "non_field_errors": [
        "Unable to login with provided credentials."
    ]
}
```
