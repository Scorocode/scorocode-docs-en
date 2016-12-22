<a name="SCValue"></a>

Protocol for data handling.

* [SCValue](#SCValue)
    * [SCBool(value)](#SCBool)
    * [SCString(value)](#SCString) 
    * [SCInt(value)](#SCInt)
    * [SCDouble(value)](#SCDouble)  
    * [SCDate(value)](#SCDate) 
    * [SCArray(value)](#SCArray) 
    * [SCDictionary(value)](#SCDictionary)

-----------------------------------------------------------------------------------------------

<a name="SCBool"></a> 

### SCBool(value)

Scorocode Boolean type

**Parameters**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| value | <code>Bool</code> | Mandatory | Logical value | `true` or `false` | 

```SWIFT
let dataBool = SCBool(true)
```

----------------------------------------------------------------------------------------------

<a name="SCString"></a> 

### SCString(value)

Scorocode String type

**Parameters**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| value | <code>String</code> | Mandatory | String value | "This is string" | 


```SWIFT
let dataString = SCString("AbCdE")
```

----------------------------------------------------------------------------------------------

<a name="SCInt"></a> 

### SCInt(value)

Scorocode Boolean type

**Parameters**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| value | <code>Int</code> | Mandatory | Integer value | -42 | 


```SWIFT
let dataInt = SCInt(5)
```

----------------------------------------------------------------------------------------------

<a name="SCDouble"></a> 

### SCDouble(value)

Scorocode Double type

**Parameters**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| value | <code>Double</code> | Mandatory | Floating-point value | 3.1415926 | 


```SWIFT
let dataDouble = SCDouble(3.1415926)
```

----------------------------------------------------------------------------------------------

<a name="SCDate"></a> 

### SCDate(value)

Scorocode Date type

**Parameters**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| value | <code>NSDate</code> | Mandatory | Date value | 2016-05-31 | 


```SWIFT
let dataDate = SCDate(dateFormatter.dateFromString("2016-05-31")!)
```

----------------------------------------------------------------------------------------------

<a name="SCArray"></a> 

### SCArray(value)

Scorocode Boolean type

**Parameters**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| value | <code>[SCValue]</code> | Mandatory | Array value | <code>[SCInt(4), SCInt(8), SCInt(15), SCInt(16), SCInt(23), SCInt(42)]</code> | 

```SWIFT
let dataBool = SCBool(true)
let dataString = SCString("AbCdE")
let dataInt = SCInt(5)
let dataDouble = SCDouble(3.1415926)
let dataDate = SCDate(dateFormatter.dateFromString("2016-05-31")!)
let dataDictionary = SCDictionary(["name" : dataString, "date" : dataDate])

let dataArray = SCArray([dataBool, dataString, dataInt, dataDouble, dataDate, dataDictionary])
```

----------------------------------------------------------------------------------------------

<a name="SCDictionary"></a>

### SCDictionary(value)

Scorocode Boolean type

**Parameters**

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| value | <code>[String: SCValue]</code> | Mandatory |Object with the "key" type of data: "value" | ["key1" : SCString("A"), "key2" : SCString("B")]|

```SWIFT
let dataDictionary = SCDictionary(["key1" : SCString("A"), "key2" : SCString("B")])
```
