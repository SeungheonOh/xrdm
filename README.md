# xrdm
X Resource Database Manager, a small yet powerful command-line tool that allow users to instantly change/set X Resource Database. 
You don't need to change your ~/.Xresouces every time from now on!



## Requirements
### Dependencies
 - xrdb
  - Comes with X11-apps package

## Installation
1. copy the script to your bin(or any path). 
2. *(Optional but Strongly recommanded)* add ```source xrdm``` for bash autocompletion
3. You're ready to go. Enjoy!

### Directories
Make some directories to store each files of X Resources. 
Here's my recommandation:
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
However, as long as the enviromental variables are current, it should workd fine.

### Enviromental Variables
Here's example for enviromental variables for directories above.
Again, this coud be varied depends on your directory location.
```bash
# at ~/.bashrc
export XRESOURCE_DIR=~/.Xresource.d
export XRESOURCE_FONT_DIR=$XRESOURCE_DIR/fonts
export XRESOURCE_COLOR_DIR=$XRESOURCE_DIR/colors
export XRESOURCE_PRESET_DIR=$XRESOURCE_DIR/presets
export XRESOURCE_PROGRAM_DIR=$XRESOURCE_DIR/programs
```

### Auto Completion
Auto completeion is one thing that makes xrdm powerful, <tab> <tab> and boom!
Inorder to use auto completion the script has to be sourced. Here's example.
```bash
# at ~/.bashrc
source xrdm
```
Unlike some other programs, different auto completion configuration is not reqired!

### Quick Installation
```bash
# Setting enviromental variables
cat > ~/.bashrc << "EOF"
# Begin xrdm settings 
export XRESOURCE_DIR=~/.Xresource.d
export XRESOURCE_FONT_DIR=$XRESOURCE_DIR/fonts
export XRESOURCE_COLOR_DIR=$XRESOURCE_DIR/colors
export XRESOURCE_PRESET_DIR=$XRESOURCE_DIR/presets
export XRESOURCE_PROGRAM_DIR=$XRESOURCE_DIR/programs

source xrdm
# End xrdm settings 
EOF
```
```bash
# Creating directories
mkdir $XRESOURCE_DIR
mkdir $XRESOURCE_FONT_DIR
mkdir $XRESOURCE_COLOR_DIR
mkdir $XRESOURCE_PRESET_DIR
mkdir $XRESOURCE_PROGRAM_DIR
```
Completed!
Now put fonts settings at font, color settings at color, and so on!

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
This not only makes make ~/.Xresource looks cleaner, but makes it more easy to tweak and recombinate

### Font
```
! $XRESOURCE_FONT_DIR/font1
! ST
st.font: font1:size=12
! urxvt
URxvt*font: xft:font1:pixelsize=12
! Xterm
xterm*faceName: xft:font1:pixelsize=12
```
### Colorscheme
```
! $XRESOURCE_COLOR_DIR/color1
! ColorScheme1 Xresources palette
*.foreground: #F8F8F2
*.background: #282A36
*.color0:     #000000
*.color8:     #4D4D4D
.
.
.
```
