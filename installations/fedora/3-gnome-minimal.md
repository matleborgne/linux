## Linux / Installations / Fedora / 3. GNOME minimal

### Preface

This guide provides instructions for a minimal installation of Fedora with :
- full-disk encryption
- BTRFS on LUKS, or BTRFS on LVM on LUKS
- GNOME "minimal" desktop environment

This part will cover the third step : the minimal installation of GNOME.

### My idea of GNOME minimal or vanilla

I like to have "clean" desktop environments. However, Fedora Workstation comes with too many "bloatwares".
Coming from ArchLinux, I am very demanding with each "heavy" package working on my system.

Thus I consider as "bloatwares" :
- **PackageKit** (the auto-updater) : too many RAM used, I prefer the gnome-extension **ArchLinux update indicator** ;
- **abrt** (the auto-bug report tool).

We could go much deeper and talk about **evolution-data-server** (the "mega" database for gnome-calendar, gnome-contacts, etc.).
But this would lead us too far, and Fedora would not let us remove it (like Arch does).

We can go with GNOME installation.

### Configuration of DNF and RPM Fusion

First, we will configure the DNF package manager.

```ini
echo "deltarpm=true
max_parallel_downloads=20
defaultyes=true 
exclude=PackageKit abrt
" >> /etc/dnf/dnf.conf
```
Then, for a desktop usage, we will activate RPM Fusion (which contains multimedia and non-free codecs).

```ini
dnf install \
  https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
  https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

dnf install \
  rpmfusion-free-release-tainted \
  rpmfusion-nonfree-release-tainted

dnf upgrade
```
