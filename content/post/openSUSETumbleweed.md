---
title: "funtoo overlay"
date:   "2000-07-16"
categories: "posts"
draft: "true"

---

Sometimes problem libzypp is mising because during update something went wrong.
correct that by:
root@kallisti /home/michael # rpm -e --nodeps zypper
wget http://download.opensuse.org/factory/repo/oss/suse/x86_64/zypper-1.12.4-1.2.x86_64.rpm
rpm -i zypper...

btrfs problems
 snapshots taking same size until kernel version X
 no size left.
 plugging in usb stick, add subvol. run balance, delete subvol.
 run scrub once in a while
 

