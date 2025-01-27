# steamos-software-install

SteamOS is read-only by default and anything installed by package managers is wiped by OS updates, so here I'll record all the commands used so I can remember and run them again when needed. Probably I'll turn it into a bash script eventually.  

  
- Disable read only mode to enable sw installs using pacman
```
sudo steamos-readonly disable  
```
- Update the key so the latest GPG signatures are recognized
```
sudo pacman-key --init  
sudo pacman-key --populate archlinux  
sudo pacman-key --populate holo  
```
- Install stuff

-- Dev tools
```
sudo pacman -S dotnet-sdk  
```
-- Needed for GitHub Desktop
```
sudo pacman -S gnome-keyring
```
- Re-enable read only mode
```
sudo steamos-readonly enable  
```
