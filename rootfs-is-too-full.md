- Check the pkg caches
```
sudo du -sh /var/cache/pacman/pkg .cache/yay 
```
- Drop unrequired dependencies
```
sudo pacman -Rs $(pacman -Qdtq)
```
- Clear the caches. Using yay will work for both the AUR and pacman. 'cc' is more aggressive than just 'c' but with so little space, desperate measures are needed.
```
yay -Scc
```
- Check the cache again. Probably this was enough.
