## Create new document

**https://api.scorocode.ru/api/v1/data/insert**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, optional, masterKey for full access
    "sess"        : "", // session ID, mandatory if acc != masterKey and app security settings do not allow anonymous access for this operation
    "coll"        : "", // collection name, mandatory
    "doc"         : {}, // document with field_name:value pairs
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "items",
        "doc": {
            "exampleField": "Today is June, 18. It's Muriel's birthday! Muriel is now 20 years old. Happy Birthday, Muriel!",
            "anotherExampleField": "I don't know what to say. I used to want to be an astrophysicist. Unfortunately, this is true."
        }
    }' "https://api.scorocode.ru/api/v1/data/insert"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
        "error"       : false,
        "result"      : {}        // document with field_name:value pairs
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

----------------------------------------------------------------------------------------------


## Delete collection documents.

**https://api.scorocode.ru/api/v1/data/remove**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, optional, masterKey for full access
    "sess"        : "", // session ID, mandatory if acc != masterKey and app security settings do not allow anonymous access for this operation
    "coll"        : "", // collection name, mandatory
    "query"       : {}, // query with field_name/operator:value pairs, optional
    "limit"       : int // limit, optional, default value is 1000 
}
```

!!! warning "Limitations" 
    Deletes 1000 documents at max

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "items",
        "query": {
            "exampleField": { 
                "$eq": "Today is June, 18. It's Muriel's birthday! Muriel is now 20 years old. Happy Birthday, Muriel!"
            }
        }
    }' "https://api.scorocode.ru/api/v1/data/remove"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
        "error"       : false,
        "result"      : {
            "count"       : int, // Amount of deleted documents
            "docs"        : [] // Array of deleted documents _id's
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

----------------------------------------------------------------------------------------------


## Update collection documents.

**https://api.scorocode.ru/api/v1/data/update**

Method: `POST`

Headers: `Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, mandatory or masterKey for full access
    "sess"        : "", // session ID, mandatory if acc != masterKey and app security settings do not allow anonymous access for this operation
    "coll"        : "", // collection name, mandatory
    "query"       : {}, // query with field_name/operator:value pairs, optional
    "doc"         : {}, // document with operator:{field_name:value} pairs, mandatory
    "limit"       : int // limit, optional, default value is 1000 
}
```

!!! warning "Limitations" 
    Updates 1000 documents at max

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "items",
        "query": {
            "exampleField": { 
                "$eq": "Today is June, 18. It's Muriel's birthday! Muriel is now 20 years old. Happy Birthday, Muriel!"
            }
        },
         "doc": {
            "$set": {
                "exampleField": "Happy Birthday, Muriel!"
            }
        },
        "limit": 1
    }' "https://api.scorocode.ru/api/v1/data/update"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
        "error"       : false,
        "result"      : {
            "count"       : int, // Amount of modified documents
            "docs"        : [] // Array of modified documents _id's
        }
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

----------------------------------------------------------------------------------------------


##  Update document by _id.

**https://api.scorocode.ru/api/v1/data/updatebyid**

Method: `POST`

Headers: `Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, mandatory or masterKey for full access
    "sess"        : "", // session ID, mandatory if acc != masterKey and app security settings do not allow anonymous access for this operation
    "coll"        : "", // collection name, mandatory
    "query"       : {}, // query with "_id": "document identifier" pair, mandatory
    "doc"         : {}, // document with operator:{field_name:value} pairs, mandatory
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "items",
        "query": {
            "_id" : "jQ4ZwEbBUj"
        },
         "doc": {
            "$set": {
                "exampleField": "Happy Birthday, Muriel!"
            }
        }
    }' "https://api.scorocode.ru/api/v1/data/updatebyid"
    ```


**Responses:**

!!! success "Success"
    ```JSON
    {
        "error"       : false,
        "result"      : {} // updated document
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

----------------------------------------------------------------------------------------------


## Retrieve collection documents.

**https://api.scorocode.ru/api/v1/data/find**

Method: `POST`

Headers: `Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, mandatory or masterKey for full access
    "sess"        : "", // session ID, mandatory if acc != masterKey and app security settings do not allow anonymous access for this operation
    "coll"        : "", // collection name, mandatory
    "query"       : {}, // query with field_name/operator:value pairs, optional
    "sort"        : {}, // sort order, "field name":1/-1 format, optional
    "fields"      : [], // array of the field names to specify fields to be returned, optional
    "limit"       : int,// maximum number of results to be returned, optional, 50 by default
    "skip"        : int,// number of documents to be skipped, optional
}
```
!!! warning "Limitations" 
    Returns 100 documents at max

!!! warning "BSON" 
    Result will be returned in base64 encoded string with [BSON](https://ru.wikipedia.org/wiki/BSON) formatted data.

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "items",
        "query": {
            "exampleField": { 
                "$eq": "Today is June, 18. It's Muriel's birthday! Muriel is now 20 years old. Happy Birthday, Muriel!"
            }
        },
        "sort": {
            "updatedAt": 1
        }, 
        "fields": ["updatedAt", "exampleField", "anotherExampleField"],
        "limit": 10,
        "skip": 20
    }' "https://api.scorocode.ru/api/v1/data/find"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
        "error"       : false,
        "result"      : string // base64 encoded string with BSON formatted data  
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

----------------------------------------------------------------------------------------------


## Count collection documents.

**https://api.scorocode.ru/api/v1/data/count**

Method: `POST`

Headers: `Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, mandatory or masterKey for full access
    "sess"        : "", // session ID, mandatory if acc != masterKey and app security settings do not allow anonymous access for this operation
    "coll"        : "", // collection name, mandatory
    "query"       : {}, // query with field_name/operator:value pairs, optional
}
```
!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "items",
        "query": {
            "exampleField": { 
                "$eq": "Today is June, 18. It's Muriel's birthday! Muriel is now 20 years old. Happy Birthday, Muriel!"
            }
        }
    }' "https://api.scorocode.ru/api/v1/data/count"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
        "error"       : false,
        "result"      : int // Returns the count of documents that would match a query
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

