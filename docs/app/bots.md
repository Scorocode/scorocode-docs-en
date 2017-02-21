## Создание бота Telegram

Прежде чем начинать разработку, в качестве первого шага, бота необходимо зарегистрировать в Telegram и получить его уникальный id. Для этого в Telegram существует специальный бот — `@BotFather`. Отправьте ему команду `/newbot` — и бот просит придумать имя новому боту. Единственное ограничение на имя — в конце оно должно оканчиваться на «bot». В случае успеха `@BotFather` возвращает id бота.

Затем, в вашем приложении на Scorocode необходимо создать серверный скрипт, который будет привязан к боту и в котором будет происходить обработка событий.

Третьим шагом, необходимо создать бота в приложении. Для этого предейтите в раздел "Боты" и нажмите на кнопку "Создать бота". В открывшейся форме создания бота задайте слeдующие данные:

| Параметр      | Свойства | Описание |
| ------------- | -------- | -------- |
| Bot name | Mandatory | Application bot name |
| Bot identifier | Mandatory | Bot's Telegram id , given by '@BotFather' |
| Script identifier | Mandatory | Choose script from the list of application server-side scripts |
| Bot activation flag | Optional, `false` by default | Set the flag to activate your bot |

Для сохранения бота, нажмите кнопку "сохранить" и ваш бот появится в списке ботов приложения. Вы в любой момент можете отредактировать любые настройки бота, заданные при его создании, нажав на кнопку редактирования бота.  

![Редактирование бота](../img/botedit.png)

## Принципы работы

При включении бота создается `webhook` на который приходят данные от `Telegram`. Эти данные доступны в серверном скрипте в объекте `pool` при каждом вызове. Полное описание полей доступно в [документации к Telegram Bot API](https://core.telegram.org/bots/api#getting-updates)

Ответные сообщения от бота передаются при помощи метода .send(data) класса sc.Bot, где data - объект, имеющий следующую структуру:

```JSON
{
    'method': 'sendMessage',                            // Telegram Bot API method
    'method_params': {                                  // method params to be passed
      'chat_id': pool.message.chat.id.toString(),
      'text': 'Hello!',
      'reply_to_message_id': pool.message.message_id,
      'reply_markup': keyBoard
    },
  }
```

See [Telegram Bot API documentation](https://core.telegram.org/bots/api#available-methods) for a complete list of available methods and their parameters.

!!! Note "Supported methods"
    All `Telegram Bot API` v 2.3.1 methods are supported, except `Telegram Bot Games API` methods.

## Bot server-side script example:

```js
var sc = require('scorocode');

var client = sc.Init({
  ApplicationID: "xxx", // <- replace xxx with your appId key
  JavaScriptKey: "xxx", // <- replace xxx with your JavaScript key
  MasterKey: "xxx"      // <- replace xxx with your MasterKey key
});

var bot = new sc.Bot("321196098:AAEDbOYD6iLWsHD7w28vqf3a9oBeJAPXXpg");
var querystring = require('querystring');

// Crate new button for ReplyKeyboardMarkup
function newKeyboardButton(text, request_contact, request_location) {
  var button = {
    'text': text
  }

  if (request_contact) {
    button.request_contact = request_contact
  }

  if (request_location) {
    button.request_location = request_location
  }

  return button
}

// Main logic

const sourceMessage = pool.message.text.toLowerCase()
var request = null

if (sourceMessage === '/start' || sourceMessage === 'Hi there') {

  var keyBoard = {
    'keyboard': [
      [ newKeyboardButton('Hi there') ],
      [ newKeyboardButton('my phone number', true)],
      [ newKeyboardButton('logo') ]
    ]
  }

  request = {
    'method': 'sendMessage',
    'method_params': {
      'chat_id': pool.message.chat.id.toString(),
      'text': 'Hello!',
      'reply_to_message_id': pool.message.message_id,
      'reply_markup': keyBoard
    },
  }

} else if (sourceMessage === 'logo') {

  request = {
    'method': 'sendPhoto',
    'method_params': {
      'chat_id': pool.message.chat.id.toString(),
      'photo': 'https://habrastorage.org/files/aab/c24/364/aabc24364c3b4e109c20ae71da646d91.jpg',
    },
  }

} else {
  return
}

bot.send(request);
```