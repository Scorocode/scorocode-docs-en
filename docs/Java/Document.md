<a name="Document"></a>

* [Document](#Document)
    * [new Document(collection_name)](#new_Scorocode.Document_new)
    * [.setField(field, value)](#Document+setField)
    * [.saveDocument(callback)](#Document+saveDocument)  
    * [.getDocumentById(documentId, callback)](#Document+getDocumentById)
    * [.getField(field)](#Document+getField)
    * [.updateDocument()](#Document+updateDocument)
    * [.uploadFile(fieldName, fileName, contentToUploadInBase64, callback)](#Document+uploadFile)
    * [.getFileLink(fieldName, fileName)](#Document+getFileLink)
    * [.removeFile( fieldName,  fileName,  callback)](#Document+removeFile)
    * [.removeDocument(callback)](#Document+removeDocument)  

----------------------------------------------------------------------------------------------
<a name="new_Scorocode.Document_new"></a>

### new Document(collection_name)

Document initialisation

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| collection_name | `String` | Обязательное | Name of the collection where the document is added  | "Things" |

**Example** 

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null);

Document exampleItem = new Document("Items");
```

----------------------------------------------------------------------------------------------
<a name="Document+setField"></a>

### .setField(field, value)

Method for setting data to document's field

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String` | Mandatory | Field name | "testcoll" |
| value | `Object` | Mandatory  | Field value | "huNr3L7QDh" |

**Example** 

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null);

final Document order = new Document(“orders”);
order.setField(“orderId”, “Ku128A439ads”);
```

----------------------------------------------------------------------------------------------
<a name="Document+saveDocument"></a>
### .saveDocument(callback)

The method saves the document in the database or updates an object that already exists there

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| callback | `CallbackDocumentSaved` | Mandatory | Callback for the request being executed. |   | 

**Example** 
 
Creating new document 

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null);


Document newDocument = new Document(“orderInfo”);
newDocument.setField("isOrderSend", false);
newDocument.setField("buyerName", “Any username”);


newDocument.saveDocument(new CallbackDocumentSaved() {
            @Override
            public void onDocumentSaved() {
                //document saved successful (New document uploaded on server).
            }


            @Override
            public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                //document save failed.
            }
        });
```

Updating the existing document

```Java
 final Document document = new Document(“orderInfo”);
 document.getDocumentById("KH3JCojAyT", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
            //we found document and we can make changes in it and save it
            //...change document fields...
            //save  
                document.saveDocument(new CallbackDocumentSaved() {
                    @Override
                    public void onDocumentSaved() {
                        //document save succeed. Document updated on server
                    }

                    @Override
                    public void onDocumentSaveFailed(String errorCode, String errorMessage) {
                        //document save failed.
                    }
                });
            }

            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
            //document not found. If we try to save document here
            //new document will be upload to server as in example 2.1
            }
        });
```

----------------------------------------------------------------------------------------------
<a name="Document+getDocumentById"></a>
### .getDocumentById(documentId, callback)

Method for retrieving a collection object from DB by its _id.

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| documentId | `String` | Mandatory | Object identifier                                    | "nV0p50CDKq" | 
| callback | `CallbackGetDocumentById` | Mandatory | Callback for the request being executed. |              | 

**Example** 

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null);

final Document document = new Document("ordersCollection");
document.getDocumentById("nV0p50CDKq", new CallbackGetDocumentById() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //document found
            }


            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found or error occured
            }
        });
```

----------------------------------------------------------------------------------------------
<a name="Document+getField"></a>
### .getField(field)

Method for retrieving data from a specified document field.

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| field | `String`   | Mandatory | Field name     | "name"    | 

**Example** 

```Java
final Document document = new Document(“ordersCollection”);
String orderId = document.getField(“orderId”);
```
----------------------------------------------------------------------------------------------
<a name="Document+updateDocument"></a>
### .updateDocument()

Method for updating the document using Update class.

----------------------------------------------------------------------------------------------
<a name="Document+uploadFile"></a>
### .uploadFile(fieldName, fileName, contentToUploadInBase64, callback)

File upload method

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| fieldName| `String`   | Mandatory | Field name                               | "attachment"    | 
| fileName | `String`   | Mandatory | Filename with extension                     | "file.txt"    | 
| contentToUploadInBase64 | `String`| Mandatory | File content in base64 encoded format   | "VEhJUyBJUyBGSUxFLUUtRS1FLUUtRS1FIQ=="    | 
| callback | `CallbackUploadFile` | Mandatory | Callback for the request being executed.  |                 | 

**Example** 

```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("nV0p50CDKq", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
            //document found and we can upload document in this file

                document.uploadFile("file_field", "any_filename.txt", 
            Base64.encodeToString("hello world".getBytes(), Base64.DEFAULT), new CallbackUploadFile() {

              @Override
                    public void onDocumentUploaded() {
                        //document upload succeed
                    }


                    @Override
                    public void onDocumentUploadFailed(String errorCode, String errorMessage) {
                        //document upload failed
                    }
                });
            }


            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```

----------------------------------------------------------------------------------------------
<a name="Document+getFileLink"></a>
### .getFileLink(fieldName, fileName)

Method for retreiving file link

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| fieldName| `String`     | Mandatory | Field name         | "attachment"    | 
| fileName | `String`   | Mandatory | Filename with extension| "file.txt"    | 

**Example** 

```Java
final Document documentWithFile = new Document(“ordersCollection”);
documentWithFile.getDocumentById("nV0p50CDKq", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                    //document found. We can try to get link on file in this document
            String fileLink = documentWithFile.getFileLink("test", "file.txt");
            }


            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```

----------------------------------------------------------------------------------------------
<a name="Document+removeFile"></a>
### .removeFile(fieldName, fileName, callback)

Method for removing the file

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| fieldName| `String`     | Mandatory | Collection field name | "attachment"    | 
| fileName | `String`   | Mandatory | Filename with extension | "file.txt"      | 
| callback | `CallbackDeleteFile` | Mandatory | Callback for the request being executed. |  | 

**Example** 

```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("nV0p50CDKq", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
            //document found we can try to delete file from this doc


                document.removeFile("file", "anyname", new CallbackDeleteFile() {
                    @Override
                    public void onDocumentDeleted() {
                        //file deletion succeed
                    }


                    @Override
                    public void onDetelionFailed(String errorCodes, String errorMessage) {
                        //file deletion failed
                    }
                });
            }


            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document not found
            }
        });
```

----------------------------------------------------------------------------------------------
<a name="Document+removeDocument"></a>
### .removeDocument(callback)

Method for removing the selected document

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| callback | `CallbackRemoveDocument` | Mandatory | Callback for the request being executed. |                 | 

**Example** 

```Java
final Document document = new Document(“ordersCollection”);
document.getDocumentById("7BOlVr1Acp", new CallbackFindDocument() {
            @Override
            public void onDocumentFound(DocumentInfo documentInfo) {
                //we found document in collection and can remove it
                document.removeDocument(new CallbackRemoveDocument() {
                    @Override
                    public void onRemoveSucceed(ResponseRemove responseRemove) {
                        //document removed
                    }


                    @Override
                    public void onRemoveFailed(String errorCode, String errorMessage) {
                        //remove operation failed
                    }
                });
            }


            @Override
            public void onDocumentNotFound(String errorCode, String errorMessage) {
                //document wasn’t found
            }
        });
```
