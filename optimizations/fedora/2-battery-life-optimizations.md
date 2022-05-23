## Linux / Optimizations / Fedora / 2. Battery Life optimizations

### Preface

This guide provides instructions for various optimizations of Fedora, like :
- SSD optimization ;
- battery life optimization.

This part will cover the second step : the optimizations of battery life.

### Tlp

We will optimize the battery life with **tlp** tool.

```ini
su -

# Installation and activation of service tlp
dnf install tlp tlp-rdw powertop
systemctl enable --now tlp
```


### Powertop

The other tool to optimize battery life (and control the Wh used) is **powertop**.
There is a command line (powertop --auto-tune) to optimize some things for battery life, however there is no service to execute it on each system start.
So we will create it.

```ini
echo "
[Unit]
Description=PowerTOP tunings

[Service]
Type=oneshot
ExecStart=/usr/sbin/powertop --auto-tune

[Install]
WantedBy=multi-user.target" >> /etc/systemd/system/powertop.service

systemctl enable --now powertop.service
```
