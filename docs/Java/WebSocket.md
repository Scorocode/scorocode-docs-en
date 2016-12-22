<a name="WebSocket"></a>

### WebSocket

To use WebSocket in your project, you can use the <https://github.com/codebutler/android-websockets> library (or similar) with the following url scheme when initializing WebSocket:

```
wss://wss.scorocode.ru/{appID}/{wsKey}/{chanName}
```

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| appID  | String | Mandatory  |  Application identifier|a3d04e75e157b2f7ae20c2fce02f63d6 |
| wsKey  | String | Mandatory   | Application websocket key  | a3d04e75e157b2f7ae20c2fce02f63d6 |
| chanName  |  String | Mandatory  | Arbitrary channel name | chat_channel |

**Initialisation example**

```Java
WebSocketClient client = new WebSocketClient(URI.create("wss://wss.scorocode.ru/a3d04e75e157b2f7ae20c2fce02f63d6/a3d04e75e157b2f7ae20c2fce02f63d6/chat_channel"), handler);
```

**Usage example**

```Java
List<BasicNameValuePair> extraHeaders = Arrays.asList(
    new BasicNameValuePair("Cookie", "session=abcd");
);

WebSocketClient client = new WebSocketClient(URI.create("wss://wss.scorocode.ru/a3d04e75e157b2f7ae20c2fce02f63d6/b3asd4e75e1fds2f7ae20c2fce02f63d6/chat_channel"), new WebSocketClient.Handler() {
    @Override
    public void onConnect() {
        Log.d(TAG, "Connected!");
    }

    @Override
    public void onMessage(String message) {
        Log.d(TAG, String.format("Got string message! %s", message));
    }

    @Override
    public void onMessage(byte[] data) {
        Log.d(TAG, String.format("Got binary message! %s", toHexString(data));
    }

    @Override
    public void onDisconnect(int code, String reason) {
        Log.d(TAG, String.format("Disconnected! Code: %d Reason: %s", code, reason));
    }

    @Override
    public void onError(Exception error) {
        Log.e(TAG, "Error!", error);
    }
}, extraHeaders);

client.connect();

// later...

client.send("hello!");
client.send(new byte[] { 0xDE, 0xAD, 0xBE, 0xEF });
client.disconnect();
```