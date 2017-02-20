On the Triggers tab, you can create descriptions for standard triggers.

![Triggers](../img/datatriggers.png)

Triggers are Java scripts that are executed when specific operations are performed with respect to data. All triggers are closed and have a local context. Select a trigger from the presented descriptions below and enter its description in the corresponding window. To save the entered description, click Save. To activate the created trigger, enable the Activate parameter. The trigger will not function without this parameter enabled.

When executing a trigger, the following objects are created in its context: `DataManager` and `pool`.


!!! warning "Trigger execution time"
    Maximum execution time for each trigger is 500 milliseconds.

!!! warning "Stack limit"
    Maximum depth of triggers calling stack is 10.
    Example:
    If you execute the "insert" operation for the same collection after the "insert" operation in the trigger, 10 documents will be inserted. After this, the call chain will be suspended.

!!! warning "Operations interruption/execution due to a trigger"
    When running triggers **before** operations "insert", "update" and "delete", one needs to execute `return true` to continue the document operations, and `return false` to interrupt them. The default result for a trigger is `false` if it doesn't return the value. 

!!! tip "Returning data when trigger operations are interrupted"
     In case there is a need to return data when a trigger operation was interrupted, one can specify data that needs to be returned in `pool.result`parameter.
    For example, inside a trigger one can create a field validation for a mandatory value before adding a document.
    
    ```js
    if (!pool.doc.hasOwnProperty('name')) { // проверим наличие поля "name" в создаваемом документе
        pool.result = "Необходимо указать имя";
        return false;                     // прервем создание документа в случае отсутствия поля
    }; 
    return true;    // В случае, если значение поля присутствует - продолжим операцию
    ```
    Now when we try to create a document with an empty field value for `name`, the operation will be interrupted and the following data will be returned: 
    
    ```js
    {
        "errCode": 412,
        "errMsg": "beforeInsert Trigger result: false",
        "error": true,
        "result": "Необходимо указать имя"
    }
    ```

## pool Object

Object `pool` contains the following data:

### Before operation `insert`:

```
{
    coll : "", // collection name
    doc : {},  // document with field_name:value pairs
}
```

### After operation `insert`:

```
{
    coll : "",   // collection name
    newDoc : {}  // newly created document with field_name:value pairs
}
```

### Before operation `remove`:

```
{
    coll : "",  // collection name
    query : {}  // search query on the basis of which documents should be removed
}
```

### After operation `remove`:

```
{
    coll : "",  // collection name
    count : int, // number of removed documents
    docs  : []  // array of deleted document IDs
```

### Before operation `update`:

```
{
    coll : "",  // collection name
    doc   : {}, // document with value update rules
    query : {}, // search query on the basis of which documents should be updated
}
```

### After operation `update`:

```
{
    coll : "", // collection name
    count : int, // number of updated documents
    docs  : []  // array of updated document IDs
}
```

### Before operation `updatebyid`:

```
{
    doc         : {}, // document with value update rules
    query       : {}, // search query {"_id" : }
}
```

### After operation `updatebyid`:

```
{
    newDoc      : { } // updated document
}
```

## DataManager Object

The `DataManager` object contains the following data handling methods:

### DataManager.Insert(data Object)

Method for inserting a document into a collection. Parameters:

`data Object` - object containing the following attributes:

```
{
    coll : "", // collection name, mandatory
    doc  : {}, // document with field_name:value pairs, optional
}
```

Returned value – `Object`:

*Success*

```
{
    error  : false
    result : {} // created document
}
```

*Error*

```
{
    error   : true,
    errCode : 4XX/5XX, // Error code
    errMsg  : "Error text"
}
```

### DataManager.Remove(data Object)

Method for removing documents from collection. Parameters:

`data Object` - object containing the following attributes:

```
{
    coll  : "", // collection name, mandatory
    query : {}, // query with field_name/operator:value pairs, optional
    limit : int // limit for the number of documents to be removed, optional,
                // if not specified, the first 1,000 documents will be removed
}
```

Returned value – `Object`:

*Success*

```
{
    error  : false
    result : {
        count : int, // number of removed documents
        docs  : []  // array of removed document IDs
    }
}
```

*Error*

```
{
    error   : true,
    errCode : 4XX/5XX, // Error code
    errMsg  : "Error text"
}
```

### DataManager.Update(data Object)

Method for updating documents in a collection. Parameters:

`data Object` - object containing the following attributes:

```
{
    coll  : "", // collection name, mandatory
    query : {}, // query with field_name/operator:value pairs, optional
    doc   : {}, // document with field_name:value pairs, mandatory
    limit : int // limit for the number of documents to be updated, optional,
                // if not specified, the first 1,000 documents will be updated
}
```

Returned value – `Object`:

*Success*

```
{
    error  : false
    result : {
        count : int, // number of removed documents
        docs  : []  // array of updated document IDs
    }
}
```

*Error*

```
{
    error   : true,
    errCode : 4XX/5XX, // Error code
    errMsg  : "Error text"
}
```

### DataManager.UpdateById(data Object)

Method for updating one document in a collection which is identified by its ID. Parameters:

`data Object` - object containing the following attributes:

```
{
    coll  : "", // collection name, mandatory
    query : {}, // query in the following format: "_id" : "<document identifier>", mandatory
    doc   : {}, // document with field_name:value pairs, mandatory
}
```

Возвращаемое значение - `Object`:

*Success*

```
{
    error  : false
    result : {} // updated document
}
```

*Error*

```
{
    error   : true,
    errCode : 4XX/5XX, // Error code
    errMsg  : "Error text"
}
```

### DataManager.Find(data Object)

Method for requesting a document from a collection. Parameters:

`data Object` - object containing the following attributes:

```
{
    coll   : "", // collection name, mandatory
    query  : {}, // query with field_name/operator:value pairs, optional if empty
                 // then first 100 documents will be returned
    sort   : {}, // sorting by fields in format field_name:1/-1, optional
    fields : [], // list of field names that will be returned in each document, optional
    limit  : int,// limit of the sample size, by default, 50
    skip   : int,// number of documents to be skipped in the sample
}

```

Returned value – `Object`:

*Success*

```
{
    error  : false
    result : [] // array of selected documents taking into account the limit
}
```

*Error*

```
{
    error   : true,
    errCode : 4XX/5XX, // Error code
    errMsg  : "Error text"
}
```

### DataManager.Count(data Object)

Method for requesting the number of documents in a collection Parameters:

`data Object` - object containing the following attributes:

```
{
    coll  : "", // collection name, mandatory
    query : {}, // query with field_name/operator:value pairs, optional
}
```

Returned value – `Object`:

*Success*

```
{
    error  : false
    result : int // number of documents
}
```

*Error*

```
{
    error   : true,
    errCode : 4XX/5XX, // Error code
    errMsg  : "Error text"
}
```

### DataManager.RunScript(data Object)

A method that runs a server-side script. Parameters:

`data Object` - object containing the following attributes:

```
{
    script   : "", // script identifier, mandatory
    pool     : {}, // object with the data that will be passed to the server-side script, optional
}
```

Returned value – `Object`:

*Success*

```
{
    error  : false
}
```

*Error*

```
{
    error   : true,
    errCode : 4XX/5XX, // Error code
    errMsg  : "Error text"
}
```

## Trigger examples

### Установка обязательности наличия значения поля.

Перед добавлением документа проверим наличие значения поля "name" и, в случае его отсутствия, прервем операцию добавления документа.

```js
if (!pool.doc.hasOwnProperty('name')) {   
        return false;                     
    } else {
        return true;                      // В случае, если значение поля присутствует - продолжим операцию
    };
```

### Установка значения по-умолчанию.

Перед добавлением документа проверим наличие значения поля "name" и, в случае его отсутствия, установим значение по-умолчанию.

```js
if (!pool.doc.hasOwnProperty('name')) { // проверим наличие поля "name" в создаваемом документе
        pool.doc.name = "Джон Сноу";    // в случае отсутствия значения, установим значение по-умолчанию
    }

return true;                    // В случае, если значение поля присутствует - продолжим операцию.
```

### Добавление связанного документа другой коллекции.

После добавления документа, создадим документ в другой коллекции со ссылкой на добавленный.

```js
DataManager.Insert({                           // выполним операцию добавления документа в коллекцию "stuff"
        coll : "stuff",
        doc  : {
                   "thing": pool.newDoc._id    // передадим _id созданного документа в поле типа "pointer"
        }
    })
```

### Удаление связанных документов другой коллекции.

Перед удалением документа, удалим все документы другой коллекции со ссылкой на удаляемый.

```js
DataManager.Remove({                           // выполним удаление связанных документов в коллекции "stuff"
    coll  : "stuff",
    query: {
        "thing": pool.query._id                // передадим _id удаляемого документа
    }
})
return true;
```

### Вызов серверного скрипта.

После добавления документа, запустим скрипт, передав ему новый документ. Скрипт может, например, осуществлять рассылку PUSH-уведомлений.

```js
DataManager.RunScript({                   // выполним запуск скрипта с ID 580b386d42d52f1ba275fc24
    script  : "580b386d42d52f1ba275fc24",
    pool: {
        "doc": pool.newDoc                // передадим новый документ
    }
})
```
