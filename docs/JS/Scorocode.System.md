<a name="sc.System"></a>

Contents

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

Scorocode.System. Designer 

```js
var sys = new sc.System();
```

!!! Note "Note"
    To use system methods you need to initialize the SDK and indicate a MasterKey.

------------------------------------------------------------------------

<a name="sc.System+getDataStats"></a>

## .getDataStats(callbacks)

Method to get the application stats.

| Parameter | Type | 	Properties	| Description |	Variable Example |
| --- | --- | --- | --- | --- |
| callbacks | <code>Object</code> | optional | success and error callbacks for the executed query | see example below |

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

**Returns**: `promise.{dataSize: int, filesSize: int, indexSize: int, store: int}` - Returns a promise, which returns an object with the application statistics:

* dataSize - application data size;
* fileSize - application files data size;
* indexSixe - application indexes data size;
* store - free data available for the application.

------------------------------------------------------------------------

<a name="sc.System+getApp"></a>

## .getApp(callbacks)

Method to get full information about the application.

| Parameter | Type | 	Properties	| Description |	Variable Example |
| --- | --- | --- | --- | --- |
| callbacks | <code>Object</code> | optional | success and error callbacks for the executed query | see example below |

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

**Returns**: `promise.<App>` - Returns a promise, which returns the `App` object.


---------------------------------------------------------------------

<a name="App.getCollections"></a>

## App.getCollections(callbacks)

Method to get a list of collections.

| Parameter | Type | 	Properties	| Description |	Variable Example |
| --- | --- | --- | --- | --- |
| callbacks | <code>Object</code> | optional | success and error callbacks for the executed query | see example below |

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

**Returns**: `promise.[Collection]` - Returns a promise, which returns an array of `Collection` objects.

---------------------------------------------------------------------
<a name="App.getFolderContent"></a>

## App.getFolderContent(path, callbacks)

Method to get a folder at the specified path.

| Parameter | Type | 	Properties	| Description |	Variable Example |
| --- | --- | --- | --- | --- |
| path | `String` | mandatory | specified folder path | "/" | 
| callbacks | <code>Object</code> | optional | success and error callbacks for the executed query | see example below |

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

**Returns**: `promise.[Script, Folder]` - Returns a promise, which returns an array of `Script` и `Folder` objects.

---------------------------------------------------------------------

<a name="App.getScript"></a>

## App.getScript(id, callbacks}

Method to get a script and its ID.

| Parameter | Type | 	Properties	| Description |	Variable Example |
| --- | --- | --- | --- | --- |
| id | <code>String</code> | mandatory | script ID | "574860d2781267d34f7a2415" | 
| callbacks | <code>Object</code> | optional | success and error callbacks for the executed query | see example below |

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

**Returns**: `promise.Script` - Returns a promise, which returns the `Script` object.

---------------------------------------------------------------------

<a name="App.getBots"></a>

## App.getBots(skip, limit, callbacks)

Method to get a list of bots.

| Parameter | Type | 	Properties	| Description |	Variable Example |
| --- | --- | --- | --- | --- |
| skip      | <code>Number</code> | optional, by-default 0  | Number of skipped objects |1|
| limit     | <code>Number</code> | optional, by-default 50 | Sampling size limit | 5 |
| callbacks | <code>Object</code> | optional | success and error callbacks for the executed query | see example below |

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

**Returns**: `promise.<Bot>` - Returns a promise, which returns the `Bot` object.
