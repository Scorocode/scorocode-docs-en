<a name="Update"></a>

Class for multiple object update operations

* [Update](#Update)
    * [new Update()](#Update_new)
	* [.set(field,value)](#Update+set)
	* [.push(field, value)](#Update+push)
	* [.popFirst(field)](#Update+popFirst)
	* [.popLast(field)](#Update+popLast)
	* [.pull(field, value)](#Update+pull)
	* [.pullAll(field, value)](#Update+pullAll)
	* [.addToSet(field, value)](#Update+addToSet)
	* [.inc(field,  increaseValue)](#Update+inc)
	* [.setCurrentDate(field)](#Update+setCurrentDate)
	* [.mul(field, value)](#Update+mul)
	* [.min(field, valueToCompare)](#Update+min)
	* [.max(field, valueToCompare)](#Update+max)
	* [.getUpdateInfo()](#Update+getUpdateInfo)


---------------------------------------------------------------------------------------------
<a name="Update_new"></a>

### new Update()
Update() constructor

```Java
Update  = new Update();
```

You can work with the methods of Update class using Document's .updateDocument method

```Java
Document document = new Document("ordersCollection");
//document.getDocumentById(...);
//document.updateDocument();
```

---------------------------------------------------------------------------------------------

<a name="Update+set"></a>
### .set(field,value)
Method for setting data to document's field

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | Field name to update  | "orderNumber"   |
| value | `Object` | Mandatory | New field value |  22 |


**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument()
                        .set("exampleField", "random Any1")
                        .set("anotherExampleField", "random Any2");


                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successfull
                    }


                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }


            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```

---------------------------------------------------------------------------------------------

<a name="Update+push"></a>
### .push(field, value)

Method for adding an element to an array field

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | Name of the field whose value should be updated | "orderNumber"   |
| value | `Object` | Mandatory | Value of the new array element | -42.42 |

**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument().push("array1", 1);


                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successful
                    }

                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }


            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```


---------------------------------------------------------------------------------------------

<a name="Update+popFirst"></a>
### .popFirst(field)
Method for removing the first array element of the field

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | Name of the field whose value should be updated | "orderNumber"   |

**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument().popFirst("array1");


                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successful
                    }


                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }


            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```

---------------------------------------------------------------------------------------------

<a name="Update+popLast"></a>
### .popLast(field)
Method for removing the last array element of the field

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | Name of the field whose value should be updated | "orderNumber"   |


**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument().popLast("array1");


                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successful
                    }


                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }


            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```

---------------------------------------------------------------------------------------------

<a name="Update+pull"></a>
### .pull(field, value)
Method for removing all array elements whose values are the same as the specified one.

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | Name of the field whose value should be updated  | "orderNumber"   |
| value | `Object` | Mandatory | Value of the element to be removed | "delete me" |

!!! note "Note"
    If there are many elements with specified value, this method will remove all of them.

**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument().pull("array2", 3);

                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successful
                    }

                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }

            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```
---------------------------------------------------------------------------------------------

<a name="Update+pullAll"></a>
### .pullAll(field, value)
Method for removing all array elements whose values are the same as one of the specified values.

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | ИName of the field whose value should be updated | "orderNumber"   |
| value | `List<Object>` | Mandatory | Array of values to be removed  | See the example below |


**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 		
                //create array of elements to delete from array
		    List<Object> objects = new ArrayList<>();
                objects.add(1);
                objects.add(2);
		    objects.add(3);

                document.updateDocument().pullAll("array2", objects);

                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successful
                    }

                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }

            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```

---------------------------------------------------------------------------------------------

<a name="Update+addToSet"></a>
### .addToSet(field, value)
Method for adding an element to an array only if there are no elements with the same name in the array.

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | Name of the field whose value should be updated  | "orderNumber"  |
| value | `List<Object>` | Mandatory | Value of the new array element  | See the example below |


**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument().addToSet("array4", 7);

                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successful
                    }

                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }

            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```
---------------------------------------------------------------------------------------------

<a name="Update+inc"></a>
### .inc(field,  increaseValue)
The method increments the numeric of date field value by a defined number of date

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | Name of the field whose value should be updated  | "counter"   |
| value | `Integer / Double / Date` | Mandatory | Increment step   | -2.2 |

**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument().inc("numberField", 2);
		    document.updateDocument().inc("anotherNumberField", -10);

                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successful
                    }

                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }

            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```

---------------------------------------------------------------------------------------------

<a name="Update+setCurrentDate"></a>
### .setCurrentDate(field)
Sets the current time as the field's value

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | Name of the field whose value should be updated | "registerDate"   |


**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument().setCurrentDate("date1");

                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successful
                    }

                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }

            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```


---------------------------------------------------------------------------------------------

<a name="Update+mul"></a>
### .mul(field, value)
The method multiplies the numeric field value by a defined number

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | Name of the field whose value should be updated  | "counter" |
| value | `Integer / Double` | Mandatory | Multiplier | -2.2 |


**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument().mul("numberForMulTest", 3);

                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successful
                    }

                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }

            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```

---------------------------------------------------------------------------------------------

<a name="Update+min"></a>
### .min(field, valueToCompare)
The method updates the numeric field value only if the new value is less than the current field value

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field           |`String`         | Mandatory | Name of the field whose value should be updated  | "price" |
| valueToCompare        | `Integer / Double`      | Mandatory | New value to be compared | 43    |

**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument().min("number2", 10);

                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successfull
                    }

                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }

            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```

---------------------------------------------------------------------------------------------

<a name="Update+max"></a>
### .max(field, valueToCompare)
The method updates the numeric field value only if the new value is greater than the current field value


| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field           |`String` | Mandatory |  Name of the field whose value should be updated  | "price" |
| valueToCompare  | `Integer / Double` | Mandatory | New value to be compared | 43    |

**Example**
```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found, we can update it
 
                document.updateDocument().max("number2", 10);

                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document updated successfull
                    }

                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document update failed
				//check update info
				//see errorCode and errorMessage
                    }
                });
            }

            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```


---------------------------------------------------------------------------------------------

<a name="Update+getUpdateInfo"></a>
### .getUpdateInfo()

Method for retrieving Update conditions info