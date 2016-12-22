<a name="ScorocodeSDK"></a>

* [ScorocodeSDK](#ScorocodeSDK)
    * [.initWith(appId, clientKey, masterKey, fileKey, messageKey, scriptKey, websocketKey)](#ScorocodeSDK+init)

----------------------------------------------------------------------------------------------
<a name="ScorocodeSDK+initWith"></a>

### ScorocodeSDK.initWith(appId, clientKey, masterKey, fileKey, messageKey)

SDK initialisation. 

| Parameter     | Type                | Properties | Description                                 | Value example                      |
|---------------|---------------------|------------|---------------------------------------------|------------------------------------|
| applicationId | <code>String</code> | Mandatory  | Application identifier                      | "db8a1b41b8543397a798a181d9891b4c" |
| clientId      | <code>String</code> | Mandatory  | Client key for the iOs platform             | "563452bbc611d8106d5da767365897de" |
| accessKey     | <code>String</code> | Mandatory  | Authentication key (master key, script key) | "28f06b89b62165c33de55265166d8781" |
| fileKey       | <code>String</code> |            | Authentication keys for access to files     | "6305ee7ac8023191a333d9267f1a07e8" |
| messageKey    | <code>String</code> |            | Authentication key for sending messages     | "9d774f6fa704f192e6aef53933f44e4f" |
| scriptKey     | <code>String</code> |            | Server-side scripts access key              | "054bcf2ktyj9369dab1c32343f1776ae" |
| websocketKey  | <code>String</code> |            | WebSocket access key                        | "694bcf2ffd29369dab1c3d0e3f1776ae" |


!!! Note "Примечания"
    - Sdk must be initialised before you use other SDK methods;

**Example**  

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, "694bcf2ffd29369dab1c3d0e3f1776ae");
```
