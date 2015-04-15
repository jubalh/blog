---
title: "Linux on Macbook"
date:   "2015-04-15"
categories: "posts"

---

# Keyboard #
$ xmodmap -e 'keycode 64 = Alt_L'

$ xev|grep keysym
state 0x2010, keycode 36 (keysym 0xff0d, Return), same_screen YES,
