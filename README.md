# Big TODOs

1. Forget Arch, focus on Ubuntu
2. Link to wal script
3. Pictures for finished look


# Partitions

Partition madness!

Welcome to my system, trying to keep some order and easy connection between systems, I have set several partitions with specific purposes. My SSD contains all of the OSs and some Swap space. Roughly half is taken by Windows, and the rest is unevenly split by Linux partitions (My main distro Ubuntu and a flavor of the month). Given that its considered a good principle to keep your SSD as empty as possible, only the OSs are stored on mine, and most data is kept on the HDD.

If attemping, its recommended to always install Windows first, then Linux. 

## SSD (Sda label)

| Windows         | Ubuntu      | Manjaro   | Swap|
| ---|---|---|---|
|  a1/a2          | a6          | a7        | a5  |


My HDD contains my data and program files. Windows programs are installed here (whenever possible). 

*The "Data" partition is linked to Windows Libraries/Collections and set as default path to free up space in the SSD. 

*The "Programs" partition contains a copy of `Program Files` and `Program Files (x86)`. The installation path is set there whenever prompted.

*The "Games" partition serves a similar function but exclusively for games. Is set as the default adress for Steam data storage.

*The "Encrypted" is reserved for (Veracrypt)[https://www.veracrypt.fr/en/Home.html], and can only be accessed through it. 

## HDD (Sdb label)

| Windows |     |       | Ubuntu | Manjaro | Swap |
| ----- | ----- | ----- | ----- | ----- | ----- |
|  b1   |bp     |bg     | b2    | b3    | b4    |
|  D:/ Data  | Programs | Games      | Encrypted          | /home        | /home  |


# Linux

# Dotfiles
//Step 1. Install dotfiles

Install Dotfiles!
Use the probably not from Atlassian method
(link)[https://www.atlassian.com/git/tutorials/dotfiles]

To add:

```
config add .vimrc
config commit -m "Add vimrc"
```

To clone:

```
# add 'config' alias to .bashrc/.zsh
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'

#Ignore self, avoid recursion problems
# .cfg -> this repo
# .config -> actual config files
echo ".cfg" >> .gitignore

# clone
git clone --bare https://github.com/smallAtlas/dotfiles $HOME/.cfg

# redefine alias
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'

#checkout! (download)
# may need to delete .bashrc

# moves conflict files to backup folder
mkdir -p .config-backup && \
config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | \
xargs -I{} mv {} .config-backup/{}

config checkout

# flag to no untracked files
config config --local status.showUntrackedFiles no

```


## Software
Inkscape
Krita
Blender
Gimp
Chrome
Spotify


# ZSH And Commandline

https://github.com/sindresorhus/pure

https://github.com/agnoster/agnoster-zsh-theme

https://github.com/powerline/fonts





# Before installs


Set up
```
  git config --global user.email "e@gmail.com"
  git config --global user.name "Ema"
``` 

To avoid conflicts with Windows, set Linux time to local

```
timedatectl set-local-rtc 1 --adjust-system-clock
```


## Software

### Visual Studio Code

https://code.visualstudio.com/
...Also add wal extension 

### Veracrypt

```
sudo apt install exfat-fuse exfat-utils libexo-1-0
```

Don't forget to save mounted volume as favorites

### Google Chrome

Makes syncing with phone so much easier. Should I switch to Chromium or Firefox?

[Chrome](https://www.google.com/chrome/)

### Spotify

For better hack-abiliy, add Spotify repository instead of installing through the store. 

[Spotify Download](https://www.spotify.com/es/download/linux/)

```
#Add repo
curl -sS https://download.spotify.com/debian/pubkey.gpg | sudo apt-key add - 
echo "deb http://repository.spotify.com stable non-free" | sudo tee /etc/apt/sources.list.d/spotify.list
#Install
sudo apt-get update && sudo apt-get install spotify-client
```

## Gnome tweak tool

How else are we applying those custom fonts and icon packs?

```
sudo apt install gnome-tweak-tool
```

### Papirus icons


[Papirus](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme/)

```
sudo add-apt-repository ppa:papirus/papirus
sudo apt-get update
sudo apt-get install papirus-icon-theme
```

## Fonts

fonts-noto 
fonts-mplus
### Microsoft Fonts

```
sudo apt-get install ttf-mscorefonts-installer
```

### Sans-Serif

#### Roboto
```
sudo apt-get install fonts-roboto
```

### Serif

#### Dejavu

https://dejavu-fonts.github.io/

### Terminal

#### Nerd fonts

Patched fonts for terminal
[Nerdfonts](https://www.nerdfonts.com/)
Has some of my favorites already!

#### Iosevka

[Iosevka](https://typeof.net/Iosevka/)

Download term

[download](https://github.com/be5invis/Iosevka/releases/tag/v2.2.1)

Use "Iosevka Term Regular" on terminal

To install fonts on a per-user basis:
```
# Linux : Copy the TTF files to your fonts directory
cp fonts ~/.fonts

# Run: 
sudo fc-cache
```
Pending:
https://github.com/belluzj/fantasque-sans
inconsolata
https://github.com/source-foundry/Hack
https://github.com/Tecate/bitmap-fonts
https://fontawesome.com/


## Japanese

https://github.com/adobe-fonts/source-han-sans/tree/release


# Vim 

Surprisingly, Ubuntu doen't already include Vim. Lets fix that:

```
sudo apt install vim
```
Now lets make it useful

## You Complete Me

[YCM](https://github.com/ycm-core/YouCompleteMe)

Compiling YCM with semantic support for C-family languages through libclang. Ubuntu 16.04 and later:
```
sudo apt install build-essential cmake python3-dev
cd ~/.vim/bundle/YouCompleteMe
python3 install.py --clang-completer
```

## Add Vundle

Install vundle plugin manager for Vim 
[Vundle](https://github.com/VundleVim/Vundle.vim)

```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```
copy dotfile

```
vim +PluginInstall +qall
```


## Add You Complete Me

[YouCompleteMe](https://github.com/Valloric/YouCompleteMe)



# ZSH + Oh my Zsh

Making the terminal useful

```
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

sudo pacman -S powerline powerline-fonts powerline-vim


(Oh My Zsh)[https://ohmyz.sh/]

Ubuntu:
```
sudo apt install zsh
chsh -s $(which zsh)
```



## Powerline -> Powerlevel9k

You then need to select this theme in your ~/.zshrc:

ZSH_THEME="powerlevel9k/powerlevel9k"
Please note if you plan to set a POWERLEVEL9K_MODE to use a specific font, as described in this section of the Wiki, you must set the MODE before OMZ is loaded (look for source $ZSH/oh-my-zsh.sh in your ~/.zshrc).



For both installation and usage



## Pip3

[Pip3](https://pip.pypa.io/en/stable/)

Pip3 python package installer. Dont use `sudo` ...

```
# Ubuntu
sudo apt install python3-pip
```


## Pywal


```
sudo apt install imagemagick
```

User install (No sudo)
```
pip3 install --user pywal

# Add local 'pip' to PATH:
# (In your .bashrc, .zshrc etc)
export PATH="${PATH}:${HOME}/.local/bin/"
```
copy walp.sh into .config/wal/

To execute
Add shortcut:
```
.config/wal/walp.sh 
```
On terminal
```
bash "/home/ema/.config/wal/walp.sh"
```

Add this line to your shell startup file. (.bashrc, .zshrc, .mkshrc etc.)
```
# Import colorscheme from 'wal' asynchronously
# &   # Run the process in the background.
# ( ) # Hide shell job control messages.
(cat ~/.cache/wal/sequences &)

# Alternative (blocks terminal for 0-3ms)
cat ~/.cache/wal/sequences

# To add support for TTYs this line can be optionally added.
source ~/.cache/wal/colors-tty.sh
```


# i3-gaps

[link](https://github.com/Airblader/i3)
[install](https://github.com/Airblader/i3/wiki/Installation)
Add external repo and install
```
#Ubuntu
sudo add-apt-repository ppa:kgilmer/speed-ricer
sudo apt-get update
sudo apt install i3-gaps-wm
```

```
sudo apt-get install i3-wm dunst i3lock i3status suckless-tools
```

DPI shenanigans
http://www.idc-online.com/technical_references/pdfs/electronic_engineering/Change_DPI_in_Ubuntu.pdf
112 DPI 1.16666


## i3-bar
Config on normal file
i3status

```
sudo apt-get install i3-wm dunst i3lock i3status suckless-tools
```



## Terminal: St

Very interesting approach to personalization. Change config file and straight up recompile!

```
#Download, unzip, and run to install
sudo make install
```

## dmenu -> rofi
Copy config file


## Polybar

```
sudo apt-get install cmake cmake-data libcairo2-dev libxcb1-dev libxcb-ewmh-dev libxcb-icccm4-dev libxcb-image0-dev libxcb-randr0-dev libxcb-util0-dev libxcb-xkb-dev pkg-config python-xcbgen xcb-proto libxcb-xrm-dev i3-wm libasound2-dev libmpdclient-dev libiw-dev libcurl4-openssl-dev libpulse-dev libxcb-composite0-dev xcb libxcb-ewmh2
libjsoncpp-dev

git clone https://github.com/polybar/polybar
cd polybar && ./build.sh
./build.sh

```

## Mutt
ncmpcpp
powerline



# Windows

Do we even need this here?



INSTALL STUFF
STEAM
CHROME
...?
VLC
7ZIP
VERACRYPT
MATLAB
VS CODE
NOTEPAD++
GITHUB DESKTOP
GIMP
SPOTIFY



## ~~yaourt~~ trizen
(link)[https://github.com/trizen/trizen]

```
git clone https://aur.archlinux.org/trizen.git
cd trizen
makepkg -si
```
