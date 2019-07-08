# vim

## 快捷键

## 目录与文件

* `ctrl+\` 显示当前目录结构 
* `,t` 文件查找
* `,b` 最近编辑的文件查找

## 折叠

* zc 折叠建立
* zC 所在范围内所有嵌套进行折叠
* zo 打开折叠 
* zO 对所在范围内所有嵌套的折叠点展开
* zf　创建折叠　10zf+　10zf-　zf56G

## showMarks

* 建立marker: m\[a-zA-Z\]
* 跳转：,a

## 跳转

| ctrl + o /  ctrl + i | jump between old and current cursor postion |
| :--- | :--- |
| ctrl + j / ctrl + k | move between functions |
| alt + number | terminal tab |
| ctrl + pageup / pagedown | vim tab |



## 性能

```sh
# 1
vim --startuptime timing.out

# 2
:profile start profile.log
:profile func *
:profile file *
" At this point do slow actions
:profile pause
:noautocmd qall!
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

- dependecies

```
sudo apt-get install build-essential cmake && sudo apt-get install python-dev python3-dev
```

- install 

```
cd ~/.vim/bundle/YouCompleteMe && git submodule update --init --recursive && python install.py --js-completer --rust-completer 
```


