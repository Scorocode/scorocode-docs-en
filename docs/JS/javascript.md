You can download Scorocode JavaScript SDK [here](https://github.com/Scorocode/scorocode-SDK-JS).

## SDK integration

To use SDK on the browser side, download the [lib/browser/scorocode.min.js](https://github.com/Scorocode/scorocode-SDK-JS/blob/master/lib/browser/scorocode.min.js) library and connect it to the project: 

```js
<script src="js/scorocode.min.js"></script>
```
 
To use SDK on the server side (NodeJS), install the SDK module `npm install scorocode` and connect it to the project:

```js
var Scorocode = require('scorocode');
```
## Быстрый старт

Зарегистрируйтесь и создайте приложение с любым именем в [Scorocode](https://scorocode.ru/).

Для разработки примера мы использовали библиотеку [react](https://facebook.github.io/react/) и утилиту для быстрого создания каркаса приложения [create-react-app](https://github.com/facebookincubator/create-react-app) Требования для установки смотрите по ссылке. Установить утилиту можно из консоли командой:

```
npm install -g create-react-app
```

Создайте новое приложение и установите JS SDK последовательностью команд в консоли:

```
create-react-app first-scorocode
cd first-scorocode
npm install scorocode --save
```

Откройте файл `src/index.js` и добавьте в него строки, заменив ключи "xxx" на соответствующие ключи из вашего приложения (раздел Настройки -> Безопасность):

```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import './index.css';
import Scorocode from 'scorocode' // <- добавить импорт SDK Scorocode

// Добавить инициализацию SDK
Scorocode.Init({
    ApplicationID: "xxx", // <- заменить xxx на ключ appId приложения
    JavaScriptKey: "xxx", // <- заменить xxx на ключ javascript приложения
    MasterKey:     "xxx"  // <- заменить xxx на ключ masterKey приложения
});

ReactDOM.render(
  &lt;App /&gt;,
  document.getElementById('root')
);
```

Откройте файл `src/App.js` замените его содержимое на следующий код:

```js
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';
import Scorocode from 'scorocode' // <- добавить импорт SDK


class App extends Component {

    constructor(props) {
        super(props);

        // Создаем переменные, которые будут хранить результаты запросов
        this.state = {
            registerResult: "",
            loginResult: ""
        };
    }

    // Заменяем содержимое
    // Создаем две формы: для регистрации и для авторизации
    render() {
        return (
            &lt;div&gt;
                &lt;h2&gt;Регистрация&lt;/h2&gt;
                &lt;form onSubmit={(event) =&gt; {this.handleRegister(event)}}&gt;
                    &lt;input type="text" placeholder="имя пользователя"/&gt; {' '}
                    &lt;input type="email" placeholder="email"/&gt; {' '}
                    &lt;input type="password" placeholder="password"/&gt;
                    &lt;button type="submit"&gt;Зарегистрироваться&lt;/button&gt;
                &lt;/form&gt;

                &lt;pre&gt;{this.state.registerResult}&lt;/pre&gt;

                &lt;h2&gt;Вход в систему&lt;/h2&gt;
                &lt;form onSubmit={(event) =&gt; {this.handleLogin(event)}}&gt;
                    &lt;input type="email" placeholder="email"/&gt; {' '}
                    &lt;input type="password" placeholder="password"/&gt;
                    &lt;button type="submit"&gt;Войти&lt;/button&gt;
                &lt;/form&gt;

                &lt;pre&gt;{this.state.loginResult}&lt;/pre&gt;
            &lt;/div&gt;
        );
    }

    // Обработчик формы регистрации
    handleRegister(event) {
        event.preventDefault()
        const username = event.target.elements[0].value
        const email = event.target.elements[1].value
        const password = event.target.elements[2].value

        // Очищаем переменную результата
        this.setState({registerResult: ""})

        // Создадим новый экземпляр Scorocode.User
        var appUser = new Scorocode.User();

        // Установим данные, необходимые для регистрации пользователя приложения
        appUser
            .set("username", username)
            .set("email", email)
            .set("password", password);

        // Зарегистрируем нового пользователя приложения
        appUser.signup()
            // Обработчик успешного выполнения запроса
            .then((data)=>{
                // Обновляем переменную результата, переводя полученный объект в строку
                this.setState({registerResult: JSON.stringify(data, null, 2)})
            })
            .catch((err) => {
                // Обновляем переменную результата, переводя полученный объект в строку
                this.setState({registerResult: JSON.stringify(err, null, 2)})
            })
    }

    // Обработчик формы авторизации
    handleLogin(event) {
        event.preventDefault()
        const email = event.target.elements[0].value
        const password = event.target.elements[1].value

        // Очищаем переменную результата
        this.setState({loginResult: ""})

        // Создадим новый экземпляр Scorocode.User
        var appUser = new Scorocode.User();

        // Аутентифицируем пользователя приложения, используя email и password
        appUser.login(email, password)
            // Обработчик успешного выполнения запроса
            .then((data)=>{
                // Обновляем переменную результата, переводя полученный объект в строку
                this.setState({loginResult: JSON.stringify(data, null, 2)})
            })
            .catch((err) => {
                // Обновляем переменную результата, переводя полученный объект в строку
                this.setState({loginResult: JSON.stringify(err, null, 2)})
            })
    }
}

export default App;
```

Сохраните файл и запустите приложение из консоли командой:

```
npm start
```

В результате в браузере откроется страница с двумя формами: регистрации и авторизации.
Поэкспериментируйте с регистрацией пользователей и их авторизацией и посмотрите на ответы от API Scorocode.
После успешной регистрации вы можете увидеть в коллекции users добавленного пользователя и авторизоваться, используя его email и пароль.
