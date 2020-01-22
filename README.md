# xrdm
<a href="https://imgur.com/441iQH5"><img src="https://i.imgur.com/441iQH5.jpg" align="right" width="400px" title="source: imgur.com" /></a>
X Resource Database Manager, a small yet powerful command-line tool that allow users to instantly change/set X Resource Database. 
Comment and uncomment colorscheme from your ~/.Xresources is not fun at all. Having hundreds of lines of commented colorscheme is not fun at all either.
Xrdm allows you to have beautifully organized list of colorschemes, settings, and fonts.
Xrdm also allows you to easily change/list/edit the segmented configurations.
From now on, you would not need to comment/uncomment ~/.Xresouces every time!

## Table of Contents

<!--ts-->
   * [xrdm](#xrdm)
      * [Table of Contents](#table-of-contents)
      * [Requirements](#requirements)
         * [Dependencies](#dependencies)
      * [Installation](#installation)
         * [Script](#script)
         * [Directories](#directories)
         * [Enviromental Variables](#enviromental-variables)
         * [Auto Completion](#auto-completion)
         * [Quick Installation](#quick-installation)
      * [Why?](#why)
      * [Usage](#usage)
      * [Formats](#formats)
         * [Presets](#presets)
         * [Font](#font)
         * [Colorscheme](#colorscheme)

<!-- Added by: seungheonoh, at: Sat 18 Jan 2020 05:44:31 PM CST -->

<!--te-->

## Requirements
### Dependencies
* xrdb
	 * Comes with X11-apps package

## Installation
### Script
copy the script to your bin(or any path)

### Directories
Make some directories to store each files of X Resources. 
Here's my recommendation:
```
+-------------------+
|                   |
|Xresource Directory|
| (~/.Xresource.d)  |
|                   |
+--+----------------+
   |
   |    +---------+
   +--> |  fonts  |
   |    +---------+
   |
   |    +---------+
   +--> | colors  |
   |    +---------+
   |
   |    +---------+
   +--> | presets |
   |    +---------+
   |
   |    +---------+
   +--> |programs |
        +---------+
```
However, as long as the environmental variables are current, it should work fine. From now on, you will need to store segmented configure files only at each directories depends on their category. These separated directories will allow user to more efficiently manage their many different kinds of options and settings. 

Also, backing up the directory to github(or any other services) will allow user to easily migrate one system to one another

### Environmental Variables
Here's example for environmental variables for directories above.
Again, this could be varied depends on your directory location.
```bash
# at ~/.bashrc
export XRDM_DIR=~/.Xresource.d
export XRDM_FONT_DIR=$XRDM_DIR/fonts
export XRDM_COLOR_DIR=$XRDM_DIR/colors
export XRDM_PRESET_DIR=$XRDM_DIR/presets
export XRDM_PROGRAM_DIR=$XRDM_DIR/programs
```

### Auto Completion
Auto completion is one thing that makes xrdm powerful, <tab> <tab> and boom!
In order to use auto completion, the script has to be sourced. Here's example.
```bash
# at ~/.bashrc
source xrdm
```
Unlike some other programs, external auto completion script is not required!

### Quick Installation
```bash
# Setting enviromental variables
cat > ~/.bashrc << "EOF"
# Begin xrdm settings 
export XRDM_DIR=~/.Xresource.d
export XRDM_FONT_DIR=$XRDM_DIR/fonts
export XRDM_COLOR_DIR=$XRDM_DIR/colors
export XRDM_PRESET_DIR=$XRDM_DIR/presets
export XRDM_PROGRAM_DIR=$XRDM_DIR/programs

source xrdm
# End xrdm settings 
EOF
```
```bash
# Creating directories
mkdir $XRDM_DIR
mkdir $XRDM_FONT_DIR
mkdir $XRDM_COLOR_DIR
mkdir $XRDM_PRESET_DIR
mkdir $XRDM_PROGRAM_DIR
```
Completed!
Start, enlarging your collection of colorscheme, configurations, and fonts!

## Why?
I bet most of X users have this line in their ```~/.xinitrc```
```
xrdb ~/.Xresources
```
where ~/.Xresouces contains few commented colorschemes and configurations; when you need to change colorscheme, you just have to uncomment the whole colorscheme. How ineffecient. With xrdm, it's just 
```
# at ~/.xinitrc
xrdm preset (your preset)
```
and if you need to change font/colorscheme/program config just run
```
$ xrdm {color, font, program} (preconfigure file)
```
without involving any uncommenting, commenting, tidious jobs.

## Usage
```
   _  _____  ___  __  ___
  | |/_/ _ \/ _ \/  |/  /
 _>  </ , _/ // / /|_/ /
/_/|_/_/|_/____/_/  /_/

X Resource Database Manager

Usage: xrdm SUBCOMMAND

SUBCOMMANDS:
  font - List fonts settings/Apply fonts
  color - List colors settings/Apply colors
  program - List programs settings/Apply settings
  preset - List presets/Apply settings
  edit - Edit given settings file
  add [Type] - Add new settings of the [Type]
  version - print version
  help - print help message

```

## Formats
Each part of configuration should be segmented and stored based on it's category.
### Presets
preset is a powerful feature, it's a presetting value of configuration that is much controllable and user-friendly then having whole ~/.Xresource file.

My ~/.Xresouces file:
```
! seoul256 (dark) theme
*.background: #262626
*.foreground: #d0d0d0
*.color0: #4e4e4e
*.color1: #d68787
*.color2: #5f865f
*.color3: #d8af5f
*.color4: #85add4
*.color5: #d7afaf
*.color6: #87afaf
*.color7: #d0d0d0
*.color8: #626262
*.color9: #d75f87
*.color10: #87af87
*.color11: #ffd787
*.color12: #add4fb
*.color13: #ffafaf
*.color14: #87d7d7
*.color15: #e4e4e4
*.cursorColor: #d0d0d0
*.cursorColor2: #3a3a3a
*.colorBD: #e4e4e4

! ST
st.font:        Iosevka Term Slab:size=12

! urxvt
URxvt*scrollBar:  false
URxvt*font: xft:DejaVuSansMono Nerd Font Mono:size=14
URxvt*letterSpace: -1
URxvt*internalBorder: 20

! Xterm
xterm*faceName: xft:DejaVu Sans Mono Nerd Font Complete Mono:pixelsize=20
xterm*faceSize: 20
xterm*font: fixed
xterm*utf8: 2
xterm*locale:ture

! Demnu
dmenu.selforeground:      #d8dee9
dmenu.background:         #2e3440
dmenu.selbackground:      #bf616a
dmenu.foreground:         #d8dee9

! rofi
rofi.terminal: st
rofi.location: 2
rofi.yoffset: 250
rofi.lines: 5
rofi.columns: 4
rofi.font: Noto Sans 14
rofi.bw: 10
rofi.padding: 0
rofi.eh: 1
rofi.separator-style: solid
rofi.hide-scrollbar: true
```
can be shorten in to with segmented thus controllable files:
```
color seoul256
font iosevka
program urxvt
program xterm
program dmenu
program rofi
```
This not only makes make ~/.Xresource looks cleaner, but makes it more easy to tweak and recombinate. 
Preset files can be configured as colection of xrdm subcommands. One subcommands at a line.

### Font
```
! $XRDM_FONT_DIR/font1
! ST
st.font: font1:size=12
! urxvt
URxvt*font: xft:font1:pixelsize=12
! Xterm
xterm*faceName: xft:font1:pixelsize=12
```
### Colorscheme
```
! $XRDM_COLOR_DIR/color1
! ColorScheme1 Xresources palette
*.foreground: #F8F8F2
*.background: #282A36
*.color0:     #000000
*.color8:     #4D4D4D
.
.
.
```


