<a name="Query"></a>

## Query
Класс для вборки документов коллекции.

**Содержание**

* [Query](#Query)
    * [new Query(name)](#Query_new)
    * [.findDocuments(callback)](#Query+findDocuments)
    * [.countDocuments(callback)](#Query+countDocuments)
    * [.updateDocument(update, callback)](#Query+updateDocument)
    * [.removeDocument(callback)](#Query+removeDocument)
    * [.setLimit(limit)](#Query+setLimit)
    * [.setSkip(skip)](#Query+setSkip)
    * [.setPage(page)](#Query+setPage)
    * [.equalTo(field, value)](#Query+equalTo)
    * [.notEqualTo(field, value)](#Query+notEqualTo)
    * [.containedIn(field, values)](#Query+containedIn)
    * [.containsAll(field, values)](#Query+containsAll)
    * [.notContainedIn(field, values)](#Query+notContainedIn)
    * [.greaterThan(field, value)](#Query+greaterThan)
    * [.greaterThenOrEqualTo(field, value)](#Query+greaterThenOrEqualTo)
    * [.lessThan(field,  value)](#Query+lessThan)
    * [.lessThanOrEqualTo(field, value)](#Query+lessThanOrEqualTo)
    * [.exists(field)](#Query+exists)
    * [.doesNotExist(field)](#Query+doesNotExist)
    * [.contains(field, regEx, options)](#Query+contains)
    * [.startsWith(field, regEx, options)](#Query+startsWith)
    * [.endsWith(field, regEx, options)](#Query+endsWith)
    * [.and(field, query)](#Query+and)
    * [.or(field, query)](#Query+or)
    * [.raw(json)](#Query+raw)
    * [.reset()](#Query+reset)
    * [.ascending(field)](#Query+ascending)
    * [.descending(field)](#Query+descending)
    * [.setFieldsForSearch(fields)](#Query+setFieldsForSearch)
    * [.getQueryInfo()](#Query+getQueryInfo)

---------------------------------------------------------------------------------------------
<a name="Query_new"></a>

### new Query()

Initialisation of a collection data query

| Parameter       | Type     | Properties | Description     | Value example |
|-----------------|----------|------------|-----------------|---------------|
| collection_name | `String` |            | Collection name | "things"      |

**Example** 

```Java
Query query = new Query("name");
```
---------------------------------------------------------------------------------------------

<a name="Query+findDocuments"></a>
### .findDocuments(callback)
Method for requesting a document from a collection. Returns data of the objects that match the sampling criteria. 


| Parameter | Type                   | Properties | Description                              | Value example |
|-----------|------------------------|------------|------------------------------------------|---------------|
| callback  | `CallbackFindDocument` | Mandatory  | Callback for the request being executed. |               |


!!! note "Note"
    If no criteria are set, the first 50 objects of the collection are returned by default.

**Example** 

```Java
Query query = new Query(“mycollection”)
                .equalTo("number3", 10)
                .exists("number2");

query.findDocuments(new CallbackFindDocument() {
            @Override
            public void onDocumentFound(List<DocumentInfo> documentInfos) {
                //found. See document list what match query
            }

            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //no documents what match query
            }
        });
```
---------------------------------------------------------------------------------------------

<a name="Query+countDocuments"></a>
### .countDocuments(callback)

Method for counting objects that meet the query conditions.

| Parameter | Type                     | Properties | Description                              | Value example |
|-----------|--------------------------|------------|------------------------------------------|---------------|
| callback  | `CallbackCountDocument ` | Mandatory  | Callback for the request being executed. |               |


**Example** 

```Java
Query query = new Query(“mycollection”);
        query.greaterThan("rating", 10);

        query.countDocuments(new CallbackCountDocument() {
            @Override
            public void onDocumentsCounted(ResponseCount responseCount) {
                //see responseCount.getResult() to find how many documents was found.
            }

            @Override
            public void onCountFailed(String errorCode, String errorMessage) {
                //error during count
            }
        });
```
---------------------------------------------------------------------------------------------

<a name="Query+updateDocument"></a>
### .updateDocument(update, callback)

Method for updating the requested objects.

| Parameter | Type                     | Properties | Description                              | Value example |
|-----------|--------------------------|------------|------------------------------------------|---------------|
| update    | `Update`                 | Mandatory  | Update object                            |               |
| callback  | `CallbackUpdateDocument` | Mandatory  | Callback for the request being executed. |               |


!!! note "Note"
    This method can update a maximum of 1000 documents in a request.

**Example** 

```Java
 Query query = new Query(“mycollection”);
        query.equalTo("number3", 10);

        Update update = new Update()
                .set("number2", 199)
                .set("numberField", 111)
                .addToSet("array1", 900);

        query.updateDocument(update, new CallbackUpdateDocument() {
            @Override
            public void onUpdateSucceed(ResponseUpdate responseUpdate) {
                //documents updated successful
            }

            @Override
            public void onUpdateFailed(String errorCode, String errorMessage) {
                //error during update
            }
        });
```
---------------------------------------------------------------------------------------------

<a name="Query+removeDocument"></a>
### .removeDocument(callback)

Method for removing the requested documents.

| Parameter | Type                     | Properties | Description                              | Value example |
|-----------|--------------------------|------------|------------------------------------------|---------------|
| callback  | `CallbackRemoveDocument` | Mandatory  | Callback for the request being executed. |               |

!!! note "Note"
    This method can remove a maximum of 1000 documents in a request.

**Example** 

```Java
Query query = new Query(“mycollection”);
        query.equalTo("_id", "aJfkipJags");

        query.removeDocument(new CallbackRemoveDocument() {
            @Override
            public void onRemoveSucceed(ResponseRemove responseRemove) {
                //succeed. See responseRemove to findout how many documents was removed
            //and get list of removed documents
            }

            @Override
            public void onRemoveFailed(String errorCode, String errorMessage) {
                //error during remove operation
            }
        });

```
---------------------------------------------------------------------------------------------

<a name="Query+setLimit"></a>
### .setLimit(limit)

Method for specifying a limit for the number of sampling, updating or removing documents.

| Parameter | Type      | Properties | Description | Value example |
|-----------|-----------|------------|-------------|---------------|
| limit     | `Integer` | Mandatory  | Limit       | 15            |


!!! note "Note"
    Limit defaults to 50, but anything from 1 to 100 is a valid limit.

**Example** 

```Java
Query query = new Query(“mycollection”);
query.setLimit(15);
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+setSkip"></a>
### .setSkip(skip)

Method for skipping some objects before sampling.

| Parameter | Type      | Properties | Description               | Value example |
|-----------|-----------|------------|---------------------------|---------------|
| skip      | `Integer` | Mandatory  | Number of skipped objects | 100           |

**Example** 

```Java
Query query = new Query(“mycollection”);
query.setSkip(12);
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+setPage"></a>
### .setPage(page)

Method for sampling results page by page

| Parameter | Type      | Properties | Description | Value example |
|-----------|-----------|------------|-------------|---------------|
| page      | `Integer` | Mandatory  | Page number | 2             |

**Example** 

```Java
Query query = new Query(“mycollection”);
//query.setLimit(15);
query.setPage(1);
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+equalTo"></a>
### .equalTo(field, value)

Method for retrieving all objects with the field value indicated in the condition.


| Parameter | Type     | Properties | Description                                        | Value example |
|-----------|----------|------------|----------------------------------------------------|---------------|
| field     | `String` | Mandatory  | Name of the field for which a condition is defined | "orderNumber" |
| value     | `Object` | Mandatory  | Field value                                        | 22            |

**Example** 

```Java
Query query = new Query(“mycollection”);
query.equalTo(“orderNumber”, 22);
//query.findDocuments(…);
```

```Java
Query query = new Query(“mycollection”);
query.equalTo(“_id”, “dasds12dskm”);
//query.findDocuments(…);
```

---------------------------------------------------------------------------------------------

<a name="Query+notEqualTo"></a>
### .notEqualTo(field, value)

Method for retrieving all objects except for objects with the field value indicated in the condition.

| Parameter | Type     | Properties | Description                                        | Value example |
|-----------|----------|------------|----------------------------------------------------|---------------|
| field     | `String` | Mandatory  | Name of the field for which a condition is defined | "orderNumber" |
| value     | `Object` | Mandatory  | Field value                                        | 22            |


**Example** 

```Java
Query query = new Query(“mycollection”);
query.notEqualTo(“orderNumber”, 22);
//query.findDocuments(…);
```

```Java
Query query = new Query(“mycollection”);
query.equalTo(“_id”, “dasds12dskm”);
//query.findDocuments(…);
```

---------------------------------------------------------------------------------------------

<a name="Query+containedIn"></a>
### .containedIn(field, values)

Method for retrieving all objects whose field value contains the array elements specified in the query.

| Parameter | Type             | Properties | Description                                        | Value example         |
|-----------|------------------|------------|----------------------------------------------------|-----------------------|
| field     | `String`         | Mandatory  | Name of the field for which a condition is defined | "orderNumbers"        |
| value     | `List<тип поля>` | Mandatory  | Array of values                                    | see the example below |


**Example** 

```Java
List<Object> numbers = new ArrayList<>();
        numbers.add(1);
        numbers.add(5);
        numbers.add(10);
        numbers.add(15);

Query query = new Query(“mycollection”).containedIn("number3", numbers);
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+containsAll"></a>
### .containsAll(field, values)

Method for retrieving all objects whose field value contains all array elements specified in the query.

| Parameter | Type             | Properties | Description                                        | Value example         |
|-----------|------------------|------------|----------------------------------------------------|-----------------------|
| field     | `String`         | Mandatory  | Name of the field for which a condition is defined | "orderNumbers"        |
| value     | `List<тип поля>` | Mandatory  | Array of values                                    | see the example below |

**Example** 

```Java
List<Object> containsAllNumbers = new ArrayList<>();
        containsAllNumbers.add(1);
        containsAllNumbers.add(2);
        containsAllNumbers.add(3);
        containsAllNumbers.add(900);
Query query = new Query(“mycollection”).containsAll("array1", containsAllNumbers);
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+notContainedIn"></a>
### .notContainedIn(field, values)
Method for retrieving all objects whose field value 

* does not contain the array elements specified in the query 
* does not exist

| Parameter | Type             | Properties | Description                                        | Value example         |
|-----------|------------------|------------|----------------------------------------------------|-----------------------|
| field     | `String`         | Mandatory  | Name of the field for which a condition is defined | "orderNumbers"        |
| value     | `List<тип поля>` | Mandatory  | Array of values                                    | see the example below |

**Example** 

```Java
List<Object> notContainsInList = new ArrayList<>();
        notContainsInList.add(1);
        notContainsInList.add(111);
        notContainsInList.add(11);
        notContainsInList.add(50);
Query query = new Query(“mycollection”).notContainedIn("orderNumbers", notContainsInList)
//query.findDocuments(…);

```
---------------------------------------------------------------------------------------------

<a name="Query+greaterThan"></a>
### .greaterThan(field, value)
Method for retrieving all objects whose field value is greater than the number specified in the query.

| Parameter | Type                      | Properties | Description                                        | Value example |
|-----------|---------------------------|------------|----------------------------------------------------|---------------|
| field     | `String`                  | Mandatory  | Name of the field for which a condition is defined | "fieldname"   |
| value     | `Integer / Double / Date` | Mandatory  | Condition value                                    | 22            |

**Example** 

```Java
Query query = new Query(“mycollection”).greaterThan("number", 22)
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+greaterThenOrEqualTo"></a>
### .greaterThenOrEqualTo(field, value)
Method for retrieving all objects whose field value is no less than the number specified in the query.

| Parameter | Type                      | Properties | Description                                        | Value example |
|-----------|---------------------------|------------|----------------------------------------------------|---------------|
| field     | `String`                  | Mandatory  | Name of the field for which a condition is defined | "fieldname"   |
| value     | `Integer / Double / Date` | Mandatory  | Condition value                                    | 22            |


**Example** 

```Java
Query query = new Query(“mycollection”).greaterThenOrEqualTo ("number", 22)
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+lessThan"></a>
### .lessThan(field, value)
Method for retrieving all objects whose field value is less than the number specified in the query.

| Parameter | Type                      | Properties | Description                                        | Value example |
|-----------|---------------------------|------------|----------------------------------------------------|---------------|
| field     | `String`                  | Mandatory  | Name of the field for which a condition is defined | "fieldname"   |
| value     | `Integer / Double / Date` | Mandatory  | Condition value                                    | 22            |

**Example** 

```Java
Query query = new Query(“mycollection”). lessThan("number", 22)
//query.findDocuments(…);

```
---------------------------------------------------------------------------------------------

<a name="Query+lessThanOrEqualTo"></a>
### .lessThanOrEqualTo(field, value)
Method for retrieving all objects whose field value is no greater than the number specified in the query.

| Parameter | Type                      | Properties | Description                                        | Value example |
|-----------|---------------------------|------------|----------------------------------------------------|---------------|
| field     | `String`                  | Mandatory  | Name of the field for which a condition is defined | "fieldname"   |
| value     | `Integer / Double / Date` | Mandatory  | Condition value                                    | 22            |

**Example** 

```Java
Query query = new Query(“mycollection”).lessThanOrEqualTo ("number", 22)
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+exists"></a>
### .exists(field)
Method for retrieving all objects with an existing value of a defined field

| Parameter | Type     | Properties | Description                                        | Value example |
|-----------|----------|------------|----------------------------------------------------|---------------|
| field     | `String` | Mandatory  | Name of the field for which a condition is defined | "fieldname"   |

**Example** 

```Java
Query query = new Query(“mycollection”).exists("phoneNumber")
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+doesNotExist"></a>
### .doesNotExist(field)
Method for retrieving all objects with a missing value in a defined field.

| Parameter | Type     | Properties | Description                                        | Value example |
|-----------|----------|------------|----------------------------------------------------|---------------|
| field     | `String` | Mandatory  | Name of the field for which a condition is defined | "fieldname"   |

**Example** 

```Java
Query query = new Query(“mycollection”).doesNotExist("phoneNumber")
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+contains"></a>
### .contains(field, regEx, options)
Method for retrieving all objects with a value of a defined field that matches a defined regular expression.


| Parameter | Type           | Properties | Description                                        | Value example         |
|-----------|----------------|------------|----------------------------------------------------|-----------------------|
| field     | `String`       | Mandatory  | Name of the field for which a condition is defined | "fieldname"           |
| regEx     | `String`       | Mandatory  | Regular expression                                 | “aB”                  |
| options   | `RegexOptions` | Optional   | Regular expression options                         | See the example below |

**Example** 

```Java
 RegexOptions regexOptions = new RegexOptions();
 regexOptions.setRegexCaseInsenssitive();

 Query query = new Query(“mycollection”).contains("exampleField", "BC", regexOptions)
 //query.findDocuments(…);         
```
---------------------------------------------------------------------------------------------

<a name="Query+startsWith"></a>
### .startsWith(field, regEx, options)
Method for retrieving all objects with a value of a defined field starting from a specified string.

| Parameter | Type           | Properties | Description                                        | Value example         |
|-----------|----------------|------------|----------------------------------------------------|-----------------------|
| field     | `String`       | Mandatory  | Name of the field for which a condition is defined | "fieldname"           |
| regEx     | `String`       | Mandatory  | Regular expression                                 | “aB”                  |
| options   | `RegexOptions` | Optional   | Regular expression options                         | See the example below |


**Example** 

```Java
 RegexOptions regexOptions = new RegexOptions();
 regexOptions.setRegexCaseInsenssitive();

 Query query = new Query(“mycollection”).startsWith ("exampleField", "a", regexOptions)
 //query.findDocuments(…);

```
---------------------------------------------------------------------------------------------

<a name="Query+endsWith"></a>
### .endsWith(field, regEx, options)

Method for retrieving all objects with a value of a defined field ending with a specified string.


| Parameter | Type           | Properties | Description                                        | Value example         |
|-----------|----------------|------------|----------------------------------------------------|-----------------------|
| field     | `String`       | Mandatory  | Name of the field for which a condition is defined | "fieldname"           |
| regEx     | `String`       | Mandatory  | Regular expression                                 | “aB”                  |
| options   | `RegexOptions` | Optional   | Regular expression options                         | See the example below |

**Example** 

```Java
 RegexOptions regexOptions = new RegexOptions();
 regexOptions.setRegexCaseInsenssitive();

 Query query = new Query(“mycollection”).endsWith("exampleField", "a", regexOptions)
 //query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+and"></a>
### .and(field, query)
Method for logical multiplication of several samplings conditions

| Parameter | Type     | Properties | Description                                         | Value example         |
|-----------|----------|------------|-----------------------------------------------------|-----------------------|
| field     | `String` | Mandatory  | Name of the field for which a condition is defined  | "fieldname"           |
| query     | `Query`  | Mandatory  | Query that is included in the conjunction operation | See the example below |

**Example** 

```Java
Query query1 = new Query(COLLECTION_NAME).greaterThan("raiting", 50);
Query query2 = new Query(COLLECTION_NAME).lessThan("raiting", 100);

query1.and("number3", query2);
//query1.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+or"></a>
### .or(field, query)
Method for logical addition of several samplings conditions

| Parameter | Type     | Properties | Description                                         | Value example         |
|-----------|----------|------------|-----------------------------------------------------|-----------------------|
| field     | `String` | Mandatory  | Name of the field for which a condition is defined  | "fieldname"           |
| query     | `Query`  | Mandatory  | Query that is included in the conjunction operation | See the example below |

**Example** 

```Java
Query query1 = new Query(“mycollection”).greaterThan("raiting", 50);
Query query2 = new Query(“mycollection”).equalTo("status", 0);

query1.or("number3", query2);
//query1.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+raw"></a>
### .raw(json)
Method for defining sampling conditions in the form of a JSON structure to create a DB query in MongoDB language.

| Parameter | Type     | Properties | Description                                         | Value example                          |
|-----------|----------|------------|-----------------------------------------------------|----------------------------------------|
| json      | `String` | Mandatory  | Applied filter in the MongoDB query language format | "{\"_id\": {\"$eq\": \"W9vrMS9SuW\"}}" |

**Example** 

```Java
  Query query = new Query(“mycollection”);
  query.raw("{\"_id\": {\"$eq\": \"W9vrMS9SuW\"}}");
  //query.findDocuments(…)
```
---------------------------------------------------------------------------------------------

<a name="Query+reset"></a>
### .reset()
Method for resetting the sampling conditions

**Example** 

```Java
Query query = new Query(“mycollection”);
query.equalTo(“_id”, “dsads123sd”);
query.reset();
query.equalTo(“_id”, “ds54522sd”);
//query.findDocuments(…)
```
---------------------------------------------------------------------------------------------

<a name="Query+ascending"></a>
### .ascending(field)
Method for sorting a specified field data in ascending order before sampling.

| Parameter | Type     | Properties | Description | Value example |
|-----------|----------|------------|-------------|---------------|
| field     | `String` | Mandatory  | Field name  | "fieldname"   |

**Example** 

```Java
Query query = new Query("ordersCollection");
query.ascending("itemId");
//query.findDocuments(...)
```
---------------------------------------------------------------------------------------------

<a name="Query+descending"></a>
### .descending(field)
Method for sorting a specified field data in descending order before sampling.

| Parameter | Type     | Properties | Description | Value example |
|-----------|----------|------------|-------------|---------------|
| field     | `String` | Mandatory  | Field name  | "fieldname"   |

**Example** 

```Java
Query query = new Query("ordersCollection");
query.descending("itemId");
//query.findDocuments(...)
```
---------------------------------------------------------------------------------------------

<a name="Query+setFieldsForSearch"></a>
### .setFieldsForSearch(fields)
Method for specifying a list of returned fields.

| Parameter | Type           | Properties | Description  | Value example         |
|-----------|----------------|------------|--------------|-----------------------|
| fields    | `List<String>` | Mandatory  | Fields names | See the example below |

**Example** 

```Java
List<Strings> fieldNames = new ArrayList<>();
fieldNames.add(“orderId”);
fieldNames.add(“buyerName”);
fieldNames.add(“phoneNumber”);

Query query = new Query(“mycollection”).setFieldsForSearch(fieldNames);
//query.findDocuments(…);
```
---------------------------------------------------------------------------------------------

<a name="Query+getQueryInfo"></a>
### .getQueryInfo()
Method for retrieving query conditions info

**Example** 

```Java
Query query = new Query(“mycollection”);
query.equalTo(“_id”, “dsads123sd”);

QueryInfo queryInfo = query.getQueryInfo();
```