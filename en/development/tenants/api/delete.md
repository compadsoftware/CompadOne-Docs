# Update tenant

An internal user with userrole 'Tenant administrator' have the permission `UpdateTenant` to update a new tenant.


**URL** : `/api/accounts/{id}`

**Method** : `DELETE`

**Auth required** : YES

**Permissions required** : `DeleteTenant`

**Data constraints**

Provide name of Tenant to be created.



## Success Response

**Condition** : If everything is OK and the tenant is deleted

**Code** : `200 OK

**Content example**

```json
{
    "id": "00000-00000-00000-00000",
}
```

#### Note

* The tenant wil only soft-deleted



## Error Responses

**Condition** : If tenant couldn't updated

**Code** : `303 SEE OTHER`

**Headers** : `Location: http://testserver/api/accounts/00000-00000-00000-00000/`

**Content** : `{}`

### Or

**Condition** : If fields are missed.

**Code** : `400 BAD REQUEST`

**Content example**

```json
{
    "name": [
        "This field is required."
    ]
}
```
