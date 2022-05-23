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

### Implement the encryption of /boot

Replace the variables with your own case.

```ini
# Set your variables here
BOOT="/dev/nvme0n1p3"

# Unmount the boot partition on remount it on /mnt
umount -R /boot
mount $BOOT /mnt

# Copy the "old" boot files (mounted on /mnt) to the new boot folder
tar -C /mnt --acls --xattrs --one-file-system -cf /tmp/boot.tar .
tar -C /boot --acls --xattrs -xf /tmp/boot.tar
rm /tmp/boot.tar

# Remount /boot/efi
mount /boot/efi

# FSTAB - Comment /boot
cp /etc/fstab /etc/fstab.BAK
sed -i "/\/boot  /s/^/#/g" /etc/fstab

# DEFAULT/GRUB modifications
cp /etc/default/grub /etc/default/grub.BAK
sed -i "/BLSCFG/s/true/false/g" /etc/default/grub
echo 'GRUB_ENABLE_CRYPTODISK="y"' >> /etc/default/grub

# BOOT/EFI and DRACUT regeneration
cp /boot/efi/EFI/fedora/grub.cfg /boot/efi/EFI/fedora/grub.cfg.BAK
dracut --force --regenerate-all --verbose
grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
```

The full disk encryption is now functional.
However, you will have to enter your password twice during each boot.
To avoid this, the root partition can be unlocked during boot by an embedded keyfile.

### Set an embedded keyfile to unlock root

Replace the variables with your own case.

```ini
# Set your variables here
ROOT="/dev/nvme0n1p2"
KEY="/etc/keys/keyfile.key"

# Keyfile creation
mkdir /etc/keys
openssl genrsa -out $KEY 2048
chown -R 400 /etc/keys

# Add the key to the LUKS device
cryptsetup luksAddKey $ROOT $KEY

# CRYPTTAB - Set the keyfile
cp /etc/crypttab /etc/crypttab.BAK
sed -i "s/none/\/etc\/keys\/keyfile.key/g" /etc/crypttab

# DRACUT - Embedded keyfile
echo "install_items+=$KEY" >> /etc/dracut.conf.d/copy-keyfile.conf

# REGENERATE all
dracut --force --regenerate-all --verbose
grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
```
