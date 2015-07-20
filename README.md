My [blog](https://github.com/jubalh/blog) which was once based on a customized version of the [flex jekyll theme](https://github.com/the-development/flex).
But is not created with hugo using my own theme.

# creating the blog #
- install go
- run go get -u -v github.com/spf13/hugo

# preview post #
hugo server
maybe with
- --buildDrafts
- --watch

# publish #
- on branch master i have the code.
- then i generate with hugo server.
- on i move the public directory in a temp directory.
- switch to branch *gh-pages* i mv the content of public in here.
- commit and push
