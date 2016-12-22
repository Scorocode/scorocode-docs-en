<a name="Script"></a>

## Script
Class for handling server-side scripts

* [Script](#Script)
    * [new Script()](#Script_new)
    * [.runScript(scriptId, dataPoolForScript, callback)](#Script+runScript1)
    * [.runScript(scriptId, callback)](#Script+runScript1)

----------------------------------------------------------------------------------------------

<a name="Script_new"></a>
### new Script()
Script constructor

```Java
Script script = new Script();
```
----------------------------------------------------------------------------------------------
<a name="Script+runScript1"></a>
### .runScript(scriptId, dataPoolForScript, callback)
Server-side script running method

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| scriptId	        | `String`	            | Mandatory	 | Server-side script identifier | "57e1503b48e5f54441189790" |
| dataPoolForScript	| `Object`	            | Optional | Object with the data that will be passed to the server-side script | See the example below |
| callback	        | `CallbackRunScript` 	| Mandatory	 | Callback for the request being executed.	| See the example below |

!!! note "Note"
    Object `dataPoolForScript` will be serialised to JSON by the Google Gson parser. See <https://github.com/google/gson> for assistance.

**Example**
```Java
Script script = new Script();
HashMap<String, Object> dataPool = new HashMap<>();
dataPool.put(“collname”,”items”);
dataPool.put(“key”,”exampleField”);
dataPool.put(“val”,”anyInfo”);
	
script.runScript("57e1503b48e5f54441189790", dataPool, new CallbackRunScript() {
            @Override
            public void onScriptSended() {
                //script sended and runned
            }

            @Override
            public void onScriptSendFailed(String errorCode, String errorMessage) {
                //error during script run
            }
        });
```



----------------------------------------------------------------------------------------------
<a name="Script+runScript2"></a>
### .runScript(scriptId, callback)
Server-side script running method

| Parameter | Type | Properties | Description | Value example |
|-----------|------|------------|-------------|---------------|
| scriptId          | `String`              | Mandatory  | Server-side script identifier | "57e1503b48e5f54441189790" |
| callback          | `CallbackRunScript`   | Mandatory  | Callback for the request being executed. | See the example below |

!!! note "Note"
    Object `dataPoolForScript` will be serialised to JSON by the Google Gson parser. See <https://github.com/google/gson> for assistance.

**Example**
```Java
Script script = new Script();
script.runScript("57e1503b48e5f54441189790", new CallbackRunScript() {
            @Override
            public void onScriptSended() {
                //script sended and runned
            }

            @Override
            public void onScriptSendFailed(String errorCode, String errorMessage) {
                //error during script run
            }
        });
```
