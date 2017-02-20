<a name="ScorocodeScript"></a>

Класс для работы со скриптами приложения.

**Содержание**

* [ScorocodeScript](#ScorocodeScript)
    * [new ScorocodeScript()](#ScorocodeScript_new)
    * [.createScript(script, callback)](#ScorocodeScript+createScript)
    * [.getScriptById(scriptId, callback)](#ScorocodeScript+getScriptById)
    * [.updateScript(scriptToUpdateId, newScriptInfo, callback)](#ScorocodeScript+updateScript)
    * [.deleteScript(scriptToDeleteId, callback)](#ScorocodeScript+deleteScript)


------------------------------------------------------------------------

<a name="ScorocodeScript_new"></a>

## new ScorocodeScript()

Конструктор ScorocodeScript

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

ScorocodeScript newScript = new ScorocodeScript();
```

!!! Note "Примечание"
    Для использования методов класса ScorocodeScript необходима инициализация SDK с указанием MasterKey.

------------------------------------------------------------------------

<a name="ScorocodeScript+createScript"></a>

## .createScript(script, callback)

Метод для создания скрипта

| Параметр | Тип | 	Свойства	| Описание |	Пример значения |
| --- | --- | --- | --- | --- |
| script | `ScorocodeScript` | Обязательный | Информация о создаваемом скрипте | см. пример ниже |
| callback | `CallbackCreateScript` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

ScorocodeScript script = new ScorocodeScript();
script.setScriptName("testscript.js");
script.setScriptPath("testscript.js");
new Script().createScript(script, new CallbackCreateScript() {
    @Override
    public void onScriptCreated(ScorocodeScript script) {
         //script created
    }

    @Override
    public void onCreationFailed(String errorCode, String errorMessage) {
        //error during request         
    }
});
```

------------------------------------------------------------------------

<a name="ScorocodeScript+getScriptById"></a>

## .getScriptById(scriptId, callback)

Метод для получения информации о скрипте по его id.

| Параметр | Тип |  Свойства    | Описание |    Пример значения |
| --- | --- | --- | --- | --- |
| scriptId | `ScorocodeScript` | Обязательный | Id запрашиваемого скрипта | см. пример ниже | 
| callback | `CallbackGetScriptById` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

Script script = new Script();
script.getScriptById(testScript.getScriptId(), new CallbackGetScriptById() {
    @Override
    public void onRequestSucceed(ScorocodeScript script) {
        //sdk returned script
    }

    @Override
    public void onRequestFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="ScorocodeScript+updateScript"></a>

## .updateScript(scriptToUpdateId, newScriptInfo, callback)

Метод для обновления информации о скрипте

| Параметр | Тип |  Свойства    | Описание |    Пример значения |
| --- | --- | --- | --- | --- |
| scriptToUpdateId | `String` | Обязательный | Id обновляемого скрипта | "123434451234" | 
| newScriptInfo | `ScorocodeScript` | Обязательный | Новая информация о скрипте | см. пример ниже |
| callback | `CallbackUpdateScript` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

ScorocodeScript newScript = new ScorocodeScript()
        .setScriptId("sdfsdfdsdsfdf")
        .setScriptName("testscript")
        .setScriptSourceCode("updated source code");

Script script = new Script();
script.updateScript("assafdfsdf", newScript, new CallbackUpdateScript() {
    @Override
    public void onUpdateScriptSucceed(ScorocodeScript scorocodeScript) {
        //script updated
    }

    @Override
    public void onUpdateScriptFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```

------------------------------------------------------------------------

<a name="ScorocodeScript+deleteScript"></a>

## .deleteScript(scriptToDeleteId, callback)

Метод для удаления скрипта по его id

| Параметр | Тип |  Свойства    | Описание |    Пример значения |
| --- | --- | --- | --- | --- |
| scriptToDeleteId | `String` | Обязательный | Id удаляемого скрипта | "fdsfsdfdsd" |
| callback | `CallbackDeleteScript` | Обязательный | Callback, который будет вызван после выполнения запроса. | см. пример ниже |

**Пример**

```Java
ScorocodeSdk.initWith("db8a1b41b8543397a798a181d9891b4c", "563452bbc611d8106d5da767365897de", "28f06b89b62165c33de55265166d8781", null, null, null, null);

new Script().deleteScript(scriptId, new CallbackDeleteScript() {
    @Override
    public void onScriptDeleted() {
       //script deleted
    }

    @Override
    public void onDeletionFailed(String errorCode, String errorMessage) {
        //error during request
    }
});
```