## Sending a task to execute the server-side script.

**https://api.scorocode.ru/api/v1/scripts**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, mandatory, scriptKey or masterKey for full access
    "sess"        : "", // session ID, mandatory, if acc != masterKey
    "script"      : "", // script ID, mandatory
    "pool"        : {}  // data pool for transferring to a script context, optional
}
```

**Responses:**

*Success*

```
{
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
    "acc": "28f06b89b62165c33de55265166d8781",
    "sess": "6rnbKKGvLLdU9Sl9"
    "script": "57484fb91c5666544db25675",
    "pool": {
        "collname": "items",
        "key": "exampleField",
        "val": "Today is June, 18. It's Muriel's birthday! Muriel is now 20 years old. Happy Birthday, Muriel!"
    }
}' "https://api.scorocode.ru/api/v1/scripts"
```