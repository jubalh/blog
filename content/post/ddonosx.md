---
title: "dd on osx"
date:   "2000-11-11"
categories: "memos"
draft: "true"

---

diskutil list
diskutil unmountDisk /dev/diskX
sudo ddif=/path of=/dev/diskX bs=1m
1M on GNU dd
diskutil eject /dev/diskX
