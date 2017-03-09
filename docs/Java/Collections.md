<a name="Collections"></a>

* [Collections](#Collections)
    * [new Collections()](#Collections_new)
    * [.getCollectionsList(callback)](#Collections+getCollectionsList)
    * [.getCollectionByName(collectionName, callback)](#Collections+getCollectionByName)
    * [.createCollection(collection, callback)](#Collections+createCollection)
    * [.updateCollcetion(collectionId, collection, callback)](#Collections+updateCollcetion)
    * [.cloneCollection(collectionId, collectionName, callback)](#Collections+cloneCollection)
    * [.createCollectionIndex(collectionName, index, callback)](#Collections+createCollectionIndex)
    * [.deleteCollectionIndex(collectionName, indexName, callback)](#Collections+deleteCollectionIndex)
    * [.updateCollectionTriggers(collectionName, triggers, callback)](#Collections+updateCollectionTriggers)
    * [.createCollectionField(collectionName, field, callback)](#Collections+createCollectionField)
    * [.deleteCollectionField(collectionName, fieldName, callback)](#Collections+deleteCollectionField)
    * [.deleteCollection(collectionId, callback)](#Collections+deleteCollection)

------------------------------------------------------------------------

<a name="Collections_new"></a>

## new Collections()

Constructor Collections

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Collections collections = new Collections();
```

!!! Note "MasterKey"
    You should initialise SDK with MasterKey to use ApplicationInfo methods.


------------------------------------------------------------------------

<a name="Collections+getCollectionsList"></a>

## .getCollectionsList(callback)

Method for retrieving an application collections list.

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| callback | `CallbackGetCollectionsList` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Collections collections = new Collections();
collections.getCollectionsList(new CallbackGetCollectionsList() {
    @Override
    public void onRequestSucceed(List<ScorocodeCollection> collections) {
        //sdk returned collections list
    }

    @Override
    public void onRequestFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------


<a name="Collections+getCollectionByName"></a>

## .getCollectionByName(collectionName, callback)

Method for retrieving a collection info by it's name.

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Mandatory | Collection name | “testcollection” |
| callback | `CallbackGetCollection` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Collections collections = new Collections();
collections.getCollectionByName("testCollection", new CallbackGetCollection() {
    @Override
    public void onRequestSucceed(ScorocodeCollection collection) {
        //sdk returned the collection
    }

    @Override
    public void onRequestFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------


<a name="Collections+createCollection"></a>

## .createCollection(collection, callback)

Method for creating new collection

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| collection | `ScorocodeCollection` | Mandatory | Class that contains new collection info | See the example below |
| callback | `CallbackCreateCollection` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

ScorocodeCollection newCollection = new ScorocodeCollection()
        .setCollectionName(“testcollection”)
        .setUseDocsACL(false)
        .setACL(getTestACL());

Collections collections = new Collections();
collections.createCollection(newCollection, new CallbackCreateCollection() {
    @Override
    public void onCollectionCreated(ScorocodeCollection collection) {
        //collection created
    }

    @Override
    public void onCreationFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------


<a name="Collections+updateCollcetion"></a>

## .updateCollcetion(collectionId, collection, callback)

Method fot Updating the existing collection


| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| collectionId | `String` | Mandatory | Collection identifier |“584fba2c42d52f1ba275fdb”|
| collection | `ScorocodeCollection` | Mandatory | Class that contains collection info | See the example below |
| callback | `CallbackUpdateCollection` | Mandatory | Сallback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Collections collections = new Collections();

ScorocodeCollection collection = new ScorocodeCollection()
        .setCollectionName("updatedcollection”))
        .setUseDocsACL(false)
        .setACL(getTestACL());

collections.updateCollection(“ahfdsjlsdlffdsdsa”, collection, new CallbackUpdateCollection() {
    @Override
    public void onCollectionUpdated(ScorocodeCollection collection) {
        //collection updated
    }

    @Override
    public void onUpdateFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="Collections+cloneCollection"></a>

## .cloneCollection(collectionId, collectionName, callback)

Method for collection clone creation.

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| collectionId | `String` | Mandatory |  Collection identifier | “584fba2c42d52f1ba275fdb”|
| collectionName | `String` | Mandatory | New collection name | See the example below |
| callback | `CallbackCloneCollection` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Collections collections = new Collections();
collections.cloneCollection(“asdhjkasdjska”, "clonedtestcollection”), new CallbackCloneCollection() {
    @Override
    public void onCollectionCloned(ScorocodeCollection collection) {
        //collection cloned
    }

    @Override
    public void onCloneOperationFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="Collections+createCollectionIndex"></a>

## .createCollectionIndex(collectionName, index, callback)

Method for collection index creation

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Mandatory | Collection name | "testcoll" |
| index | `Index` | Mandatory |  Class that contains index information | See the example below |
| callback | `CallbackCreateCollectionIndex` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

List<IndexField> indexFields = new ArrayList<>();
indexFields.add(new IndexField("readACL", 1));

Index index = new Index(“newindex”, indexFields);

Collections collections = new Collections();
collections.createCollectionIndex(“testcollection”, index, new CallbackCreateCollectionIndex() {
    @Override
    public void onIndexCreated() {
        //index created
    }

    @Override
    public void onIndexCreationFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="Collections+deleteCollectionIndex"></a>

## .deleteCollectionIndex(collectionName, indexName, callback)

Method for collection index deletion

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Mandatory | Collection name | "testcoll" |
| indexName | `String` | Mandatory |  Index name | "testindex" |
| callback | `CallbackDeleteCollectionIndex` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Collections collections = new Collections();
collections.deleteCollectionIndex(testCollection.getCollectionName(), INDEX_NAME, new CallbackDeleteCollectionIndex() {
    @Override
    public void onIndexDeleted() {
        //index deleted
    }

    @Override
    public void onIndexDeletionFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="Collections+updateCollectionTriggers"></a>

## .updateCollectionTriggers(collectionName, triggers, callback)

Method for updating collection triggers

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Mandatory | Collection name | "testcoll" |
| collection | `ScorocodeCollection` | Mandatory | Class that contains Trigger info | See the example below |
| callback | `CallbackUpdateCollectionTriggers` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

boolean isActive = false;
ScorocodeTriggers triggers = new ScorocodeTriggers();
triggers.setBeforeInsert(new Trigger("BFI code", isActive));
triggers.setAfterInsert(new Trigger("AFI code", isActive));
triggers.setBeforeRemove(new Trigger("BFR code", isActive));
triggers.setAfterRemove(new Trigger("AFR code", isActive));
triggers.setBeforeUpdate(new Trigger("BFU code", isActive));
triggers.setAfterUpdate(new Trigger("AFU code", isActive));

Collections collections = new Collections();
collections.updateCollectionTriggers(“testcollection”, triggers, new CallbackUpdateCollectionTriggers() {
    @Override
    public void onTriggersUpdated(ScorocodeTriggers triggers) {
        //trigger updated
    }

    @Override
    public void onUpdateFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="Collections+createCollectionField"></a>

## .createCollectionField(callback)

Method for creating collection field

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Mandatory | Collection name | "testcoll" |
| field | `ScorocodeField` | Mandatory | Class that contains field's info | See the example below |
| callback | `CallbackAddField` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

ScorocodeField field = new ScorocodeField("testnumberfield", ScorocodeTypes.TypeNumber, "", false, false, false);

Collections collections = new Collections();
collections.createCollectionField(“testcollection”, field, new CallbackAddField() {
    @Override
    public void onFieldAdded(ScorocodeField field) {
        //field created
    }

    @Override
    public void onAddFieldFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```


------------------------------------------------------------------------

<a name="Collections+deleteCollectionField"></a>

## .deleteCollectionField(collectionName, fieldName, callback)

Method for deleteing collection field

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Mandatory | Collection idenifier | "Testcoll" |
| fieldName | `String` | Mandatory |  Field name | "testfield" |
| callback | `CallbackDeleteField` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Collections collections = new Collections();
collections.deleteCollectionField(“testcoll”, "testnumberfield", new CallbackDeleteField() {
    @Override
    public void onFieldDeleted(ScorocodeCollection collection) {
        //field deleted
    }

    @Override
    public void onDeletionFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="Collections+deleteCollection"></a>

## .deleteCollection(collectionId, callback)

Method for deleteing collection and all it's documents

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| collectionId | `String` | Mandatory | Collection idenifier | "584fba2c42d52f1ba275fdb" |
| callback | `CallbackDeleteCollection` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Collections collections = new Collections();
collections.deleteCollection(“sdfjksdlf2312fdsj”, new CallbackDeleteCollection() {
    @Override
    public void onCollectionDeleted() {
        //collection deleted
    }

    @Override
    public void onDeletionFailed(String errorCodes, String errorMessage) {
        //error during request
    }
});
```
