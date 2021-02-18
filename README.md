# Emojis-4-Arch
*Simple way to add emojis for Arch Linux.*

Simple tutorial to install emojis on Arch Linux. Note that this install of emojis will only effect certain applications. This will not add emoji support to every single application on Arch Linux.

## Installation
To install the emoji package get the `noto-fonts-emoji` with pacman (Arch Linux's package manager.) There are other fonts listed on the Arch Wiki [here](https://wiki.archlinux.org/index.php/Fonts#Emoji_and_symbols). I will list all of the commands to install them here:  
`sudo pacman -S noto-fonts-emoji` (This is Google's open-source emojis.)  
`sudo pacman -S ttf-joypixels` (This is the EmojiOne creator's proprietary Emoji 13.1.)  
Installing Twitter's open-source emojis are a little harder to install because you will need to get it from the AUR (Arch User Repository.) Please do,  
`git clone https://aur.archlinux.org/ttf-twemoji` (This is will clone the files from the repo.)  
`cd ttf-twemoji` (This will change the directory to the folder.)  
`makepkg -si` (This will install the emojis.)

This will install the fonts, but you are not entirely done yet. You will need to create the configuration file so the emojis actually work.

## Creating the Configuration File
To create the configuration file you will need to go to the directory `~/.config/fontconfig/conf.d/01-emoji.conf`. If you do not see the *fontconfig* folder you will need to create the folder. You may also want to create the *conf.d*. Once you are in the *conf.d* create a file and name it to `01-emoji.conf` and put the following:  
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <!-- Use Google Emojis -->
  <match target="pattern">
    <test qual="any" name="family"><string>Segoe UI Emoji</string></test>
    <edit name="family" mode="assign" binding="same"><string>Noto Color Emoji</string></edit>
  </match>
</fontconfig>
```  
Replace `Noto Color Emoji` with the emoji pack you installed.  
Example:  
`Twemoji`  
`Joypixels`  

## Congrats
After that you are finished! Now refresh the applications that you need emoji support on and it shall appear as a emoji rather than a weird rectangular box! :smile: :muscle:
