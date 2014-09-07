---
layout: post
title: Changing Flags
cover: cover.jpg
date:   2014-09-04 12:28:00
categories: posts

---
Since March 2014 I am running [Funtoo Linux](http://www.funtoo.org/Welcome) on one of my main machines.
It's a great distribution, I learn a lot while using it.

Updating always went smoothly until yesterday, when I had troubles for the first time.

I started my computer after the update and couldn't connect through to my wifi anymore. I wondered what was the reason but didn't find it fast enough, because I had to go to work. Taking the notebook with me I connect it to the  universities LAN and all goes well.

At home again, I try to find the error. I use NetworkManager and nm-applet to configure my connections. nm-applet always gave me an *device not present*
I tried to remember if any configuration files changed during updating. Usually I update like this:

```
  $: emerge --sync
  $: emerge -aDNuv world
  $: emerge --depclean
  $: revdep-rebuild
  $: dispatch-conf
```

I didn't remember any network related changes during *dispatch-conf*.

When searching for wlan0 in dmesg the only thing I got was:

```
  IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

I booted into my Debian which is installed alongside Funtoo, in case I break something but need a working environment for work. wifi worked here. Good. It was neither a hardware problem nor was the access point unavailable.

Not wanting to reboot all the time to try things out (I was listening to an audiobook ;D), I chrooted into Funtoo:

```
  $: cd /mnt/funtoo
  $: mount -t proc none proc
  $: mount --rbind /sys sys
  $: mount --rbind /dev dev && cp /etc/resolv.conf etc/
  $: chroot /mnt/funtoo /bin/bash -i
```

I tried an `iwlist scan` which showed me my access point, seems like network and wifi was generally working, must be an issue of networkmanager or nm-applet.
On IRC I stumbled upon somebody who solved the same problem a day ago. And he advised me to look for changed use flags.

```
  $: emerge -pv networkmanager

  These are the packages that would be merged, in order:

  Calculating dependencies -  ... done!
  [ebuild   R    ] net-misc/networkmanager-0.9.8.10-r1  USE="consolekit dhcpcd introspection nss policykit resolvconf -avahi -bluetooth -connection-sharing -dhclient -gnutls -modemmanager -plugins_openconnect -plugins_openswan -plugins_openvpn -plugins_pptp -plugins_sstp -plugins_vpnc -ppp -systemd {-test} -upower -vala -wext -wifi" 0 k
```


Ohoh! What's that **-wifi**!

Okay let's see if this flag is useful in general:
```
  $: eix -U wifi
```

Shows me a bunch of packages which contain this flag, for example *Thunderbird*. Uh? What will this flag do in Thunderbird?
Okay, since I have no idea, I am going for the standard way and change the use flag on a per package basis.

Adding `net-misc/networkmanager wifi` to */etc/portage/package.use* and doing an `emerge -aDNuv networkmanager` to rebuild the package I solved the problem.

So because netoworkmanager got an additional flag to enable wifi management which was disabled by default my wifi didn't work anymore. This was the first time I came across a problem like this and I wouldn't have thought about this before. Let's keep this in mind!
