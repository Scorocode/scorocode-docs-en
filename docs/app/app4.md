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
    When running triggers **before** operations "insert", "update" and "delete", you need to execute `return true` to continue the document operations, and `return false` to interrupt them. The default result for a trigger is `false` if it doesn't return the value. 

!!! tip "Returning data when trigger operations are interrupted"
     In case there is a need to return data when a trigger operation was interrupted, you can specify data that needs to be returned in `pool.result`parameter.
    For example, inside a trigger you can create a field validation for a mandatory value before adding a document.
    
    ```js
    if (!pool.doc.hasOwnProperty('name')) {  // check if pool.doc does not have property "name"
        pool.result = "You Shall Not Pass";  
        return false;                        // interrupt document creation
    }; 
    return true;    // else - create the document
    ```
    Now when we try to create a document with an empty field value for `name`, the operation will be interrupted and the following data will be returned: 
    
    ```js
    {
        "errCode": 412,
        "errMsg": "beforeInsert Trigger result: false",
        "error": true,
        "result": "You Shall Not Pass"
    }
    ```

## pool Object

Object `pool` contains the following data:

### Before operation `insert`:

```
{
    coll : "", // collection name
    doc : {}   // document with field_name:value pairs
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
    query : {}  // search query on the basis of which documents should be updated
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
    coll        : "", // collection name
    doc         : {}, // document with value update rules
    query       : {}, // search query {"_id" : }
}
```

### After operation `updatebyid`:

```
{
    coll        : "", // collection name
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
    doc  : {}  // document with field_name:value pairs, optional
}
```

Returned value – `Object`:

*Success*

```
{
    error  : false,
    result : {}     // created document
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
    error  : false,
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
    error  : false,
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
    query : {}, // query in the following format: "_id" : "document identifier", mandatory
    doc   : {}  // document with field_name:value pairs, mandatory
}
```

Returned value - `Object`:

*Success*

```
{
    error  : false,
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
    skip   : int // number of documents to be skipped in the sample
}

```

Returned value – `Object`:

*Success*

```
{
    error  : false,
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
    query : {}  // query with field_name/operator:value pairs, optional
}
```

Returned value – `Object`:

*Success*

```
{
    error  : false,
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
    pool     : {}  // object with the data that will be passed to the server-side script, optional
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

### Setting a field value as mandatory.

Before adding a document you can check whether a value is specified in the "name" field. In case it is not, you can interrupt the operation of adding the document.

```js
if (!pool.doc.hasOwnProperty('name')) {   
        return false;                     // if name is not specified then document creation will be interrupted
    } else {
        return true;                      
    };
```

### Setting a default value.

Before adding a document you can check whether a value is specified in the "name" field. In case it is not, you can set the value as a default one.

```js
if (!pool.doc.hasOwnProperty('name')) { 
        pool.doc.name = "John Snow";    // if not specified, name is now "John Snow" dy default 
    }

return true;                    
```

### Creating a document related in a different collection.

After adding a document, you can create another document in a different collection with a link to the added one.

```js
DataManager.Insert({                           // create new document in the "stuff" collection
        coll : "stuff",
        doc  : {
                   "thing": pool.newDoc._id    // pass _id value to the new document's field "thing"
        }
    })
```

### Deleting related documents from a different collection.

Before deleting a document, you can delete all documents from a different collection with a link to the document you want to delete.

```js
DataManager.Remove({                           //  delete all related documents in the "stuff" collection
    coll  : "stuff",
    query: {
        "thing": pool.query._id                // pass _id to the document which is about to be deleted
    }
})
return true;
```

### Running a server-side script from a trigger.

After a document is created, a script can be executed with the new document data. As an example, the script can send PUSH-notifications.
 
```js
DataManager.RunScript({                   // run a script with the ID 580b386d42d52f1ba275fc24
    script  : "580b386d42d52f1ba275fc24",
    pool: {
        "doc": pool.newDoc                // pass a new document to the script 
    }
})
```
