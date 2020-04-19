title: Install macOS Mojave 10.14 on VirtualBox on Windows PC
author: Jun Hu
tags:
  - macOS
  - Mojave
  - VirtualBox

date: 2019-06-08 00:52:00
---
*(I am not able to connect iOS devices onto a macOS installed on VirtualBox as instructed below. So unless you like VirtualBox a lot and do not expect connecting an iOS device, I'd recomend you go to [this post](https://da0mao.github.io/post/install-macos-mojave-1014-on-vm-workstation-15-player-on-windows-pc/) instead.)*

I've successfully installed macOS Mojave 10.14.4 on VirtualBox on Windows recently. Here is how...

<!-- more -->

1. Download **VirtualBox** and **Oracle VM VirtualBox Extension Pack** from [here](https://www.virtualbox.org/)
![](/images/macOS/1559983226076.PNG)

2. Download [macOS Mojave 10.14.4 HFS Image by Techsviewer.rar](https://drive.google.com/drive/folders/1fygnTmfvRDLg_V3naDIa1Ko-EQc1rVBV?usp=sharing)

3. Install VirtualBox and open

4. Create Virtual Machine
![](/images/macOS/1559989661172.PNG)

5. Edit Settings
![](/images/macOS/1559989818630.PNG)
![](/images/macOS/1559989822146.PNG)
![](/images/macOS/1559989824582.PNG)
![](/images/macOS/1559989826587.PNG)
![](/images/macOS/1559990295754.PNG)

5. Use Windows command line (CMD) to add code to VirtualBox, update the VirtualBox installation path *"C:\Program Files\Oracle\VirtualBox"* and the virtual machine name *"macOS"* as necessary
```cmd
cd "C:\Program Files\Oracle\VirtualBox\"
VBoxManage.exe modifyvm "macOS" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
VBoxManage setextradata "macOS" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3"
VBoxManage setextradata "macOS" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
VBoxManage setextradata "macOS" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"
VBoxManage setextradata "macOS" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
VBoxManage setextradata "macOS" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
VBoxManage setextradata "macOS" VBoxInternal2/EfiGraphicsResolution 1920x1080
```

6. Start your Vrtual Machine
![](/images/macOS/1559990652460.PNG)
----------



Reference:


*- [https://techsviewer.com/install-macos-10-14-mojave-virtualbox-windows/](https://techsviewer.com/install-macos-10-14-mojave-virtualbox-windows/)*
