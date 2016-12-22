## Sending push notifications to devices.

**https://api.scorocode.ru/api/v1/sendpush**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "",     // application identifier, mandatory
    "cli"         : "",     // client key, mandatory
    "acc"         : "",     // access key, mandatory, messageKey or masterKey for full access
    "sess"        : "",     // session ID, mandatory, if acc != masterKey
    "coll"        : "",     // collection name, mandatory, "users", "roles" or "devices"
    "query"       : {},     // devices collection query for sampling addressees with field_name/operator:value pairs, optional
    "msg"         : {
        "text"        : "", // Email text
        "data"        : { } // object with transferred data
    }
}
```

**Responses:**

*Success*

```
{
    "count"       : int       //Количество отправленных сообщений 
    "error"       : false
}
```

*Error*

```
{
    "error"       : true,
    "errCode"     : 4XX/5XX, // Error code
    "errMsg"      : "Error text"
}
```

**cURL example**

```
curl -X POST -H "Content-Type: application/json" -d '{
    "app": "db8a1b41b8543397a798a181d9891b4c",
    "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
    "acc": "fb33e473e08515ff6b57ef6f59392e5d",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "devices",
    "query": {
        "userId": {
            "$exists": true
        }
    },
    "msg": {
        "text": "PUSH text"
    }
}' "https://api.scorocode.ru/api/v1/sendpush"
```

## Отправка sms на номера пользователей.

**https://api.scorocode.ru/api/v1/sendsms**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "",     // application identifier, mandatory
    "cli"         : "",     // client key, mandatory
    "acc"         : "",     // access key, mandatory, messageKey or masterKey for full access
    "sess"        : "",     // session ID, mandatory, if acc != masterKey
    "coll"        : "",     // collection name, mandatory, "users" or "roles"
    "query"       : {},     // users collection query for sampling the addressees with field_name/operator:value pairs, optional
    "msg"         : {
        "text"        : "", // sms text
    }
}
```

**Responses:**

*Success*

```
{
    "count"       : int      
    "error"       : false
}
```

*Error*

```
{
    "error"       : true,
    "errCode"     : 4XX/5XX, // Error code
    "errMsg"      : "Error text"
}
```

**cURL example**

```
curl -X POST -H "Content-Type: application/json" -d '{
    "app": "db8a1b41b8543397a798a181d9891b4c",
    "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
    "acc": "fb33e473e08515ff6b57ef6f59392e5d",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "users",
    "query": {
        "phone": {
            "$exists": true
        }
    },
    "msg": {
        "text": "SMS text"
    }
}' "https://api.scorocode.ru/api/v1/sendsms"
```