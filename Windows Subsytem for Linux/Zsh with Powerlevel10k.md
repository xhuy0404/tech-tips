# Zsh + Powerlevel10k Installation guide
## Install [Zsh](https://zsh.sourceforge.io/)   
- Arch Linux : ```sudo pacman -S zsh```  

- Gentoo Linux : ```emerge --ask app-shells/zsh```  

- Start Zsh : ```zsh```  

- Change your shell to Zsh : ```chsh -s /bin/zsh```  

## Install [Oh-my-zsh](https://ohmyz.sh/)  
  ```
  cd $HOME  
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"  
  ```  

## Install Oh-my-zsh's plugins (Optional)
  
## Install [Powerlevel10k](https://github.com/romkatv/powerlevel10k#readme)  
  Make sure the default font of your Terminal app (I'm using [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701)) is a [nerd font](https://www.nerdfonts.com/font-downloads).  
  ```  
  cd $HOME  
  git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k  
  ```  
  Then set ```ZSH_THEME="powerlevel10k/powerlevel10k"``` in ```~/.zshrc```  
  
  ## 
