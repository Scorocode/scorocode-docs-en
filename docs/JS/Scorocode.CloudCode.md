<a name="Scorocode.CloudCode"></a>

Class for handling server-side scripts 

**Contents:**

* [.CloudCode](#Scorocode.CloudCode)
    * [new CloudCode(id)](#new_Scorocode.CloudCode_new)
    * [.run(pool, callbacks)](#Scorocode.CloudCode+run) ⇒ <code>promise.{error: Boolean}</code>

----------------------------------------------------------------------------------------------

<a name="new_Scorocode.CloudCode_new"></a>

## new CloudCode(id)

Creates a new subclass of Scorocode.CloudCode() for the given script identifier


**Returns**: <code>[Scorocode.CloudCode](#Scorocode.CloudCode)</code> - Returns new Scorocode.CloudCode instance

| Parameter  | Type | Description |
| --- | --- | --- |
| id | <code>String</code> | Server-side script identifier |
| logger | <code>Object</code> | Logger object for debugging |

----------------------------------------------------------------------------------------------

<a name="Scorocode.CloudCode+run"></a>

## .run(pool, debug, callbacks) 

Server code running method

| Parameter  | Type | Description |
| --- | --- | --- |
| pool | <code>Object</code> | Object with the data that will be passed to the server-side script |
| debug | <code>Boolean</code> | Flag for debug mode  |
| callbacks | <code>Object</code> | Success and error callbacks for the executed query |

**Example**

```js
// Подключим SDK и инициализируем его. 
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey",
    ScriptKey: "scriptKey"
});

var Prompt = require('prompt');
Prompt.start();
Prompt.get(['email', 'password', 'username'], function (err, result) {
    var newUserRegistration = new Scorocode.CloudCode("574860d2781267d34f7a2415");
    var pool = {
        "email":result.email,
        "password":result.password,
        "username":result.username
    };
    newUserRegistration.run(pool)
        .then((success)=>{
            console.log(success);
        })
        .catch((error)=>{
            console.log(error)
        });
  });
```

**Returns**: <code>promise.{error: Boolean}</code> - Returns promise that returns object 

```js
{
    error: false
}
```

**Exceptions**:

- <code>String</code> 'Invalid type of pool'

----------------------------------------------------------------------------------------------

## Debug

When you use JavaScript SDK it can be possible to debug server-side scripts. To access debug mode you need to initialise sdk <code>Scorocode.Init({})</code> with MasterKey and WebsocketKey. 

You need to create <code>Logger</code> object to activate debug mode.

**Example**

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey",
    ScriptKey: "scriptKey"
    MasterKey: "masterKey" // necessary for debug
    WebSocketKey: "websocketKey" // necessary for debug
});

var Prompt = require('prompt');
Prompt.start();
Prompt.get(['email', 'password', 'username'], function (err, result) {

// Создадим новый экземпляр запроса к серверному скрипту "574860d2781267d34f7a2415".
// Вторым параметром передаем вновь созданный объект Logger
var newUserRegistration = new Scorocode.CloudCode("574860d2781267d34f7a2415", {logger: new Scorocode.Logger()});

// Определим данные, которые будут переданы скрипту при запуске
var pool = {
    "email":result.email,
    "password":result.password,
    "username":result.username
};

// Запустим выполнение серверного кода
// Вторым параметром передаем true - включаем режим отладки
// Теперь если в скрипте написать console.log("Hello, Scorocode!"), это выведется в вашу консоль
newUserRegistration.run(pool, true)
    .then((success)=>{
        console.log(success);
    })
    .catch((error)=>{
        console.log(error)
    });
});
```
