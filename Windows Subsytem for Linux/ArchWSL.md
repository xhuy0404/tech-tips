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
  
- Then run ```pacman -Syyu``` to update all packages to the latest versions  
> When asked question on hwids, choose Yes (default option)  
## Create a user  
- Uncomment ```%wheel ALL=(ALL:ALL) ALL``` and ```%sudo ALL=(ALL) ALL``` in ```/etc/sudoers``` :  
  ```  
  sed '82s/^#//' -i /etc/sudoers  
  sed '88s/^#//' -i /etc/sudoers  
  ```  
  
- Add a new admin user (replace **xhuy0** with your username) : ```useradd -m -G wheel xhuy0```  
  
- Set the password for that user : ```passwd xhuy0```  
  
- Set default user : ```echo -e "[user]\ndefault=xhuy0\n" > /etc/wsl.conf```  

## Finalize  
- Install some useful packages : ```pacman -S base-devel git openssh wget```  

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
  
- Install [Powerlevel10k](https://github.com/romkatv/powerlevel10k#readme) :  
  Make sure the default font of your Terminal app (I'm using [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701)) is a [nerd font](https://www.nerdfonts.com/font-downloads).  
  ```  
  cd $HOME  
  git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k  
  ```
  Then set ```ZSH_THEME="powerlevel10k/powerlevel10k"``` in ```~/.zshrc```  
  
Bonus
