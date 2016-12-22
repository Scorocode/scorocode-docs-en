SDK provides access to the Scorocode platform for creating java-based applications. Details can be found on our website: https://scorocode.ru 


SDK предоставляет доступ к платформе Scorocode для построения приложений, основанных на Java / Android.Подробности на нашем сайте: https://scorocode.ru

## SDK integration

Scorocode Java SDK distribution pack can be found in the repository <https://github.com/Scorocode/scorocode-sdk-java>

You can integrate SDK with your project using Gradle by adding following dependencies:

```
dependencies {
   compile 'ru.prof-itgroup:scorocode_sdk:1.0.15-beta'
}
```

Make sure, that gradle looking for a libraries in the `jcenter` repository, that recommended by Goolge (and includes `maven` libraries):

```java
repositories {
   jcenter()
}
```
