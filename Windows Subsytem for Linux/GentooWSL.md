# Gentoo Linux on WSL installation guide (Still Compiling)
## References :  
- [Gentoo Linux introduction page](https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/About#Welcome)  
- [Original guide](https://wiki.gentoo.org/wiki/Gentoo_in_WSL)

## Basic Installation
- Download a stage 3 tarball [here](https://www.gentoo.org/downloads/) , pick a folder (For example, `C:\Gentoo`) for Gentoo Linux and extract the tarball file to that folder.
- Use this command to import Gentoo into WSL :  
  `wsl --import C:\Gentoo C:\Gentoo\stage3 ... .tar`  
