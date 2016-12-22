## Uploading a file to storage.

**https://api.scorocode.ru/api/v1/upload**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, mandatory, fileKey or masterKey for full access
    "sess"        : "", // session ID, mandatory, if acc != masterKey
    "coll"        : "", // collection name, mandatory
    "docId"       : "", // document ID, mandatory
    "field"       : "", // field name, mandatory
    "file"        : "", // file name, mandatory
    "content"     : ""  // file body, base64 encoding, mandatory
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
    "acc": "8c23d74f447f63ce495cc8fd9ee4d543",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "items",
    "docId": "Y3bET236FX",
    "field": "attachment",
    "file": "file.txt",
    "content": "VEhJUyBJUyBGSUxFLUUtRS1FLUUtRS1FIQ=="
}' "https://api.scorocode.ru/api/v1/upload"
```

## Retrieve file.

**https://api.scorocode.ru/api/v1/getfile/{app}/{coll}/{field}/{docId}/{file}**

Method: `GET`

Query:

```
https://api.scorocode.ru/api/v1/getfile/{app}/{coll}/{field}/{docId}/{file}
```

, where

```
    {app}     - application identifier, mandatory
    {coll}    - collection name, mandatory
    {field}   - field name, mandatory
    {docId}   - document identifier, mandatory
    {file}    - file name, mandatory
```

**Responses:**

*Success*

```
    Status: 302 (Redirect to file)
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
curl -X GET -H "Content-Type: application/json" "https://api.scorocode.ru/api/v1/getfile/db8a1b41b8543397a798a181d9891b4c/items/attachment/Y3bET236FX/file.txt"
```

## File removal.

**https://api.scorocode.ru/api/v1/deletefile**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, mandatory, fileKey or masterKey for full access
    "sess"        : "", // session ID, mandatory, if acc != masterKey
    "coll"        : "", // collection name, mandatory
    "docId"       : "", // document ID, mandatory
    "field"       : "", // field name, mandatory
    "file"        : ""  // file name, mandatory
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
    "acc": "8c23d74f447f63ce495cc8fd9ee4d543",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "items",
    "docId": "Y3bET236FX",
    "field": "attachment",
    "file": "file.txt"
}' "https://api.scorocode.ru/api/v1/deletefile"
```