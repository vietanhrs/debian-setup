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
sudo apt install curl git
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

