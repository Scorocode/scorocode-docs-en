<a name="SCScript"></a>

A class that works with the server-side scripts of the application

* [SCScript](#SCScript)
    * [.run(scriptId, pool, callback)](#SCScript+run)


----------------------------------------------------------------------------------------------

<a name="SCScript+run"></a>

## .run(scriptID, pool, callback)

A method that calls a server-side script

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- |
| scriptID | <code>String</code> | Mandatory | Server script ID	 | "57484fb91c5666544db25675" | 
| pool | <code>[String: AnyObject]</code> |  | Data pool to be passed to the server-side script	 | ["data": {"array": [0,1,2,3,"строка"], "logic": false}, "weekday": "friday"] |
| callback | <code>(Bool, SCError?) -> Void</code> | | Callback for the request being executed | |


**Example**   

```SWIFT
SCScript.run("57484fb91c5666544db25675", ["collname": "items", "key": "relToQuests", "val": ["CF4Gk9WP6L", "MwORD9llTM", "Jw4INX328A"]]) {
    success, error in
}
```

