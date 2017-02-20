<a name="Bot"></a>

Класс для работы с ботами приложениия.

**Содержание**

* [Bot](#Bot)
    * [new Bot()](#Bot_new)
    * [.getBotsList(callback)](#Bot+getBotsList)
    * [.createBot(botInfo, callback)](#Bot+createBot)
    * [.updateBot(botId, newBotInfo, callback)](#Bot+updateBot)
    * [.deleteBot(botId, callback)](#Bot+deleteBot)


------------------------------------------------------------------------

<a name="Bot_new"></a>

## new Bot()

Конструктор Bot

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Bot bot = new Bot();
```

!!! Note "Примечание"
    Для использования методов класса Bot необходима инициализация SDK с указанием MasterKey.

------------------------------------------------------------------------

<a name="Bot+getBotsList"></a>

## .getBotsList(callback)

Метод для получения списка всех ботов приложения.

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| callback | `CallbackGetBotList` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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

Метод для создания нового бота.

| Параметр | Тип |  Свойства    | Описание |    Пример значения |
| --- | --- | --- | --- | --- |
| botInfo | `ScorocodeBot` | Обязательный | Класс, содержащий информацию о создаваемом боте | см. пример ниже |
| callback | `CallbackGetBotList` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**
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

Метод для обновления информации уже существующего бота.

| Параметр | Тип |  Свойства    | Описание |    Пример значения |
| --- | --- | --- | --- | --- |
| botId | `String` | Обязательный | Уникальный Id обновляемого бота  | см. пример ниже |
| newBotInfo | `ScorocodeBot` | Обязательный | Класс, содержащий информацию о создаваемом боте | см. пример ниже |
| callback | `CallbackGetBotList` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**
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

Метод для удаления бота

| Параметр | Тип |  Свойства    | Описание |    Пример значения |
| --- | --- | --- | --- | --- |
| botId | `String` | Обязательный | Уникальный Id обновляемого бота  | см. пример ниже |
| callback | `CallbackGetBotList` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

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
