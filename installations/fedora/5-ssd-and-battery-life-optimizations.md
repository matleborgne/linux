## Linux / Installations / Fedora / 5. SSD and Battery life optimizations

### Preface

This guide provides instructions for a minimal installation of Fedora with :
- full-disk encryption
- BTRFS on LUKS, or BTRFS on LVM on LUKS
- GNOME "minimal" desktop environment

The installation is now completed.

This part will cover an optional step : the optimizations for SSD disks and battery life.

### SSD optimizations

We will optimize the SSD by :
- avoiding too much writing tasks ;
- discarding, but not with the mount option in FSTAB.

Indeed, I have read that too much discarding can be bad for battery life, as much as no discarding at all.
So, we will use a systemd-timer for that (normally already implemented in Fedora).

Generally, I use this configuration in FSTAB :
```ini
BTRFS_OPTS="ssd,noatime,space_cache,commit=120,compress=zstd:1,x-systemd.device-timeout=0"
```
Fedora does have some already implemented, so we do :

```ini
BTRFS_OPTS="ssd,noatime,space_cache,commit=120,compress=zstd"

cp /etc/fstab /etc/fstab.BAK
sed -i "/btrfs/s/compress=zstd/$BTRFS_OPTS/g" /etc/fstab
```
Then, we check if the discard service **fstrim.timer** is working

```ini
systemctl enable --now fstrim.timer
systemctl status fstrim.timer
```

If it is **active (waiting)** it's ok.
Else if it raises an error :
```ini
echo "
[Unit]
Description=Discard unused blocks once a week
Documentation=man:fstrim
ConditionVirtualization=!container
ConditionPathExists=!/etc/initrd-release

[Timer]
OnCalendar=weekly
AccuracySec=1h
Persistent=true
RandomizedDelaySec=6000

[Install]
WantedBy=timers.target
" > /etc/systemd/system/timers.target.wants/fstrim.timer

systemctl enable --now fstrim.timer
```
