<a name="Message"></a>

Class for message sending

* [Message](#Message)
    * [new Message(from, subject, text)](#Message_new)
    * [.sendPush(messagePush, query, callback)](#Message+sendPush1)
    * [.sendPush(messagePush, callback)](#Message+sendPush2)
    * [.sendSms(messageSms, query, callback)](#Message+sendSms1)
    * [.sendSms(messageSms, callback)](#Message+sendSms2)

----------------------------------------------------------------------------------------------

<a name="Message_new"></a>

Message constructor

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| from    | `String` |  Optional     | Message sender | "Any name" | 
| text    | `String` |  Optional     | Message text   | "Any text" |

**Example**

```Java
MessagePush messagePush = new MessagePush("Any text", null);
```

----------------------------------------------------------------------------------------------

<a name="Message+sendPush1"></a>
### .sendPush(messagePush, query, callback)

Push sending method

| Parameter   | Type               | Properties | Description                                 | Value example |
|-------------|--------------------|------------|---------------------------------------------|---------------|
| messagePush | `MessagePush`      | Mandatory  | Object, that contains message               |               |
| query       | `Query`            | Optional   | Users/Devices collection query for sampling |               |
| callback    | `CallbackSendPush` | Mandatory  | Callback for the request being executed.    |               |

**Example**

```Java
MessagePush messagePush = new MessagePush("Any text", null);

Query query = new Query("USERS");
query.equalTo("_id", "XukL1FrVoL");

Message message = new Message();
message.sendPush(messagePush, query, new CallbackSendPush() {
            @Override
            public void onPushSended() {
                //push send
            }

            @Override
            public void onPushSendFailed(String errorCode, String errorMessage) {
                //error during sending
            }
        });
```

----------------------------------------------------------------------------------------------

<a name="Message+sendPush2"></a>
### .sendPush(messagePush, callback)

Push sending method

| Parameter   | Type               | Properties | Description                                | Value example |
|-------------|--------------------|------------|--------------------------------------------|---------------|
| messagePush | `MessagePush`      | Mandatory  | Object, that contains message              |               |
| callback    | `CallbackSendPush` | Mandatory  | Callback for the request being executed.   |               |

**Example**

```Java
MessagePush messagePush = new MessagePush("Any text", null);

Query query = new Query("USERS");
query.equalTo("_id", "XukL1FrVoL");

Message message = new Message();
message.sendPush(messagePush, query, new () {
            @Override
            public void onPushSended() {
                //push send
            }

            @Override
            public void onPushSendFailed(String errorCode, String errorMessage) {
                //error during sending
            }
        });
```

----------------------------------------------------------------------------------------------

<a name="Message+sendSms1"></a>
### .sendSms(messageSms, query, callback)

SMS sending method

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| messageSms   |  `messageSms`     |  Mandatory     |  Object, that contains message                  |   |
| query        | `Query`             |  Optional   |  Users collection query for sampling.            |   |
| callback     | `CallbackSendSms` |  Mandatory     |   Callback for the request being executed.      |   |

**Example**

```Java
MessageSms messageSms = new MessageSms("Hello world");

Query query = new Query("USERS");
query.equalTo("_id", "XukL1FrVoL");

message.sendSms(messageSms, query, new CallbackSendSms() {
            @Override
            public void onSmsSended() {
                //sms send
            }

            @Override
            public void onSmsSendFailed(String errorCode, String errorMessage) {
                //error during sending
            }
        });

```


----------------------------------------------------------------------------------------------

<a name="Message+sendSms2"></a>
### .sendSms(messageSms, callback)

SMS sending method

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| messageSms   |  `messageSms`     |  Mandatory     |  Object, that contains message                |   |
| callback     | `CallbackSendSms` |  Mandatory     |   Callback for the request being executed.    |   |

**Example**

```Java
MessageSms messageSms = new MessageSms("Hello world");
message.sendSms(messageSms, new CallbackSendSms() {
            @Override
            public void onSmsSended() {
                //sms send
            }

            @Override
            public void onSmsSendFailed(String errorCode, String errorMessage) {
                //error during sending
            }
        });
```