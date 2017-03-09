<a name="Scorocode.Object"></a>

* [.Object](#Scorocode.Object)
    * [new Object(collName)](#new_Scorocode.Object_new) ⇒ <code>[Scorocode.Object](#Scorocode.Object)</code>
    * [.getById(_id, options)](#Scorocode.Object+getById) ⇒ <code>promise.[Scorocode.Object](#Scorocode.Object)</code>
    * [.get(key)](#Scorocode.Object+get)
    * [.getFileLink(field)](#Scorocode.Object+getFileLink) ⇒ <code>String</code>
    * [.uploadFile(field, filename, file, options)](#Scorocode.Object+uploadFile) ⇒ <code>promise.&lt;String&gt;</code>
    * [.save(options)](#Scorocode.Object+save) ⇒ <code>promise.[Scorocode.Object](#Scorocode.Object)</code>
    * [.remove(options)](#Scorocode.Object+remove) ⇒ <code>promise.{count: Number, docs: Array}</code>
    * [.extend(collName, childObject)](#Scorocode.Object+extend) ⇒ <code>[\[Scorocode.Object\]](#Scorocode.Object)</code>
    * [.set(data)](#Scorocode.Object+set)
    * [.push(key, value)](#Scorocode.Object+push) 
    * [.pull(key, value)](#Scorocode.Object+pull) 
    * [.pullAll(key, value)](#Scorocode.Object+pullAll) 
    * [.addToSet(key, value)](#Scorocode.Object+addToSet) 
    * [.pop(key, pos)](#Scorocode.Object+pop) 
    * [.inc(key, amount)](#Scorocode.Object+inc)
    * [.currentDate()](#Scorocode.Object+currentDate)
    * [.mul(key, number)](#Scorocode.Object+mul)
    * [.min()](#Scorocode.Object+min)
    * [.max()](#Scorocode.Object+max)

----------------------------------------------------------------------------------------------

<a name="new_Scorocode.Object_new"></a>

## new Object(collName)
Scorocode.Object represents the application data object and includes methods for handling this data. The constructor creates a minimal basic "wrap" for user data.

| Parameter | Type | Description |
| --- | --- | --- |
| collName | <code>String</code> | Name of the collection where the object is added |

**Example** 
```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var questItem = new Scorocode.Object("items"); 
questItem.set("name", "Water chip").set("relatedquests", ["huNr3L7QDh"]); 
questItem.save()
    .then((saved) => {
         console.log(saved);
     })
    .catch((error) => {
         console.log(error)
    });
```
See.

* [.set(data)](#Scorocode.Object+set)
* [.save(options)](#Scorocode.Object+save) ⇒ <code>[Scorocode.Object](#Scorocode.Object)</code>

**Exceptions**:

- <code>Error</code> "Invalid collection name" 

```object
{ 
    errCode: 404,
    errMsg: 'Invalid collection: \'items\'',
    error: true 
}
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+getById"></a>

## .getById(_id, options)
Method for retrieving a collection object from DB by its _id.

**Parameters**

| Parameter | Type | Description |
| --- | --- | --- |
| _id | <code>String</code> | Object identifier |
| options | <code>Object</code> | Success and error callbacks for the executed query. |

**Example**

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItem = new Scorocode.Object("items");
getItem.getById("NseSaqqd5v")
    .then((success) => {
         console.log(success);
     })
    .catch((error) => {
         console.log(error)
    });
```

*see*

* [new Object(collName)](#new_Scorocode.Object_new)
* [.getById(_id, options)](#Scorocode.Object+getById) ⇒ <code>[Promise.&lt;Scorocode.Object&gt;](#Scorocode.Object)</code>

**Returns**: <code>[Promise.&lt;Scorocode.Object&gt;](#Scorocode.Object)</code> -  Returns promise that returns the requested object.

```object
{
    _id: 'NseSaqqd5v',
    name: 'Water chip',
    relatedquests: [ 'huNr3L7QDh' ],
    createdAt: Mon May 23 2016 19:37:04 GMT+0300 (RTZ 2 (зима)),
    updatedAt: Mon May 23 2016 19:37:04 GMT+0300 (RTZ 2 (зима)),
    readACL: [],
    updateACL: [],
    removeACL: []
}
```

**Exception**:

- `Error` "Document not found"

```
 [Error: Document not found]
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+get"></a>

## .get(key)

Method for retrieving data from a specified object field.

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be retrieved |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItem = new Scorocode.Object("items");
getItem.getById("NseSaqqd5v")
    .then((success) => {
        console.log(getItem.get("name"));
     })
    .catch((error) => {
         console.log(error)
    });
```

*See*

* [new Object(collName)](#new_Scorocode.Object_new)    
* [.getById(_id, options)](#Scorocode.Object+getById) ⇒ <code>[Promise.&lt;Scorocode.Object&gt;](#Scorocode.Object)</code>

**Returns**: <code>value</code> - Returns the field value
```
Water chip
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+uploadFile"></a>

## .uploadFile(field, filename, file, options)
File upload method

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Collection field name |
| filename | <code>String</code> | File name |
| file | <code>String</code> | File content in base64 format |
| options | <code>Object</code> | Success and error callbacks for the executed query. |

**Example**

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey",
    FileKey: "fileKey"
});

var attachToItem = new Scorocode.Object("items");
attachToItem.getById("xL0uOFtiJx")
    .then((success)=>{
        attachToItem.uploadFile("attachment", "file.txt", "VEhJUyBJUyBGSUxFLUUtRS1FLUUtRS1FIQ==")
        .then((uploaded)=>{
            console.log(uploaded);
        })
        .catch((error) => {
            console.log(error)
        });
    })
    .catch((error) => {
        console.log(error)
    });
    
```

*See*

* [new Object(collName)](#new_Scorocode.Object_new)
* [.getById(_id, options)](#Scorocode.Object+getById) ⇒ <code>[Promise.&lt;Scorocode.Object&gt;](#Scorocode.Object)</code>

**Returns**: <code>promise.&lt;String&gt;</code> - Returns promise that returns the uploaded file name
```
file.txt
```

**Exceptions**:

- <code>String</code> 'You must first create a document' 

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+save"></a>

## .save(options)

The method saves the object in the data warehouse or updates an object that already exists there

| Parameter | Type | Description |
| --- | --- | --- |
| options | <code>Object</code> | Success and error callbacks for the executed query. |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var questItem = new Scorocode.Object("items"); 
questItem.set("name", "Water chip").set("relatedquests", ["huNr3L7QDh"]); 
questItem.save()
    .then((saved) => {
         console.log("saved");
     })
    .catch((error) => {
         console.log(error);
    });
```

*See*

* [new Object(collName)](#new_Scorocode.Object_new)
* [.set(data)](#Scorocode.Object+set)

**Returns**: <code>[Promise.&lt;Scorocode.Object&gt;](#Scorocode.Object)</code> - Returns promise that returns the saved object.

```object
 { 
    _id: 'NseSaqqd5v',
    name: 'Water chip',
    relatedquests: [ 'huNr3L7QDh' ],
    createdAt: Mon May 23 2016 19:37:04 GMT+0300 (RTZ 2 (зима)),
    updatedAt: Mon May 23 2016 19:37:04 GMT+0300 (RTZ 2 (зима)),
    readACL: [],
    updateACL: [],
    removeACL: [] 
}
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+removeFile"></a>

## .removeFile(options)

Method for removing the file

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Collection field name |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItem = new Scorocode.Object("items");
getItem.getById("hejJU4BEGP")
    .then((success)=>{
        getItem.removeFile("attachment")
        .then((removed)=>{
            console.log(removed);
        })
        .catch((error) => {
            console.log(error)
        });
    })
    .catch((error) => {
            console.log(error)
    });
```

*See*

* [new Object(collName)](#new_Scorocode.Object_new)
* [.getById(_id, options)](#Scorocode.Object+getById) ⇒ <code>[Promise.&lt;Scorocode.Object&gt;](#Scorocode.Object)</code>

**Returns**: <code>Promise.{error: Boolean}</code> - Returns promise that returns the result:

```
{ 
    error: false 
}
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+remove"></a>

## .remove(options)

Method for removing the selected object

| Parameter | Type | Description |
| --- | --- | --- |
| options | <code>Object</code> | Success and error callbacks for the executed query. |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItem = new Scorocode.Object("items");
getItem.getById("hejJU4BEGP")
    .then((success)=>{
        getItem.remove(success)
        .then((removed)=>{
            console.log(removed);
        })
        .catch((error) => {
            console.log(error)
        });
    })
    .catch((error) => {
            console.log(error)
    });
```

*See*

* [new Object(collName)](#new_Scorocode.Object_new)
* [.getById(_id, options)](#Scorocode.Object+getById) ⇒ <code>[Promise.&lt;Scorocode.Object&gt;](#Scorocode.Object)</code>

**Returns**: <code>Promise.{count: Number, docs: Array}</code> - Returns promise that returns the object:

- "count" - <code>Number</code>  -  number of removed objects
- "doc" - <code>Array</code>  - array of removed objects' Ids

```
{ 
    count: 1, 
    docs: [ 'hejJU4BEGP' ] 
}
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+extend"></a>

## .extend(collName, childObject)

Method for converting the Scorocode.Query sample data into individiual Scorocode.Object instances

| Parameter | Type | Description |
| --- | --- | --- |
| collName | <code>String</code> | Collection name |
| childObject | <code>Object</code> | Data to be converted |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var data = new Scorocode.Query("items");
data.find()
    .then((finded) =>{
        var objects = finded.result.map((data)=>{
            return Scorocode.Object.extend("items", data)
        });
        return objects;
    })
    .then((result) => {
        console.log(result);
    })
    .catch((err)=>{
        console.log(err)
    });    
```

*See*

* [new Object(collName)](#new_Scorocode.Object_new)
* [.find(options)](Scorocode.Query.md#Scorocode.Query+find) ⇒ <code>Promise.{error: Boolean, limit: Number, skip: Number, result: [{Scorocode.Object}]}</code>

**Returns**: <code>Scorocode.Object</code> - Returns Scorocode.Object

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+set"></a>

## .set(data)
Method for transferring data to object

| Parameter | Type | Description |
| --- | --- | --- |
| data | <code>Object</code> | Data in {"key", "value"} format, where key is the collection field name. |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var questItem = new Scorocode.Object("items"); 
questItem.set("_id", "NseSaqqd5v").set("name", "Water chip"); 
questItem.save()
    .then((success) => {
         console.log(success);
     })
    .catch((error) => {
         console.log(error)
    });
```

*See*

* [new Object(collName)](#new_Scorocode.Object_new)
* [.save(options)](#Scorocode.Object+save) ⇒ <code>[Scorocode.Object](#Scorocode.Object)</code>

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+push"></a>

## .push(key, value)

Method for adding an element to an array

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| value | <code>String / Number / Boolean / Date / Array / Object </code> | Value of the new array element |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Item = new Scorocode.Object("items"); 
Item.getById("NseSaqqd5v")
    .then((success)=>{
        console.log(success);
        Item.push("arrayField", "new element");
        Item.save()
        .then((saved)=>{
            console.log(saved);
        })
        .catch((error) => {
            console.log(error);
        })
    })
    .catch((error) => {
            console.log(error)
    });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+pull"></a>

## .pull(key, value)
Method for removing all array elements whose values are the same as the specified one.


| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| value | <code>String / Number / Boolean / Date / Array / Object </code> | Value to be removed |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Item = new Scorocode.Object("items"); 
Item.getById("MgYs9BEQUM")
    .then((getted) => {
        Item.pull("arrayField", {"Delete": true});
        Item.save()
            .then((result) => {
                console.log(result);
            })
            .catch((error) => {
                console.log(error)
            });
    })   
    .catch((error) => {
         console.log(error)
    });
```

**Exceptions**:

- <code>Error</code> "For a new document use the method Set"
- <code>Error</code> 'Field must by a type of array'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+pullAll"></a>

## .pullAll(key, value)

Method for removing all array elements whose values are the same as one of the specified values.

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| value | <code>Array</code> | Array of values to be removed |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Item = new Scorocode.Object("items"); 
Item.getById("CrT49joIxn")
    .then((getted) => {
        Item.pullAll("arrayField", ["Delete me", 42, {"important": false}]);
        Item.save()
        .then((result) => {
            console.log(result);
        })
        .catch((error) => {
            console.log(error)
        });
    })   
    .catch((error) => {
         console.log(error)
    });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of array'
- <code>Error</code> 'Value must by a type of array'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+addToSet"></a>

## .addToSet(key, value)
Method for adding an element to an array only if there are no elements with the same name in the array.

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| value | <code>String / Number / Boolean / Date / Array / Object</code> | Value of the added element |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Item = new Scorocode.Object("items"); 
Item.getById("CrT49joIxn")
    .then((getted) => {
        Item.addToSet("arrayField", ["First element", {"isSecond": true}]);
        Item.save()
        .then((result) => {
            console.log(result);
        })
        .catch((error) => {
            console.log(error)
        });
    })   
    .catch((error) => {
         console.log(error)
    });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of array'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+pop"></a>

## .pop(key, pos)
Method for removing the first or the last array element

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| pos | <code>Number</code> | Position of the element to be removed in the array: -1 for the first element and 1 for the last |

**Example**

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItem = new Scorocode.Object("items"); 
getItem.getById("NseSaqqd5v")
    .then((success)=>{
        console.log(success);
        getItem.pop("arrayField", 1);
        getItem.save()
        .then((saved)=>{
            console.log(saved);
        })
        .catch((error) => {
            console.log(error);
        })
    })
    .catch((error) => {
            console.log(error)
    });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of array'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+inc"></a>

## .inc(key, amount)
The method increments the numeric field value by a defined number

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| amount | <code>Number</code> | Increment step |


**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Item = new Scorocode.Object("items"); 
Item.getById("gNxzwAfvDj")
    .then((success)=>{
        console.log(Item.get("price")); //44.42
        Item.inc("price", -2.42);
        Item.save()
        .then((incremented)=>{
            console.log(Item.get("price")); // 42
        })
        .catch((error) => {
            console.log(error);
        })
    })
    .catch((error) => {
            console.log(error)
    });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of number'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+currentDate"></a>

## .currentDate()
Sets the current time as the field's value

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| type | <code>String / Boolean</code> | Date type. Accepts the following values: true, "date" or "timestamp" |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Item = new Scorocode.Object("items");
Item.set("_id", "gNxzwAfvDj").currentDate("someDate", true);
Item.save()
    .then((success)=>{
        console.log(Item.get("someDate")); // 2016-05-27T14:10:00.013+03:00
    })
    .catch((error) => {
        console.log(error)
    });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Invalid type'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+mul"></a>

## .mul(key, number)

The method multiplies the numeric field value by a defined number

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| number | <code>Number</code> | Multiplier |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Item = new Scorocode.Object("items"); 
Item.getById("8Qcfll2GwE")
    .then((success)=>{
        console.log(Item.get("price")); // 42
        Item.mul("price", -1);
        Item.save()
        .then((incremented)=>{
            console.log(Item.get("price")); // -42
        })
        .catch((error) => {
            console.log(error);
        })
    })
    .catch((error) => {
            console.log(error)
    });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of number'
- <code>Error</code> 'Value must by a type of number'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Object+min"></a>

## .min()
The method updates the numeric field value only if the new value is less than the current field value

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| number | <code>Number</code> | New value |


**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Item = new Scorocode.Object("items"); 
Item.getById("CrT49joIxn")
    .then((success)=>{
        console.log(Item.get("price")); // 42
        Item.min("price", 41.999);
        Item.save()
        .then((changed)=>{
            console.log(Item.get("price")); // 41.999
        })
        .catch((error) => {
            console.log(error);
        })
    })
    .catch((error) => {
            console.log(error)
    });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of number'
- <code>Error</code> 'Value must by a type of number'

----------------------------------------------------------------------------------------------


<a name="Scorocode.Object+max"></a>

## .max()

The method updates the numeric field value only if the new value is greater than the current field value

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| number | <code>Number</code> | New value |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Item = new Scorocode.Object("items"); 
Item.getById("CrT49joIxn")
    .then((success)=>{
        console.log(Item.get("price")); // 41.999
        Item.max("price", 40);
        Item.save()
        .then((changed)=>{
            console.log(Item.get("price")); // 41.999
        })
        .catch((error) => {
            console.log(error);
        })
    })
    .catch((error) => {
            console.log(error)
    });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of number'
- <code>Error</code> 'Value must by a type of number'