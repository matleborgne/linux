## Linux / Installations / Fedora / 2. Full Disk Encryption

### Preface

This guide provides instructions for a minimal installation of Fedora with :
- full-disk encryption
- BTRFS on LUKS, or BTRFS on LVM on LUKS
- GNOME "minimal" desktop environment

This part will cover the second step : the full disk encryption (including /boot).


### Install some utilities

For this part, we will need some utilies. Some of them are probably already installed.
```ini
dnf install \
 cryptsetup btrfs-progs nano openssl tar \
 grub2 grub2-efi-x64-modules shim efitools
```

If you want to work through ssh, you have to do :
```ini
dnf install openssh-server
systemctl enable --now sshd
```
