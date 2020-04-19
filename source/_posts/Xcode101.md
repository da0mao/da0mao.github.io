title: Xcode101
author: Jun Hu
tags:
  - Xcode
  - SwiftUI
date: 2019-06-13 20:18:00
---
My first xcode project...

<!-- more -->
```java
import UIKit
import AVFoundation

class ViewController: UIViewController {
    var audioPlayer:AVAudioPlayer?
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    @IBAction func atap(_ sender: Any) {
        let url = Bundle.main.url(forResource: "a", withExtension: "mp3")
        guard url != nil else {
            return
        }
        do {
            audioPlayer = try AVAudioPlayer(contentsOf: url!)
            audioPlayer?.play()
        }
        catch {
            print("error")
        }
    }
    @IBAction func btap(_ sender: Any) {
        let url = Bundle.main.url(forResource: "b", withExtension: "mp3")
        guard url != nil else {
            return
        }
        do {
            audioPlayer = try AVAudioPlayer(contentsOf: url!)
            audioPlayer?.play()
        }
        catch {
            print("error")
        }
    }
    @IBAction func ctap(_ sender: Any) {
        let url = Bundle.main.url(forResource: "c", withExtension: "mp3")
        guard url != nil else {
            return
        }
        do {
            audioPlayer = try AVAudioPlayer(contentsOf: url!)
            audioPlayer?.play()
        }
        catch {
            print("error")
        }
    }
    @IBAction func dtap(_ sender: Any) {
        let url = Bundle.main.url(forResource: "d", withExtension: "mp3")
        guard url != nil else {
            return
        }
        do {
            audioPlayer = try AVAudioPlayer(contentsOf: url!)
            audioPlayer?.play()
        }
        catch {
            print("error")
        }
    }
}
```