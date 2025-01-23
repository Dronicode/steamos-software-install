# steamos-software-install

SteamOS is read-only by default and anything installed by package managers is wiped by OS updates, so here I'll record all the commands used so I can remember and run them again when needed. Probably I'll turn it into a bash script eventually.

sudo steamos-readonly disable

sudo pacman-key --init
sudo pacman-key --populate archlinux
sudo pacman-key --populate holo

sudo pacman -S dotnet-sdk

sudo steamos-readonly enable
