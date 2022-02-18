# Zsh + Powerlevel10k Installation guide
## Install [Zsh](https://zsh.sourceforge.io/)   
- On Arch Linux : ```sudo pacman -S zsh```  

- On Gentoo Linux : ```emerge --ask app-shells/zsh```  

- Start Zsh : ```zsh```  

- Change your shell to Zsh : ```chsh -s /bin/zsh```  

## Install [Oh-my-zsh](https://ohmyz.sh/)  
- `cd $HOME` (the place you want to install oh-my-zsh)  
- `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`  

## Install Oh-my-zsh's plugins (Optional)
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
  
## Install [Powerlevel10k](https://github.com/romkatv/powerlevel10k#readme)  
  Make sure the default font of your Terminal app (I'm using [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701)) is a [nerd font](https://www.nerdfonts.com/font-downloads).  
  
- `cd $HOME` (or the directory of /oh-my-zsh)  
- `git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k`  
  
Then set ```ZSH_THEME="powerlevel10k/powerlevel10k"``` in ```~/.zshrc```  

## Customize Powerlevel10k

  
