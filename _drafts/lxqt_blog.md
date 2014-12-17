---
layout: post
title: Dev LXQt on Funtoo
cover: cover.jpg
date:   2014-12-13 17:00:00
categories: posts

---

This post is about making Funtoo/Gentoo ready for developing on LXQt or just have the latest version installed for testing.
Some people came with questions about this to the #lxde IRC channel, and since most of the LXQt developers run Arch Linux there is not always somebody online who can help with Gentoo questions.

Note: I am doing this on Funtoo, but will use "Gentoo" from now on since it is the same procedure for both.

The main point of confusion is that Gentoo has Qt5 still masked, but that is not problem at all.
In this post I will descript how to unmask Qt5 install, unmask the needed packages and install them. Then we will clone the LXQt git repository, build it and start it.

# Unmasking #
<br/>
First let's unmask Qt5.

```
$: vim /etc/portage/profile/use.mask
```

And write **-qt5** in there. Since Qt5 *is* masked, we need to take it away(-).

Now add the following lines to */etc/portage/package.unmask*:
<br/>

```
>=kde-frameworks/kwindowsystem-5.4.0
>=dev-qt/qtwidgets-5.4.0
>=dev-qt/qtx11extras-5.4.0
>=dev-qt/qtgui-5.4.0
>=dev-qt/qtcore-5.4.0
>=dev-qt/qtxml-5.4.0
>=dev-qt/qtsvg-5.4.0
>=dev-qt/linguist-tools-5.4.0
>=dev-libs/libpcre-8.36
>=kde-frameworks/kguiaddons-5.4.0
>=dev-qt/qtdbus-5.4.0
>=dev-qt/qtconcurrent-5.4.0
>=dev-qt/qtsvg-5.4.0
>=dev-qt/qtscript-5.4.0
>=dev-qt/qtprintsupport-5.4.0
>=kde-frameworks/kguiaddons-5.4.0
```

This will unmask all the names packages with from version 5.4.0 and on. You could also just add *=kde-frameworks/kguiaddons-5.4.0* without the *>* to only unmask that one version.
Since you might read ths blog post later I added it to make sure it works on all later versions too. And besides I use it like that, too.

# USE flags #

Fire up *vim* and add the following packages with USE flags to your */etc/portage/package.use*:

```
dev-libs/libpcre-8.36 pcre16
sys-auth/polkit-qt qt5 -qt4
```

# Installation #
## Dependencies ##

First let's try if an example KF5 package can be installed.

```
$: emerge -a kwindowsystem

These are the packages that would be merged, in order:

Calculating dependencies... done!
[ebuild   R    ] dev-libs/libpcre-8.36  USE="pcre16*" 
[ebuild  NS   #] dev-qt/qtcore-5.4.0 [4.8.6-r1] USE="icu -debug -systemd {-test}" 
[ebuild  N    #] dev-qt/qtxml-5.4.0  USE="-debug {-test}" 
[ebuild  N    #] dev-qt/linguist-tools-5.4.0  USE="-debug -qml {-test}" 
[ebuild  N     ] dev-libs/extra-cmake-modules-1.4.0  USE="-doc" 
[ebuild  NS   #] dev-qt/qtgui-5.4.0 [4.8.6-r1] USE="gif harfbuzz jpeg opengl png udev xcb -accessibility -debug -egl -eglfs -evdev -gles2 -ibus -kms {-test}" 
[ebuild  N    #] dev-qt/qtwidgets-5.4.0  USE="opengl png xcb -debug -gles2 {-test}" 
[ebuild  N     ] kde-frameworks/kf-env-3 
[ebuild  N    #] dev-qt/qtx11extras-5.4.0  USE="-debug {-test}" 
[ebuild  N    #] kde-frameworks/kwindowsystem-5.4.0  USE="X nls -debug -doc {-test}" 

Would you like to merge these packages? [Yes/No] Yes
```

Nice. So our changes were right.

For LXQt we will need to install the following additional packages:

- kguiaddons
- liboobs
- polkit-qt
- qtsvg
- qtscript
- qtprintsupport
- libconfig

And because LXQt uses openbox as it's window manager you should also install the *openbox* package.
Actually you can configure it to use another one, but the install script still checks for *obrender* and another package by openbox.

# Building #

Okay, just go somewhere and clone the repo in there. I have the habit of putting all code in *~/src*.

```
$: cd src
$: git clone https://github.com/lxde/lxqt
$: git submodule init
$: git submodule update --remote --rebase

$: LXQT_PREFIX=/usr USE_QT5=true ./build_all.sh
```

The project is splitted in different repositories. The first git command will clone the main repository, then we will get the others, which are added as git submodules.
Although there is also an CMake script in the repo, this doesn't get much love from the devs, at least I have never found it to work properly. I guess eventually it will get removed and only the bas script will be there.
Qt5 is still not set as default in the build script, altough LXQt 0.8.0 is able to use Qt5, and from any version greater than the it is even mandatory. Qt4 support is totally dropped. Anyways, that's the reason we need to tell the script in detail. Also I want to install all stuff in the */usr* directory, so I added the prefix.

That's it. We did it.

Last step: add one of the following lines to your *.xinitrc*, or in case you use a loging manager, configure it to start LXQt:

```
exec ck-launch-session dbus-launch --sh-syntax --exit-with-session startlxqt
exec startlxqt
```

<br/>
<a href="{{ site.baseurl }}/images/lxqt_screenshot_1920x1080.png">
<img src="{{ site.baseurl }}/images/lxqt_screenshot_1920x1080.png" alt="LXQt screenshot" style="width: 734px;"/>
</a>

# Other Options #
Gentoo offers several ebuilds for LXQt, for example *lxqt-meta* which will give you a working 0.7.0 version of the desktop environment. 0.8.0 is also available but masked, the packagers decided to only support the Qt5 version of 0.8.0 altough it's not mandatory.
There is also an live ebuild, but since this post is centered around people who want to change the code and not just install the latest version available I described the way using git.

# References #

[Build LXDE-Qt from source](http://wiki.lxde.org/en/Build_LXDE-Qt_From_Source)

[Qt5 on Gentoo Wiki](http://wiki.gentoo.org/wiki/Qt/Qt5)

[Frameworks 5 on Gentoo Wiki](http://wiki.gentoo.org/wiki/KDE/Overlay/Frameworks_5)
