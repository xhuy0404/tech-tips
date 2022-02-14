# Arch Linux on WSL installation guide
## References  
- [Arch Linux introduction page](https://wiki.archlinux.org/title/Arch_Linux)  
- [Original guide](https://gist.github.com/ld100/3376435a4bb62ca0906b0cff9de4f94b)  

## Basic Installation  
- Download [ArchWSL installer zip](https://github.com/yuk7/ArchWSL/releases/latest) , pick a folder (For example, ```C:\Arch```) for Arch Linux and extract **Arch.zip** in that folder.  
  
- Then run **Arch.exe** to start the installtion process : ```C:\Arch\Arch.exe```

- Then start Arch in WSL by : ```wsl -d Arch``` or just ```wsl``` if Arch is your default/first WSL distro.  
  
## Initialize package manager  
- Refresh Pacman GPG keys (It will take a while) :    
  ```
  pacman-key --init
  pacman-key --populate
  pacman-key --refresh-keys
  pacman -Sy archlinux-keyring --noconfirm  
  ```
> Tip : You can use this command to clear the terminal screen : ```clear```  
  
- Then run `pacman -Syyu` to update all packages to the latest versions  
> When asked question on hwids, choose Yes (default option)  

- Install **base-devel** group (and other packages if you want) : `pacman -S base-devel git openssh wget`  
> When asked question on fakeroot, choose No  

## Create a user  
- Uncomment `%wheel ALL=(ALL:ALL) ALL` and `%sudo ALL=(ALL) ALL` in `/etc/sudoers` :  
  ```  
  sed '82s/^#//' -i /etc/sudoers  
  sed '88s/^#//' -i /etc/sudoers  
  ```  
  
- Add a new admin user (replace **xhuy0** with your username) : `useradd -m -G wheel xhuy0`  
  
- Set the password for that user : `passwd xhuy0`  
  
- Set default user : `echo -e "[user]\ndefault=xhuy0\n" > /etc/wsl.conf`  

## Finalize  
- Open a Windows shell : `cmd.exe`  
  
- Shutdown the WSL : `wsl --shutdown`  
  
Now, if Arch is your first/default WSL distro, it will launch everytime you start WSL. 
Otherwise, you can use `wsl -d Arch` to start it or `wsl -s Arch` to set it to default WSL distro.

**Welcome to Arch Linux !**  
## Extras
### Install AUR Helper - yay (Optional)
[Original guide](https://www.tecmint.com/install-yay-aur-helper-in-arch-linux-and-manjaro/)  
- Then run the following commands :  
  ```  
  cd $HOME  
  git clone https://aur.archlinux.org/yay-git.git  
  cd yay-git  
  makepkg -si  
  ```  
- Remove the leftovers : `rm -rf ~/yay-git`  
  
### [Install ZSH & Powerlevel10k](https://github.com/xhuy0404/tech-tips/blob/main/Windows%20Subsytem%20for%20Linux/Zsh%20with%20Powerlevel10k.md) (Optional)  

