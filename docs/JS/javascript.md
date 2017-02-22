You can download Scorocode JavaScript SDK [here](https://github.com/Scorocode/scorocode-SDK-JS).

## SDK integration

To use SDK on the browser side, download the [lib/browser/scorocode.min.js](https://github.com/Scorocode/scorocode-SDK-JS/blob/master/lib/browser/scorocode.min.js) library and connect it to your project: 

```js
<script src="js/scorocode.min.js"></script>
```
 
To use SDK on the server side (NodeJS), install the SDK module `npm install scorocode` and connect it to the project:

```js
var Scorocode = require('scorocode');
```
## Fast Start

Register and create an application with any name inside [Scorocode](https://scorocode.ru/).

For the purpose of showing you an expample development process, we used the [react](https://facebook.github.io/react/) library and the [create-react-app](https://github.com/facebookincubator/create-react-app) utility for fast development of an application template. Installation requirements are avaliable upon the links above. To install the utility you can use the following console command:

```
npm install -g create-react-app
```

Create a new application and install JS SDK with the following console commands sequence:

```
create-react-app first-scorocode
cd first-scorocode
npm install scorocode --save
```

Open the `src/index.js` file and add the code lines below, replacing "xxx" keys with the appropriate keys from your application security settings:

```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import './index.css';
import Scorocode from 'scorocode' // <- добавить импорт SDK Scorocode

// Initiate SDK
Scorocode.Init({
    ApplicationID: "xxx", // <- replace xxx with appId application key
    JavaScriptKey: "xxx", // <- replace xxx with javascript application key
    MasterKey:     "xxx"  // <- replace xxx with masterKey application key
});

ReactDOM.render(
  &lt;App /&gt;,
  document.getElementById('root')
);
```

Open  the `src/App.js` file and replace its contents with the following code:

```js
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';
import Scorocode from 'scorocode' // <- add SDK import


class App extends Component {

    constructor(props) {
        super(props);

        // Creating values to store Создаем переменные, которые будут хранить результаты запросов
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
