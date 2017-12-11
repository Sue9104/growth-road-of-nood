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

