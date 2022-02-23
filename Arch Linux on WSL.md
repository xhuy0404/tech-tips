# Arch Linux on WSL Installation Guide  
## Enable WSL/WSL2 on your Windows PC  💻
Just-the-recipes version of : https://docs.microsoft.com/en-us/windows/wsl/install-manual

Make sure you enabled **Virtualization** in your **BIOS** before doing this.  
- Use this command in a terminal app (as administrator) to enable **Windows Subsystem for Linux** feature :  
  `dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`  
  
- Then enable **Virtual Machine Platform** feature :  
  `dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`  
  
- Restart your computer to complete the installation : ```shutdown /r```  
  
- Then update/install WSL : `wsl --update`  
  
- Complete the installation process : `wsl --shutdown`    

## Install Arch 💾
![image](https://user-images.githubusercontent.com/85998116/154880089-c00634f4-0cd8-412d-aeed-fdc417fb6dca.png)  
> Fastfetch, a "useful" tool on Linux ...  
### References  
- [Arch Linux introduction page](https://wiki.archlinux.org/title/Arch_Linux)  
- [Original guide](https://gist.github.com/ld100/3376435a4bb62ca0906b0cff9de4f94b)  

### Basic Installation  
- Download [ArchWSL installer zip](https://github.com/yuk7/ArchWSL/releases/latest) , pick a folder (For example, `C:\Arch`) for Arch Linux and extract **Arch.zip** in that folder.  
  
- Then run **Arch.exe** to start the installtion process : `C:\Arch\Arch.exe`

- Then start Arch in WSL by : `wsl -d Arch` or just `wsl` if Arch is your default/first WSL distro.  
  
### Initialize package manager  
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

### Create a user  
- Uncomment `%wheel ALL=(ALL:ALL) ALL` and `%sudo ALL=(ALL) ALL` in `/etc/sudoers` :  
  ```  
  sed '82s/^#//' -i /etc/sudoers  
  sed '88s/^#//' -i /etc/sudoers  
  ```  
  
- Add a new admin user (replace **xhuy0** with your username) : `useradd -m -G wheel xhuy0`  
  
- Set the password for that user : `passwd xhuy0`  
  
- Set default user : `echo -e "[user]\ndefault = xhuy0\n" > /etc/wsl.conf`  

### Finalize  
- Open a Windows shell : `cmd.exe`  
  
- Shutdown the WSL : `wsl --shutdown`  
  
Now, if Arch is your first/default WSL distro, it will launch everytime you start WSL. 
Otherwise, you can use `wsl -d Arch` to start it or `wsl -s Arch` to set it to default WSL distro.

**Welcome to Arch Linux !**  

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

## Zsh with Powerlevel10k (Optional)  ✨  
![image](https://user-images.githubusercontent.com/85998116/154880423-6fea82e4-9dd4-4fe7-9e45-1feec2073916.png)  
> Zsh with Oh-my-zsh & Powerlevelk
### Install [Zsh](https://zsh.sourceforge.io/)   
- On Arch Linux : ```sudo pacman -S zsh```  

- On Gentoo Linux : ```emerge --ask app-shells/zsh```  

- Start Zsh : ```zsh```  

- Change your shell to Zsh : ```chsh -s /bin/zsh```  

### Install [Oh-my-zsh](https://ohmyz.sh/)  
- `cd $HOME` (the place you want to install oh-my-zsh)  
- `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`  

### Install Oh-my-zsh's plugins (Optional)  
- `cd $HOME` (or the directory of /oh-my-zsh)  
  
- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) :  
  ```
  git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions  
  ```

- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) :  
  ```
  git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
  ```
  
Then add them to `~/.zshrc` at the line `plugins=(...)`  
For example : `plugins=(git zsh-autosuggestions zsh-syntax-highlighting)`  

### Install [Powerlevel10k](https://github.com/romkatv/powerlevel10k)  
- `cd $HOME` (or the directory of /oh-my-zsh)  
- `git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k`  
- Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`  
- For advanced settings : `nano ~/.p10k.zsh`  
