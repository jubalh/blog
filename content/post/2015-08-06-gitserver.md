---
title: "The dotfiles"
date:   "2015-08-06"
categories: "posts"

---

I store most of my configuration files [publicly](https://github.com/jubalh/dotfiles) on GitHub.
However there are some programs which contain passwords in their config files, among these are irssi, Pidgin and osc.

It was very annoying to always configure those programs from the start on each computer.

So today I took the time and created a small *server* out of an old netbook.
I switch it on on days I know I need a service on it and leave it off if I don't.

It works as a git server so I can store my *private-dotfiles* in there. I also configured it to connect to my companies VPN and run irssi on it in a tmux session. This way I can reboot/shutdown my main computer as much as I want or can switch to another computer which I need to do from time to time. I would have used my Raspberry Pi for this, but I turned it into a game station and gave it to someone else.

# Git #
On the netbook I run Funtoo and git was already installed on it.

First I created a new user as which we will log in, and added my public SSH keys to the *authorized_keys* file:

```
$: ssh root@avalon
$: useradd git
$: su - git
$: mkdir .ssh
$: chmod 700 .ssh
$: vim .ssh/authorized_keys
```

The public SSH key can be found in `~/.ssh/id_rsa.pub`. So I copied the ones from all of my computers and just pasted them into the file, one after another.
The reason for using SSH keys is that only computers that got registered (which key got added) can access the repos there, so we won't user a password.

I store all git repos in `/home/git/`. There I create a folder with the suffix *.git* for each repo:


```
$: mkdir privatedotfiles.git
$: cd privatedotfiles.git
$: git init --bare

Initialized empty Git repository in /home/git/privaterepos.git/
```

From my main machine I now run the following to push my private dotfiles to the server:

```
$: cd ~/where/my/privatedotfiles/reside
$: git init
$: git add . && git commit -m "initial"
$: git remote add avalon git@avalon:/home/git/privaterepos.git
$: git push avalon master
```

And from all the others I just clone to have it on my machine:


```
$: git clone git@avalon:/home/git/privaterepos.git

```

In case you already have a git repository on your machine and just want to add the new remote repository use 

```
git remote add avalon ssh://git@avalonsipordomain.net:23/home/git/privaterepos.git
```

References: [git-scm](https://git-scm.com/book/it/v2/Git-on-the-Server-Setting-Up-the-Server)
