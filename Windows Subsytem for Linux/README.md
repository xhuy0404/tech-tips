# I. Enable WSL/WSL2 on your Windows PC 💿
Just-the-recipes version of : https://docs.microsoft.com/en-us/windows/wsl/install-manual

Make sure you enabled **Virtualization** in your **BIOS** before doing this.  
- Use this command in a terminal app (as administrator) to enable **Windows Subsystem for Linux** feature :  
  ```dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart```  
  
- Then enable **Virtual Machine Platform** feature :  
  ```dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart```  
  
- Restart your computer to complete the installation : ```shutdown /r```  
  
- Then update/install WSL : ```wsl --update```  
  
- Complete the installation process : ```wsl --shutdown```    

# II. Install a Linux distro 🐧
There are [some Linux distros that available on Microsoft Store](https://docs.microsoft.com/en-us/windows/wsl/install-manual#step-6---install-your-linux-distribution-of-choice)  
But I like somthing special, I went with :   
- [Arch Linux](https://github.com/xhuy0404/tech-tips/blob/main/Windows%20Subsytem%20for%20Linux/ArchWSL.md) : Lightweight & Up-to-date !   
- [Gentoo Linux](https://github.com/xhuy0404/tech-tips/blob/main/Windows%20Subsytem%20for%20Linux/GentooWSL.md) : Even more lightweight than Arch ! But you'll need a good CPU and really MUCH time for compiling packages yourself...  

# III. Extras
- [Install Zsh & Powerlevel10k](https://github.com/xhuy0404/tech-tips/blob/main/Windows%20Subsytem%20for%20Linux/Zsh%20with%20Powerlevel10k.md)  
