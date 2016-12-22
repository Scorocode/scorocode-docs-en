<a name="Scorocode.User"></a>

* [.User](#Scorocode.User)
    * [new User()](#new_Scorocode.User_new)
    * [.signup(options)](#Scorocode.User+signup) ⇒ <code>[promise.&lt;Scorocode.User&gt;](#Scorocode.User)</code>
    * [.login(email, password, options)](#Scorocode.User+login) ⇒ <code>[promise.&lt;Scorocode.User&gt;](#Scorocode.User)</code>
    * [.logout(options)](#Scorocode.User+logout) 

----------------------------------------------------------------------------------------------

<a name="new_Scorocode.User_new"></a>

## new User()
Class for application user handling.

**Example**  

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var appUser = new Scorocode.User();
appUser.set("email", "user@mailserver.domain").set("password", "52c7ab3dab2c").set("username", "ChosenOne");
appUser.signup()
    .then((success)=>{
        console.log(success);
    })
    .catch((error)=>{
        console.log(error)
    });
```

----------------------------------------------------------------------------------------------

<a name="Scorocode.User+signup"></a>

## .signup(options)
Method for application user registration.

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| callback | <code>Object</code>| | Success and error callbacks for the executed query. |  |


**Example**
```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var appUser = new Scorocode.User();
appUser.set("email", "user@domain.zone").set("password", "CorrectHorseBatteryStaple").set("username", "ChosenOne");
appUser.signup()
    .then((success)=>{
        console.log(success);
    })
    .catch((error)=>{
        console.log(error)
    });
```

**Возвращает** <code>promise.{Scorocode.User}</code> - returns promise that returns `Scorocode.User` data

----------------------------------------------------------------------------------------------


<a name="Scorocode.User+login"></a>

## .login(email, password, options)

Method for application user authentication and user session retrieval.

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| email    | <code>String</code>| Mandatory  | User email                                   | "user@domain.zone"          | 
| password | <code>String</code>| Mandatory  | User password                                | "CorrectHorseBatteryStaple" |
| callback | <code>Object</code>|            | Success and error callbacks for the executed query. |                             |

**Example**

```js
var Scorocode = require('scorocode');
Scorocode.Init({
    ApplicationID: "applicationId",
    JavaScriptKey: "javascriptKey"
});

var appUser = new Scorocode.User();
appUser.login("user@domain.zone", "CorrectHorseBatteryStaple")
    .then((loggedIn)=>{
        console.log("User successfully logged in \n", loggedIn);
        setTimeout( function () {
            appUser.logout()
                .then((loggedOut)=>{
                    console.log("User successfully logged out \n");
                })
                .catch((errLogout)=>{
                    console.log(errLogout)
                });
            },10000);
    })
    .catch((errLogin)=>{
        console.log(errLogin)
    });
```

**Returns** <code>promise.{Scorocode.User}</code> -  returns promise that returns `Scorocode.User` data

----------------------------------------------------------------------------------------------

<a name="Scorocode.User+logout"></a>

## .logout(options) 

Method for application user deauthentication and user session deletion.


| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| callback | <code>Object</code>|            | Success and error callbacks for the executed query. |                             |

**Example**

```js
var appUser = new Scorocode.User();
appUser.login("user@domain.zone", "CorrectHorseBatteryStaple")
    .then((loggedIn)=>{
        console.log("User successfully logged in \n", loggedIn);
        setTimeout( function () {
            appUser.logout()
                .then((loggedOut)=>{
                    console.log("User successfully logged out \n");
                })
                .catch((errLogout)=>{
                    console.log(errLogout)
                });
            },10000);
    })
    .catch((errLogin)=>{
        console.log(errLogin)
    });
```



