## SDK integration

SDK provides access to the Scorocode platform for creating swift-based applications. Details can be found on our website: https://scorocode.ru Scorocode SWIFT SDK distribution pack can be found in the repository (https://github.com/Scorocode/scorocode-sdk-swift)

### Installation
Connecting a library to a project

Install [Carthage](https://github.com/Carthage/Carthage)

Create an application

Create the "Cartfile" file in the project root and write the following lines in it:

```
github "Alamofire/Alamofire" ~> 3.3
github "SwiftyJSON/SwiftyJSON"
github "daltoniam/Starscream"
```

Close the project in Xcode, start in the console:

```
carthage update --platform iOS,Mac
```
Re-open the project in Xcode. To Target -> General -> Linked Frameworks and Libraries from <Project folder> -> Carthage -> Build -> iOS, drag and drop 3 files:

```
Alamofire.framework
SwiftyJSON.framework
Starscream.framework
```  

To Target -> Build Phases, add New Run Script Phase:

Script:

```
/usr/local/bin/carthage copy-frameworks
```
Three Input Files:

```
$(SRCROOT)/Carthage/Build/iOS/Alamofire.framework
```
```
$(SRCROOT)/Carthage/Build/iOS/SwiftyJSON.framework
```
and
```
$(SRCROOT)/Carthage/Build/iOS/Starscream.framework
```

If bridging header is missing, create it with the following contents:

```
#import "BSONSerialization.h"
```

Create a new group in the project (for example, SCLib).

Add three folders to it (BSON, API, Model) from the SCLib project folder retrieved from the repository.