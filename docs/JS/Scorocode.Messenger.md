<a name="Scorocode.Messenger"></a>

* [Messenger](#Scorocode.Messenger)
    * [new Messenger()](#new_Scorocode.Messenger_new)
    * [.sendPush(options, callbacks)](#Scorocode.Messenger+sendPush) ⇒ <code>{error: Boolean, count: Number}</code>
    * [.sendSms(options, callbacks)](#Scorocode.Messenger+sendSms) ⇒ <code>{error: Boolean, count: Number}</code>

----------------------------------------------------------------------------------------------

<a name="new_Scorocode.Messenger_new"></a>

## new Messenger()

Class for message sending

**Example**
```js
var broadcast = new Scorocode.Messenger();
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.Messenger+sendPush"></a>

## .sendPush(options, callbacks)

Method to send Push notifications


| Parameter | Type | Properties |
| --- | --- | --- |
| options | <code>Object</code> | Message parameters |
| callbacks | <code>Object</code> | Success and error callbacks for the executed query. |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey",
    MessageKey: "messageKey"
});

var devices = new Scorocode.Query("devices");
var broadcast = new Scorocode.Messenger();
Broadcast.sendPush({
        where: devices,
        data: {
            "data": {
                "message": "PUSH text!",
                }           
            }
        })
        .then((success)=>{
            console.log(success);
        })
        .catch((error)=>{
            console.log(error)
        });
```

**Returns**: <code>promise.{error: Boolean, count: Number}</code> - Returns a promise, which returns the object containing the result of the query execution.

- "error" - <code>Boolean</code> - Error flag
- "count" - <code>Number</code>  - Number of messages sent

**Exception**:

- <code>String</code> 'Invalid options type'
- <code>String</code> 'Where must be a type of Query'
- <code>String</code> 'Invalid data type'
- <code>String</code> 'Missing subject or text message'


----------------------------------------------------------------------------------------------

<a name="Scorocode.Messenger+sendSms"></a>

## .sendSms(options, callbacks)

Method to send SMS

| Parameter | Type | Properties |
| --- | --- | --- |
| options | <code>Object</code> | Message parameters |
| callbacks | <code>Object</code> | Success and error callbacks for the executed query. |

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey",
    MessageKey: "messageKey"
});

var findUsers = new Scorocode.Query("users");
var broadcast = new Scorocode.Messenger();
broadcast.sendPush({
        where: findUsers,
        data: {
            "text": "SMS text"     
            }
        })
        .then((success)=>{
            console.log(success);
        })
        .catch((error)=>{
            console.log(error)
        });
```

**Returns**: <code>{error: Boolean, count: Number}</code> - Returns a promise, which returns the object containing the result of the query execution.

- "error" - <code>Boolean</code> - Error flag
- "count" - <code>Number</code>  - Number of messages sent
