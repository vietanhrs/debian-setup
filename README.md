# debian-setup
Setup my Debian Distro

## Necessary .deb files
[VS Code](https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64)
[Google Chrome](https://www.google.com/intl/vi/chrome/next-steps.html)

## Add myself to the sudoers file
```bash
su
nano /etc/sudoers
```
Add 
```
anhtv   ALL=(ALL:ALL) ALL
```
under `# User privilege specification`

## Update and upgrade
```bash
sudo apt update
sudo apt upgrade
```

## Necessary packages
```bash
sudo apt install curl git build-essential
```

## Git setup
```bash
ssh-keygen -t ed25519 -C "vietanhtran.uet@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
git config --global user.name "openVietAnh"
git config --global user.email "vietanhtran.uet@gmail.com"
```

## Install ghostty
```bash
curl -sS https://debian.griffo.io/EA0F721D231FDD3A0A17B9AC7808B4DD62C41256.asc | sudo gpg --dearmor --yes -o /etc/apt/trusted.gpg.d/debian.griffo.io.gpg
echo "deb https://debian.griffo.io/apt $(lsb_release -sc 2>/dev/null) main" | sudo tee /etc/apt/sources.list.d/debian.griffo.io.list
sudo apt update

sudo apt install zig ghostty lazygit yazi eza uv fzf zoxide bun tigerbeetle
```

## Install the Source Code Pro fonts
```bash
mkdir -p ~/.fonts/adobe-fonts/source-code-pro
git clone https://github.com/adobe-fonts/source-code-pro.git ~/.fonts/adobe-fonts/source-code-pro
fc-cache -f -v ~/.fonts/adobe-fonts/source-code-pro
```

## Install oh-my-zsh
```bash
sudo apt install zsh zplug
sh -c "$(curl ****-fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Install the Rust programming language
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
. "$HOME/.cargo/env"
```

## Install Node.js with nvm
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
nvm ls-remote
nvm install v24 # replace with the latest LTS version
nvm use v2
npm install -g corepack
```

## Install NVIDIA driver (for machines with NVIDIA GPU)
```bash
lspci -nn | egrep -i "3d|display|vga"
sudo apt install linux-headers-amd64
sudo nano /etc/apt/sources.list
```
Edit the file
```
deb http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware
deb-src http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware

deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
deb-src http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware

deb http://deb.debian.org/debian/ bookworm-updates main contrib non-free non-free-firmware
deb-src http://deb.debian.org/debian/ bookworm-updates main contrib non-free non-free-firmware
```
```bash
sudo apt update
sudo apt install nvidia-driver firmware-misc-nonfree
reboot
```

## VPN setup and enable VPN in GNOME Setting
```bash
sudo apt-get install openvpn network-manager-openvpn-gnome
```

## Install ibus-bamboo
Download link: [Build Service](https://download.opensuse.org/repositories/home:/lamlng/Debian_12/amd64/ibus-bamboo_0.8.4-0_amd64.deb)
```bash
ibus restart
env DCONF_PROFILE=ibus dconf write /desktop/ibus/general/preload-engines "['BambooUs', 'Bamboo']" && gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'us'), ('ibus', 'Bamboo')]"
```

## Setup Flatpak
```bash
sudo apt install flatpak
sudo apt install gnome-software-plugin-flatpak
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```