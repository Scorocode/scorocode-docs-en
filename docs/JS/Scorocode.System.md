<a name="sc.System"></a>

Содержание

* [.System](#sc.System)
    * [new System()](#new_sc.System)
    * [.getDataStats(callbacks)](#sc.System+getDataStats) 
    * [.getApp(callbacks)](#sc.System+getApp) 
    * [App.getCollections(callbacks)](#App.getCollections)
    * [App.getFolderContent(path, callbacks)](#App.getFolderContent)
    * [App.getScript(id, callbacks}](#App.getScript)
    * [App.getBots(skip, limit, callbacks)](#App.getBots)

--------------------------------------------------------------------------------

<a name="new_sc.System"></a>

## new System()

Конструктор Scorocode.System.

```js
var sys = new sc.System();
```

!!! Note "Примечание"
    Для использования системных методов необходима инициализация SDK с указанием MasterKey.

------------------------------------------------------------------------

<a name="sc.System+getDataStats"></a>

## .getDataStats(callbacks)

Метод для получения статистики приложения.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| callbacks | <code>Object</code> | необязательный | Коллбэки success и error для выполняемого запроса. | см. пример ниже |

```js
var sc = require('scorocode');

sc.Init({
    ApplicationID: "5c46ec2f6f94aa92sdfef83122ff1gc",
    JavaScriptKey: "86df1sd52d81dbhskn32f1d6a8e15936",
    MasterKey: "e9c6vf5b9d6acd5tyu3aav1405c1e6dc3"
});

var sys = new sc.System();

sys.getDataStats()
   .then((stats)=>{
   		console.log(stats);
    })
    .catch((error)=>{
        console.log(error)
    });
```

**Возвращает**: `promise.{dataSize: int, filesSize: int, indexSize: int, store: int}` - Возвращает promise, который возвращает объект со статистикой приложения:

* dataSize - объем данных приложения;
* fileSize - объем данных, занятый файлами приложения;
* indexSixe - объем данных, занятый индексами приложения;
* store - объем данных, доступных приложению.

------------------------------------------------------------------------

<a name="sc.System+getApp"></a>

## .getApp(callbacks)

Метод для получения полной информации о приложении.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| callbacks | <code>Object</code> | необязательный | Коллбэки success и error для выполняемого запроса. | см. пример ниже |

```js
var sc = require('scorocode');

sc.Init({
    ApplicationID: "5c46ec2f6f94aa92sdfef83122ff1gc",
    JavaScriptKey: "86df1sd52d81dbhskn32f1d6a8e15936",
    MasterKey: "e9c6vf5b9d6acd5tyu3aav1405c1e6dc3"
});

var sys = new sc.System();

sys.getApp()
   .then((app)=>{
   		console.log(app);
    })
    .catch((error)=>{
        console.log(error)
    });
```

**Возвращает**: `promise.<App>` - Возвращает promise, который возвращает объект `App`.


---------------------------------------------------------------------

<a name="App.getCollections"></a>

## App.getCollections(callbacks)

Метод для получения списка коллекций приложения.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| callbacks | <code>Object</code> | необязательный | Коллбэки success и error для выполняемого запроса. | см. пример ниже |

```js
var sc = require('scorocode');

sc.Init({
    ApplicationID: "5c46ec2f6f94aa92sdfef83122ff1gc",
    JavaScriptKey: "86df1sd52d81dbhskn32f1d6a8e15936",
    MasterKey: "e9c6vf5b9d6acd5tyu3aav1405c1e6dc3"
});

var system = new sc.System();
system.getApp()
  .then((app)=>{
   		app.getCollections()
     	  	.then((result) => {
     		   	console.log(result);
          })
  })
  .catch((error)=>{
      console.log(error)
  });
```

**Возвращает**: `promise.[Collection]` - Возвращает promise, который возвращает массив объектов `Collection`.

---------------------------------------------------------------------
<a name="App.getFolderContent"></a>

## App.getFolderContent(path, callbacks)

Метод для получения папки по указанному пути.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| path | `String` | Обязательный | Путь к папке | "/" | 
| callbacks | <code>Object</code> | необязательный | Коллбэки success и error для выполняемого запроса. | см. пример ниже |

```js
var sc = require('scorocode');

sc.Init({
    ApplicationID: "5c46ec2f6f94aa92sdfef83122ff1gc",
    JavaScriptKey: "86df1sd52d81dbhskn32f1d6a8e15936",
    MasterKey: "e9c6vf5b9d6acd5tyu3aav1405c1e6dc3"
});

var system = new sc.System();
system.getApp()
  .then((app)=>{
   		app.getFolderContent("/")
     	  	.then((result) => {
     		   	console.log(result);
          })
  })
  .catch((error)=>{
      console.log(error)
  });
```

**Возвращает**: `promise.[Script, Folder]` - Возвращает promise, который возвращает массив объектов `Script` и `Folder`

---------------------------------------------------------------------

<a name="App.getScript"></a>

## App.getScript(id, callbacks}

Метод для получения скрипта по его id.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| id | <code>String</code> | Обязательный | Идентификатор скрипта | "574860d2781267d34f7a2415" | 
| callbacks | <code>Object</code> | необязательный | Коллбэки success и error для выполняемого запроса. | см. пример ниже |

```js
var sc = require('scorocode');

sc.Init({
    ApplicationID: "5c46ec2f6f94aa92sdfef83122ff1gc",
    JavaScriptKey: "86df1sd52d81dbhskn32f1d6a8e15936",
    MasterKey: "e9c6vf5b9d6acd5tyu3aav1405c1e6dc3"
});

var system = new sc.System();
system.getApp()
  .then((app)=>{
   		app.getScript("57c941e50293e02aea8b5b14")
     	  	.then((result) => {
     		   	console.log(result);
          })
  })
  .catch((error)=>{
      console.log(error)
  });
```

**Возвращает**: `promise.Script` - Возвращает promise, который возвращает объект `Script`

---------------------------------------------------------------------

<a name="App.getBots"></a>

## App.getBots(skip, limit, callbacks)

Метод для получения списка ботов.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| skip      | <code>Number</code> | необязательный, по-умолчанию 0  | Количество пропускаемых объектов |1|
| limit     | <code>Number</code> | необязательный, по-умолчанию 50 | Лимит выборки | 5 |
| callbacks | <code>Object</code> | необязательный | Коллбэки success и error для выполняемого запроса. | см. пример ниже |

```js
var sc = require('scorocode');

sc.Init({
    ApplicationID: "5c46ec2f6f94aa92sdfef83122ff1gc",
    JavaScriptKey: "86df1sd52d81dbhskn32f1d6a8e15936",
    MasterKey: "e9c6vf5b9d6acd5tyu3aav1405c1e6dc3"
});

var system = new sc.System();
system.getApp()
  .then((app)=>{
   		app.getBots()
     	  	.then((result) => {
     		   	console.log(result);
          })
  })
  .catch((error)=>{
      console.log(error)
  });
```

**Возвращает**: `promise.<Bot>` - Возвращает promise, который возвращает массив объектов `Bot`
