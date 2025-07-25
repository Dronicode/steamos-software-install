## WIP until I've tested it a few times to make sure it works consistently.

Some things will fail to install with errors like 

```
# runtime/cgo
In file included from /usr/include/errno.h:28,
                 from cgo-gcc-prolog:32:
/usr/include/bits/errno.h:26:11: fatal error: linux/errno.h: No such file or directory
   26 | # include <linux/errno.h>
      |           ^~~~~~~~~~~~~~~
compilation terminated.


# runtime/cgo
In file included from /usr/include/bits/errno.h:26,
                 from /usr/include/errno.h:28,
                 from cgo-gcc-prolog:32:
/usr/include/linux/errno.h:5:10: fatal error: uapi/linux/errno.h: No such file or directory
    5 | #include <uapi/linux/errno.h>
```

This is because SteamOS is missing key headers.  
Check the kernel version with 
```uname -r```
Then check the current headers with
```sudo pacman -Ss neptune | grep headers```
Expect to see something like 6.11.11-valve19-1-neptune-611-g88b36d49a5e3 in both. If there is no match, get the correct header file. Either install it with this script but with the corregt name,
```
sudo pacman -U https://steamdeck-packages.steamos.cloud/archlinux-mirror/jupiter-3.7/os/x86_64/linux-neptune-611-headers-6.11.11.valve19-1-x86_64.pkg.tar.zst
```
or go to https://steamdeck-packages.steamos.cloud/archlinux-mirror/jupiter-main/os/x86_64/ to find and download the file, eg linux-neptune-611-headers-6.11.11.valve19-1-x86_64.pkg.tar.zst then install it with 
```
 sudo pacman -Q linux-neptune-611-headers-6.11.11.valve19-1-x86_64.pkg.tar.zst
```
symlinking will then be needed.
```
sudo ln -s /usr/lib/modules/$(uname -r)/build/include/linux /usr/include/linux
sudo mkdir -p /usr/include/linux/uapi
sudo ln -s /usr/lib/modules/$(uname -r)/build/include/uapi/linux/* /usr/include/linux/uapi/
```
