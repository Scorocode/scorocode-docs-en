This Java SDK provides access to the Scorocode platform which allows you to create java-based applications, e.g. for Andorid. Details can be found on our website: https://scorocode.ru 


## SDK Integration

Scorocode Java SDK distribution pack can be found in the repository <https://github.com/Scorocode/scorocode-sdk-java>

You can integrate this SDK with your project using Gradle. To do this, add the following dependencies:

```
dependencies {
   compile 'ru.prof-itgroup:scorocode_sdk:1.0.15-beta'
}
```

Make sure that Gradle is looking for libraries in the `jcenter` repository, recommended by Goolge (it includes `maven` libraries):

```java
repositories {
   jcenter()
}
```
