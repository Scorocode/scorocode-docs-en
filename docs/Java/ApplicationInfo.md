<a name="ApplicationInfo"></a>

Класс для работы с информацией о приложении.

**Содержание**

* [ApplicationInfo](#ApplicationInfo)
    * [new ApplicationInfo()](#ApplicationInfo_new)
    * [.getApplicationInfo(callback)](#ApplicationInfo+getApplicationInfo)


------------------------------------------------------------------------

<a name="ApplicationInfo_new"></a>

## new ApplicationInfo()

Constructor ApplicationInfo

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

ApplicationInfo applicationInfo = new ApplicationInfo();
```

!!! Note "MasterKey"
    You should initialise SDK with MasterKey to use ApplicationInfo methods.

------------------------------------------------------------------------

<a name="ApplicationInfo+getApplicationInfo"></a>

## .getApplicationInfo(callback)

Retreive full application info.

| Parameter | Type | 	Properties	| Description |	Example |
| --- | --- | --- | --- | --- |
| callback | `CallbackGetApplicationInfo` | Mandatory | Callback for the request being executed | See the example below |

**Example**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

ApplicationInfo applicationInfo = new ApplicationInfo();
applicationInfo.getApplicationInfo(new CallbackGetApplicationInfo() {
    @Override
    public void onRequestSucceed(ScorocodeApplicationInfo appInfo) {
         //sdk  returned info
    }

    @Override
    public void onRequestFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```
