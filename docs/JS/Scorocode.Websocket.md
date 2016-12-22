<a name="Scorocode.WebSocket"></a>

Class for WebSocket connection handling.


An example of implementing a chat application using Scorocode.WebSocket – [Scorochat](https://niksmith.github.io/). The application's source code is published on GitHub in the following repository:[NikSmith/niksmith.github.io](https://github.com/NikSmith/niksmith.github.io)


* [.WebSocket](#Scorocode.WebSocket)
    * [new WebSocket(channame)](#new_Scorocode.WebSocket_new)
    * [.on(event, callback)](#Scorocode.WebSocket+on) 
    * [.send(message)](#Scorocode.WebSocket+send) 

----------------------------------------------------------------------------------------------

<a name="new_Scorocode.WebSocket_new"></a>

## new WebSocket(channame)

WebSocket channel opening.

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| channame | <code>String</code> | Mandatory | Channel name | "chatroom" |

**Example**

```js
var WS = new Scorocode.WebSocket('chatroom');
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.WebSocket+on"></a>

## .on(event, callback)
Method for assigning a callback to one of the events:

* open - Connection established
* close - Connection closed
* error - Error
* message -  Data received


| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| event | <code>String</code> | Mandatory, value from the list   | Event to which a callback is assigned | "open", "message", "error", "close"  |
| callback | <code>Object</code> |  | Callback for an event| |

**Example**  

```js
var Scorocode = require('scorocode');

Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey",
    WebSocketKey: "webSocketKey"
});


var WS = new Scorocode.WebSocket('Helloworld');


WS.on("open", onOpen () {});
WS.on("close", onClose () {});
WS.on("error", onError () {});
WS.on("message", onMessage(data) {
    console.log(data)
    });


var data = "Wello Horld";
WS.send(data);
```
----------------------------------------------------------------------------------------------

<a name="Scorocode.WebSocket+send"></a>

## .send(message)
Method for sending a message to channel


| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| message | <code>String</code> | Mandatory  | Message to be sent to the channel | "Wello Horld" |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey",
    WebSocketKey: "webSocketKey"
});

var WS = new Scorocode.WebSocket('Helloworld');
var data = "Wello Horld";

WS.on('open', function(){
    WS.send(data);
});
```