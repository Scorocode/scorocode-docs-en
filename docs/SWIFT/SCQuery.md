<a name="SCQuery"></a>

* [.Query](#SCQuery)
    * [.init(collection)](#SCQuery+init)
    * [.find(callback -> Void)](#SCQuery+find) 
    * [.count(callback -> Void)](#SCQuery+count)
    * [.update(update, callback -> Void)](#SCQuery+update) 
    * [.remove(callback)](#SCQuery+remove) 
    * [.limit(limit)](#SCQuery+limit)
    * [.skip(skip)](#SCQuery+skip)
    * [.page(page)](#SCQuery+page)
    * [.raw(json)](#SCQuery+raw)
    * [.reset()](#SCQuery+reset)
    * [.ascending(name)](#SCQuery+ascending)
    * [.descending(name)](#SCQuery+descending) 
    * [.fields(names)](#SCQuery+fields) 
    * [.addOperator(name, oper)](#SCQuery+addOperator) 
    * [.equalTo(name, _ value)](#SCQuery+equalTo) 
    * [.notEqualTo(name, _ value)](#SCQuery+notEqualTo)
    * [.containedIn(name, _ value)](#SCQuery+containedIn) 
    * [.containsAll(name, _ value)](#SCQuery+containsAll) 
    * [.notContainedIn(name, _ value)](#SCQuery+notContainedIn)
    * [.greaterThan(name, _ value)](#SCQuery+greaterThan)
    * [.greaterThanOrEqualTo(name, _ value)](#SCQuery+greaterThanOrEqualTo)
    * [.lessThan(name, _ value)](#SCQuery+lessThan)
    * [.lessThanOrEqualTo(name, _ value)](#SCQuery+lessThanOrEqualTo)
    * [.exists(name)](#SCQuery+exists)
    * [.doesNotExist(name)](#SCQuery+doesNotExist)
    * [.contains(name, _ pattern)](#SCQuery+contains)
    * [.startsWith(name, _ pattern)](#SCQuery+startsWith)
    * [.endsWith(name, _ pattern)](#SCQuery+endsWith)
    * [.and(operators)](#SCQuery+and)
    * [.or(operators)](#SCQuery+or)

----------------------------------------------------------------------------------------------------------------------


<a name="SCQuery+init"></a>
### init(collection)

Initialization of collection data query.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| collection | <code>String</code> | Mandatory | Name of the collection where the object is added  | "items" | 

**Example**

```SWIFT
var query = SCQuery(collection: "users")
```

----------------------------------------------------------------------------------------------------------------------

<a name="SCQuery+find"></a> 
### .find(callback) 

Method for searching objects based on the created sampling condition.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| callback  | <code>(Bool, SCError?, [String: AnyObject]?) -> Void</code> |        | Callback for the request being executed. |                 |

**Example**

```SWIFT
var query = SCQuery(collection: "users")
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
----------------------------------------------------------------------------------------------------------------

<a name="SCQuery+count"></a> 

### .count(callback) 

Method for counting objects that meet the query conditions.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| callback   | <code>(Bool, SCError?, Int?) -> Void</code> |        | Callback for the request being executed. |                 |

**Example**

```SWIFT
var query = SCQuery(collection: "users")
query.count() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
-----------------------------------------------------------------------------------------------------------------
<a name="SCQuery+update"></a> 

### .update(update, callback)

Method for updating the objects matching the sampling conditions.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| update | <code>SCUpdate</code> | Mandatory | SCUpdate object to which data for updating is transferred  |                                    | 
| callback()   | <code>(Bool, SCError?, [String: AnyObject]?) -> Void</code> |        | Callback for the request being executed. |                 |

**Example**

```SWIFT
var userArrivalTime = SCUpdate()
let currentDate = SCUpdateOperator.currentDate("fieldName", typeSpec: "timestamp")
logArrivalTime.addOperator(currentDate)

var arrivedUsers = SCQuery(collection: "users")
arrivedUsers.equalTo("flightRace", SCString("AF4926"))
arrivedUsers.update(userArrivalTime) {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
-----------------------------------------------------------------------------------------------------------------
<a name="SCQuery+remove"></a>

### .remove(callback) 

Method for removing the objects matching the sampling conditions.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| callback()   | <code>(Bool, SCError?, [String: AnyObject]?) -> Void</code> |        | Callback for the request being executed. |                 |

**Example**

```SWIFT
var oldStuff = SCQuery(collection: "Stuff")
oldStuff.lessThan("createdAt", SCDate("2016-06-54T17:24:23.091+03:00"))
oldStuff.remove() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
-----------------------------------------------------------------------------------------------------------------
<a name="SCQuery+limit"></a> 

### .limit(limit)

Method for setting the sampling limit.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| limit | <code>Int</code> | Mandatory | Sampling limit   | 100 | 

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.limit(25)
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
------------------------------------------------------------------------------------------------------------------
<a name="SCQuery+skip"></a>

### .skip(skip) 

Method for defining the number of documents to be skipped before document sampling

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| limit | <code>Int</code> | Mandatory | Number of skipped documents      | 1000 | 

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.skip(1000)
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}

```
-----------------------------------------------------------------------------------------------------------------
<a name="SCQuery+page"></a>

### .page(page)

Method for "per-page" output of sampling results in accordance with the specified sampling limit.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| page | <code>Int</code> | Mandatory | Page number  | 4 | 

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.limit(25)
query.page(4)
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
----------------------------------------------------------------------------------------------------------------
<a name="SCQuery+raw"></a> 

### .raw(json) 

Method for defining sampling conditions in the form of a JSON structure to create a DB query in MongoDB language.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| json| <code>String</code> | Mandatory | Sampling conditions | {location: {$in: ['New California Republic', 'Vault City']}}| 

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.raw("{ \"fieldString\" : \"Строка\" }")
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}

```
--------------------------------------------------------------------------------------------------------------
<a name="SCQuery+reset"></a> 

### .reset() 

Method for resetting the sampling conditions

**Example**

```SWIFT
var query = SCQuery(collection: "items")

query.equalTo("fieldName", SCString("John Doe"))
query.raw("{ \"fieldString\" : \"Строка\" }")
query.ascending("field1")
query.descending("field2")
query.fields(["field1", "field2"])
let and1 = SCOperator.EqualTo("fieldString", SCString("Строка"))
let and2 = SCOperator.EqualTo("fieldNumber", SCInt(33))
query.and([and1, and2])

query.reset()

```
------------------------------------------------------------------------------------------------------------
<a name="SCQuery+ascending"></a> 

### .ascending(name) 

Method for sorting data in ascending order of specified field values before sampling.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| name | <code>String</code> | Mandatory | Field name   | "price" | 

**Example**

```SWIFT
var sortByPrice = SCQuery(collection: "items")
sortByPrice.ascending("price")
sortByPrice.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}

```
-----------------------------------------------------------------------------------------------------------
<a name="SCQuery+descending"></a>

### .descending(name) 

Method for sorting data in the descending order of specified field values before sampling.


**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| name | <code>String</code> | Mandatory | Field name | "reward" | 

**Example**

```SWIFT
var sortByReward = SCQuery(collection: "items")
sortByReward.descending("reward")
sortByReward.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```

-----------------------------------------------------------------------------------------------------------
<a name="SCQuery+fields"></a>

### .fields(names)

Method for specifying a list of returned fields.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| names | <code>[String]</code> | Mandatory | Array of requested field values  | ["price", "reward"] | 

**Example**

```SWIFT
var getPriceAndReward = SCQuery(collection: "items")
getPriceAndReward.fields(["price", "reward"])
getPriceAndReward.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```

------------------------------------------------------------------------------------------------------------
<a name="SCQuery+addOperator"></a> 

### .addOperator(name, oper)

Method for transferring a sampling condition to SCQuery

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| name | <code>String</code> | Mandatory | Name of the field to which the condition is assigned  | "testcoll" | 
| oper | <code>SCOperator</code> | Mandatory | The assigned condition |  | 

**Example**

```SWIFT
let lessNorEqual = SCOperator.LessThanOrEqualTo("price", 42)
SCQuery.addOperator(name, oper: lessNorEqual)
```
-------------------------------------------------------------------------------------------------------------
<a name="SCQuery+equalTo"></a> 

### .equalTo(name, _ value)

Method for retrieving all documents with the field value indicated in the condition.

**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|--------|
| name           | <code>String</code>       | Mandatory | Name of the field to which the condition is assigned    | "tags" |
| _ value        | <code>SCValue</code>      | Mandatory | Field value                                | 42     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.equalTo("equality", SCString("yep"))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
----------------------------------------------------------------------------------------------------------
<a name="SCQuery+notEqualTo"></a>

### .notEqualTo(name, _ value) 

Method for retrieving all documents except for objects with the field value indicated in the condition.

**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|--------|
| name           | <code>String</code>       | Mandatory | Name of the field to which the condition is assigned   | "tags" |
| _ value        | <code>SCValue</code>      | Mandatory | Field value                                 | 43     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.notEqualTo("unequality", SCString("nope"))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
------------------------------------------------------------------------------------------------------------
<a name="SCQuery+containedIn"></a> 

### .containedIn(name, _ value)

Method for retrieving all objects whose field value contains the array elements specified in the query.

**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|--------------|----------------------------------------------|---------|
| name           | <code>String</code>       | Mandatory | Name of the field to which the condition is assigned      | "price" |
| _ value        | <code>SCArray</code>      | Mandatory | Array of values                             | [-42, 41.999, 42]     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.containedIn("someField", SCArray([SCString("A"), SCString("B")]))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
------------------------------------------------------------------------------------------------------------
<a name="SCQuery+containsAll"></a> 

### .containsAll(name, _ value)

Method for retrieving all objects whose field value contains all array elements specified in the query.

**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|--------|
| name           | <code>String</code>       | Mandatory | Name of the field to which the condition is assigned   | "strangeNumbers" |
| _ value        | <code>SCArray</code>      | Mandatory | Array of values                             | [4, 8, 15, 16, 23, 42]     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.containsAll("someField", SCArray([SCString("A"), SCString("B")]))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}

```
----------------------------------------------------------------------------------------------------------
<a name="SCQuery+notContainedIn"></a>

### .notContainedIn(name, _ value)

Method for retrieving all objects whose field value does not contain the array elements specified in the query.


**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|--------|
| name           | <code>String</code>       | Mandatory |   Name of the field to which the condition is assigned     | "tags" |
| _ value        | <code>SCArray</code>      | Mandatory | Array of values                        | 42     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.notContainedIn("someField", SCArray([SCString("A"), SCString("B")]))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
-----------------------------------------------------------------------------------------------------------
<a name="SCQuery+greaterThan"></a>

### .greaterThan(name, _ value)

Method for retrieving all objects whose field value is greater than the number specified in the query.

**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|--------|
| name           | <code>String</code>       | Mandatory |   Name of the field to which the condition is assigned    | "reward" |
| _ value        | <code>SCValue</code>      | Mandatory |  Condition value                           | 42     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.greaterThan("reward", SCInt(100))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
----------------------------------------------------------------------------------------------------------
<a name="SCQuery+greaterThanOrEqualTo"></a>

### .greaterThanOrEqualTo(name, _ value)

Method for retrieving all objects whose field value is no less than the number specified in the query.

**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|--------|
| name           | <code>String</code>       | Mandatory |   Name of the field to which the condition is assigned    |"reward"|
| _ value        | <code>SCValue</code>      | Mandatory |  Condition value                             | 42     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.greaterThanOrEqualTo("createdAt", SCDate("2016-06-04T17:24:23.091+03:00"))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
----------------------------------------------------------------------------------------------------------
<a name="SCQuery+lessThan"></a>

### .lessThan(name, _ value)

Method for retrieving all objects whose field value is less than the number specified in the query.

**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|--------|
| name           | <code>String</code>       | Mandatory |  Name of the field whose value should be updated   | "price"|
| _ value        | <code>SCValue</code>      | Mandatory |  Condition value                             | 42     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.lessThan("price", SCInt(42))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
----------------------------------------------------------------------------------------------------------
<a name="SCQuery+lessThanOrEqualTo"></a>

### .lessThanOrEqualTo(name, _ value)

Method for retrieving all objects whose field value is no greater than the number specified in the query.

**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|--------|
| name           | <code>String</code>       | Mandatory |  Name of the field whose value should be updated     | "price"|
| _ value        | <code>SCValue</code>      | Mandatory |  Condition value                             | 42     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.lessThanOrEqualTo("price", SCInt(42))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
--------------------------------------------------------------------------------------------------------
<a name="SCQuery+exists"></a>

### .exists(name)

Method for retrieving all objects with an existing value of a defined field

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| name | <code>String</code> | Mandatory | Name of the field for which a condition is defined    | "price" | 

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.exists("reward")
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
------------------------------------------------------------------------------------------------------------
<a name="SCQuery+doesNotExist"></a>

### .doesNotExist(name)

Method for retrieving all objects with a missing value in a defined field.

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| name | <code>String</code> | Mandatory |  Name of the field for which a condition is defined  | "price" | 

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.doesNotExist("price")
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
-----------------------------------------------------------------------------------------------------------
<a name="SCQuery+contains"></a>

### .contains(name, _ pattern)

Method for retrieving all objects with a value of a defined field that matches a defined regular expression.

**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|----------------------|
| name           | <code>String</code>       | Mandatory |  Name of the field for which a condition is defined         | "stringsWithNumbers" |
| _ pattern      | <code>String</code>       | Mandatory | Regular expression                            | [0-9]                |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.contains("description", "[a-zA-Z0-9]")
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
----------------------------------------------------------------------------------------------------------
<a name="SCQuery+startsWith"></a>

### .startsWith(name, _ pattern)

Method for retrieving all objects with a value of a defined field starting from a specified string.


**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|--------|
| name           | <code>String</code>       | Mandatory | Name of the field for which a condition is defined           | "labels" |
| _ pattern        | <code>String</code>      | Mandatory | Condition value                             | "neverendi"     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.startsWith("fieldString", "[A-Z]")
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
---------------------------------------------------------------------------------------------------------
<a name="SCQuery+endsWith"></a>

### .endsWith(name, _ pattern)

Method for retrieving all objects with a value of a defined field ending with a specified string.

**Properties**

| Parameter | Type | Properties | Description | Value example |
|----------------|---------------------------|------------|------------------------------------------------|-------------------|
| name           | <code>String</code>       | Mandatory |  Name of the field whose value should be updated   | "labels"          |
| _ pattern        | <code>String</code>      | Mandatory | Condition value                          | "ngdocuments"     |

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.endsWith("fieldString", "ing")
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
---------------------------------------------------------------------------------------------------------
<a name="SCQuery+and"></a>

### .and(operators)

Method for logical multiplication of conditions of several samplings

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| operators | <code>[SCOperator]</code> | Mandatory | Sampling condition which is included in the conjunction|  | 

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.notEqualTo("unequality", SCString("nope"))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
----------------------------------------------------------------------------------------------------------
<a name="SCQuery+or"></a>

### .or(operators)

Method for Boolean addition of conditions of several samplings

**Properties**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| operators | <code>[SCOperator]</code> | Mandatory | Sampling condition which is included in the disjunction|  | 

**Example**

```SWIFT
var query = SCQuery(collection: "items")
query.notEqualTo("unequality", SCString("nope"))
query.find() {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```