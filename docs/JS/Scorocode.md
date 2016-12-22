<a name="Scorocode"></a>

* [Scorocode](#Scorocode)
    * [.Init(opt) - Инициализация SDK](#Scorocode+Init)

<a name="Scorocode+Init"></a>

## .Init(opt) - SDK initialization

| Параметр | Тип | Описание |
| --- | --- | --- |
| opt | <code>Object</code> | Keys for ititialisation: application identifier, your platform client key and access keys that necessary. |

**Properties**

| Parameter | Type | Description |
| --- | --- | --- |
| ApplicationID | <code>String</code> | Application identifier |
| JavaScriptKey | <code>String</code> | Client key for JavaScript platform |
| AndroidKey | <code>String</code> | Client key for Android platform |
| iOsKey | <code>String</code> | Client key for iOs platform |
| WinPhoneKey | <code>String</code> | Client key for Windows Phone platform |
| FileKey | <code>String</code> | File access key  |
| ScriptKey | <code>String</code> | Server-side scripts access key  |
| MessageKey | <code>String</code> | Messages access key  |
| WebSocketKey |<code>String</code> | WebSocket access key |
| MasterKey | <code>String</code> | Application master-key |

**Example**  

```Javascript
Scorocode.Init({
    ApplicationID: "a3d04e75e157b2f7ae20c2fce02f63d6",
    JavaScriptKey: "ad6a8fe72ef7dfb9c46958aacb15196a",
    FileKey: "2aceceec7d2e96b1487ec399f5afa101",
    MessageKey: "e215ed465646775b42d65cca2d2f5db9"
});
```