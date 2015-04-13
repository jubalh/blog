---
title: "symfony on osx"
date:   "2000-10-30"
categories: "posts"
draft: "true"

---

# install code sniffer #
there are 3 ways of installing code sniffer
1. using homebrew:  brew install php-code-sniffer
2. using pear: pear install PHP_CodeSniffer
3. using Composer: composer global require "squizlabs/php_codesniffer=*"

# set symfony2 standard #
go to code sniffer directory

when using homebrew since php-code-sniffer is in a git repository already because of using homebrew we will clone somewhere else and copy the files.

cd ~
git clone https://github.com/escapestudios/Symfony2-coding-standard
cp -r Symfony2-coding-standard /usr/local/Cellar/php-code-sniffer/1.5.5/CodeSniffer/Standards
without .git!
phpcs --config-set default_standard Symfony2

# vim #
in vimrc
Bundle 'joonty/vim-phpqa'


# Read about #
about pear and codesniffer: http://pear.php.net/manual/en/package.php.php-codesniffer.coding-standard-tutorial.php
http://techportal.inviqa.com/2009/10/12/usphp_code_sniffer/

learn composer: https://getcomposer.org/doc/00-intro.md

shows how to use manually and installation in linux: http://coreymaynard.com/blog/finding-what-stinks-and-cleaning-up-the-mess/
