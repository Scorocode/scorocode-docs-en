## Create new document

**https://api.scorocode.ru/api/v1/data/insert**

Method: `POST`

Headers: `Content-Type: application/json`

```
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
    ```
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "items",
        "doc": {
            "exampleField": "We are here to laugh at the odds and live our lives so well that Death will tremble to take us.",
            "anotherExampleField": "The free soul is rare, but you know it when you see it - basically because you feel good, very good, when you are near or with them."
        }
    }' "https://api.scorocode.ru/api/v1/data/insert"
    ```


**Responses:**

!!! success "Success"
    ```
    {
        "error"       : false,
        "result"      : {}        // document with field_name:value pairs
    }
    ```

!!! failure "Error"
    ```
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```


## Удаление документа из коллекции.

**https://api.scorocode.ru/api/v1/data/remove**

Method: `POST`

Headers: `Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "acc"         : "", // access key, optional, masterKey for full access
    "sess"        : "", // session ID, mandatory if acc != masterKey and app security settings do not allow anonymous access for this operation
    "coll"        : "", // collection name, mandatory
    "query"       : {}, // запрос с парами имя_поля/оператор:значение, необязательный
    "limit"       : int // лимит количества удаляемых документов, необязательный, если не указан, то удалятся первые 1000 документов
}
```

!!! warning "Limitations" 
    Deletes 1000 documents at max

!!! tip "cURL example"
    ```
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "items",
        "query": {
            "exampleField": { 
                "$eq": "We are here to laugh at the odds and live our lives so well that Death will tremble to take us."
            }
        }
    }' "https://api.scorocode.ru/api/v1/data/remove"
    ```



**Responses:**

!!! success "Success"
    ```
    {
        "error"       : false,
        "result"      : {
            "count"       : int, // Amount of deleted documents
            "docs"        : [] // Array of deleted documents _id's
    }
    ```

!!! failure "Error"
    ```
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

## Изменение документов в коллекции.

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
    "query"       : {}, // запрос с парами имя_поля/оператор:значение, необязательный
    "doc"         : {}, // документ с парами оператор:значение, обязательный
    "limit"       : int // лимит количества обновляемых документов, необязательный, если не указан, то обновятся первые 1000 документов
}
```

!!! warning "Limitations" 
    Updates 1000 documents at max

**Responses:**

!!! success "Success"
    ```
    {
        "error"       : false,
        "result"      : {
            "count"       : int, // Amount of modified documents
            "docs"        : [] // Array of modified documents _id's
        }
    }
    ```

!!! failure "Error"
    ```
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

!!! tip "cURL example"
    ```
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "items",
        "query": {
            "exampleField": { 
                "$eq": "We are here to laugh at the odds and live our lives so well that Death will tremble to take us."
            }
        },
         "doc": {
            "$set": {
                "exampleField": "being alone never felt right. sometimes it felt good, but it never felt right."
            }
        },
        "limit": 1
    }' "https://api.scorocode.ru/api/v1/data/update"
    ```

##  Изменение одного документа в коллекции по идентификатору.

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
    "query"       : {}, // запрос в формате "_id" : "&ltидентификатор документа&gt", обязательный
    "doc"         : {}, // документ с парами оператор:значение, обязательный
}
```

!!! tip "cURL example"
    ```
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
                "exampleField": "being alone never felt right. sometimes it felt good, but it never felt right."
            }
        }
    }' "https://api.scorocode.ru/api/v1/data/updatebyid"
    ```


**Responses:**

!!! success "Success"
    ```
    {
        "error"       : false,
        "result"      : {} // обновленный документ
    }
    ```

!!! failure "Error"
    ```
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```


## Запрос документов из коллекции.

**https://api.scorocode.ru/api/v1/data/find**

Method: `POST`

Headers: `Content-Type: application/json`

```
{
    "app"         : "", // идентификатор приложения, обязательный
    "cli"         : "", // клиентский ключ, обязательный
    "acc"         : "", // ключ доступа, необязательный, для полного доступа masterKey
    "sess"        : "", // ID сессии, обязательный, если ACLPublic приложения на операцию == false и acc != masterKey
    "coll"        : "", // имя коллекции, обязательный
    "query"       : {}, // запрос с парами имя_поля/оператор:значение, необязательный, если пустой, то будут возвращены первые 100 документов
    "sort"        : {}, // сортировка по полям в формате имя_поля:1/-1, необязательный
    "fields"      : [], // список имен полей, которые будут возвращены в каждом документе, необязательный
    "limit"       : int,// лимит размера выборки, необязательный, по умолчанию 50
    "skip"        : int,// количество документов, которое нужно пропустить в выборке
}
```
!!! warning "Limitations" 
    Returns 100 documents at max

!!! warning "BSON" 
    Для повышения производительности сервиса результат выборки метода **find** возвращается в формате [bson](https://ru.wikipedia.org/wiki/BSON). Все SDK самостоятельно реализуют декодирование bson в json.

!!! tip "cURL example"
    ```
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "acc": "",
        "sess": "rYgRe6xL2y8VccMJ",
        "coll": "items",
        "query": {
            "exampleField": { 
                "$eq": "being alone never felt right. sometimes it felt good, but it never felt right."
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
    ```
    {
        "error"       : false
        "result"      : string // base64 encoded string with BSON formatted data  
    }
    ```

!!! failure "Error"
    ```
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```



## Запрос количества документов из коллекции.

**https://api.scorocode.ru/api/v1/data/count**

Method: `POST`

Headers: `Content-Type: application/json`

```
{
    "app"         : "", // идентификатор приложения, обязательный
    "cli"         : "", // клиентский ключ, обязательный
    "acc"         : "", // ключ доступа, необязательный, для полного доступа masterKey
    "sess"        : "", // ID сессии, обязательный, если ACLPublic приложения на операцию == false и acc != masterKey
    "coll"        : "", // имя коллекции, обязательный
    "query"       : {}, // запрос с парами имя_поля/оператор:значение, необязательный
}
```

**Responses:**

!!! success "Success"

```
{
    "error"       : false
    "result"      : int // количество документов
}
```

!!! failure "Error"

```
{
    "error"       : true,
    "errCode"     : 4XX/5XX, // Error code
    "errMsg"      : "Error text"
}
```

!!! tip "cURL example"

```
curl -X POST -H "Content-Type: application/json" -d '{
    "app": "db8a1b41b8543397a798a181d9891b4c",
    "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
    "acc": "",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "items",
    "query": {
        "exampleField": { 
            "$eq": "being alone never felt right. sometimes it felt good, but it never felt right."
        }
    }
}' "https://api.scorocode.ru/api/v1/data/count"
```