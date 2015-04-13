---
title: "my wat to php - 1"
date:   "2014-10-30"
categories: "posts"
draft: "true"

---

Working two jobs while studying at university, doing sports, being around for
family and friends, it's sometimes hard to find time for all I want to do and
learn.

For example I wanted to learn more about PHP and the world of web development since some time already. Now, I finally took the time to dive into it.

Altough sometimes it's just better to start and get stuff done, in general I like it to get the overall picture of a subject. First only a shallow one, then digging deeper while using things and thus get a better understanding.

In case of PHP I got the impression that many deprecated material is around and that many examples contain anti-best-practices. People wrote many instructions about this, often without any explanation, so I was never sure what were the pros and cons of each method, and which fitted me best. At some of my earlier attempts this discouraged me, but not this time.

This already started when I wanted to install PHP on OSX. There are several methods of doing so.

# Installation #
## PHP ##

First you should know that OSX comes with an preinstalled version of PHP which is located in /usr/bin/php. Also the Apache webserves is preinstalled. However you still need to install MySQL either by [downloading the .dmg](https://dev.mysql.com/doc/refman/5.6/en/macosx-installation-pkg.html) or using homebrew `brew install mysql`.

In this case you have to configure these packages yourself and they might not work together out of the box. Maybe [this article](http://brianflove.com/2013/10/23/os-x-mavericks-and-apache/) can help you with that.

Another option is to use the PHP provided by the homebrew tab *homebrew-php* which is maintained by OSX users who code PHP and thus this repository should be fairly up to date.
Install this with:

```
brew tap homebrew/dupes
brew tap homebrew/versions
brew tap homebrew/php
brew install php56
```

For details take a look at [their Readme](https://github.com/Homebrew/homebrew-php|their).

Then there is a pre-configured binary package of PHP distributed by [Liip](http://www.liip.ch/). From their website:

>It installs many useful extensions and ini-settings and is what we at Liip use for our development. It's especially suited for Symfony 2 development. It also provides a decent php.ini with all settings configured according to "Best Practices".
Followed by a list of extensions:
>  bcmath bz2 calendar Core ctype curl date dom dtrace ereg exif fileinfo filter ftp gd gettext hash iconv imap intl json ldap libxml mbstring mcrypt memcache memcached mhash mongo mssql mysql mysqli mysqlnd OAuth odbc openssl pcntl pcre PDO pdo_dblib pdo_mysql pdo_pgsql pdo_sqlite pgsql Phar posix Reflection session shmop SimpleXML soap sockets solr SPL SQLite sqlite3 standard sysvmsg sysvsem sysvshm tidy tokenizer wddx xdebug xhprof xml xmlreader xmlrpc xmlwriter xsl zip zlib Xdebug
> 
> available but disabled by default: apc, xslcache, twig, uploadprogress 

Installation is done via a script:
`curl -s http://php-osx.liip.ch/install.sh | bash -s 5.6`
But please take a look at [their website](http://php-osx.liip.ch/) to get detailed information.

All methods so far required you to install MySQL additionally by hand.

The option which I chose was using [MAMP](http://www.mamp.info/) which is a softwware bundle compiled together for people doing web development. It contains the Apache webserver, MySQL database and PHP, Python and Perl scripting languages.
It's used for development environments not actual production environments.
I chose to use it because it's easy to set up and it doesn't mess with the system configuration. In case I screw up my Apache configuration or something I just remove the MAMP folder and install it anew.
Also it's pretty fast to start up the development environment. I just type CMD+Space and type in MAMP, which starts it. Then I just click on *Start Servers* and am good to go.

Of course I could just use the individual programs and save the initial configuration and write a script to start servers, but for OSX I chose to use this option.

You can type `which php` to which installation of PHP you are using.
In my *.zshrc* I have something like the following line to make sure I use the MAMP version.

{% highlight ruby %}
#only on OSX
if [[ `uname` == "Darwin" ]] ; then
	PATH=/usr/local/bin:/usr/local/sbin:$PATH

	#if MAMP is installed use its php and mysql version
	PHPPATH="/Applications/MAMP/bin/php/php5.5.10/bin"
	if [[ -d $PHPPATH ]] ; then
		PATH=$PHPPATH:$PATH
	fi

	MYSQLPATH="/Applications/MAMP/Library/bin"
	if [[ -d $MYSQLPATH ]] ; then
		PATH=$MYSQLPATH:$PATH
	fi
fi
{% endhighlight %}

I am aware that it's not a perfect set up since there is still the version 5.5.10 in *.zshrc*, but I will go with this for now.

## Composer ##
phar: http://php.net/manual/en/intro.phar.php
