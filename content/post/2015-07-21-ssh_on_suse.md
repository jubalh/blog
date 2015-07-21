---
title: "Enable ssh on openSUSE"
date:   "2015-07-21"
categories: "posts"

---

Okay, going to explain how to install and enable ssh on your openSUSE box here. Some people didn't seem to get it to work altough there is [an older article](http://www.fene-blog.de/linux/ssh-zugriff-opensuse-112-113-installieren-freischalten-aktivieren/) describing how to do it with SysVInit. My article will have the same format just with the new commands. On the [openSUSE wiki](https://en.opensuse.org/SDB:OpenSSH_basics) they explain it via yast.

- Check if package is installed:

```
zypper if openssh
```

Install package if it isn't installed:

```
zypper in openssh
```

- Check if ssh server is running:

```
systemctl status sshd
```

Start service:

```
systemctl start sshd vs rcsshdstart?
```


Check if service is launched at startup:
```
systemctl is-enabled sshd
```

Launch it on system startup:
```
systemctl enable sshd
```

- Check if Firewall blocks port 22 for ssh:

```
SuSEfirewall2 status | grep 22
```

If you don't get any output from that command open the port with:

```
SuSEfirewall2 open EXT TCP ssh
SuSEfirewall2
```

That's it!

