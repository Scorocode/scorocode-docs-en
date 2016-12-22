<a name="SCMessage"></a>

* [SCMessage](#SCMessage)
    * [.sendPush(query: SCQuery, subject: String, text: String, callback: (Bool, SCError?, Int?) -> Void)](#SCScript+sendPush)
    * [.sendSms(query: SCQuery, subject: String, text: String, callback: (Bool, SCError?, Int?) -> Void)](#SCScript+sendSms)

----------------------------------------------------------------------------------------------
<a name="SCMessage+sendPush"></a>
## .sendPush(query, subject, text, callback)

Push sending method
 
| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| query    | <code>SCQuery</code>                        |              | Users/Devices collection query for sampling addressees |          | 
| text     | <code>String</code>                         |              | Push text                                   | "Push text"         |
| callback | <code>(Bool, SCError?, Int?) -> Void</code> |              | Callback for the request being executed.    |                     |

**Example**   

```SWIFT
var queryUserDevices = SCQuery(collection: "devices")
var broadcast = SCMessage()

queryUserDevices.exists("userRelation")
broadcast.sendPush(queryUserDevices, text:"Push text") {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
----------------------------------------------------------------------------------------------
<a name="SCMessage+sendSms"></a>
## .sendSms(query, subject, text, callback)

SMS sending method

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| query    | <code>SCQuery</code>                        |              | Users collection query for sampling addressees |                    | 
| text     | <code>String</code>                         |              | SMS text                                       | "SMS text"         |
| callback | <code>(Bool, SCError?, Int?) -> Void</code> |              | Callback for the request being executed.       |                    |

**Example**   

```SWIFT
var queryUsersWithPhone = SCQuery(collection: "users")
var broadcast = SCMessage()

queryUsersWithPhone.exists("phone")
broadcast.sendSms(queryUsersWithPhone, text:"SMS text") {
    success, error, result in
    if success {
        print("Success")
    } else {
        if let error = error {
            print("Error")
        }
    }
}
```
