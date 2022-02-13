# Enable WSL/WSL2 on your Windows PC
Just-the-recipes version of : https://docs.microsoft.com/en-us/windows/wsl/install-manual

Make sure you enabled **Virtualization** in your BIOS before doing this.  

- Step 1 : Open a terminal app as administrator  

- Step 2 : Use this command to enable **WSL** feature  
  ```dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart```
  
- Step 3 : Then use this command to enable **Virtual Machine** feature  
  ```dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart```
  
- Step 4 : Restart your computer to complete the installation  

- Step 5 : Then use this command (as administrator) to update/install WSL  
  ```wsl --update``` 

We've just completed the Linux kernel installion process !  

# Install a Linux distro  
There are [some Linux distros that available on Microsoft Store](https://docs.microsoft.com/en-us/windows/wsl/install-manual#step-6---install-your-linux-distribution-of-choice)  
But I like somthing special, I went with :   
- [Arch Linux](https://github.com/xhuy0404/tech-tips/edit/main/Windows%20Subsystem%20for%20Linux.md#option-1-arch-linux-installation-guide) : Lightweight & Up-to-date !   
- [Gentoo Linux](https://github.com/xhuy0404/tech-tips/edit/main/Windows%20Subsystem%20for%20Linux.md#option-2-gentoo-linux-installation-guide) : Even more lightweight than Arch ! But you'll need a good CPU and time for compiling packages yourself.

  
## Option 1 - Arch Linux installation guide  
References :  
- [Arch Linux introduction page](https://wiki.archlinux.org/title/Arch_Linux)  
- [Original guide](https://gist.github.com/ld100/3376435a4bb62ca0906b0cff9de4f94b)  

Instruction :  
- Step 1 : Download [ArchWSL installer zip](https://github.com/yuk7/ArchWSL/releases/latest) (Arch.zip)
  

## Option 2 - Gentoo Linux installation guide  
[Introduction](https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/About#Welcome)  
