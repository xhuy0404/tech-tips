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
- [Arch Linux](https://github.com/xhuy0404/tech-tips/edit/main/Windows%20Subsystem%20for%20Linux.md#option-1---arch-linux-installation-guide) : Lightweight & Up-to-date !   
- [Gentoo Linux](https://github.com/xhuy0404/tech-tips/edit/main/Windows%20Subsystem%20for%20Linux.md#option-2---gentoo-linux-installation-guide) : Even more lightweight than Arch ! But you'll need a good CPU and really MUCH time for compiling packages yourself...  
  
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
> Tip : You can use this command to clear the terminal screen : ```clear```  
  
- Then run ```pacman -Syyu``` to update all packages to the latest versions  
> When asked question on hwids, choose Yes (default option)  
### Create a user  
- Uncomment ```%wheel ALL=(ALL:ALL) ALL``` and ```%sudo ALL=(ALL) ALL``` in ```/etc/sudoers``` :  
  ```  
  sed '82s/^#//' -i /etc/sudoers  
  sed '88s/^#//' -i /etc/sudoers  
  ```  
  
- Add a new admin user (replace **xhuy0** with your username) : ```useradd -m -G wheel xhuy0```  
  
- Set the password for that user : ```passwd xhuy0```  
  
- Set default user : ```echo -e "[user]\ndefault=xhuy0\n" > /etc/wsl.conf```  

### Finalize  
- Open a Windows shell : ```cmd.exe```  
  
- Shutdown the WSL : ```wsl --shutdown```  
  
Now, if Arch is your first/default WSL distro, it will launch everytime you start WSL. Otherwise, you can use ```wsl -d Arch``` to start it.

**Welcome to Arch Linux !**  

### Install AUR Helper - yay (Optional)
[Original guide](https://www.tecmint.com/install-yay-aur-helper-in-arch-linux-and-manjaro/)  
- ```sudo pacman -S base-devel git openssh go```  
> When asked question on fakeroot and fakeroot-tcp, choose No (default option)  
- Then run the following commands :  
  ```  
  cd $HOME  
  git clone https://aur.archlinux.org/yay-git.git  
  cd yay-git  
  makepkg -si  
  rm -rf ~/yay-git  
  ```  
  
### Install ZSH & Powerlevel10k (Optional)  
- Install [Zsh](https://wiki.archlinux.org/title/zsh) : ```sudo pacman -S zsh```  

- Start Zsh : ```zsh```  

- Change your shell to Zsh : ```chsh -s /bin/zsh```  

- Install [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) :  
  ```
  cd $HOME  
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"  
  ```  
  
- Install [powerlevel10k](https://github.com/romkatv/powerlevel10k#readme) :  
  ```
  cd $HOME  
  git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k  
  ```  
  
  
Bonus
  
## Option 2 - Gentoo Linux installation guide (Still Compiling)
### References :  
- [Gentoo Linux introduction page](https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/About#Welcome)  
- [Original guide](https://wiki.gentoo.org/wiki/Gentoo_in_WSL)
