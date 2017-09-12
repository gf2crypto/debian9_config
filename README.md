# debian9_config
Configuration files of my debian9 installation

Installation of the basic packets
--------

```bash
su -c
apt-get installbuild-essential module-assistant fonts-roboto fonts-inconsolata qpdfview gksu texlive-full chromium zsh fbxkb pcmanfm arc-theme fonts-noto curl i3lock xfonts-terminus dmenu i3status git lightdm sudo xorg apt-transport-https mc proxychains python-pip
```

# configuartion of sudo

```bash
usermod -a -G sudo surehand
exit
```

Installation of the sublime-text editor
---------

```bash
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
sudo apt-get update
sudo apt-get install sublime-text
```

Installation of i3-gaps
-----------------
# installation the dependencies

sudo apt-get install libxcb-keysyms1-dev libpango1.0-dev libxcb-util0-dev xcb libxcb1-dev libxcb-icccm4-dev libyajl-dev libev-dev libxcb-xkb-dev libxcb-cursor-dev libxkbcommon-dev  libxcb-xinerama0-dev libxkbcommon-x11-dev libstartup-notification0-dev libxcb-randr0-dev libxcb-xrm0 libxcb-xrm-dev

# goto to the temp folder
cd /path/where/you/want/the/repository

# clone the repository
git clone https://www.github.com/Airblader/i3 i3-gaps
cd i3-gaps

# compile & install
autoreconf --force --install
rm -rf build/
mkdir -p build && cd build/

# Disabling sanitizers is important for release versions!
# The prefix and sysconfdir are, obviously, dependent on the distribution.
../configure --prefix=/usr --sysconfdir=/etc --disable-sanitizers
make
sudo make install