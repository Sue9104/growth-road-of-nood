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
Bundle 'ervandew/supertab'
Bundle 'Valloric/YouCompleteMe'
``` 
- in ```~/.vimrc```,避免ultisnips与YouCompleteMe快捷键冲突

```vim
" make YCM compatible with UltiSnips (using supertab)
let g:ycm_key_list_select_completion = ['<C-n>', '<Down>']
let g:ycm_key_list_previous_completion = ['<C-p>', '<Up>']
let g:SuperTabDefaultCompletionType = '<C-n>'

" better key bindings for UltiSnipsExpandTrigger
let g:UltiSnipsExpandTrigger = "<tab>"
let g:UltiSnipsJumpForwardTrigger = "<tab>"
let g:UltiSnipsJumpBackwardTrigger = "<s-tab>"
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
cd ~/.vim/bundle/YouCompleteMe && python install.py --js-completer --rust-completer 
```