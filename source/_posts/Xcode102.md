title: Xcode102
author: Jun Hu
tags:
  - Xcode
  - SwiftUI

date: 2019-06-23 01:41:00
---
Yet another piece of code...

<!-- more -->

```java

import UIKit

class ViewController: UIViewController {

    var imgnumber = 1
    
    @IBOutlet weak var mainview: UIImageView!
    @IBOutlet weak var leftbutton: UIButton!
    @IBOutlet weak var rightbutton: UIButton! 
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    @IBAction func leftbuttontap(_ sender: Any) {
        if imgnumber <= 1 {
            imgnumber = 4
        }
        else {
            imgnumber -= 1
        }
        mainview.image = UIImage(named: "IMG_\(imgnumber)")
    }
    
    @IBAction func rightbuttontap(_ sender: Any) {
        if imgnumber >= 4 {
            imgnumber = 1
        }
        else {
            imgnumber += 1
        }
         mainview.image = UIImage(named: "IMG_\(imgnumber)")
    }
}

```

-