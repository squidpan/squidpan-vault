---
categories:
  - "[[Installs]]"
rating:
created: 2026-01-13
last: 2026-01-13
topics:
apps:
title: Debian 13 Github-desktop Jetbrain toolbox
---
# Summary

```code
install github desktop on debian 13 linux

39  dpkg --print-architecture
   40  sudo apt update && sudo apt upgrade
   41  sudo apt install curl gnupg
   42  curl -fsSL https://mirror.mwt.me/shiftkey-desktop/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/mwt-desktop.gpg
   43  cat <<EOF | sudo tee /etc/apt/sources.list.d/mwt-desktop.sources
Types: deb
URIs: https://mirror.mwt.me/shiftkey-desktop/deb/
Suites: any
Components: main
Architectures: $(dpkg --print-architecture)
Signed-By: /usr/share/keyrings/mwt-desktop.gpg
EOF

   44  sudo apt update
   45  apt-cache policy github-desktop
   46  sudo apt install github-desktop
   47  github-desktop --version
   
Install Obsidian on Debian 13
   48  sudo apt update
   49  sudo apt install snapd
   50  sudo snap install obsidian --classic
   51  cd pjs/vaults/
   52  ls -l
   
Install Jetbrain toolbox for IntelliJ IDEA and Goland
   53  cd ~/Downloads/
   54  ls
   55  sudo apt install ./code_1.108.0-1767881962_amd64.deb 
   56  code
   57  ls -l
   58  tar -xvf jetbrains-toolbox-*.tar.gz -C ~/.local/share/JetBrains/Toolbox
   59  tar -xvf ./jetbrains-toolbox-*.tar.gz -C ~/.local/share/JetBrains/Toolbox
   60  tar -xvf ./jetbrains-toolbox-3.2.0.65851.tar.gz -C ~/.local/share/JetBrains/Toolbox
   61  mkdir ~/.local/share/JetBrains/Toolbox
   62  mkdir -p ~/.local/share/JetBrains/Toolbox
   63  tar -xvf ./jetbrains-toolbox-3.2.0.65851.tar.gz -C ~/.local/share/JetBrains/Toolbox
   64  ~/.local/share/JetBrains/Toolbox/jetbrains-toolbox
   65  ~/.local/share/JetBrains/Toolbox/jetbrains-toolbox-3.2.0.65851/bin/jetbrains-toolbox 

```

# Prerequisites

# Steps




