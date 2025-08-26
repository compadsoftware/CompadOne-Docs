
# Logout user
User logout for specific application 


## Endpoints

**URL** : `/api/authentication/`

**Method** : `POST`

**Auth required** : NO

**Permissions required** : None

**Data constraints**

```json
{
    "productlineCode": "[1 to 100 chars]",
    "applicationCode": "[1 to 100 chars]"
    "emailAddress": "[valid email address (1 to 300 chars)]",
}
```


**Data examples**

```json
{   
    "productlineCode": "CompadOne",
    "applicationCode": "pos",
    "emailAddress": "esmeijer@compad.nl",
}
```


### Success Responses

**Condition** :  If everything is OK 

**Code** : `200 OK`

**Content example** : Response will reflect back the user information.

## Error Response

**Condition** : If 'productlineCode', 'applicationCode' or 'emailAddress' are empty or 'productlineCode', 'applicationCode' doesn't exists.

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

**Condition** : If 'emailAddress' doesn't exists

**Code** : `401 NOT FOUND

**Content** :

```json
{
    "non_field_errors": [
        "Emailaddress not found."
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
