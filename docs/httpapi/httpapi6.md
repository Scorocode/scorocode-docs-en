## Application statistics retrieval.

**https://api.scorocode.ru/api/v1/stat**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : ""  // access key, mandatory, masterKey only
}
```

**Responses:**

*Success*

```
{
    "error"       : false
    "results"     : {
        "dataSize"    : int, // Application data size, bytes
        "indexSize"   : int, // "Size" of application indexes, bytes
        "filesSize"   : int  // Application file size, bytes
    }
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
    "acc": "2aceceec7d2e96b1121ec399f5afa101"
}' "https://api.scorocode.ru/api/v1/stat"
```