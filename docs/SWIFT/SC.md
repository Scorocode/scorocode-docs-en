<a name="Scorocode"></a>

Core class for SDK handling

* [SC](#Scorocode)
    * [.initWith(opt)](#Scorocode+initWith)

------------------------------------------------------------------------------------------

<a name="Scorocode+initWith"></a>

## .initWith(applicationId, clientId, accessKey, fileKey, messageKey)

SDK initialization. Parameter values are defined in AppDelegate.swift

| Parameter	 | Type | Properties | Description	 | Value example |
| --- | --- | --- | --- | --- |
| applicationId | <code>String</code> | Mandatory	 | Application identifier | "db8a1b41b8543397a798a181d9891b4c" |
| clientId      | <code>String</code> | Mandatory | Client key for the iOs platform	 | "563452bbc611d8106d5da767365897de" |
| accessKey     | <code>String</code> | Mandatory | Authentication key (master key, script key)	 | "28f06b89b62165c33de55265166d8781"  |
| fileKey       | <code>String</code> |  | Authentication keys for access to files | "6305ee7ac8023191a333d9267f1a07e8" |
| messageKey    | <code>String</code> |  | Authentication key for sending messages |  "9d774f6fa704f192e6aef53933f44e4f" |


**Example**  

In `AppDelegate.swift`, specify initialization parameter values in the `didFinishLaunchingWithOptions` method:


```SWIFT
let applicationId = "db8a1b41b8543397a798a181d9891b4c"
let clientId = "563452bbc611d8106d5da767365897de"
let accessKey = "28f06b89b62165c33de55265166d8781"
let fileKey = "6305ee7ac8023191a333d9267f1a07e8"
let messageKey = "9d774f6fa704f192e6aef53933f44e4f"
```

SDK initialization

```SWIFT
SC.initWith(applicationId: applicationId, clientId: clientId, accessKey: accessKey, fileKey: fileKey, messageKey: messageKey)
```