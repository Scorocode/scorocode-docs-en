## New user registration.

**https://api.scorocode.ru/api/v1/register**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "username"    : "", // username, mandatory, 5 characters minimum
    "email"       : "", // email, mandatory
    "password"    : "", // password, mandatory, 6 characters minimum
    "doc"         : { } // user field values in the "users" collection, optional
}
```

**Responses:**

*Success*

```
{
    "error"       : false
}
```

*Error*

```
{
    "error"       : true,
    "errCode"     : 4XX/5XX, // Error code
    "errMsg"      : "Error text"
}
```

**cURL example**

```
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

## User authentication

**https://api.scorocode.ru/api/v1/login**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "email"       : "", // email, mandatory
    "password"    : "", // password, mandatory
}
```

**Responses:**

*Success*

```
{
    "error"       : false,
    "result"      : {
        "sessionId"     : "", // session ID
        "user"          : {}  // Document containing the user
    }
}
```

*Error*

```
{
    "error"       : true,
    "errCode"     : 4XX/5XX, // Error code
    "errMsg"      : "Error text"
}
```

**cURL example**

```
curl -X POST -H "Content-Type: application/json" -d '{
    "app": "db8a1b41b8543397a798a181d9891b4c",
    "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
    "email": "useremail@domain.zone",
    "password": "CorrectHorseStapleButton"
}' "https://api.scorocode.ru/api/v1/login"
```

## User deauthentication

**https://api.scorocode.ru/api/v1/logout**

Method: `POST`

Headers:

`Content-Type: application/json`

```
{
    "app"         : "", // application identifier, mandatory
    "cli"         : "", // client key, mandatory
    "sess"        : ""  // session ID, mandatory
}
```

**Responses:**

*Success*

```
{
    "error"       : false
}
```

*Error*

```
{
    "error"       : true,
    "errCode"     : 4XX/5XX, // Error code
    "errMsg"      : "Error text"
}
```

**cURL example**

```
curl -X POST -H "Content-Type: application/json" -d '{
    "app": "db8a1b41b8543397a798a181d9891b4c",
    "cli": "ad6a8fe72ef7dfb9c46958aacb15196a",
    "sess": "6rnbKKGvLLdU9Sl9"
}' "https://api.scorocode.ru/api/v1/logout"
```