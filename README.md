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
- install yay for AUR access
```
git clone https://aur.archlinux.org/yay-bin.git
cd yay-bin
git checkout 96f90180a3cf72673b1769c23e2c74edb0293a9f
makepkg -si
```
- 1Password (GPG key: 3FEF9748469ADBE15DA7CA80AC2D62742012EA22 (13/02/2025))
```
curl -sS https://downloads.1password.com/linux/keys/1password.asc | gpg --import
git clone https://aur.archlinux.org/1password.git
cd 1password
makepkg -si
```
- Need gnome keyring for GitHub Desktop
```
sudo pacman -S gnome-keyring
sudo pacman -S seahorse
```
- Real version of VSCode because the flatpak doesn't let me enable themes with awesome ridiculous custom CSS animations.
- Also set self as owner to run it as admin so the custom CSS can be enabled.
- Need to repeat both these commands for each update.
```
yay -S visual-studio-code-bin
sudo chown -R $(whoami) /opt/visual-studio-code
```
- SDKs
```
sudo pacman -S dotnet-sdk  
```
- Re-enable read only mode
```
sudo steamos-readonly enable  
```
