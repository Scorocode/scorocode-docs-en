## New user registration.

**https://api.scorocode.ru/api/v1/register**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "username"    : "", // username, mandatory
    "email"       : "", // email, mandatory
    "password"    : "", // password, mandatory
    "doc"         : { } // user field values in the "users" collection, optional
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "username": "username",
        "email": "useremail@domain.zone",
        "password": "CorrectHorseStapleButton",
        "doc": {
            "exampleField": "Today is June, 18. It's Muriel's birthday! Muriel is now 20 years old. Happy Birthday, Muriel!",
            "anotherExampleField": "I don't know what to say. I used to want to be an astrophysicist. Unfortunately, this is true."
        }
    }
    ' "https://api.scorocode.ru/api/v1/register"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
        "error"       : false
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```


-----------------------------------------------------------------------------------------------------------------------------------------------------------

## User authentication

**https://api.scorocode.ru/api/v1/login**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "email"       : "", // email, mandatory
    "password"    : "", // password, mandatory
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "email": "useremail@domain.zone",
        "password": "CorrectHorseStapleButton"
    }' "https://api.scorocode.ru/api/v1/login"
    ```


**Responses:**

!!! success "Success"
    ```JSON
    {
        "error"       : false,
        "result"      : {
            "sessionId"     : "", // session ID
            "user"          : {}  // Document containing the user information
        }
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

-----------------------------------------------------------------------------------------------------------------------------------------------------------


## User deauthentication

**https://api.scorocode.ru/api/v1/logout**

Method: `POST`

Headers: `Content-Type: application/json`

```JSON
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "sess"        : ""  // session ID, mandatory
}
```

!!! tip "cURL example"
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{
        "app": "db8a1b41b8543397a798a181d9891b4c",
        "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
        "sess": "6rnbKKGvLLdU9Sl9"
    }' "https://api.scorocode.ru/api/v1/logout"
    ```

**Responses:**

!!! success "Success"
    ```JSON
    {
        "error"       : false
    }
    ```

!!! failure "Error"
    ```JSON
    {
        "error"       : true,
        "errCode"     : 4XX/5XX, // Error code
        "errMsg"      : "Error text"
    }
    ```

