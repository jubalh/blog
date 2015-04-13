---
title: "nudoku"
date:   "2015-02-27"
categories: "posts"
draft: "true"

---

learned:

ncurses
Makefile
autotools
	- http://mij.oltrelinux.com/devel/autoconf-automake/
	- http://inti.sourceforge.net/tutorial/libinti/autotoolsproject.html
	- https://autotools.io/autoconf/index.html
	- https://blog.flameeyes.eu/tag/autoconf#gsc.tab=0
	- http://www.freesoftwaremagazine.com/books/autotools_a_guide_to_autoconf_automake_libtool
	- https://bitbucket.org/mgorny/pshs/src

ebuild:
	- http://wiki.gentoo.org/wiki/Basic_guide_to_write_Gentoo_Ebuilds
	- https://devmanual.gentoo.org/quickstart/
	- http://devmanual.gentoo.org/
	- http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/www-servers/pshs/pshs-9999.ebuild?view=markup

https://help.github.com/articles/creating-releases/
eautoreconf

http://gpo.zugaina.org/AJAX/Ebuild/2960886/View

<Pinkbyte> colonolGron, look at dev-ml/gd4o/gd4o-1.0_alpha5.ebuild for example about how to deal with different tarball and Gentoo version scheme naming

I know: Every computer kid has the deep desire to write a curses based application at least once in a lifetime.
Of course, being on terminal is just cool. The clean and minimalistic environment. Knowing that every computer can handle your challenging and artful graphics is deeply satisfactioning too. Like that you will never exclude anybody from using your awesome application.
And of course, growing up with text based interfaces it brings to mind warm childhood memories.

So yeah. I wanted to write a pretty text based application since, well, since alyways. I even started several attempts, creating prototypes for different programs. However all the time it was a too ambiguous goal, since everybody unfortunately has limited free time.

A couple of weeks ago I was ill, resting on the couch while listening to some audio book and playing Sudoku.
Indeed, it was pretty comfortable. On the next day, I knew what text based application I would do, and this time I would finish it. Not too demanding and quite some fun.

Thus I got out my laptop and started hacking away on *nudoku* - *n*curses based s*udoku* game.
