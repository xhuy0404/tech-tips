**Linux** is a great OS for programming but as a student, I need some Windows's softwares (For example : Microsoft Office/Microsoft 365).  
There are other methods for this problem such as : Dual boot, Virtual machine, MSYS2, ...  
But in my case, I just need its tool, not the whole GUI so WSL is the best solution : Lightweight & Compatible.  

# Enable WSL/WSL2 on your Windows PC
Just a shorter version of : https://docs.microsoft.com/en-us/windows/wsl/install-manual

- Step 1: Open a terminal app as administrator  

- Step 2: Use this command to enable **WSL** feature  
  ```dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart```
  
- Step 3: Then use this command to enable **Virtual Machine** feature  
  ```dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart```
  
- Step 4: Restart your computer to complete the installation  

We've just completed the Linux kernel installion process !  

# Install a Linux distro  
I'm not here to guide you to install Ubuntu, you can download it on **Microsoft Store**  
We're going with something more advanced. Choose one of these two (or both):  
- [Arch Linux](https://github.com/xhuy0404/tech-tips/edit/main/Windows%20Subsystem%20for%20Linux.md#option-1-arch-linux-installation-guide): Up-to-date, reliable and lightweight.  
- [Gentoo Linux](https://github.com/xhuy0404/tech-tips/edit/main/Windows%20Subsystem%20for%20Linux.md#option-2-gentoo-linux-installation-guide): Beautiful, elegant, ~~better~~ than Arch. But it REALLY takes pretty much time for installing and updating packages.    
  
### Option 1: Arch Linux installation guide  
Just 


### Option 2: Gentoo Linux installation guide  


# Customize your workspace
