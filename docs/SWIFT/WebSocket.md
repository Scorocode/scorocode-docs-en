<a name="WebSocket"></a>

## WebSocket

To use WebSocket in your project, you can use the [daltoniam/Starscream](https://github.com/daltoniam/Starscream) library with the following url scheme when initializing WebSocket:

```SWIFT
    var socket = WebSocket(url: NSURL(string: "wss://wss.scorocode.ru/{appID}/{wsKey}/{chanName}")!)
    socket.connect()
```
where

| Parameter | Type | Properties | Description | Value example |
| --- | --- | --- | --- | --- | 
| appID | <code>String</code> | Mandatory | The appld key of your application | a3d04e75e157b2f7ae20c2fce02f63d6 |
| wsKey | <code>String</code> | Mandatory | The websocketKey of your application | 563452bbc611d8106d5da767365897de |
| chanName | <code>String</code> | Mandatory | Arbitrary channel name  | chatroom |

**Example**

```SWIFT
    var socket = WebSocket(url: NSURL(string: "wss://wss.scorocode.ru/a3d04e75e157b2f7ae20c2fce02f63d6/563452bbc611d8106d5da767365897de/chatroom")!)
    socket.connect()
```

### Connection of the Starscream library

**See Readme.md of the [daltoniam/Starscream](https://github.com/daltoniam/Starscream) repository for details of the Starscream library connection.**

[Carthage](https://github.com/Carthage/Carthage) must be installed to connect the library to your project.

 
Create the "Cartfile" file in the Xcode project root or modify an existing "Cartfile" by writing the following string in it:

```SWIFT
github "daltoniam/Starscream"
```

Close the project in xcode, start in the console:

```SWIFT
carthage update --platform iOS,Mac
```

Re-open the project in Xcode. To Target -> General -> Linked Frameworks and Libraries from <Project folder> -> Carthage -> Build -> iOS drag and drop 1 file:

```SWIFT
Starscream.framework
```

To Target -> Build Phases, add New Run Script Phase:

```SWIFT
/usr/local/bin/carthage copy-frameworks
```

and Input File:

```SWIFT
$(SRCROOT)/Carthage/Build/iOS/Starscream.framework
```

### Example of Starscream library usage

**See Readme.md of the [daltoniam/Starscream](https://github.com/daltoniam/Starscream) repository for details of the Starscream library connection.**

```SWIFT
import UIKit
import Starscream

class ViewController: UIViewController {
    
    var socket: WebSocket!

    @IBOutlet private weak var textField: UITextField!
    @IBOutlet private weak var textView: UITextView!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
    }

    @IBAction private func connectTapped() {
        
        socket = WebSocket(url: NSURL(string: "wss://wss.scorocode.ru/a3d04e75e157b2f7ae20c2fce02f63d6/563452bbc611d8106d5da767365897de/chatroom")!)
        socket.connect()
        
        socket.onConnect = {
            print("connected")
        }
        
        socket.onText = {
            text in
            print(text)
            self.textView.text = self.textView.text + "\n\(text)"
        }
        
        socket.onData = {
            data in
            print(data)
        }
        
    }
    
    @IBAction private func disconnectTapped() {
        
    }
    
    @IBAction private func sendTapped() {
        socket.writeString(textField.text!)
    }
    

}
```