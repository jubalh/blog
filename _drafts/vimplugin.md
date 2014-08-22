neocomplcache vs youcompleteme vs neocomplete

YMC:
wget https://github.com/Valloric/ycmd/blob/master/cpp/ycm/.ycm_extra_conf.py
nach .vim
let g:ycm_global_ycm_extra_conf = '~/.ycm_extra_conf.py'

brew install macvim --enable-interp="lua, python, python3, ruby"
brew install vim --enable-interp="lua, python, python3, ruby"
brew linkapps

check with vim --version if lua is there

http://mikegrouchy.com/blog/2012/05/compile-vim-with-python-support-on-osx-with-homebrew.html

look for plugins nice vimrc format at: http://vim.spf13.com/

vim-indent-guides

16:54 < zamaterian> gundo is great for visualing vims undo tree, and
                    vim-dispatch for async dispatching vim-fugative for git
					                    integration, rainbow_parentheses.vim

ctrlp
utilsnip

