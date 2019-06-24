# Big TODOs

1. Doesn reflect actual system. Use new Data | Programs | Games structure
a. Fix tables
2. Separate Windows from Linux
3. Upload Arch dot files
4. Zsh instalation details
5. Link to wal script
6. Pictures for finished look


# My System

SSD -> Sda

| Windows         | Ubuntu      | Manjaro   | Swap|
| ---|---|---|---|
|  a1/a2          | a6          | a7        | a5  |

HDD -> Sdb

| Windows         | Ubuntu      | Manjaro   | Swap|
| -------------   |-------------| -----     |-----|
|  b1          | b2          | b3        | b4  |
|  D:/          | Encrypted          | /home        | /home  |


# Dotfiles


STUFF HERE

GIT

ZSH

ZSH COMPLETION

## Clone
```
git clone --bare https://github.com/smallAtlas/dotfiles.git $HOME/.vimrc 
```

# Ubuntu

## TO DOs
1. 


## Time 

To avoid conflicts with Windows, set Linux time to local

```
timedatectl set-local-rtc 1 --adjust-system-clock
```

## VIM

Install Vim

```
sudo apt install vim
```
## Add Vundle

Install vundle plugin manager for Vim 
[Vundle](https://github.com/VundleVim/Vundle.vim)

```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

## Add You Complete Me

[YouCompleteMe](https://github.com/Valloric/YouCompleteMe)

Ubuntu 16.04 and later:
```
sudo apt install build-essential cmake python3-dev
```
Compiling YCM with semantic support for C-family languages through libclang:
```
cd ~/.vim/bundle/YouCompleteMe
python3 install.py --clang-completer
```


## Add veracrypt

## Add Google Chrome

Should I switch to Chromium?

[Chrome](https://www.google.com/chrome/)

## Add Spotify

Install Spotify through Ubuntu store

[Spotify Download](https://www.spotify.com/es/download/linux/)

## Pip3

Pip3 python package installer
Dont use `sudo`
[Pip3](https://pip.pypa.io/en/stable/)

```
# Ubuntu
sudo apt install python3-pip
```

## Theming

### Pywal

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


### Papirus icons

[Papirus](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme/)

```
sudo add-apt-repository ppa:papirus/papirus
sudo apt-get update
sudo apt-get install papirus-icon-theme
```
## Fonts

### Roboto
```
sudo apt-get install fonts-roboto
```
### Iosevka

[Iosevka](https://typeof.net/Iosevka/)

Download term

[download](https://github.com/be5invis/Iosevka/releases/tag/v2.2.1)

```
# Linux : Copy the TTF files to your fonts directory
cp fonts ~/.fonts
# Run: 
sudo fc-cache
```
Use "Iosevka Term Regular" on terminal


