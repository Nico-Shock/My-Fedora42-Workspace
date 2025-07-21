# General Steps

### Additional Packages Installation

Install additional packages:
```
sudo dnf in -y flatpak git wget gedit thermald ufw fzf python3 python3-pip bluez blueman bluez-libs fastfetch vim
sudo systemctl enable --now bluetooth ufw
sudo ufw default deny
```

### Make Download Faster
```
sudo vim /etc/dnf/dnf.conf
```
Add the following lines:
```
max_parallel_downloads=20
fastestmirror=True
```

### Install Nvidia Drivers
```
sudo dnf in -y @base-x kernel-devel kernel-headers gcc make dkms acpid libglvnd-devel pkgconf xorg-x11-server-Xwayland libxcb egl-wayland --skip-broken --allowerasing
sudo reboot now
```
Download the Linux/Unix NVIDIA driver from the official website.  
Make it executable (right-click, enable checkbox).  
In the terminal:
```
cd ~/Downloads
sudo ./NVIDIA-Linux-x86_64-xxx.x.xx.run
```
Click "Continue" and "Yes" for DKMS installations.
```
sudo reboot now
```

### Installing the CachyOS Kernel
```
sudo dnf copr enable bieszczaders/kernel-cachyos
sudo dnf in -y kernel-cachyos kernel-cachyos-devel-matched
sudo dnf copr enable bieszczaders/kernel-cachyos-addons
sudo dnf in -y cachyos-settings --allowerasing
sudo dracut -f --regenerate-all
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```

### Installing Gaming Meta
```
sudo dnf in -y @c-development @development-tools steam lutris wine bottles gamescope mangohud libva-utils vulkan-tools mesa-dri-drivers mesa-vulkan-drivers gamemode libadwaita wine-dxvk dxvk-native goverlay --skip-broken
sudo dnf copr enable atim/heroic-games-launcher
sudo dnf in -y heroic-games-launcher-bin
```

### Debloating Desktop
```
sudo dnf rm -y gnome-contacts gnome-maps mediawriter totem simple-scan gnome-boxes gnome-user-docs rhythmbox evince gnome-photos gnome-documents gnome-initial-setup yelp winhelp32 dosbox winehelp fedora-release-notes firefox gnome-characters gnome-logs fonts-tweak-tool timeshift epiphany gnome-weather cheese pavucontrol qt5-settings
sudo dnf clean all
```

### Install Microsoft-Edge

```
sudo tee /etc/yum.repos.d/microsoft-edge.repo <<EOF
[microsoft-edge]
name=Microsoft Edge
baseurl=https://packages.microsoft.com/yumrepos/edge
enabled=1
gpgcheck=1
gpgkey=https://packages.microsoft.com/keys/microsoft.asc
EOF

sudo dnf install microsoft-edge-stable
```

### Upgrading and Updating System
```
sudo dnf up -y
```

# Gnome Setup

## Extensions

- Application and KStatusNotifierItem Support (optional)
- Blur My Shell
- Just Perfection
- Dash to Dock
- Arc Menu
- Coverflow
- Impatience
- Gnome 4x UI Improvements
- Caffeine
- Tiling Shell (optional)
- Open Bar
- User Themes
- System Monitor
- Extension List

## Extension Settings

### Blur My Shell
- Default Rounded Pipeline: Radius 20, Brightness: 100
- Panel: Dynamic: 29, Sigma: Brightness: 1.00
- Applications: Opaque focused windows: off, blur in overview: off, enable all by default: on, disable manually: browser

### Dash to Dock
- Intelligent auto-hide: off
- Size: 32
- Menu moved to the left
- Show drives and devices: off
- Minimize appearance: on
- Window counter indicators: dots

### Just Perfection
- Panel button spacing: 0px
- Panel indicator spacing: 2px
- Clock position: right + 6 to 9 px offset
- Dash icon size: 32px

### Arc Menu
- Menu button: Arch
- Menu view: Startmenu: Runner
- Width: 450
- Height: 300

### Open Bar
- Configuration: https://github.com/Nico-Shock/My-OpenBar-configs

## Commands

### Extensions Manager
Install via flatpak:
```
sudo flatpak install -y flathub com.mattjakeman.ExtensionManager
```

### WhiteSur Theme
```
sudo dnf in -y git
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git
cd WhiteSur-gtk-theme
./install.sh -l
cd ..
sudo rm -rf WhiteSur-gtk-theme
```

### Tokyonight Theme
```
git clone --depth 1 https://github.com/Fausto-Korpsvart/Tokyonight-GTK-Theme.git
cd Tokyonight-GTK-Theme/themes
./install.sh -l --tweaks black macos
cd ../..
sudo rm -rf Tokyonight-GTK-Theme
```

### Tela Circle Icons
```
git clone --depth 1 https://github.com/vinceliuice/Tela-circle-icon-theme.git
cd Tela-circle-icon-theme
./install.sh -n blue
cd ..
sudo rm -rf Tela-circle-icon-theme
```

## Gnome Tweaks
- Do not change the font (set via KDE Plasma to avoid font rendering issues in Ptyxis with "apply system font").
- Shell theme: `WhiteSur-Dark`
- Other theme: `Tokyonight` (ensures compact apps via WhiteSur shell styling and Tokyo Night theme via libadwaita).

### Zsh
```
sudo dnf in -y zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
chsh -s $(which zsh)
```

### Terminal (Ptyxis)
```
sudo dnf in -y dejavu-sans-mono-fonts powerline-fonts
gsettings set 'org.gnome.Ptyxis.Profile:/org/gnome/Ptyxis/Profiles/'$PTYXIS_PROFILE'/' 'opacity' '0.70'
```
- Set Ptyxis font to DejaVu Sans Mono or Powerline font.

# KDE Plasma

## Installation
```
sudo dnf in -y plasma-desktop konsole kvantum
```

## Theme Installation
```
git clone https://github.com/vinceliuice/Layan-kvantum-theme.git
cd Layan-kvantum-theme
./install.sh
cd ..
sudo rm -rf Layan-kvantum-theme
```

### Details
- Apply Layan theme and Kvantum version via settings menu.
- Customize taskbar as preferred.
- Consider trying Latte Dock in the future.

### Settings
- Fensterverwaltung + Arbeitsflächen Effekte:
  - Schweben (hover effect)
  - Transparenz: Set to very opaque
  - Verwischen (blur effect)
  - Explore additional effects later

### Konsole
- Create a new profile in Settings and set as default.
- In Erscheinungsbild (Appearance), use aritim-dark theme.
- Edit theme and set background blur to 20.

# KDE Plasma 2

## Theme
- Global Settings: Utterly Nord + Utterly Nord Kvantum Theme
- Konsole Theme: Utterly Nord Solid with 40% Transparency

## Desktop Effects
- Blur: Set to level 6 (from left)

## Taskbar (designed like a dock) and Top Bar
- Top Bar: Utterly theme default layout, system menu removed, grey icon from repo.
- Taskbar/Dock: Blue "andere" default Arch logo, keep download shortcut.

# General Things

## Fonts
- Install Inter Semi Bold: https://fonts.google.com/specimen/Inter

- Install additional fonts:
```
sdfsdfsdfsvvsdfergf
```

## Mouse Cursor

- Babita Mouse Cursor: https://github.com/ful1e5/Bibata_Cursor/releases
- Windows XP Modern Cursor: https://www.pling.com/find?search=Windows%20xp%20cursor
- May change cursors occasionally.

## Other Themes
For legacy applications:
- https://github.com/kayozxo/GNOME-macOS-Tahoe
- https://github.com/Fausto-Korpsvart/Tokyonight-GTK-Theme
