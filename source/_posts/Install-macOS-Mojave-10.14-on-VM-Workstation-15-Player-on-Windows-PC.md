title: Install macOS Mojave 10.14 on VM Workstation 15 Player on Windows PC
tags:
  - macOS
  - VMware
  - Mojave
date: 2019-06-13 22:37:00
---
Not being able to connect to an iOS device made me go to VMware, and then it worked! VMware Workstation Player is free for personal, non-commercial use.

<!-- more -->

1. Download [VMware Workstation Player](https://www.vmware.com/products/workstation-player.html)

2. Download [macOS Mojave 10.14.4 APFS by Techsviewer.rar](https://drive.google.com/drive/folders/1fygnTmfvRDLg_V3naDIa1Ko-EQc1rVBV?usp=sharing)

3. Download [Patch Tool.rar](https://drive.google.com/drive/folders/1fygnTmfvRDLg_V3naDIa1Ko-EQc1rVBV?usp=sharing)

4. Run win-install.cmd in Patch Tool as administractor

4. Install VMware and open

5. Create Virtual Machine
![](/images/macOS/post-images/1560436901048.PNG)
![](/images/macOS/post-images/1560436850655.PNG)
![](/images/macOS/post-images/1560436854371.PNG)
![](/images/macOS/post-images/1560436857543.PNG)

6. Edit Settings
![](/images/macOS/post-images/1560436860640.PNG)
![](/images/macOS/post-images/1560436863450.PNG)
![](/images/macOS/post-images/1560436866973.PNG)

7. Rmove Hard Disk and add the new one with downloaded vmdk file
![](/images/macOS/post-images/1560436871479.PNG)
![](/images/macOS/post-images/1560436876217.PNG)
![](/images/macOS/post-images/1560436881119.PNG)

8. I found changing USB compatiblity to 2.0 (and connect your iPhone to a USB 2.0 port can help macOS recognize your iPhone)
![](/images/macOS/post-images/1560436884514.PNG)

7. Play Vrtual Machine
![](/images/macOS/post-images/1560437656524.PNG)
----------

Reference:


*- [https://techsviewer.com/install-macos-mojave-vmware-windows/](https://techsviewer.com/install-macos-mojave-vmware-windows/)*

*- [Using VMware Workstation Player for Windows](https://docs.vmware.com/en/VMware-Workstation-Player-for-Windows/15.0/com.vmware.player.win.using.doc/GUID-B8509247-258C-4B11-8637-5DABACEA4965.html)*

