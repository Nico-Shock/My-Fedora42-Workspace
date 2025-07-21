# Gnome Setup

## Installation

Install GNOME and additional packages:
```bash
sudo dnf in gnome-tweaks flatpak git wget gedit thermald ufw fzf python3 python3-pip bluez blueman bluez-libs fastfetch nano vim
```
Full Guide: https://nico-shock.github.io/Arch-Linux-on-Nvidia/#install-a-desktop-environment

Note: With multiple Desktops, I prefer sddm.

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
```bash
sudo flatpak install -y flathub com.mattjakeman.ExtensionManager
```

### WhiteSur Theme
```bash
sudo dnf install -y git
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git
cd WhiteSur-gtk-theme
./install.sh -l
cd ..
sudo rm -rf WhiteSur-gtk-theme
```

### Tokyonight Theme
```bash
git clone --depth 1 https://github.com/Fausto-Korpsvart/Tokyonight-GTK-Theme.git
cd Tokyonight-GTK-Theme/themes
./install.sh -l --tweaks black macos
cd ../..
sudo rm -rf Tokyonight-GTK-Theme
```

### Tela Circle Icons
```bash
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
```bash
sudo dnf install -y zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
chsh -s $(which zsh)
```

### Terminal (Ptyxis)
```bash
sudo dnf install -y ptyxis dejavu-sans-mono-fonts powerline-fonts
gsettings set 'org.gnome.Ptyxis.Profile:/org/gnome/Ptyxis/Profiles/'$PTYXIS_PROFILE'/' 'opacity' '0.70'
```

- Set Ptyxis font to DejaVu Sans Mono or Powerline font.

# KDE Plasma

## Installation
```bash
sudo dnf install -y plasma-desktop konsole kvantum
```

## Theme Installation
```bash
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

# General Things

## Fonts
- Install Inter Semi Bold: https://fonts.google.com/specimen/Inter
```bash
wget https://fonts.google.com/download?family=Inter -O inter.zip
unzip inter.zip -d inter
sudo mkdir -p /usr/share/fonts/inter
sudo mv inter/*.ttf /usr/share/fonts/inter/
sudo fc-cache -fv
rm -rf inter inter.zip
```

- Install additional fonts:
```bash
sudo dnf install -y jetbrains-mono-fonts noto-fonts noto-cjk-fonts noto-emoji-fonts dejavu-fonts liberation-fonts powerline-fonts
```

### Unifont
```bash
wget http://unifoundry.com/pub/unifont/unifont-15.0.06/unifont-15.0.06.ttf
sudo mkdir -p /usr/share/fonts/unifont
sudo mv unifont-15.0.06.ttf /usr/share/fonts/unifont/
sudo fc-cache -fv
```

### Symbola
```bash
wget https://fontlibrary.org/assets/downloads/symbola/0e4e2e6f7b050f4e43e3f6b4e7e3c1f7/symbola.zip
unzip symbola.zip -d symbola
sudo mkdir -p /usr/share/fonts/symbola
sudo mv symbola/Symbola.ttf /usr/share/fonts/symbola/
sudo fc-cache -fv
rm -rf symbola symbola.zip
```

## Mouse Cursor
```bash
sudo dnf install -y bibata-cursor-theme
```

- Windows XP Modern Cursor: https://www.pling.com/find?search=Windows%20xp%20cursor
- May change cursors occasionally.

## Icons
```bash
sudo dnf install -y tela-icon-theme
```

## Other Themes
For legacy applications:
- https://github.com/kayozxo/GNOME-macOS-Tahoe
- https://github.com/Fausto-Korpsvart/Tokyonight-GTK-Theme
