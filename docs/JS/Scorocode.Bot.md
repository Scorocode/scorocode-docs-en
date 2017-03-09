<a name="sc.Bot"></a>


* [.Bot](#sc.Bot)
    * [new Bot(botId)](#new_sc.Bot)
    * [.send(data)](#sc.Bot+send) 

----------------------------------------------------------------------------------------------

<a name="new_sc.Bot"></a>

## new Bot(botId)

Constructor sc.Bot

**Returns**: <code>[sc.Bot](#sc.Bot)</code> - returns the `sc.Bot`

| Parameter | Type | Description |
| --- | --- | --- |
| botId | <code>String</code> | Telegram Bot identifier `@BotFather` |

**Example**

```js
var sc = require('scorocode');

sc.Init({
    ApplicationID: "xxx", // <- replace xxx with ApplicationID  key
    JavaScriptKey: "xxx", // <- replace xxx with JavaScriptKey  key
    MasterKey: "xxx" // <- replace xxx with MasterKey
});

var bot = new sc.Bot("321196098:AAEDbOYD6iLWsHD7w28vqf3a9oBeJAPXXpg");

var data = {
    "method": "methodname", // Telegram bot API method name 
    "method_params": {
        // Telegram Bot API method params
    }};
bot.send(data)
```

--------------------------------------------------------------------------

<a name="sc.Bot+send"></a>

## .send(data) 

Making request to Telegram Bot API

| Parameter | Type | Description |
| --- | --- | --- |
| data | <code>Object</code> | Object, containing data to request Telegram Bot API |

`data` object properties.

| Name | Type | Description |
| --- | --- | --- |
| method | <code>String</code> |  Telegram bot API method name   |
| method_params | <code>Object</code> |  Telegram Bot API method params |

**Example**

```js
var sc = require('scorocode');

sc.Init({
    ApplicationID: "xxx", // <- replace xxx with ApplicationID  key
    JavaScriptKey: "xxx", // <- replace xxx with JavaScriptKey  key
    MasterKey: "xxx" // <- replace xxx with MasterKey
});

var bot = new sc.Bot("321196098:AAEDbOYD6iLWsHD7w28vqf3a9oBeJAPXXpg");

var data = {
    "method": "methodname", // Telegram bot API method name 
    "method_params": {
        // Telegram Bot API method params
    }};

bot.send(data);
```