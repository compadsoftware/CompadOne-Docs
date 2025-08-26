# Update tenant

An internal user with userrole 'Tenant administrator' have the permission `UpdateTenant` to update a new tenant.


**URL** : `/api/accounts/{id}`

**Method** : `PUT`

**Auth required** : YES

**Permissions required** : `UpdateTenant`

**Data constraints**

Provide name of Tenant to be created.


```json
{
    "companyName": "[1 to 200 chars]",
    "tradeName": "[1 to 200 chars]",
    "address": 
    {
      "street" :"[1 to 100 chars]",
      "homenumber" :"[1 to 100 chars]",
      "homenumberExtention" :"[1 to 100 chars]",
      "postalcode" :"[1 to 100 chars]",
      "city" :"[1 to 100 chars]",
      "region" :"[1 to 100 chars]"
      "countryCode" :"[1 to 100 chars]",
    },
    "chamberOfCommerce": "[1 to 100 chars]",
    "taxNumber": "[1 to 100 chars]",
    "phoneNumber": "[valid phonenumber]",
    "emailAddress": "[valid email address]",
    "website": "[valid url]",
}
```


**Data examples**


```json
{
    "companyName": "Compad Smart Business B.V.",
    "tradeName": "Compad Software",
    "address": 
    {
      "street" :"Demmersweg ",
      "homenumber" :"92",
      "homenumberExtention" :"",
      "postalcode" :"7556 BN",
      "city" :"Hengelo",
      "region" :"Overijssel",
      "countryCode" :"nl"
    },
    "chamberOfCommerce": "123456789",
    "taxNumber": "NL182.822.828.B.01",
    "phoneNumber": "+31(0)743200200",
    "emailAddress": "info@compad.nl",
    "website": "www.compad.nl",
}
```

## Success Response

**Condition** : If everything is OK and an Account didn't exist for this User.

**Code** : `200 OK

**Content example**

```json
{
    "id": "00000-00000-00000-00000",
}
```

#### Note

* After creating a new tenant a new instance will be created
* After creating a new tenant a new database will be created
* After creating the tenant, the user receives an invitation email
* Depending on the role of the user, the user can create new administrations (tenants) himself



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
