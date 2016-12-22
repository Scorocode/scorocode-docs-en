<a name="SCObject"></a>

* [SCObject](#SCObject)
    * [init Object(collection, id?)](#SCObject+init)
    * [.set(dic)](#SCObject+set)
    * [.save(callback](#SCObject+save)  
    * [.getById(id, collection, callback)](#SCObject+getById)
    * [.get(name)](#SCObject+get)
    * [.upload(field, filename, data, callback](#SCObject+upload)
    * [.getFileLink(fieldName, callback)](#SCObject+getFileLink)
    * [.deleteFile (field, filename, callback)](#SCObject+deleteFile)  
    * [.remove(callback)](#SCObject+remove) 
    * [.push(name, _ value)](#SCObject+push)
    * [.pushEach(name, _ value)](#SCObject+pushEach)  
    * [.pull(name, _ value)](#SCObject+pull) 
    * [.pullAll(name, _ value)](#SCObject+pullAll) 
    * [.addToSet(name, _ value)](#SCObject+addToSet)
    * [.addToSetEach(name, _ value)](#SCObject+addToSetEach) 
    * [.pop(name, _ value)](#SCObject+pop) 
    * [.inc(name, _ value)](#SCObject+inc)
    * [.currentDate(name, typeSpec)](#SCObject+currentDate)
    * [.mul(name, _ value)](#SCObject+mul)
    * [.min(name, _ value)](#SCObject+min)
    * [.max(name, _ value)](#SCObject+max)

---------------------------------------------------------------------------------------------

<a name="SCObject+init"></a>

### init Object(collection, id?)
SCObject represents the application data object and includes methods for handling this data. The constructor creates a minimal basic "wrap" for user data.

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| collection | <code>String</code> | Обязательное | Имя коллекции в которую добавляется объект | "testcoll" | 
| id | <code>String</code> |   | _id объекта | "huNr3L7QDh" |

**Example** 

```SWIFT
// Создадим новый экземпляр объекта коллекции items.
let obj1 = SCObject(collection: "items", id: "huNr3L7QDh")
let obj2 = SCObject(collection: "items")
```

----------------------------------------------------------------------------------------------

<a name="SCObject+set"></a>

### .set(dic)
Method for setting data to object

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| dic        |<code>[String: SCValue]</code> |              | Dictionary with data to be transferred to document  | ["fieldString": SCString("NewValue")] |

**Example** 

```SWIFT
let newItem = SCObject(collection: "items")
newItem.set([
    "fieldString": SCString("Some test string"),
    "readACL": SCArray([SCString("*"), SCString("0123456789")])
    ])
newItem.save() {
    success, error, result in
    if success {
        // ... 
    } else {
        if let error = error {
            // ...
        }
    }
}
```
----------------------------------------------------------------------------------------------

<a name="SCObject+save"></a>

### .save(callback)
The method saves the object in the data warehouse or updates an object that already exists there

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|-----------------|
| callback |  <code>(Bool, SCError?, [String: AnyObject]?)</code> |              | Callback for the request being executed.   |                 |

**Example**  

```SWIFT
let newItem = SCObject(collection: "items")
newItem.set(["fieldName": SCString("Value")])
newItem.save() {
    success, error, result in
    if success {
        // ... 
    } else {
        if let error = error {
            // ...
        }
    }
}
```
----------------------------------------------------------------------------------------------

<a name="SCObject+getById"></a>

### .getById(id, collection, callback)
Method for retrieving a collection object from DB by its _id.

**Example**

| Parameter | Type | Properties | Description | Value example |
|--------------|-------------------------------------------------------------|--------------|------------------------------------|-----------------|
| id           | <code>String</code>                                         | Обязательный | Document identifier                | "huNr3L7QDh"    |
| collection   | <code>String</code>                                         | Обязательный | Collection name                    | "items"         |
| callback     | <code>(Bool, SCError?, [String: AnyObject]?) -> Void</code> |              | Callback for the request being executed.  ||

**Example**  

```SWIFT
SCObject.getById("p3OtsLXw8p", collection: "items") {
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
----------------------------------------------------------------------------------------------

<a name="SCObject+get"></a>

### .get(name)
Method for retrieving data from a specified object field.


| Parameter | Type | Properties | Description | Value example |
|--------------|------------------------|--------------|------------------------------------|-----------------|
| name  | <code>String</code>   |  Mandatory   |  Field name              |  "price" |

**Example**  

```SWIFT
let dataItem = SCObject(collection: "items", id: "huNr3L7QDh")
dataItem.get("price")
```
----------------------------------------------------------------------------------------------

<a name="SCObject+upload"></a>

### .upload(field, filename, data, callback)
File upload method

| Parameter | Type | Properties | Description | Value example |
|-----------|---------------------------------|--------------|--------------------------------------|-----------------|
| field     | <code>String</code>             | Mandatory    |  Field name                            | "attachments"   |
| filename  | <code>String</code>             |  Mandatory   |  File name                            |  "docname.pdf" |
| data       | <code>NSData</code>           | Mandatory |    File content                                  |                 |
| callback   | <code>(Bool, SCError?)</code>   |              | Callback for the request being executed.  |                 |

**Example**  

```SWIFT
let newItem = SCObject(collection: "items")
let image = UIImage(named:"forupload")
newItem.set([
    "description": SCString("Example upload")
    ])
newItem.save() {
    success, error, result in
    if success {
        newItem.upload("attachment", "image.jpg", data: image) {
            success, error, result in
            if success {
                print("Success")
            } else {
            if let error = error {
                    print("Error")
                }
            }
        }   
    } else {
        if let error = error {
             print("Error")
        }
    }
}
```
----------------------------------------------------------------------------------------------

<a name="SCObject+getFile"></a>

### .getFile(field, filename, callback)
Method for retrieving file contents

| Parameter | Type | Properties | Description | Value example |
|-----------|---------------------------------|--------------|--------------------------------------|-----------------|
| field     | <code>String</code>             | Mandatory    |  Field name                            | "attachments"   |
| filename  | <code>String</code>             |  Mandatory   |  File name                            |  "docname.pdf" |
| callback   | <code>(Bool, SCError?)</code>   |              | Callback for the request being executed.  |                 |

**Example**

```SWIFT
let item = SCObject(collection: "items", id: "huNr3L7QDh")
item.getFileLink("attachment")
    if success {
        print("Success")
    } else {
    if let error = error {
            print("Error")
        }
    }
}

```

----------------------------------------------------------------------------------------------

<a name="SCObject+deleteFile"></a>

### .deleteFile(field, filename, callback)

Method for file deletion

| Parameter | Type | Properties | Description | Value example |
|-----------|---------------------------------|--------------|--------------------------------------|-----------------|
| field     | <code>String</code>             | Mandatory    |  Field name                            | "attachments"   |
| filename  | <code>String</code>             |  Mandatory   |  File name                            |  "docname.pdf" |
| callback   | <code>(Bool, SCError?)</code>   |              | Callback for the request being executed.  |                 |

**Example** 

```SWIFT
let item = SCObject(collection: "items", id: "huNr3L7QDh")
item.delete("attachment", "swiftDocs.pdf")
    if success {
        print("Success")
    } else {
    if let error = error {
            print("Error")
        }
    }
}
```

----------------------------------------------------------------------------------------------

<a name="SCObject+remove"></a>

### .remove(callback)
Method for removing the selected document

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|-----------------|
| callback   | <code>(Bool, SCError?)</code> |              | Callback for the request being executed.   |                 |


**Example**  

```SWIFT
let item = SCObject(collection: "items", id: "huNr3L7QDh")
obj.remove() {
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

**Exception**

"Id is not specified" - <code>String</code>

----------------------------------------------------------------------------------------------

<a name="SCObject+push"></a>

### .push(name, _ value)
Method for adding an element to an array

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>          | Обязательный |  Name of the field whose value should be updated     | "tags" |
| _ value        | <code>SCValue</code>        | Обязательный |  Value of the new array element             | 42     |


**Example**

```SWIFT
let editItem = SCObject(collection: "items")
editItem.push("location", SCString("Sierra Army Depot"))
```

----------------------------------------------------------------------------------------------

<a name="SCObject+pushEach"></a>

### .pushEach(name, _ value)
Method for adding several elements to an array.


| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           | <code>String</code>       | Обязательный |  Name of the field whose value should be updated    | "tags" |
| _ value        | <code>SCValue</code>      | Обязательный |  Values of new array elements            | 42, [43,43], 44     |


**Example**

```SWIFT
let editItem = SCObject(collection: collection)
editItem.pushEach("location", SCArray([SCString("Sierra Army Depot"), SCString("Navarro")]))
```

----------------------------------------------------------------------------------------------

<a name="SCObject+pull"></a>

### .pull(name, _ value)
Method for removing all array elements whose values are the same as the specified one.

  
| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           | <code>String</code>       | Обязательный |  Name of the field whose value should be updated   | "tags" |
| _ value        | <code>SCPullable</code>      | Обязательный | Value to be removed               | 42     |

----------------------------------------------------------------------------------------------

<a name="SCObject+pullAll"></a>

### .pullAll(name, _ value)

Method for removing all array elements whose values are the same as one of the specified values.


| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           | <code>String</code> | Обязательный |  Name of the field whose value should be updated      | "tags" |
| _ value        | <code>SCValue</code>| Обязательный |  Array of values to be removed              | [42, 44]     |

----------------------------------------------------------------------------------------------

<a name="SCObject+addToSet"></a>

### .addToSet(name, _ value)
Method for adding an element to an array only if there are no elements with the same name in the array.

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>         | Обязательный |  Name of the field whose value should be updated   | "tags" |
| _ value        | <code>SCValue</code>      | Обязательный |  Value of the new array element               | 42     |

**Example**

```SWIFT
let editItem = SCObject(collection: "items")
editItem.addToSet("location", SCString("A"))

```

----------------------------------------------------------------------------------------------

<a name="SCObject+addToSetEach"></a>

### .addToSetEach(name, _ value)
Method for adding elements to an array only if there are no elements with the same name in the array.

| Parameter | Type | Properties | Description | Value example |
|------------|------------------|--------------|--------------------------------------|---------------------------------------|
| name           |<code>String</code>         | Обязательный |  Name of the field whose value should be updated  | "tags" |
| _ value        | <code>SCValue</code>      | Обязательный |  Array of new array element values                | [42, 43]     |

**Example**

```SWIFT
let editItem = SCObject(collection: "items")
editItem.addToSetEach("location", SCArray([SCString("Sierra Army Depot"), SCString("Navarro")]))
```

----------------------------------------------------------------------------------------------

<a name="SCObject+pop"></a>

### .pop(name, _ value)
Method for removing the first or the last array element


| Parameter | Type                | Properties   | Description                                                                     | Value example |
|-----------|---------------------|--------------|---------------------------------------------------------------------------------|---------------|
| name      | <code>String</code> | Обязательный | Name of the field whose value should be updated                                 | "tags"        |
| _ value   | <code>Int</code>    | Обязательный | Position of the element to be removed in the array: -1 for the first element and 1 for the last | -1            |

**Example** 

```SWIFT
let editItem = SCObject(collection: "items")
editItem.pop("location", 1)
```



----------------------------------------------------------------------------------------------

<a name="SCObject+inc"></a>

### .inc(name, _ value)
The method increments the numeric field value by a defined number

| Parameter | Type                 | Properties   | Description                                     | Value example |
|-----------|----------------------|--------------|-------------------------------------------------|---------------|
| name      | <code>String</code>  | Обязательный | Name of the field whose value should be updated | "price"       |
| _ value   | <code>SCValue</code> | Обязательный | Increment step                                  | 5             |


**Example** 

```SWIFT 
let editItem = SCObject(collection: "items")
editItem.inc("amount", SCInt(-14))
```

----------------------------------------------------------------------------------------------

<a name="SCObject+currentDate"></a>

### .currentDate(name, typeSpec)
Sets the current time as the field's value

| Parameter | Type                 | Properties   | Description                                                          | Value example |
|-----------|----------------------|--------------|----------------------------------------------------------------------|---------------|
| name      | <code>String</code>  | Обязательный | Name of the field whose value should be updated                      | "price"       |
| typeSpec  | <code>SCValue</code> | Обязательный | Date type. Accepts the following values: true, "date" or "timestamp" | "timestamp"   |

**Example**:

```SWIFT
let editItem = SCObject(collection: "items")
editItem.currentDate("someDate", typeSpec: "date")

```


----------------------------------------------------------------------------------------------

<a name="SCObject+mul"></a>

### .mul(name, _ value)
The method multiplies the numeric field value by a defined number

| Parameter | Type                 | Properties   | Description                                     | Value example |
|-----------|----------------------|--------------|-------------------------------------------------|---------------|
| name      | <code>String</code>  | Обязательный | Name of the field whose value should be updated | "price"       |
| _ value   | <code>SCValue</code> | Обязательный | Multiplier                                      | 2.5           |

**Example**  

```SWIFT
let editItem = SCObject(collection: "items")
editItem.min("price", SCDouble(42.42))
```

----------------------------------------------------------------------------------------------

<a name="SCObject+min"></a>

### .min(name, _ value)
The method updates the numeric field value only if the new value is less than the current field value

| Parameter | Type                 | Properties   | Description                                     | Value example |
|-----------|----------------------|--------------|-------------------------------------------------|---------------|
| name      | <code>String</code>  | Обязательный | Name of the field whose value should be updated | "price"       |
| _ value   | <code>SCValue</code> | Обязательный | New value                                       | 42            |

**Example**  

```SWIFT
let editItem = SCObject(collection: "items")
editItem.min("price", SCInt(42))
```

----------------------------------------------------------------------------------------------


<a name="SCObject+max"></a>

### .max(name, _ value)
The method updates the numeric field value only if the new value is greater than the current field value

| Parameter | Type                 | Properties   | Description                                     | Value example |
|-----------|----------------------|--------------|-------------------------------------------------|---------------|
| name      | <code>String</code>  | Обязательный | Name of the field whose value should be updated | "price"       |
| _ value   | <code>SCValue</code> | Обязательный | New value                                       | 43            |

**Example**  

```SWIFT
let editItem = SCObject(collection: "items")
```

