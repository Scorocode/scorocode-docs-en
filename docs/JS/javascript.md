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

For the purpose of showing you an example development process, we are using the [react](https://facebook.github.io/react/) library and the [create-react-app](https://github.com/facebookincubator/create-react-app) utility for fast development of an application template. Installation requirements are available upon the links above. To install the utility you can use the following console command:

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

        // Creating variables to store request results  
        this.state = {
            registerResult: "",
            loginResult: ""
        };
    }

    // Changing the content
    // Let's create two forms: a registration one and an authorization one
    render() {
        return (
            &lt;div&gt;
                &lt;h2&gt;Registration&lt;/h2&gt;
                &lt;form onSubmit={(event) =&gt; {this.handleRegister(event)}}&gt;
                    &lt;input type="text" placeholder="user name"/&gt; {' '}
                    &lt;input type="email" placeholder="email"/&gt; {' '}
                    &lt;input type="password" placeholder="password"/&gt;
                    &lt;button type="submit"&gt;Register&lt;/button&gt;
                &lt;/form&gt;

                &lt;pre&gt;{this.state.registerResult}&lt;/pre&gt;

                &lt;h2&gt;System Login&lt;/h2&gt;
                &lt;form onSubmit={(event) =&gt; {this.handleLogin(event)}}&gt;
                    &lt;input type="email" placeholder="email"/&gt; {' '}
                    &lt;input type="password" placeholder="password"/&gt;
                    &lt;button type="submit"&gt;Login&lt;/button&gt;
                &lt;/form&gt;

                &lt;pre&gt;{this.state.loginResult}&lt;/pre&gt;
            &lt;/div&gt;
        );
    }

    // Handling the registration form
    handleRegister(event) {
        event.preventDefault()
        const username = event.target.elements[0].value
        const email = event.target.elements[1].value
        const password = event.target.elements[2].value

        // Clearing the result variable 
        this.setState({registerResult: ""})

        // Creating new Scorocode.User sample
        var appUser = new Scorocode.User();

        // Setting data needed to register an application user
        appUser
            .set("username", username)
            .set("email", email)
            .set("password", password);

        // Registering a new application user
        appUser.signup()
            // Event handler for a successful request run
            .then((data)=>{
                // Updating the result variable by transferring the object in the code line
                this.setState({registerResult: JSON.stringify(data, null, 2)})
            })
            .catch((err) => {
                // Updating the result variable by transferring the object in the code line
                this.setState({registerResult: JSON.stringify(err, null, 2)})
            })
    }

    // Handling the authorization form
    handleLogin(event) {
        event.preventDefault()
        const email = event.target.elements[0].value
        const password = event.target.elements[1].value

        // Clearing the result variable
        this.setState({loginResult: ""})

        // Creating new Scorocode.User sample
        var appUser = new Scorocode.User();

        // Authenticating an application user with their email and password
        appUser.login(email, password)
            // Ivent handler for a successful request run
            .then((data)=>{
                // ОUpdating the result variable by transferring the object in the code line
                this.setState({loginResult: JSON.stringify(data, null, 2)})
            })
            .catch((err) => {
                // Updating the result variable by transferring the object in the code line
                this.setState({loginResult: JSON.stringify(err, null, 2)})
            })
    }
}

export default App;
```

Save the file and run your application with the console command:

```
npm start
```

As a result, a page with two forms will open in your browser: a registration form and an authorization form.
Experiment with users registration and authorization, and check the Scorocode API responses.
After a successful registration you can see the added user in the User collection and authorize it using its email and password. 
