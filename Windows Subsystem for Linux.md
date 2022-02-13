# I. Enable WSL/WSL2 on your Windows PC 💿
Just-the-recipes version of : https://docs.microsoft.com/en-us/windows/wsl/install-manual

Make sure you enabled **Virtualization** in your BIOS before doing this.  
- Use this command to enable **WSL** feature (as administrator) :  
  ```dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart```  
  
- Then enable **Virtual Machine** feature :  
  ```dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart```  
  
- Restart your computer to complete the installation : ```shutdown /r```  
  
- Then update/install WSL : ```wsl --update```  
  
- Complete the installation process : ```wsl --shutdown```    

# II. Install a Linux distro 🐧
There are [some Linux distros that available on Microsoft Store](https://docs.microsoft.com/en-us/windows/wsl/install-manual#step-6---install-your-linux-distribution-of-choice)  
But I like somthing special, I went with :   
- [Arch Linux](https://github.com/xhuy0404/tech-tips/edit/main/Windows%20Subsystem%20for%20Linux.md#option-1---arch-linux-installation-guide) : Lightweight & Up-to-date !   
- [Gentoo Linux](https://github.com/xhuy0404/tech-tips/edit/main/Windows%20Subsystem%20for%20Linux.md#option-2---gentoo-linux-installation-guide) : Even more lightweight than Arch ! But you'll need a good CPU and time for compiling packages yourself...  
  
## Option 1 - Arch Linux installation guide  
### References  
- [Arch Linux introduction page](https://wiki.archlinux.org/title/Arch_Linux)  
- [Original guide](https://gist.github.com/ld100/3376435a4bb62ca0906b0cff9de4f94b)  

### Basic Installation  
- Download [ArchWSL installer zip](https://github.com/yuk7/ArchWSL/releases/latest) , pick a folder (For example, ```C:\Arch```) for Arch Linux and extract **Arch.zip** in that folder.  
  
- Then run **Arch.exe** to start the installtion process : ```C:\Arch\Arch.exe```

- Then start Arch in WSL by : ```wsl -d Arch``` or just ```wsl``` if Arch is your default/first WSL distro.  
  
### Initialize package manager  
- Refresh Pacman GPG keys (It will take a while) :  
  ```  
  pacman-key --init  
  pacman-key --populate  
  pacman-key --refresh-keys  
  pacman -Sy archlinux-keyring --noconfirm  
  ```  
> Tip : You can use this command to clear the screen : ```clear```  
  
- Then run ```pacman -Syyu``` to update all packages to the latest versions  
  
### Create a user  
- Add a sudo group: ```groupadd sudo```  
  
- Uncomment ```%wheel ALL=(ALL) NOPASSWD: ALL``` and ```%sudo ALL=(ALL) ALL``` in ```/etc/sudoers``` :  
  ```
  sed "/NOPASSWD/s/^#//g" -i /etc/sudoers  
  sed "/%sudo/s/^#//g" -i /etc/sudoers  
  ```  
  
- Add a new admin user (replace **xhuy0** with your username) : ```useradd -m -G wheel xhuy0```  
  
- Set the password for that user : ```passwd xhuy0```  
  
- Set default user : ```echo -e "[user]\ndefault=xhuy0\n" > /etc/wsl.conf```  

### Finalize  
- Finalize the installation : ```wsl --shutdown```  
  
Now, if Arch is your fist/default WSL distro, it will launch everytime you start WSL

**Welcome to Arch Linux !**  

## Option 2 - Gentoo Linux installation guide (UNFINISHED)
### References :  
- [Gentoo Linux introduction page](https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/About#Welcome)  
- [Original guide](https://wiki.gentoo.org/wiki/Gentoo_in_WSL)

