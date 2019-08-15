# vim
## dotfile

> [https://github.com/skwp/dotfiles](https://github.com/skwp/dotfiles)

```
git clone https://github.com/Sue9104/custom-yadr.git
cd custom-yadr
make install
```

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

## 跳转

| ctrl + o /  ctrl + i | jump between old and current cursor postion |
| :--- | :--- |
| ctrl + j / ctrl + k | move between functions |
| alt + number | terminal tab |
| ctrl + pageup / pagedown | vim tab |



