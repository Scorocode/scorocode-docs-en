<a name="Bot"></a>

* [Bot](#Bot)
    * [new Bot()](#Bot_new)
    * [.getBotsList(callback)](#Bot+getBotsList)
    * [.createBot(botInfo, callback)](#Bot+createBot)
    * [.updateBot(botId, newBotInfo, callback)](#Bot+updateBot)
    * [.deleteBot(botId, callback)](#Bot+deleteBot)


------------------------------------------------------------------------

<a name="Bot_new"></a>

## new Bot()

Constructor Bot

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Bot bot = new Bot();
```

!!! Note "MasterKey"
    You should initialise SDK with MasterKey to use Bot methods.

------------------------------------------------------------------------

<a name="Bot+getBotsList"></a>

## .getBotsList(callback)

Retrieve application bots list.

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| callback | `CallbackGetBotList` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Bot bot = new Bot();
bot.getBotsList(new CallbackGetBotList() {
    @Override
    public void onRequestSucceed(List<ScorocodeBot> botList) {
        //sdk returned bot list
    }

    @Override
    public void onRequestFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------


<a name="Bot+createBot"></a>

## .createBot(botInfo, callback)

Method for create a new bot.

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| botInfo | `ScorocodeBot` | Mandatory | Class that contains bot information | See the example below |
| callback | `CallbackCreateBot` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

String botName = "scorocodeSdkTestBotName";
String telegramBotId = "scorocodeSdkTestTelegramBotId";
String scriptId = “584fba2c42d52f1ba275fdb5”;

ScorocodeBot botInfo = new ScorocodeBot(botName, telegramBotId, scriptId, false);
Bot bot = new Bot();
bot.createBot(botInfo, new CallbackCreateBot() {
    @Override
    public void onBotCreated(ScorocodeBot bot) {
          //bot created
    }

    @Override
    public void onCreationFailed(String errorCode, String errorMessage) {
        //error during bot creation        
    }
});
```


------------------------------------------------------------------------
<a name="Bot+updateBot"></a>


## .updateBot(botId, newBotInfo, callback)

Method for updating a bot that already exists

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| botId | `String` | Mandatory | Scorocode bot identifier | See the example below |
| newBotInfo | `ScorocodeBot` | Mandatory | Class that contains bot information| See the example below |
| callback | `CallbackUpdateBot` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

String botId = “584fba2c42d52f1ba275fdb5”;

ScorocodeBot newBotInfo = new ScorocodeBot("updated"+botName, "updated"+ telegramBotId, scriptId, false);

Bot bot = new Bot();
bot.updateBot(botId, newBotInfo, new CallbackUpdateBot() {
    @Override
    public void onBotUpdated(ScorocodeBot bot) {
        //bot updated
    }

    @Override
    public void onUpdateFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="Bot+deleteBot"></a>

## .deleteBot(botId, callback)

Method for deleteing a bot

| Parameter | Type |    Properties  | Description | Example |
| --- | --- | --- | --- | --- |
| botId | `String` | Mandatory | Scorocode bot identifier | See the example below |
| callback | `CallbackDeleteBot` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

String botId = “584fba2c42d52f1ba275fdb5”;

Bot bot = new Bot();
bot.deleteBot(botId, new CallbackDeleteBot() {
    @Override
    public void onBotDeleted() {
        //bot deleted
    }

    @Override
    public void onDeletionFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```
