<a name="sc.Bot"></a>

Содержание

* [.Bot](#sc.Bot)
    * [new Bot(botId)](#new_sc.Bot)
    * [.send(data)](#sc.Bot+send) 

----------------------------------------------------------------------------------------------

<a name="new_sc.Bot"></a>

## new Bot(botId)

Конструктор sc.Bot

**Возвращает**: <code>[sc.Bot](#sc.Bot)</code> - Возвращает новый экземпляр sc.Bot

| Параметр | Тип | Описание |
| --- | --- | --- |пше ыефегы
| botId | <code>String</code> | Telegram id бота, полученный от `@BotFather` |

**Пример**
```js
var sc = require('scorocode');

sc.Init({
    ApplicationID: "xxx", // <- заменить xxx на ключ appId приложения
    JavaScriptKey: "xxx", // <- заменить xxx на ключ javascript приложения
    MasterKey: "xxx" // <- заменить xxx на ключ masterKey приложения
});

var bot = new sc.Bot("321196098:AAEDbOYD6iLWsHD7w28vqf3a9oBeJAPXXpg");

var data = {
    "method": "methodname", //название метода Telegram bot API 
    "method_params": {
        // параметры метода Telegram Bot API
    }};
bot.send(data)
```
--------------------------------------------------------------------------

<a name="sc.Bot+send"></a>

## .send(pool, callbacks) 

Метод для запуска серверного кода

| Параметр | Тип | Описание |
| --- | --- | --- |
| data | <code>Object</code> | Объект, содержащий данные для передачи Telegram Bot API |

Свойства параметра `data`

| Имя | Тип | Описание |
| --- | --- | --- |
| method | <code>String</code> | Название метода Telegram bot API  |
| method_params | <code>Object</code> | Объект с параметрами для указанного метода |

**Пример**

```js
var sc = require('scorocode');

sc.Init({
    ApplicationID: "xxx", // <- заменить xxx на ключ appId приложения
    JavaScriptKey: "xxx", // <- заменить xxx на ключ javascript приложения
    MasterKey: "xxx" // <- заменить xxx на ключ masterKey приложения
});

var bot = new sc.Bot("321196098:AAEDbOYD6iLWsHD7w28vqf3a9oBeJAPXXpg");

var data = {
    "method": "methodname", //название метода Telegram bot API 
    "method_params": {
        // параметры метода Telegram Bot API
    }};

bot.send(data);
```