---
title: "Linux on Macbook"
date:   "2015-04-15"
categories: "posts"

---

# Keyboard #
$ xmodmap -e 'keycode 64 = Alt_L'

$ xev|grep keysym
state 0x2010, keycode 36 (keysym 0xff0d, Return), same_screen YES,

Try setkxbmap, there seem to be some mac layouts there.
xmodmap -e 'clear mod1' -e 'keycode 64 = Alt_L' -e 'add mod1 = Alt_L'
thanks to CcxCZ
