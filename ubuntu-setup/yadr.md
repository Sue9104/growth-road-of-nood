# YADR
> [https://github.com/skwp/dotfiles](https://github.com/skwp/dotfiles)

## Install

```
sh -c "`curl -fsSL https://raw.githubusercontent.com/skwp/dotfiles/master/install.sh`"
```

## Upgrading

```
cd ~/.yadr
git pull --rebase
rake update
```

## Changing Highlight Color

- in ~/.vimrc.before

```
let g:yadr_using_unsolarized_terminal = 1
``` 

- in ~/.vimrc.after

```
let g:yadr_disable_solarized_enhancements = 1
colorscheme desert 
```

## YouCompleteMe

- in ~/.vim/vundles/vim-improvements.vundle
 
```
Bundle "Valloric/YouCompleteMe"
``` 

- run the cmd

``` 
vim +PluginInstall +qall
```

- install dependecy

```
sudo apt-get install build-essential cmake && sudo apt-get install python-dev python3-dev
```

- install 

```
cd ~/.vim/bundle/YouCompleteMe && ./install.py --clang-completer --tern-completer --racer-completer 
```