# steamos-software-install

SteamOS is read-only by default and anything installed by package managers is wiped by OS updates, so here I'll record all the commands used so I can remember and run them again when needed. Probably I'll turn it into a bash script eventually.  

When the system updates and removes the packages, some leave behind files which will conflict with attempts to reinstall them. This can be worked around with the flag --overwrite "*". This is noted beside the relevant commands.
  
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
- Just in case
```
sudo pacman -S --needed git base-devel plymouth
```
- install yay for AUR access (for a reinstall after OS update, a reboot may be necessary after this step to proceed further.)
```
git clone https://aur.archlinux.org/yay-bin.git
cd yay-bin
makepkg -si
```
- Check for anything that needs updates
```
yay -Syu
```
- Probably at this point go through linux-headers.md in case that needs doing (again).
- 1Password
```
yay -S 1password
yay -S 1password-cli
```
``` 
yay -S 1password --overwrite "*"
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
sudo pacman -S aspnet-sdk  
```
- Golang
```
sudo pacman -S go gopls go-tools
```
- Real version of VSCode because the flatpak doesn't let me enable themes with awesome ridiculous custom CSS animations.
- Also set self as owner to run it as admin so the custom CSS can be enabled.
- Need to repeat both these commands for each update.
```
yay -S visual-studio-code-bin
sudo chown -R $(whoami) /opt/visual-studio-code
```
```
yay -S visual-studio-code-bin --overwrite "*"
sudo chown -R $(whoami) /opt/visual-studio-code
```
- Don't use flatpak Discord, the RPC is busted.
```
sudo pacman -S discord
```
```
sudo pacman -S discord --overwrite "*"
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
