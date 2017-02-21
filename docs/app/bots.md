## Telegram Bot creation

Before you start developing your new bot, at first you need to register bot in Telegram and receive his unique identifier. On Telegram, open the `@BotFather` profile, and start to talk with “him”. Type the command “/newbot”. `@BotFather` will ask you for a bot name, which is a free text, and a bot username: it always end by “bot”. After that `@BotFather` will give you new bot id, which looks like `321196098:AAEDbOYD6iLWsHD7w28vqf3a9oBeJAPXXpg`

Secondly, you need to create server-side script in your Scorocode application that will be associated with the bot to hande all data processing.

After that you need to create new Scorocode bot. You can do it in the "Bots" page by pressing "Create new bot" button. This action will show you a form in witch you can specify bot's data:

| Parameter      | Properties | Description |
| ------------- | -------- | -------- |
| Bot name | Mandatory | Application bot name |
| Bot identifier | Mandatory | Bot's Telegram id , given by '@BotFather' |
| Script identifier | Mandatory | Choose script from the list of application server-side scripts |
| Bot activation flag | Optional, `false` by default | Set the flag to activate your bot |

Press save button to save new bot. At any time you can edit bot's setting by pressing "edit" button.

![Edit bot](../img/botedit.png)

## Main principles

When your bot is activated Scorocode creates the `webhook` to receive Telegram data. This data is available in your server-side script 'pool' object everytime it receives update from Telegram. See ['getting updates' documentation](https://core.telegram.org/bots/api#getting-updates) for a complete `Update` object description.

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