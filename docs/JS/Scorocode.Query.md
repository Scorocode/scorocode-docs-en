* [.Query](#Scorocode.Query)
    * [new Query(collName)](#new_Scorocode.Query_new) ⇒ <code>Scorocode.Object</code>
    * [.find(options)](#Scorocode.Query+find) ⇒ <code>promise.{error: Boolean, limit: Number, skip: Number, result: [{Scorocode.Object}]}</code>
    * [.count(options)](#Scorocode.Query+count) ⇒ <code>promise.{error: Boolean, result: Number}</code>
    * [.update(Object, options)](#Scorocode.Query+update) ⇒ <code>promise.{error: Boolean, result: {count: Number, docs: Array}}</code>
    * [.remove(options)](#Scorocode.Query+remove) ⇒ <code>promise.{count: Number, docs: Array}</code> 
    * [.reset()](#Scorocode.Query+reset) 
    * [.equalTo(field, value)](#Scorocode.Query+equalTo) 
    * [.notEqualTo(field, value)](#Scorocode.Query+notEqualTo) 
    * [.containedIn(field, value)](#Scorocode.Query+containedIn) 
    * [.containsAll(field, value)](#Scorocode.Query+containsAll) 
    * [.notContainedIn(field, value)](#Scorocode.Query+notContainedIn) 
    * [.greaterThan(field, value)](#Scorocode.Query+greaterThan) 
    * [.greaterThanOrEqualTo(field, value)](#Scorocode.Query+greaterThanOrEqualTo) 
    * [.lessThan(field, value)](#Scorocode.Query+lessThan) 
    * [.lessThanOrEqualTo(field, value)](#Scorocode.Query+lessThanOrEqualTo) 
    * [.exists(field)](#Scorocode.Query+exists) 
    * [.doesNotExist(field)](#Scorocode.Query+doesNotExist) 
    * [.contains(field, value)](#Scorocode.Query+contains) 
    * [.startsWith(field, value)](#Scorocode.Query+startsWith) 
    * [.endsWith(field, value)](#Scorocode.Query+endsWith) 
    * [.limit(limit)](#Scorocode.Query+limit) 
    * [.skip(skip)](#Scorocode.Query+skip)
    * [.page(page)](#Scorocode.Query+page) 
    * [.ascending(field)](#Scorocode.Query+ascending)
    * [.descending(field)](#Scorocode.Query+descending) 
    * [.or(query)](#Scorocode.Query+or)
    * [.and(query)](#Scorocode.Query+and) 
    * [.select()](#Scorocode.Query+select) 
    * [.raw(filter)](#Scorocode.Query+raw) 

----------------------------------------------------------------------------------------------

<a name="new_Scorocode.Query_new"></a>

## new Query(collName)

Instance of a collection data query


| Parameter | Type | Description |
| --- | --- | --- |
| collName | <code>String</code> | Collection name |

**Example**

```js
var sc = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var data = new Scorocode.Query("items");
data.find()
    .then((finded) =>{
        console.log(finded);
    })
    .catch((err)=>{
        console.log(err)
    });    
```
**Returns**: <code>[Scorocode.Query](#Scorocode.Query)</code> - Returns the `Scorocode.Query`

**Exception**:

- <code>String</code> 'Collection name must be a type of string'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+find"></a>

## .find(options)

Method for requesting a document from a collection. Returns data of the objects that match the sampling criteria. If no criteria are set, the first 50 objects of the collection are returned by default.


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

var data = new Scorocode.Query("items");
data.find()
    .then((finded) =>{
        var util = require('util');
        console.log(util.inspect(finded, {showHidden: false, depth: null}))
    })
    .catch((err)=>{
        console.log(err)
    });    
```

**Returns**: <code>promise.{error: Boolean, limit: Number, skip: Number, result: [{Scorocode.Object}]}</code> - Returns promise, which returns the object containing the result of the query execution.

- "error" - <code>Boolean</code> - Error flag
- "limit" - <code>Number</code>  - Sampling size limit
- "skip" - <code>Number</code>  - How many documents were skipped during the sampling
- "result" - <code>Array</code>  - Obtained data array

```
{ 
    error: false,
    limit: 100,
    skip: 0,
    result:
    [ 
       { _id: 'CrT49joIxn',
           createdAt: Wed May 25 2016 17:24:17 GMT+0300 (RTZ 2 (зима)),
           updatedAt: Wed May 25 2016 22:15:03 GMT+0300 (RTZ 2 (зима)),
           readACL: [],
           updateACL: [],
           removeACL: [],
           arrayField: [ false,"",42.42,[1,2,3],["Array",{"123": 4}],{ "Object": true }],
           price: 41.999 
       },
       // ...
       { _id: 'NseSaqqd5v',
           createdAt: Wed May 25 2016 17:24:17 GMT+0300 (RTZ 2 (зима)),
           updatedAt: Wed May 25 2016 22:15:03 GMT+0300 (RTZ 2 (зима)),
           readACL: [],
           updateACL: [],
           removeACL: []
       } 
    ]
}
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+count"></a>

## .count(options)

Method for counting objects that meet the query conditions.


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

var countItems = new Scorocode.Query("items");
countItems.exists("price")
    .count()
        .then((counted) => {
            console.log(counted) // { error: false, result: 5 }
        })
        .catch((error) => {
            console.log(error)
        });
```

**Returns**: <code>promise.{error: Boolean, result: Number}</code> -  Returns promise, which returns the object containing the result of the query execution.

- "error" - <code>Boolean</code> - Error flag
- "result" - <code>Number</code>  - Number of objects that meet the sampling condition.

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+update"></a>

## .update(Object, options) 

Method for updating the requested objects.

| Parameter | Type | Description |
| --- | --- | --- |
| Object | <code>Scorocode.UpdateOps</code> | `Scorocode.UpdateOps` object to which the updated data is transferred. |
| options | <code>Object</code> | Success and error callbacks for the executed query. |


**Example**

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.notEqualTo("price", 42)
    .find()
        .then((result) => {
            updateItems.set("price", 42);
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
        }) 
        .catch((error) => {
            console.log(error)
        });

```

**Returns**: <code>promise.{error: Boolean, result: {count: Number, docs: Array}}</code> - Returns promise, which returns the object containing the result of the query execution.

- "error" - <code>Boolean</code> - Error flag
- "result" - <code>Object</code>  - Query execution result
    - "count" - <code>Number</code>  - Number of modified objects
    - "docs" - <code>Array</code>  - _id array of modified objects

```
{ error: false,
  result:
   { count: 8,
     docs:[ 
        'CrT49joIxn',
        '8Qcfll2GwE',
        'dMSYsK8jld',
        '6TFVG5UqV6',
        'gNxzwAfvDj',
        'eoVWeg9oeY',
        'vRf58kEDpo',
        'abOkjQAnYE' 
        ] 
    } 
}
```
----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+remove"></a>

## .remove(options)

Method for removing the requested objects.

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

Items.exists("arrayField")
    .find()
        .then((finded) => {
            Items.remove(finded)
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

**Returns**: <code>promise.{ecount: Number, docs: Array}</code> - Returns promise, which returns the object containing the result of the query execution.

- "count" - <code>Number</code>  - Number of deleted objects
- "docs" - <code>Array</code>  - _id array of deleted objects

```
{ 
    count: 4, 
    docs:[ 
        'CrT49joIxn', 
        'eoVWeg9oeY', 
        'vRf58kEDpo', 
        'abOkjQAnYE'
        ] 
}
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+reset"></a>

## .reset() 

Method for resetting the sampling conditions

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.equalTo("price", 42)
    .find()
        .then((result) => {
            console.log(result)
        })
        .catch((error) => {
            getItems.reset()
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+equalTo"></a>

## .equalTo(field, value)

Method for retrieving all objects with the field value indicated in the condition.

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>String / Number / Boolean / Date / Array / Object</code> | Field value |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.equalTo("price", 42)
    .find()
        .then((result) => {
            console.log(result) 
            getItems.reset()
        })
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+notEqualTo"></a>

## .notEqualTo(field, value)

Method for retrieving all objects except for objects with the field value indicated in the condition.

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>String / Number / Boolean / Date / Array / Object </code> | Field value |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.notEqualTo("price", 42)
    .find()
        .then((result) => {
            console.log(result) // { error: false, result: 5 }
        })
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+containedIn"></a>

## .containedIn(field, value)

Method for retrieving all objects whose field value contains the array elements specified in the query.

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>Array</code> | Array of values |

**Example**

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.containedIn("price",[-42, 41.999, 42])
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

**Exceptions**

- <code>String</code> 'Value must be of Тип: Array'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+containsAll"></a>

## .containsAll(field, value)

Method for retrieving all objects whose field value contains all array elements specified in the query.

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>Array</code> | Array of values |

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.containsAll("arrayField",[4, 8, 15, 16, 23, 42])
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

**Exceptions**:

- <code>String</code> 'Value must be of Тип: Array'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+notContainedIn"></a>

## .notContainedIn(field, value)

Method for retrieving all objects whose field value does not contain the array elements specified in the query.

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>Array</code> | Array of values |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.notContainedIn("price",[41.999, 42])
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

**Exceptions**:

- <code>String</code> 'Value must be of Тип: Array'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+greaterThan"></a>

## .greaterThan(field, value)

Method for retrieving all objects whose field value is greater than the number specified in the query.

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>Number / Date</code> | Condition value |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.greaterThan("createdAt", "2016-05-19T15:35:16.000Z")
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+greaterThanOrEqualTo"></a>

## .greaterThanOrEqualTo(field, value)

Method for retrieving all objects whose field value is no less than the number specified in the query.

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>Number / Date</code> | Condition value |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.greaterThanOrEqualTo("price", 41.999)
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+lessThan"></a>

## .lessThan(field, value)

Method for retrieving all objects whose field value is less than the number specified in the query.

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>Number / Date</code> | Condition value |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.lessThan("price", 41)
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+lessThanOrEqualTo"></a>

## .lessThanOrEqualTo(field, value) 

Method for retrieving all objects whose field value is no greater than the number specified in the query.

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>Number / Date</code> | Condition value |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.lessThanOrEqualTo("updatedAt", "2016-05-19T15:35:16.000Z")
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+exists"></a>

## .exists(field)

Method for retrieving all objects with an existing value of a defined field

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Items = new Scorocode.Query("items");
Items.exists("price")
    .find()
        .then((result) => {
            console.log(result)
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+doesNotExist"></a>

## .doesNotExist(field)

Method for retrieving all objects with a missing value in a defined field.


| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Items = new Scorocode.Query("items");
Items.doesNotExist("price")
    .find()
        .then((result) => {
            console.log(result)
        .catch((error) => {
            console.log(error)
        });
```


----------------------------------------------------------------------------------------------


<a name="Scorocode.Query+contains"></a>

## .contains(field, value)

Method for retrieving all objects with a value of a defined field that matches a defined regular expression.


| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>String</code> | Regular expression |

**Example**

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.contains("someString","[0-9]")
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

**Exception**:

- <code>String</code> '"Value must be a string"'

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+startsWith"></a>

## .startsWith(field, value) 

Method for retrieving all objects with a value of a defined field starting from a specified string.

| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Name of the field for which a condition is defined |
| value | <code>String</code> | Condition value |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.startsWith("name", "ite");
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

**Exception**:

- <code>String</code> "Value must be a string"

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+endsWith"></a>

## .endsWith(field, value)

Method for retrieving all objects with a value of a defined field ending with a specified string.


| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Field name |
| value | <code>String</code> | Condition value |

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.endsWith("name", "чип");
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

**Exception**:

- <code>String</code> "Value must be a string"

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+limit"></a>

## .limit(limit) 

Method for specifying a limit for the number of sampling objects

| Parameter | Type | Description |
| --- | --- | --- |
| limit | <code>Number</code> | Sampling limit |

**Example** 

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.limit(1000).contains("someString","[a-zA-Z-0-9]")
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

**Exception**:

- <code>String</code> "Limit must be a positive number"

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+skip"></a>

## .skip(skip)

Method for skipping some objects before sampling.

| Parameter | Type | Description |
| --- | --- | --- |
| skip | <code>Number</code> | Number of skipped objects |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.limit(1000).skip(1000).contains("someString","[a-zA-Z-0-9]")
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

**Exception**

- <code>String</code> "Skip must be a positive number"

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+page"></a>

## .page(page)

Method for sampling results page by page

| Parameter | Type | Description |
| --- | --- | --- |
| page | <code>Number</code> | Page number |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.limit(30).page(2).contains("someString","[a-zA-Z-0-9]")
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

**Exception**:

- <code>String</code> "Page must be a positive number"

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+ascending"></a>

## .ascending(field)

Method for sorting a specified field data in ascending order before sampling.


| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Field name |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.limit(30).ascending("updatedAt").page(1).contains("someString","[a-zA-Z-0-9]")
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+descending"></a>

## .descending(field)

Method for sorting a specified field data in descending order before sampling.


| Parameter | Type | Description |
| --- | --- | --- |
| field | <code>String</code> | Field name |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
getItems.limit(30).descending("price").page(1).contains("someString","[a-zA-Z-0-9]")
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+or"></a>

## .or(query)

Method for logical addition of several samplings conditions

| Parameter | Type | Description |
| --- | --- | --- |
| query | <code>Scorocode.Query</code> | Query that is included in the disjunction operation |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
var range1 = new Scorocode.Query("items");
var range2 = new Scorocode.Query("items");

var getItems = new Scorocode.Query("items");
range1.lessThanOrEqualTo("createdAt", "2016-05-19T10:00:00.000Z");
range2.greaterThanOrEqualTo("createdAt", "2016-05-21T15:00:00.000Z");
getItems.or(range1).or(range2)
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

**Exception**:

- <code>String</code> "Invalid type of Query"

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+and"></a>

## .and(query) 

Method for logical multiplication of several samplings conditions

| Parameter | Type | Description |
| --- | --- | --- |
| query | <code>Scorocode.Query</code> | Query that is included in the conjunction operation |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var getItems = new Scorocode.Query("items");
var range = new Scorocode.Query("items");
var price = new Scorocode.Query("items");

var getItems = new Scorocode.Query("items");
range.greaterThanOrEqualTo("createdAt", "2016-05-19T10:00:00.000Z");
price.doesNotExists("price");
getItems.and(range).and(price)
    .find()
        .then((result) => {
            console.log(result) 
        })
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+select"></a>

## .select() 

Method for specifying a list of returned fields.

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var data = new Scorocode.Query("items");
data.select("price", "reward").find()
    .then((finded) =>{
        console.log(finded);
    })
    .catch((err)=>{
        console.log(err)
    });    

```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Query+raw"></a>

## .raw(filter) 

| Parameter | Type | Description |
| --- | --- | --- |
| filter | <code>Object</code> | Applied filter in the MongoDB query language format |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var query = Scorocode.Query("items");
query.raw("{ \"fieldString\" : \"String\" }");
query.find()
    .then((finded) =>{
        console.log(finded);
    })
    .catch((err)=>{
        console.log(err)
    });    
```
