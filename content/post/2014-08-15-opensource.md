---
layout: post
title: Participate in open source
cover: cover.jpg
date:   2014-08-15 11:25:00
categories: posts
started at:   2014-07-16 11:25:00

---

On twitter and on some blogs there are quite some people describing themselves as *open source evangelists* and stuff like that. Some of whom I know personally. And all they do is running around and talking about how great open source is. Mostly because, they don't have to pay money for using software. Which undoubtedly is a valid reason, but not the only one. Anyway I would appreciate if they would go deeper into the subject and inform themselves about the philosophy behind Free Software, participate in open source either by writing code, creating artwork, translating or creating documentation instead of only spreading the word. Since, In my opinion, open source is already popular, and doesn't need any more advertising but people who **do** something.

Which brings me to the point: Most people hype open source only because they don't have to pay anything for using it. That's what they mean by *open source evangelist*. The second most frequent reason people claim they are *linux geeks* is because its **in**. At university I met (too) many people talking about Linux and claiming they know their shit but have no idea about anything.

Just google your stuff, read a short overview and claim you know something. Real knowledge about a subject isn't required only shallow understanding and reading the headings.

# Stop crying, man #
Okay, I hear ya.
Now let's get to the point :-)

I am using GNU/Linux since 10 or 11 years and since a few months I wanted to participate, learn more and give back to the community.

Sometimes it's hard to find the right way to do something, this post is about ways to contribute and my first contributions.

# Finding a project #
For several weeks I was on and off looking at [OpenHatch](http://openhatch.org/search/) and scanning the abandoned projects at [SourceForge](http://sourceforge.net/) and the likes.

Somehow I didn't find the right fit.

So after looking at several projects which didn't match me, I let go of the idea, shortly after that, I found my first project.

## Example Contributions ##
I am only going to cover the ways in which I contributed to Open Source software, while mentioning an example.

### HashTWM ###
At my last employer we were running Windows. Because I was spoiled by using [i3](http://i3wm.org/) at home, which increased my speed and productivity, I wanted to be as fast navigating around in Windows.

So it came, that I was looking for a tiling window manager for Windows.
At GitHub I found [HashTWM](https://github.com/ZaneA/HashTWM), and I think this was the project I tried to contribute to.

I remember being quite interested in understanding the code. My [first commit](https://github.com/ZaneA/HashTWM/commit/6f3af81cbe7964c4b01a3a8b6f059a5d3fdf294e) was to move the sourcecode to it's own directory. And then created a VisualStudio project beside the existing Makefile. Both were received by the creator welcomly. Which encouraged me to look for more ways to help.

I made the project ANSI C compatible and fixed some small error which occured on newer versions of Windows because of the duplicate function called *RegisterShellHookWindowProc*.

Funny enough I didn't use HashTWM long; only considering it led to my first open source contribution without really looking for it.

### Diaspora Webclient ###
While checking out mobile applications for [Diaspora](https://diasporafoundation.org/) I came across [Diaspora-Webclient](https://github.com/voidcode/Diaspora-Webclient) on [F-Droid ](https://f-droid.org/repository/browse/?fdid=com.voidcode.diasporawebclient). Right after starting the app, there was welcome message displayed. And there was a typo in it. Of course Mr. Perfectionista couldn't endure that. So I pulled the source, corrected the typo and [pushed my change](https://github.com/voidcode/Diaspora-Webclient/commit/1bd1175a9bfd6c0d8d63ed7960db92b5f9f3c984). I know it's nothing fancy, but still it's increases the overall value of the product. At least I tend to think so..

### Vimperator Colors ###
Like a lot computer folks, I enjoy using **vim**, and like the sometimes overly-enthusiastic person I am, I wanted to vimify **everything**. To have Firefox understand the vi-keybindings I installed the [Vimperator plugin](https://addons.mozilla.org/de/firefox/addon/vimperator/).

Browsing without taking my hands of the keyboard. I was really happy.

The only thing, that managed to impair my joy was the not-so-pretty standard color theme. No problem, let's find some on google!
Quite strange was, that the [main color theme repository](https://github.com/vimpr/vimperator-colors) contained merely *one* theme! On google I found some more, some worked, some did not. So I made them work and put my fresh collection [repository](https://github.com/jubalh/vimperator-colors) on GitHub. It was a little better than having them scattered around the web, but for others to easily find them I made pull request to the main repository. I did wait for some time, because I was not sure if it really was the official repo, but the guys on IRC told me it was the right one.
Although it took *one year and a half* until the owners [saw my pull request](https://github.com/vimpr/vimperator-colors/pull/1) and accepted it, I helped to expand the color theme collection from 1 to 13.

### Vifm ###
Still on the course to use my freshly learned vi-keybindings everywhere I came to use [vifm file explorer](http://vifm.info/).
Regarding color themes, it was the same situation like with vimperator. So I created a [GitHub repo](https://github.com/vifm/vifm-colors) to share my collection of themes. I collected 7 stars and got 2 people to watch my repo, which was something new and exciting for me. After some time the [vifm organisation](https://github.com/vifm) was created, and the vifm source repository was moved from ksteen to the organisation. Due to the creation of the organisation I got an email from the maintainer and main developer of vifm, asking me whether I wanted to transfer my repo containing the collections to the vifm organisation. Of course I wanted to!

While porting vim color themes to vifm, I realized that vifm only supports 8-Bit colors.
I emailed the author and when he politely replied that he will include more color support, I offered to do it myself, to get some experience. He agreed and encouraged me to do so. So it came [I made vifm support 256 color names](https://github.com/vifm/vifm/pull/43/commits).

Later I made a minor contribution by [removing trailing whitespaces](https://github.com/vifm/vifm/pull/46), which is a bad habit of mine. I just can't stand them... ;-)

### Jessy ###
At Uni we had to learn Java. However the exercises didn't really catch my attention. So to understand all the concepts I thought about creating a [project of my own](https://github.com/jubalh/jessy).
Because I was playing chess at this time, I wanted to create a little chess game. Actually just the representation of a board, containing figures. Nothing else. No move checking, no KI, man.. at first I didn't plan to give the possibillity to move at all. Just a representation of the board.
I had so much fun with this project. Probably I will create a post of it's own for it.

Anyway, at some point I came to use a chess engine, called [Flux](http://fluxchess.com/), through including it in my project I came to [fix a small error](https://github.com/fluxroot/flux/pull/79) in the project setup.

Through Jessy I learned a lot, at some point two people joined the team and contributed to it. I learned how to manage and coordinate a project over the internet and to use GitHub properly. And I found a mentor who was an experienced Java developer who checked my code.

### Homebrew ###
After Jessy, I wanted to learn more about Java, and because I was interested in web development for some time, I looked at different frameworks.

I came across the [Play Framework](https://www.playframework.com/) and looking for a quick way to install it, `brew search`ed it.
The Tutorial used version 2.3 of Play, which was newer than what Homebrew provided, so I intended to update the formula.

Because Play switched to Typesafe-Activator it [turned out](https://github.com/Homebrew/homebrew/pull/30262) that there was a formula containing Activator and thus Play.
Someone pointed out that version 2.2 of Play was still in heavy used and so it came, I [added an caveat](https://github.com/jubalh/homebrew/commit/67f8919f11b0e7ca5b8987876aa750ceabdf2d4f) but then [removed Play altogether](https://github.com/jubalh/homebrew/commit/19413541411e58759faadde24138c789d80ee944) and [added it to homebrew-versions](https://github.com/Homebrew/homebrew-versions/pull/462).

## Reading code ##
Generally I think reading code of others is a good thing to do. Sometimes you can learn a lot from it, and it trains you to understand different styles and easily comprehend what's going on. Though I have to say, most of the time it's hard for me ;-) Understanding comes slowly, but that is okay for now.

So whenever I came across something interesting, or read about new open source software on [Hacker News](https://news.ycombinator.com/) and had some free time (or not) I checked out the code and sometimes I was able to make some minor improvements. Mostly making the coding style consistent or hunting whitespaces while reading the code.

In such ways I contributed to [HElib](https://github.com/shaih/HElib), a library that implements homomorphic encryption, the Telegram [desktop](https://github.com/telegramdesktop/tdesktop) and [console](https://github.com/vysheng/tg) clients, and the [ubuntu-terminal-app-plugin](https://code.launchpad.net/~ubuntu-terminal-dev/ubuntu-terminal-app/plugin) used by [cool-old-term](https://github.com/Swordifish90/cool-old-term).

When I came across cool-old-term I wrote a post entitled [Canonical Launchpad]({% post_url 2014-07-30-launchpad %}). Check it out to read more about my contribution.

# Ways to contribute #
- I used something and came across an error/something unclear as a user: *Diaspora-Webclient, Homebrew*
- I used something and wanted to improve it: *vifm*
- I created something: *Jessy*
- I read code and found a mistake/inconsistent style: *HELib, cool-old-term, telegram console, telegram desktop, vifm*
- I wrote software and use third party libraries, but came across an error: *Flux*
- Creating color themes/artwork: *vifm, Vimperator*

# Fazit #
I am aware that most of my contributions were only of a minor nature. Anyway I learned something from every single one of them. And in my eyes every little improvement is an improvement still.
