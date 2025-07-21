# Gnome Setup:

## Installation:

```bash
sudo dnf install -y gnome-shell gnome-terminal gnome-control-center gnome-software gnome-menus gnome-shell-extension-common gnome-system-monitor mutter gdm
sudo systemctl enable gdm --now
```

Full Guide: https://nico-shock.github.io/Arch-Linux-on-Nvidia/#install-a-desktop-environment

With multiple Desktops i like sddm more.

## Extensions:

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

## Extension Settings:

### Blur My Shell:

- Default Rounded Pipeline: Radius 20, Brightness: 100  
- Panel: Dynamic: 29, Sigma: Brightness: 1.00  
- Applications: opaque focused windows: off, blur in overview: off, enable all by default: on, disable manually: browser

### Dash to Dock:

- Intelligent auto-hide: off  
- Size: 32  
- Menu moved to the left  
- Show drives and devices: off  
- Minimize appearance: on  
- Window counter indicators: dots

### Just Perfection:

- Panel button spacing: 0px  
- Panel indicator spacing: 2px  
- Clock position: right + 6 to 9 px offset  
- Dash icon size: 32px

### Arc Menu:

- Menu button: Arch  
- Menu view: Startmenu: Runner  
- Width: 450  
- Height: 300

### Open Bar:

- https://github.com/Nico-Shock/My-OpenBar-configs

## Commands:

### Extensions Manager Installation:

```bash
flatpak install flathub com.mattjakeman.ExtensionManager
```

### WhiteSur Theme:

```bash
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git  
cd WhiteSur-gtk-theme  
./install.sh -l  
cd ..  
rm -rf WhiteSur-gtk-theme
```

### Tokyonight Theme:

```bash
git clone --depth 1 https://github.com/Fausto-Korpsvart/Tokyonight-GTK-Theme.git
cd Tokyonight-GTK-Theme/themes
./install.sh -l --tweaks black macos
cd ../..
rm -rf Tokyonight-GTK-Theme
```

## Gnome Tweaks

- Do not change the font here — it's set through KDE Plasma. Changing it in GNOME can mess up the font rendering in Ptyxis if "apply system font" is used.  
- Set the Shell theme to `WhiteSur-Dark`  
- Set the other theme to the `Tokyonight` theme — this way, all apps stay compact thanks to the WhiteSur shell styling, and everything else uses the Tokyo Night theme via the libadwaita system.

### Zsh:

```bash
sudo dnf install -y zsh git
```

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k  
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
chsh -s $(which zsh)
```

### Terminal (Ptyxis):

```bash
sudo dnf install -y ptyxis dejavu-sans-mono-fonts powerline-fonts
```

```bash
gsettings set 'org.gnome.Ptyxis.Profile:/org/gnome/Ptyxis/Profiles/'$PTYXIS_PROFILE'/' 'opacity' '0.70'
```

- Select this font for the Ptyxis terminal.

# KDE Plasma:

## Installation:

```bash
sudo dnf install -y plasma-desktop konsole kvantum
```

## Installations:

```bash
git clone https://github.com/vinceliuice/Layan-kvantum-theme.git
cd Layan-kvantum-theme
./install.sh
cd ..
rm -rf Layan-kvantum-theme
```

### Details:

- Install the Layan theme and the Kvantum version via the link in the settings from the theme description in the installation menu under settings  
- Personalize the taskbar – it always changes on how I like to customize it  
- (Maybe I will try Latte Dock in the future)

### Settings:

- Fensterverwaltung + Arbeitsflächen Effekte: still finding some:  
- Schweben (hover effect)  
- Transparenz: set everything to the same settings (very opaque)  
- Verwischen (blur effect)  
- Maybe some other effects in the future

### Konsole

- In Settings, create a new profile and set it as default  
- In Erscheinungsbild (Appearance), search for new color schemes  
- I use the aritim-dark theme for now  
- Then select the theme, click on edit, and set the background blur to something like 20

# KDE Plasma 2

### Theme

- Global Settings Theme: Utterly Nord + Utterly Nord Kvantum Theme  
- Konsole Theme: Utterly Nord Solid with 40% Transparency

### Desktop Effects

- Blur: everything at level 6 (from left)

# General Things:

### Fonts:

https://fonts.google.com/specimen/Inter

- I use the Semi Bold one

### Mouse Cursor:

```bash
sudo dnf install -y bibata-cursor-theme
```

- Windows XP Modern Cursor: https://www.pling.com/find?search=Windows%20xp%20cursor  
- Maybe other cursors – I always like to change it a bit

### Icons:

```bash
sudo dnf install -y tela-icon-theme
```

## Other Themes:

For "veraltete Anwendungen": https://github.com/kayozxo/GNOME-macOS-Tahoe  
or: https://github.com/Fausto-Korpsvart/Tokyonight-GTK-Theme

## Taskbar (designed like a dock) and Top Bar

- Top Bar default layout from the Utterly theme but with the system menu removed  
- Top Bar should have the grey icon from this repo  
- The taskbar/dock should have the blue "andere" default Arch logo  
- The taskbar/dock should keep the download shortcut

## Fonts:

```bash
sudo dnf install -y jetbrains-mono-nerd noto-fonts noto-fonts-cjk noto-fonts-emoji dejavu-sans-mono liberation-fonts
```
