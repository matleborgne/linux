## Fedora installation - 1. Minimal installation

### Preface

This guide provides instructions for a minimal installation of Fedora with :
- full-disk encryption
- BTRFS on LUKS, or BTRFS on LVM on LUKS
- GNOME "minimal" desktop environment

This part will cover the first step : the minimal installation with the Fedora installer (Anaconda).
For more information, refer to the Fedora documentation :
https://docs.fedoraproject.org/en-US/fedora/latest/install-guide/install/Installing_Using_Anaconda/


### Prepare the installer

First step is to download the server version of Fedora : https://getfedora.org/en/server/download/
Then, like any other distribution, put it on a bootable key with Ventoy, Balena Etcher, Rufus, Fedora Media Writer, etc.

When, you boot into the installer :
- choose your locales
- configure your user account / root account
- choose your installation packages : **Minimal Install**
- configure the storage with advanced option **blivet-gui**

### Choose your strategy

Now it's time to choose your partitioning strategy. I usually use :
- option 1 : EFI **+**   LUKS **<** BTRFS-ROOT **>** **+**   LUKS **<** EXT4-HOME **>**
- option 2 : EFI **+**   LUKS **<** LVM (BTRFS-ROOT + EXT4-HOME) **>**
