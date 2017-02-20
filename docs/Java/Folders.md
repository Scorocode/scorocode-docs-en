<a name="Folders"></a>

Класс для работы с папками приложения.

**Содержание**

* [Folders](#Folders)
    * [new Folders()](#Folders_new)
    * [.getFoldersList(pathToFolder, callback)](#Folders+getFoldersList)
    * [.createFolder(pathToFolder, callback)](#Folders+createFolder)
    * [.deleteFolder(pathToFolder, callback)](#Folders+deleteFolder)

------------------------------------------------------------------------

<a name="Folders_new"></a>

## new Folders()

Конструктор Folders

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Folders folders = new Folders();
```

!!! Note "Примечание"
    Для использования методов класса Folders необходима инициализация SDK с указанием MasterKey.

------------------------------------------------------------------------

<a name="Folders+getFoldersList"></a>

## .getFoldersList(pathToFolder, callback)

Метод для получения списка папок по указанному пути.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| pathToFolder | `String` | Обязательный | Путь к папке | "server_scripts" | 
| callback | `CallbackGetFoldersList` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Folders folders = new Folders();
folders.getFoldersList("server_code", new CallbackGetFoldersList() {
    @Override
    public void onRequestSucceed(List<ScorocodeFolder> folderList) {
        //sdk returned list of folders
    }

    @Override
    public void onRequestFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="Folders+createFolder"></a>

## .createFolder(pathToFolder, callback)

Метод для создания новой папки по указанному пути

| Параметр | Тип |  Свойства    | Описание |    Пример значения |
| --- | --- | --- | --- | --- |
| pathToFolder | `String` | Обязательный | Путь к папке | "server_scripts" | 
| callback | `CallbackCreateNewFolder` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Folders folders = new Folders();
folders.createFolder("test_path", new CallbackCreateNewFolder() {
    @Override
    public void onFolderCreated() {
        //folder created
    }

    @Override
    public void onCreationFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="Folders+deleteFolder"></a>

## .deleteFolder(pathToFolder, callback)

Метод для создания новой папки по указанному пути

| Параметр | Тип |  Свойства    | Описание |    Пример значения |
| --- | --- | --- | --- | --- |
| pathToFolder | `String` | Обязательный | Путь к папке | "server_scripts" | 
| callback | `CallbackDeleteFolder` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Folders folders = new Folders();
folders.deleteFolder("server_code", new CallbackDeleteFolder() {
    @Override
    public void onFolderDeleted() {
        //folder deleted
    }

    @Override
    public void onDeletionFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```