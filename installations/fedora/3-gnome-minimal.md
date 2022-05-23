## Linux / Installations / Fedora / 3. GNOME minimal

### Preface

This guide provides instructions for a minimal installation of Fedora with :
- full-disk encryption
- BTRFS on LUKS, or BTRFS on LVM on LUKS
- GNOME "minimal" desktop environment

This part will cover the third step : the minimal installation of GNOME.

### My idea of GNOME minimal or vanilla

I like to have "clean" desktop environments. However, Fedora Workstation comes with too many "bloatwares".
Coming from ArchLinux, I am very demanding with every "heavy" package that work on my system.

Thus I consider as "bloatwares" :
- **PackageKit** (the auto-updater) : too many RAM used, I prefer the gnome-extension **ArchLinux update indicator** ;
- **abrt** (the auto-bug report tool)

We could go much deeper and talk about **evolution-data-server** (the mega manager of gnome-calendar, gnome-contacts, etc.).
But this would lead us too far, and Fedora would not let us remove it (like Arch does).

We can go with GNOME installation.

### Configuration of DNF

First, we will configure the DNF package manager.

```ini
echo "deltarpm=true
max_parallel_downloads=20
defaultyes=true 
exclude=PackageKit abrt
" >> /etc/dnf/dnf.conf
```
