```bash
# CLAVIER / SOURIS  
gsettings set org.gnome.desktop.input-sources sources \[\(\'xkb\',\ \'fr\'\)\]  
gsettings set org.gnome.desktop.peripherals.touchpad tap-to-click true  
gsettings set org.gnome.desktop.peripherals.touchpad speed 0.25  
gsettings set org.gnome.desktop.peripherals.mouse speed 0.25  
  
# MODE NUIT  
gsettings set org.gnome.settings-daemon.plugins.color night-light-enabled true  
gsettings set org.gnome.settings-daemon.plugins.color night-light-schedule-automatic false  
gsettings set org.gnome.settings-daemon.plugins.color night-light-schedule-from 4  
gsettings set org.gnome.settings-daemon.plugins.color night-light-schedule-to 3.99  
gsettings set org.gnome.settings-daemon.plugins.color night-light-temperature 4700  

# BATTERIE  
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 0  
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0  
  
# RACCOURCIS  
gsettings set org.gnome.desktop.wm.keybindings move-to-workspace-left "['<Alt><Shift>Left']"  
gsettings set org.gnome.desktop.wm.keybindings move-to-workspace-right "['<Alt><Shift>Right']"  
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-left "['<Alt>Left']"  
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-right "['<Alt>Right']"  

# DASH FAVORITES
gsettings set org.gnome.shell favorite-apps \[\'firefox.desktop\',\ \'org.gnome.Nautilus.desktop\',\ \'virt-manager.desktop\',\ \'mozilla-thunderbird.desktop\',\ \'GitHub.desktop\',\ \'separator4.desktop\',\ \'Webmail.desktop\',\ \'Tchap.desktop\',\ \'focalboard.desktop\',\ \'Notion.desktop\',\ \'obsidian.desktop\',\ \'codium.desktop\',\ \'drawio.desktop\',\ \'separator3.desktop\',\ \'discord_perso.desktop\',\ \'Youtube.desktop\',\ \'org.clementine_player.Clementine.desktop\'\]

# UI DIVERS  
gsettings set org.gnome.desktop.wm.preferences button-layout ":minimize,close"  
gsettings set org.gnome.desktop.interface clock-show-weekday true  
  
# FONTS / ICONS  
gsettings set org.gnome.desktop.interface font-name 'Fira Sans Semi-Light 11'  
gsettings set org.gnome.desktop.interface document-font-name 'Fira Sans Semi-Light 11'  
gsettings set org.gnome.desktop.interface monospace-font-name 'Fira Mono Regular 11'  
gsettings set org.gnome.desktop.wm.preferences titlebar-font 'Fira Sans Bold 11'  
gsettings set org.gnome.desktop.interface icon-theme 'Papirus'   
  
# TERMINAL 
# Reste la barre de défilement
# gsettings set org.gnome.Terminal.Legacy.Settings theme-variant \'dark\'  
gsettings set org.gnome.Terminal.Legacy.Settings theme-variant \'system\'
  
# VIRT-MANAGER  
gsettings set org.virt-manager.virt-manager xmleditor-enabled true  
gsettings set org.virt-manager.virt-manager enable-libguestfs-vm-inspection true  
gsettings set org.virt-manager.virt-manager.console resize-guest 1  
gsettings set org.virt-manager.virt-manager.details show-toolbar false
gsettings set org.virt-manager.virt-manager.paths image-default ~/.local/share/libvirt/images   
  
# NAUTILUS  
gsettings set org.gnome.nautilus.preferences show-hidden-files true  
gsettings set org.gtk.Settings.FileChooser show-hidden true  
gsettings set org.gnome.nautilus.preferences show-delete-permanently true  
gsettings set org.gnome.nautilus.preferences show-create-link true  
gsettings set org.gtk.Settings.FileChooser sort-directories-first true  
gsettings set org.gnome.nautilus.preferences default-folder-viewer \'list-view\'  
gsettings set org.gnome.nautilus.list-view default-zoom-level \'small\'   
gsettings set org.gnome.nautilus.list-view default-visible-columns \[\'name\',\ \'size\',\ \'type\',\ \'owner\',\ \'group\',\ \'permissions\',\ \'date_modified\',\ \'starred\'\]  
  
# EPIPHANY  
gsettings set org.gnome.Epiphany.web:/ enable-webextensions true  
  
# IMPRESSION / SCANNER  
gsettings set org.gnome.SimpleScan jpeg-quality 23  

# EXTENSIONS  
gsettings set org.gnome.shell disabled-extensions []  
gsettings set org.gnome.shell enabled-extensions \[\'just-perfection-desktop@just-perfection\',\ \'gnome-fuzzy-app-search@gnome-shell-extensions.Czarlie.gitlab.com\',\ \'pop-shell@system76.com\',\ \'trayIconsReloaded@selfmade.pl\',\ \'blur-my-shell@aunetx\'\]

# BLUR MY SHELL
gsettings set org.gnome.shell.extensions.blur-my-shell sigma 4
gsettings set org.gnome.shell.extensions.blur-my-shell.panel blur false
gsettings set org.gnome.shell.extensions.blur-my-shell.lockscreen blur false
gsettings set org.gnome.shell.extensions.blur-my-shell.applications blur false
gsettings set org.gnome.shell.extensions.blur-my-shell.window-list blur false

# Enlever BLUR pour dash
gsettings set org.gnome.shell.extensions.blur-my-shell.overview customize true
gsettings set org.gnome.shell.extensions.blur-my-shell.overview sigma 4
gsettings set org.gnome.shell.extensions.blur-my-shell.overview style-components 0


# JUST PERFECTION - un peu sioux, indiquer le schéma de clé
gsettings --schemadir /usr/share/gnome-shell/extensions/just-perfection-desktop@just-perfection/schemas/ set org.gnome.shell.extensions.just-perfection animation 3
gsettings --schemadir /usr/share/gnome-shell/extensions/just-perfection-desktop@just-perfection/schemas/ set org.gnome.shell.extensions.just-perfection panel-in-overview true
gsettings --schemadir /usr/share/gnome-shell/extensions/just-perfection-desktop@just-perfection/schemas/ set org.gnome.shell.extensions.just-perfection panel false
gsettings --schemadir /usr/share/gnome-shell/extensions/just-perfection-desktop@just-perfection/schemas/ set org.gnome.shell.extensions.just-perfection search false

# TRAY ICONS RELOADED
gsettings --schemadir /usr/share/gnome-shell/extensions/trayIconsReloaded@selfmade.pl/schemas/ set org.gnome.shell.extensions.trayIconsReloaded icon-size 16
gsettings --schemadir /usr/share/gnome-shell/extensions/trayIconsReloaded@selfmade.pl/schemas/ set org.gnome.shell.extensions.trayIconsReloaded icons-limit 15
gsettings --schemadir /usr/share/gnome-shell/extensions/trayIconsReloaded@selfmade.pl/schemas/ set org.gnome.shell.extensions.trayIconsReloaded icon-brightness -50
gsettings --schemadir /usr/share/gnome-shell/extensions/trayIconsReloaded@selfmade.pl/schemas/ set org.gnome.shell.extensions.trayIconsReloaded tray-margin-left 4
gsettings --schemadir /usr/share/gnome-shell/extensions/trayIconsReloaded@selfmade.pl/schemas/ set org.gnome.shell.extensions.trayIconsReloaded icon-margin-horizontal 0
gsettings --schemadir /usr/share/gnome-shell/extensions/trayIconsReloaded@selfmade.pl/schemas/ set org.gnome.shell.extensions.trayIconsReloaded icon-margin-vertical 4
gsettings --schemadir /usr/share/gnome-shell/extensions/trayIconsReloaded@selfmade.pl/schemas/ set org.gnome.shell.extensions.trayIconsReloaded icon-padding-horizontal 3


# POP SHELL  
gsettings set org.gnome.shell.extensions.pop-shell tile-by-default true  
gsettings set org.gnome.shell.extensions.pop-shell gap-inner uint32\ 3  
gsettings set org.gnome.shell.extensions.pop-shell gap-outer uint32\ 3


# THEMING
gsettings set org.gnome.desktop.interface gtk-theme '$THEME'  
gsettings set org.gnome.desktop.wm.preferences theme '$THEME'  
```
