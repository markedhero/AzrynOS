`AzrynOS` is a Linux-based derivative of Gentoo. The primary goal is to 
automate the installation of my own ideal Gentoo setup though the 
current design allows for others to fork or submit PR's should it be
desired. Keep in mind that this project is NOT a replacement for reading
the Gentoo Handbook. Sabayon tries to do this and I don't want to repeat
this line of thinking.

I'm aware that Gentoo is a highly personal system and much of what I've
added may be undesired. Despite this I think that this project may serve
as a subjectively decent example of getting started with Gentoo.


## Warnings
- AzrynOS is not production-ready, proceed with caution.
- You must manually partition and mount your disks.
  - Consult your Gentoo Handbook.


## FAQ
- "How much about Gentoo will I need to know to use AzrynOS?"
  - I would suggest reading the Gentoo Handbook and every file in this
    project before proceeding.
- "How long does this take to install?"
  - About 1 to 4 hours for the minimal install.
    - Most time-consuming packages are GCC 6.4 and Linux.
  - About 4 to 24 hours for the complete installation.
    - Most time-consuming packages are Mesa and Chromium.
- "I keep getting boot failures after installing in a VirtualBox VM?"
  - Remove the virtual disk drive from the boot order and restart.
- "The display is lagging when using LXQT on my Nvidia GPU?"
  - Run `eselect opengl set nvidia` as root.


## Installation
```
# Run the following from a Gentoo LiveCD
$ wget -q http://os.aswl.org/install.sh
$ sh /mnt/gentoo/install.sh
AzrynOS: Linux-based derivative of Gentoo
  help         Shows help output

Pre-install tasks:
  bootstrap    Bootstrap the stage3 tarball

Installation options:
  minimal      Install minimal Gentoo
  i3wm         Install Gentoo and i3wm desktop
  lxqt         Install Gentoo and LXQT desktop

Post-install tasks:
  cleanup      Remove junk created during install
```


## Post-boot tasks
### Adding an administrative user
```
useradd -m -g wheel -G audio,network,video -s /bin/bash username
passwd username
```

### Administering the system
`azryn` is meant to act as a simplification script for performing
administrative tasks. Later on this script will allow setting up a
package server, building stage3 tarballs, and live images.
```
$ azryn
Available options:
  cleanup,  -c    Remove unneeded packages
  install,  -i    Install a package
  reconfig, -R    Get latest configuration files
  remove,   -r    Safely remove a package
  sync,     -s    Sync portage
  update,   -u    Update @world without rebuild
  upgrade,  -U    Update @system and @world with rebuild
```

