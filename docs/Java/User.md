<a name="User"></a>

* [User](#User)
    * [new User(name)](#User_new)
    * [.register(username, email,  password,  documentContent,  callback)](#User+register1) 
    * [.register(username, email, password, callback)](#User+register2)
    * [.login(email, password, callback)](#User+login)
    * [.logout(callback)](#User+logout)

----------------------------------------------------------------------------------------------

<a name="User_new"></a>

### new User()

User initialization

**Example** 
```Java
User appUser = new User();
```

----------------------------------------------------------------------------------------------
<a name="User+register1"></a>

### .register(callback, username, email, password)

Method for application user registration, using associated Document

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| username  | `String`              | Mandatory | Username                 | "Jovan"                     | 
| email     | `String`              | Mandatory | User email               | "user@domain.zone"          | 
| password  | `String`              | Mandatory | User password            | "CorrectHorseBatteryStaple" |
| documentContent  | `DocumentInfo`  | Optional | Document, associated with user | See the example below |
| callback  | `CallbackRegisterUser` | Mandatoryй | Callback for the request being executed. | See the example below  |

**Example** 

```Java
Document doc = new Document("users");
doc.setField("city", "Moscow");
doc.setField("isPlaceAnyOrder", true);
User user = new User();
user.register("any_username", "anyemail@mailinator.com", "test1111", doc.getDocumentContent(), 

    new CallbackRegisterUser() {
            @Override
            public void onRegisterSucceed() {
                //user register succeed
            }

            @Override
            public void onRegisterFailed(String errorCode, String errorMessage) {
                //user regiser failed
                //See errorCode and errorMessage
            }
        });

```

----------------------------------------------------------------------------------------------
<a name="User+register2"></a>

### .register(username, email, password, callback)

Method for application user registration

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| username  | `String`              | Mandatory | Username                 | "Jovan"                     | 
| email     | `String`              | Mandatory | User email               | "user@domain.zone"          | 
| password  | `String`              | Mandatory | User password            | "CorrectHorseBatteryStaple" |
| callback  | `CallbackRegisterUser` | Mandatory | Callback for the request being executed. |  See the example below |


**Example** 

```Java
User user = new User();
user.register("any_username", "anyemail@gmail.com", "test1111", doc.getDocumentContent(), 
    new CallbackRegisterUser() {
            @Override
            public void onRegisterSucceed() {
                //user register succeed
            }

            @Override
            public void onRegisterFailed(String errorCode, String errorMessage) {
                //user regiser failed
        //See errorCode and errorMessage
            }
        });
```


----------------------------------------------------------------------------------------------
<a name="User+login"></a>

### .login(email, password, callback)

Method for application user authentication

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| email     | `String`              | Mandatory | User email     | "user@domain.zone" | 
| password  | `String`              | Mandatory | User password  | "CorrectHorseBatteryStaple" |
| callback  | `CallbackLoginUser` |  | Callback for the request being executed.  |  See the example below  | 


**Example** 

```Java
User user = new User();
user.login(“anymail@mail.com”, “any pass”, new CallbackLoginUser() {
            @Override
            public void onLoginSucceed(ResponseLogin responseLogin) {
                 //login succed. See returned responseLogin instance:
                 //which contain session id and user info   
            }

            @Override
            public void onLoginFailed(String errorCode, String errorMessage) {
                 //Login failed. 
          //See errorCode and errorMessage
            }
        });

```
----------------------------------------------------------------------------------------------
<a name="User+logout"></a>

### .logout(callback)

Method for application user deauthentication. 

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| callback  | `CallbackLogoutUser` | Mandatory | Callback for the request being executed.   |  See the example below | 


**Example** 

```Java
User user = new User();
user.logout(new CallbackLogoutUser() {
            @Override
            public void onLogoutSucceed() {
                //user logout succeed
            }

            @Override
            public void onLogoutFailed(String errorCode, String errorMessage) {
                //user logout failed
                //See errorCode and errorMessage
            }
        });

```
