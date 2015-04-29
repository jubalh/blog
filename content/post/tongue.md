---
title: "tongue"
date:   "2015-04-29"
categories: "posts"

---

# Preface #

I wanted to learn go. But as everybody knows, I need do use something to learn how to use it.
After a while reading articles and watching talks about Go I started to think about what I could do, and what I did, was creating (a) tongue.

I like learning languages, yeah, human languages that is. Unfortunately I am not able to speak any single one except my native language to a good level but I like it anyways. You can't be good at everything you know?

When creating tongue, I wanted it to be as simple as possible. It should be easy to use it with other programs. Meaning it should just store and retrieve my vocabulary, but I might use different things to display them. Maybe I would like to interact directly with tongue on the command line, but chances are good I will also want to use it to display my "vocabulary of the hour" via conky. Or use the notifcation-daemon to display a foreign word to me.

Long story short, I tried to adhere to the UNIX philosophy, of doing just one task, and doing it well.

Okay I am not so sure about the latter, but i will try my best.

# Development #

I love Go because it let's me stay on the command line all day long. I used vim with the vim-go plugin to write my code. The experience was awesome.
Go is such a simple and clean language that vim is perfectly capable of handling it without any heavy customization. At work I am coding in PHP using the Symfony2 Framework, and at first I tried to do it with vim. But at some point a collegue made me try out PHPStrom, and I have to say it's good. There is even a vim plugin which makes things much more comfortable. So it's a good trade-off.

The beautiy about Go is, that you don't need a heavy IDE. *Everything* works great with vim.

Usually I opened a terminal, started tmux, created two panels with vim on top and a shell below. I coded in vim, switched to the pane below and built and tested my program.

gofmt
govet
goimports
gd
gofix
gocover
golint

release rest-reminder post first. and link to it for same possiblities with notifdy-send etc.

conky
TEXT
${execi 5 tongue show}

