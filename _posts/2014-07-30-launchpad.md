---
layout: post
title: Canonical Launchpad
cover: cool-old-term-cut.png
date:   2014-07-30 14:51:00
categories: posts
---
Through a [tweet](https://twitter.com/nixcraft/statuses/494081428661870593), I stumbled upon [cool-old-term](https://github.com/Swordifish90/cool-old-term), a terminal emulator with the looks of an old cathode tube screen realized with QML.
It was a funny idea and because I wrote a small QML Hello World example once, but didn't dig deeper into QML,I decided to check out the sourcecode and give it a look.

But again, I didnt't spent much time reading the QML but rather looked at the C++ terminal plugin behind cool-old-term.

My vim is configured to display spaces and tabs, and because of this I found some of them at unnecessary places. I fixed them out of perfectionism (yeah I know, I am a great guy), and went on to submit my changes.

So it came, that I used [Bazaar](http://bazaar.canonical.com/en/) for the first time, registered at [Launchpad](https://launchpad.net/) and made my first contribution on that platform.

# Terminology #
Bazaar is a version control system which is sponsored by Canonical. It's similiar to git in the way that it's also distributed and doesn't use a central server like for example SVN.

Launchpad is a platform to host sourcecode, report bugs and generally administer open source projects, similar to GitHub or Sourceforge. Like Bazaar it's maintained by Canonical and thus heavily used in the development of Ubuntu Linux related software.

# Making the change #

I just intend to read the code not compile it, so I stay on OSX and install Bazaar via Homebrew.

```
  brew install bzr
```

Since I know nothing more about Bazaar other than what it is and some of it's differences and similarities related to git. I read a the basic introduction [Bazaar in five minutes](http://doc.bazaar.canonical.com/latest/en/mini-tutorial/) to learn the most basic commands.

This was already enough to get me started, so I set my username and checked out the ubuntu-terminal-app.
Like on GitHub you need to register an ssh key on Launchpad, which I copy using the last of the following lines.

```
cd ~/src/ubuntu-terminal-app
$ bzr branch https://launchpad.net/ubuntu-terminal-app
Not checking SSL certificate for launchpad.net.
Branched 101 revisions.

$ bzr whoami "Michael Vetter <g.bluehut@gmail.com>"
$ bzr launchpad-login g-bluehut
$ cat ~/.ssh/id_rsa.pub | pbcopy
```
Now I [paste them to my profile](https://launchpad.net/people/+me/+editsshkeys) and am ready to make my changes.
Adding and commiting files is similar like with git:

```
$ bzr add

$ bzr commit
Committing to: /Users/michael/src/bzr2/ub-kn/bluehut/
modified src/plugin/konsole/Character.h
modified src/plugin/konsole/ColorScheme.cpp
modified src/plugin/konsole/Vt102Emulation.cpp
...
modified src/plugin/konsole/ksession.h
Committed revision 102.

$ bzr push lp:~/g-bluehut/ubuntu-terminal-app/whitespacefix/
bzr: ERROR: Permission denied: "~g-bluehut/g-bluehut/ubuntu-terminal-app/whitespacefix/":
: Cannot create branch at '/~g-bluehut/g-bluehut/ubuntu-terminal-app/whitespacefix'
```

At first I got confused why I didn't have permission to push to my repo and looked for different causes, reading the line again I saw that I wasted the time because of an typo...
The first slash on the line was evildoer. The good thing was, while looking for my mistake I learned that I can abbreviate my last command to `$ bzr push:~/ubuntu-terminal-app/whitespacefix` because Bazaar knows my username already.

My branch is now publicly available on Launchpad, so I [navigate to it](https://code.launchpad.net/~g-bluehut/ubuntu-terminal-app/whitespacefix) and click on *Propose for merging* choose the branch to merge into, which in my case is *lp:ubuntu-terminal-app*, I don't provide a description because I assume the commit message is meaningful enough for this small change and click on *propose merge*.

The change is now [pending for review](https://code.launchpad.net/~g-bluehut/ubuntu-terminal-app/whitespacefix/+merge/228807).

![pending for review]({{ site.baseurl }}/images/ubuntu-terminal-app-review.png)

# The end #

At first Launchpad seemed quite confusing to me, and even though it got better after some time of using it I still think GitHub is much more clear and easier to use.

After committing my change I read some pages which I found during my journey. Thanks again slash-typo!

- [Patches to Packages](http://packaging.ubuntu.com/html/patches-to-packages.html)
- [Fixing a bug](http://packaging.ubuntu.com/html/fixing-a-bug.html)
- [Bazaar for git users](http://doc.bazaar.canonical.com/migration/en/survival/bzr-for-git-users.html)
