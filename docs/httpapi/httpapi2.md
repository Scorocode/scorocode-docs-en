## Создание нового документа в коллекции.

**https://api.scorocode.ru/api/v1/data/insert**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // идентификатор приложения, обязательный
    "cli"         : "", // клиентский ключ, обязательный
    "acc"         : "", // ключ доступа, необязательный, для полного доступа masterKey
    "sess"        : "", // ID сессии, обязательный, если ACLPublic приложения на операцию == false и acc != masterKey
    "coll"        : "", // имя коллекции, обязательный
    "doc"         : {}, // документ с парами имя_поля:значение, необязательный
}
```

**Responses:**

*Success*

```
{
    "error"       : false
    "result"      : {} // созданный документ
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
    "acc": "",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "items",
    "doc": {
        "exampleField": "Сегодня 18 июня, и это день рождения Мюриэл! Мюриэл сейчас 20. С днём рождения, Мюриэл!",
        "anotherExampleField": "Не знаю, что и сказать. Когда-то я хотел быть астрофизиком. К сожалению, это правда."
    }
}' "https://api.scorocode.ru/api/v1/data/insert"
```

## Удаление документа из коллекции.

**https://api.scorocode.ru/api/v1/data/remove**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // идентификатор приложения, обязательный
    "cli"         : "", // клиентский ключ, обязательный
    "acc"         : "", // ключ доступа, необязательный, для полного доступа masterKey
    "sess"        : "", // ID сессии, обязательный, если ACLPublic приложения на операцию == false и acc != masterKey
    "coll"        : "", // имя коллекции, обязательный
    "query"       : {}, // запрос с парами имя_поля/оператор:значение, необязательный
    "limit"       : int // лимит количества удаляемых документов, необязательный, если не указан, то удалятся первые 1000 документов
}
```

!!! warning "Ограничения" 
    Удаляет не более 1000 документов


**Responses:**
*Success*

```
{
    "error"       : false
    "result"      : {
        "count"       : int, // количество удаленных документов
        "docs"        : [] // массив ID удаленных документов
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
    "acc": "",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "items",
    "query": {
        "exampleField": { 
            "$eq": "Сегодня 18 июня, и это день рождения Мюриэл! Мюриэл сейчас 20. С днём рождения, Мюриэл!"
        }
    }
}' "https://api.scorocode.ru/api/v1/data/remove"
```

## Изменение документов в коллекции.

**https://api.scorocode.ru/api/v1/data/update**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // идентификатор приложения, обязательный
    "cli"         : "", // клиентский ключ, обязательный
    "acc"         : "", // ключ доступа, необязательный, для полного доступа masterKey
    "sess"        : "", // ID сессии, обязательный, если ACLPublic приложения на операцию == false и acc != masterKey
    "coll"        : "", // имя коллекции, обязательный
    "query"       : {}, // запрос с парами имя_поля/оператор:значение, необязательный
    "doc"         : {}, // документ с парами оператор:значение, обязательный
    "limit"       : int // лимит количества обновляемых документов, необязательный, если не указан, то обновятся первые 1000 документов
}
```

!!! warning "Ограничения" 
    Изменяет не более 1000 документов

**Responses:**

*Success*

```
{
    "error"       : false
    "result"      : {
        "count"       : int, // количество измененных документов
        "docs"        : [] // массив ID измененных документов
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
    "acc": "",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "items",
    "query": {
        "exampleField": { 
            "$eq": "Сегодня 18 июня, и это день рождения Мюриэл! Мюриэл сейчас 20. С днём рождения, Мюриэл!"
        }
    },
     "doc": {
        "$set": {
            "exampleField": "Сегодня 18 июня, и это день рождения Мюриэл! Мюриэл сейчас 21. С днём рождения, Мюриэл!"
        }
    },
    "limit": 1
}' "https://api.scorocode.ru/api/v1/data/update"
```

##  Изменение одного документа в коллекции по идентификатору.

**https://api.scorocode.ru/api/v1/data/updatebyid**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // идентификатор приложения, обязательный
    "cli"         : "", // клиентский ключ, обязательный
    "acc"         : "", // ключ доступа, необязательный, для полного доступа masterKey
    "sess"        : "", // ID сессии, обязательный, если ACLPublic приложения на операцию == false и acc != masterKey
    "coll"        : "", // имя коллекции, обязательный
    "query"       : {}, // запрос в формате "_id" : "&ltидентификатор документа&gt", обязательный
    "doc"         : {}, // документ с парами оператор:значение, обязательный
}
```

**Responses:**

*Success*

```
{
    "error"       : false
    "result"      : {} // обновленный документ
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
    "acc": "",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "items",
    "query": {
        "_id" : "jQ4ZwEbBUj"
    },
     "doc": {
        "$set": {
            "exampleField": "Сегодня 18 июня, и это день рождения Мюриэл! Мюриэл сейчас 21. С днём рождения, Мюриэл!"
        }
    }
}' "https://api.scorocode.ru/api/v1/data/updatebyid"

```

## Запрос документов из коллекции.

**https://api.scorocode.ru/api/v1/data/find**

Method: `POST`

Headers:

`Content-Type: application/json`

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
!!! warning "Ограничения" 
    Возвращает не более 100 документов

!!! warning "BSON" 
    Для повышения производительности сервиса результат выборки метода **find** возвращается в формате [bson](https://ru.wikipedia.org/wiki/BSON). Все SDK самостоятельно реализуют декодирование bson в json.

**Responses:**

*Success*

```
{
    "error"       : false
    "result"      : string // bson результат запроса, закодированный в base64
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
    "acc": "",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "items",
    "query": {
        "exampleField": { 
            "$eq": "Сегодня 18 июня, и это день рождения Мюриэл! Мюриэл сейчас 20. С днём рождения, Мюриэл!"
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
## Запрос количества документов из коллекции.

**https://api.scorocode.ru/api/v1/data/count**

Method: `POST`

Headers:

`Content-Type: application/json`

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

*Success*

```
{
    "error"       : false
    "result"      : int // количество документов
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
    "acc": "",
    "sess": "rYgRe6xL2y8VccMJ",
    "coll": "items",
    "query": {
        "exampleField": { 
            "$eq": "Сегодня 18 июня, и это день рождения Мюриэл! Мюриэл сейчас 20. С днём рождения, Мюриэл!"
        }
    }
}' "https://api.scorocode.ru/api/v1/data/count"
```