<a name="Scorocode.UpdateOps"></a>

* [.UpdateOps](#Scorocode.UpdateOps)
    * [.set(data)](#Scorocode.UpdateOps+set)
    * [.push(key, value)](#Scorocode.UpdateOps+push) 
    * [.pull(key, value)](#Scorocode.UpdateOps+pull) 
    * [.pullAll(key, value)](#Scorocode.UpdateOps+pullAll) 
    * [.addToSet(key, value)](#Scorocode.UpdateOps+addToSet) 
    * [.pop(key, pos)](#Scorocode.UpdateOps+pop) 
    * [.inc(key, amount)](#Scorocode.UpdateOps+inc)
    * [.currentDate()](#Scorocode.UpdateOps+currentDate)
    * [.mul(key, number)](#Scorocode.UpdateOps+mul)
    * [.min()](#Scorocode.UpdateOps+min)
    * [.max()](#Scorocode.UpdateOps+max)

--------------------------------------------------------------------------------

<a name="new_Scorocode.UpdateOps_new"></a>

## new UpdateOps()
Class for multiple object update operations

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
            console.log("Что-то пошло не так: \n", error)
        });
```

**Returns**: <code>[UpdateOps](#Scorocode.UpdateOps)</code> - Returns the Scorocode.UpdateOps instance  

----------------------------------------------------------------------------------------------

<a name="Scorocode.UpdateOps+set"></a>

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

*See*

* [new Object(collName)](#new_Scorocode.Object_new)
* [.save(options)](#Scorocode.UpdateOps+save) ⇒ <code>[Scorocode.UpdateOps](#Scorocode.UpdateOps)</code>

----------------------------------------------------------------------------------------------

<a name="Scorocode.UpdateOps+push"></a>

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

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.exists("arrayField")
    .find()
        .then((result) => {
            updateItems.push("arrayField", "New element");
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
        }) 
        .catch((error) => {
            console.log(error)
        });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.UpdateOps+pull"></a>

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

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.exists("arrayField")
    .find()
        .then((result) => {
            updateItems.pull("arrayField", {"Удалить этот объект": true});
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
        }) 
        .catch((error) => {
            console.log("Что-то пошло не так: \n", error)
        });
```

**Exceptions**:

- <code>Error</code> "For a new document use the method Set"
- <code>Error</code> 'Field must by a type of array'

----------------------------------------------------------------------------------------------

<a name="Scorocode.UpdateOps+pullAll"></a>

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

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.exists("arrayField")
    .find()
        .then((result) => {
            updateItems.pullAll("arrayField", ["Delete me", 42, {"Important": false}]);
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
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

<a name="Scorocode.UpdateOps+addToSet"></a>

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

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.exists("arrayField")
    .find()
        .then((result) => {
        	updateItems.addToSet("arrayField", ["First element of new element", {"isSecond": true}]);
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
        }) 
        .catch((error) => {
            console.log(error)
        });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of array'

----------------------------------------------------------------------------------------------

<a name="Scorocode.UpdateOps+pop"></a>

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

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.exists("arrayField")
    .find()
        .then((result) => {
        	updateItems.pop("arrayField", 1);
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
        }) 
        .catch((error) => {
            console.log(error)
        });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of array'

----------------------------------------------------------------------------------------------

<a name="Scorocode.UpdateOps+inc"></a>

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

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.exists("price")
    .find()
        .then((result) => {
        	updateItems.inc("price", -2.42);
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
        }) 
        .catch((error) => {
            console.log(error)
        });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of number'

----------------------------------------------------------------------------------------------

<a name="Scorocode.UpdateOps+currentDate"></a>

## .currentDate()

Sets the current time as the field's value

| Parameter | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | Name of the field whose value should be updated |
| type | <code>String / Boolean</code> | Date type. Accepts the following values: true, "date" or "timestamp" |

**Example**:

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.find()
        .then((result) => {
			updateItems.currentDate("someDate", "timestamp");
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
        }) 
        .catch((error) => {
            console.log(error)
        });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Invalid type'

----------------------------------------------------------------------------------------------

<a name="Scorocode.UpdateOps+mul"></a>

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

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.exists("price")
    .find()
        .then((result) => {
        	updateItems.mul("price", 0.5);
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
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

<a name="Scorocode.UpdateOps+min"></a>

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

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.exists("price")
    .find()
        .then((result) => {
        	updateItems.min("price", 42);
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
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


<a name="Scorocode.UpdateOps+max"></a>

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

var Items = new Scorocode.Query("items");
var updateItems = new Scorocode.UpdateOps("items");

Items.exists("price")
    .find()
        .then((result) => {
	        updateItems.max("price", 42);
            return Items.update(updateItems)
        })
        .then((updated) => {
            console.log(updated);
        }) 
        .catch((error) => {
            console.log(error)
        });
```

**Exceptions**:

- <code>Error</code> 'For a new document use the method Set'
- <code>Error</code> 'Field must by a type of number'
- <code>Error</code> 'Value must by a type of number'
