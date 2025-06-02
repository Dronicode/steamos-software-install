# steamos-software-install

SteamOS is read-only by default and anything installed by package managers is wiped by OS updates, so here I'll record all the commands used so I can remember and run them again when needed. Probably I'll turn it into a bash script eventually.  

Note from first update, it seems like anything installed with makepkg cannot simply be reinstalled the same way. It cannot overwrite or force itself over the residual files from the previous installation.
--overwrite "*"
  
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
- install yay for AUR access (for a reinstall after OS update, a reboot may be necessary after this step to proceed further.)
```
git clone https://aur.archlinux.org/yay-bin.git
cd yay-bin
git checkout 96f90180a3cf72673b1769c23e2c74edb0293a9f
makepkg -si
```
- 1Password
```
yay -S 1password
yay -S 1password-cli
```
- Need gnome keyring for GitHub Desktop
```
sudo pacman -S gnome-keyring
sudo pacman -S seahorse
```
- Dotnet
```
sudo pacman -S dotnet-sdk  
sudo pacman -S dotnet-runtime  
sudo pacman -S aspnet-runtime  
```
- Real version of VSCode because the flatpak doesn't let me enable themes with awesome ridiculous custom CSS animations.
- Also set self as owner to run it as admin so the custom CSS can be enabled.
- Need to repeat both these commands for each update.
```
yay -S visual-studio-code-bin
sudo chown -R $(whoami) /opt/visual-studio-code
```
- Don't use flatpak Discord, the RPC is busted.
```
sudo pacman -S discord
```
- Add this to ~/.config/discord/settings.json
```
{
  "SKIP_HOST_UPDATE": true
}
```
- Also add Vencord
```
sh -c "$(curl -sS https://raw.githubusercontent.com/Vendicated/VencordInstaller/main/install.sh)"
```
- Re-enable read only mode
```
sudo steamos-readonly enable  
```
