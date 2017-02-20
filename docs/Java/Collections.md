<a name="Collections"></a>

Класс для работы с коллекциями приложения

**Содержание**

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

Конструктор Collections

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Collections collections = new Collections();
```

!!! Note "Примечание"
    Для использования методов класса Collections необходима инициализация SDK с указанием MasterKey.

------------------------------------------------------------------------

<a name="Collections+getCollectionsList"></a>

## .getCollectionsList(callback)

Метод для получения списка коллекций приложения.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| callback | `CallbackGetCollectionsList` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для получения информации о коллекции по ее имени.

| Параметр | Тип | 	Свойства	| Описание | Пример значения |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Обязательный | Имя запрашиваемой коллекции| “testcollection” |
| callback | `CallbackGetCollection` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для создания новой коллекции.

| Параметр | Тип | 	Свойства	| Описание | Пример значения |
| --- | --- | --- | --- | --- |
| collection | `ScorocodeCollection` | Обязательный | Информация о создаваемой коллекции | см. пример ниже |
| callback | `CallbackCreateCollection` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для обновления параметров коллекции

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| collectionId | `String` | Обязательный | Id обновляемой коллекции |“584fba2c42d52f1ba275fdb”|
| collection | `ScorocodeCollection` | Обязательный | Новая информация о коллекции |см. пример ниже|
| callback | `CallbackUpdateCollection` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для клонирования коллекции

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| collectionId | `String` | Обязательный | Id  клонируемой коллекции |“584fba2c42d52f1ba275fdb”|
| collectionName | `String` | Обязательный |  Имя новой коллекции |см. пример ниже|
| callback | `CallbackCloneCollection` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для создания индекса коллекции

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Обязательный | Имя новой коллекции | "testcoll" |
| index | `Index` | Обязательный |  Информация о создаваемом индексе коллекции | см. пример ниже |
| callback | `CallbackCreateCollectionIndex` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для удаления индекса коллекции.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Обязательный | Имя новой коллекции | "testcoll" |
| indexName | `String` | Обязательный |  Название удаляемого индекса | "testindex" |
| callback | `CallbackDeleteCollectionIndex` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для обновления информации о триггерах коллекции.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Обязательный | Имя коллекции в которой мы обновляем триггеры | "testcoll" |
| triggers | `ScorocodeTriggers` | Обязательный |  Информаци о триггерах для обновления | см. пример ниже |
| callback | `CallbackUpdateCollectionTriggers` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для создания нового поля коллекции.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Обязательный | Имя коллекции в которую мы добавляем поле  | "testcoll" |
| field | `ScorocodeField` | Обязательный |  Информация о добавляемом поле | см. пример ниже |
| callback | `CallbackAddField` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для удаления поля из коллекции.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| collectionName | `String` | Обязательный | Имя коллекции из которой мы удаляем поле  | "testcoll" |
| fieldName | `String` | Обязательный |  Имя удаляемого поля | "testfield" |
| callback | `CallbackDeleteField` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для удаления коллекции и всех её документов

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| collectionId | `String` | Обязательный | Id удаляемрй коллекции  | "584fba2c42d52f1ba275fdb" |
| callback | `CallbackDeleteCollection` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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
