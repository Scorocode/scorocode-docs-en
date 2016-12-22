<a name="SCUpdate"></a>

* [SCUpdate](#SCUpdate)
    * [.addOperator(oper: SCUpdateOperator)](#SCUpdate+addOperator)
    * [.set(dic: [String: SCValue])](#SCUpdate+set) 
    * [.push(name: String, _ value: SCValue)](#SCUpdate+push)
    * [.pushEach(name: String, _ value: SCValue)](#SCUpdate+pushEach)  
    * [.pull(name: String, _ value: SCPullable)](#SCUpdate+pull) 
    * [.pullAll(name: String, _ value: SCValue)](#SCUpdate+pullAll) 
    * [.addToSet(name: String, _ value: SCValue)](#SCUpdate+addToSet)
    * [.addToSetEach(name: String, _ value: SCValue)](#SCUpdate+addToSetEach) 
    * [.pop(name: String, _ value: Int)](#SCUpdate+pop) 
    * [.inc(name: String, _ value: SCValue)](#SCUpdate+inc)
    * [.currentDate(name: String, typeSpec: String)](#SCUpdate+currentDate)
    * [.mul(name: String, _ value: SCValue)](#SCUpdate+mul)
    * [.min(name: String, _ value: SCValue)](#SCUpdate+min)
    * [.max(name: String, _ value: SCValue)](#SCUpdate+max)

----------------------------------------------------------------------------------------------
<a name="SCUpdate+addOperator"></a> 

### .addOperator(name, oper)

Method for transferring the SCUpdate operator to modify data

**Parameters**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| oper | <code>SCUpdateOperator</code> | Mandatory | Sampling condition |  | 

```SWIFT
var update = SCUpdate()
let currentDate = SCUpdateOperator.currentDate("fieldName", typeSpec: "timestamp")
update.addOperator(currentDate)
```

----------------------------------------------------------------------------------------------

<a name="SCUpdate+set"></a>

### .set(dic: [String: SCValue])

Method for transferring data to object

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| dic        |<code>[String: SCValue]</code>  |              | Object with data to be transferred to object   | ["fieldString": SCString("NewValue")] |

**Example**  

```SWIFT
var update = SCUpdate()
update.set(["fieldName": SCString("A")])
```

----------------------------------------------------------------------------------------------

<a name="SCUpdate+push"></a>

### .push(name: String, _ value: SCValue))

Method for adding an element to an array

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>         | Mandatory |  Name of the field whose value should be updated   | "tags" |
| _ value        | <code>SCValue</code>       | Mandatory |  Value of the new array element              | 42     |

**Example**

```SWIFT
var update = SCUpdate()
update.push("fieldName", SCString("A"))
update.save()
```

----------------------------------------------------------------------------------------------

<a name="SCUpdate+pushEach"></a>

### .pushEach(name: String, _ value: SCValue))

Method for adding several elements to an array.

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           | <code>String</code>       | Mandatory |  Name of the field whose value should be updated  | "tags" |
| _ value        | <code>SCValue</code>      | Mandatory |  Value of the new array element            | 42, [43,43], 44     |


**Example**

```SWIFT
var update = SCUpdate()
update.pushEach("fieldName", SCArray([SCString("A")]))
```

----------------------------------------------------------------------------------------------

<a name="SCUpdate+pull"></a>

### .pull(name: String, _ value: SCPullable)

Method for removing all array elements whose values are the same as the specified one.

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           | <code>String</code>       | Mandatory |  Name of the field whose value should be updated  | "tags" |
| _ value        | <code>SCPullable</code>      | Mandatory | Value to be removed               | 42     |

**Example**

```SWIFT
var update = SCUpdate()
update.pull("fieldName", SCString("A"))
```



----------------------------------------------------------------------------------------------

<a name="SCUpdate+pullAll"></a>

### .pullAll(name: String, _ value: SCValue)

Method for removing all array elements whose values are the same as one of the specified values.

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           | <code>String</code> | Mandatory |  Name of the field whose value should be updated  | "tags" |
| _ value        | <code>SCValue</code>| Mandatory |  Array of values to be removed             | [42, 44]     |

**Example**

```SWIFT
var update = SCUpdate()
update.pullAll("fieldName", SCArray([SCString("A")]))
```

----------------------------------------------------------------------------------------------

<a name="SCUpdate+addToSet"></a>

### .addToSet(name: String, _ value: SCValue)

Method for adding an element to an array only if there are no elements with the same name in the array.

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>         | Mandatory |  Name of the field whose value should be updated  | "tags" |
| _ value        | <code>SCValue</code>      | Mandatory | Value of the new array element               | 42     |

**Example**

```SWIFT
var update = SCUpdate()
update.addToSet("fieldName", SCString("A"))
```

----------------------------------------------------------------------------------------------

<a name="SCUpdate+addToSetEach"></a>

### .addToSetEach(name: String, _ value: SCValue)

Method for adding elements to an array only if there are no elements with the same name in the array.

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>         | Mandatory |  Name of the field whose value should be updated  | "tags" |
| _ value        | <code>SCValue</code>      | Mandatory |  Array of new array element values         | [42, 43]     |

**Example**

```SWIFT
var update = SCUpdate()
update.addToSetEach("fieldName", SCArray(SCString("A"))
```

----------------------------------------------------------------------------------------------

<a name="SCUpdate+pop"></a>

### .pop(name: String, _ value: Int)

Method for removing the first or the last array element


| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>         | Mandatory |  Name of the field whose value should be updated  | "tags" |
| _ value        | <code>Int</code>      | Mandatory | Position of the element to be removed in the array: -1 for the first element and 1 for the last   | -1     |

**Example**

```SWIFT
var update = SCUpdate()
update.pop("fieldName", 1)
```



----------------------------------------------------------------------------------------------

<a name="SCUpdate+inc"></a>

### .inc(name: String, _ value: SCValue)

The method increments the numeric field value by a defined number

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>          | Mandatory |  Name of the field whose value should be updated  | "price" |
| _ value        | <code>SCValue</code>        | Mandatory |  Increment step     | 5     |

**Example** 

```SWIFT 
var update = SCUpdate()
update.inc("fieldName", SCInt(1))
```

----------------------------------------------------------------------------------------------

<a name="SCUpdate+currentDate"></a>

### .currentDate(name: String, typeSpec: String)

Sets the current time as the field's value


| Parameter | Type | Properties | Description | Value example |
|------------|---------------------|--------------|------------------------------------------------------------|---------------|
| name       |<code>String</code>  | Mandatory |  Name of the field whose value should be updated                | "price"       |
| typeSpec   | <code>SCValue</code>| Mandatory | Date type. Accepts the following values: true, "date" or "timestamp"    | "timestamp"   |

**Example**

```SWIFT
var update = SCUpdate()
update.currentDate("fieldName", typeSpec: "date")
```


----------------------------------------------------------------------------------------------

<a name="SCUpdate+mul"></a>

### .mul(name: String, _ value: SCValue)

The method multiplies the numeric field value by a defined number


| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>         | Mandatory |  Name of the field whose value should be updated  | "price" |
| _ value        | <code>SCValue</code>      | Mandatory | Multiplier    | 2.5    |

**Example**  

```SWIFT
var update = SCUpdate()
update.mul("fieldName", SCInt(5))
```

----------------------------------------------------------------------------------------------

<a name="SCUpdate+min"></a>

### .min(name: String, _ value: SCValue)

The method updates the numeric field value only if the new value is less than the current field value

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>         | Mandatory |  Name of the field whose value should be updated  | "price" |
| _ value        | <code>SCValue</code>      | Mandatory | New value    | 42    |


**Example**  

```SWIFT
var update = SCUpdate()
update.min("fieldName", SCInt(5))
```

----------------------------------------------------------------------------------------------


<a name="SCUpdate+max"></a>

### .max(name: String, _ value: SCValue)

The method updates the numeric field value only if the new value is greater than the current field value

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>         | Mandatory |  Name of the field whose value should be updated  | "price" |
| _ value        | <code>SCValue</code>      | Mandatory | New value  | 42    |

**Example**  

```SWIFT
var update = SCUpdate()
update.max("fieldName", SCInt(5))
```