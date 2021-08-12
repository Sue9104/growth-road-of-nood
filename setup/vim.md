# Vim

## Configuration

> [https://github.com/skwp/dotfiles](https://github.com/skwp/dotfiles)

```text
git clone https://github.com/Sue9104/custom-yadr.git
cd custom-yadr
make install
```

## Shortcut

### 文本内跳转

| shortcut | function |
| :--- | :--- |
| 0 | first word |
| ^ | line first |
| $ | line end |
| w | skip to start by word |
| e | skip to end by word |
| % | show paird symbol \( { |
| \* | skip to next same word |
| \# | skip to previous same word |

### 剪切

| symbol | function |
| :--- | :--- |
| D | from cursor to line end |
| dd | the whole line |
| d2w | from cursor to the next 2 word |

### 快速插入相同字符

30i\#Esc

### 大小写转换

| symbol | function |
| :--- | :--- |
| gU | convert to uppercase |
| gu | convert to lowercase |

### 文本对齐

| symbol | function |
| :--- | :--- |
| gg=G | whole script alignment |
| 3== | the next 3 line alignment |
| =a{ | alignment in the {} block |

## Performance

```bash
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

