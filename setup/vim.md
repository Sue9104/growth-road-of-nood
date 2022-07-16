# Vim

## Configuration

> [https://github.com/skwp/dotfiles](https://github.com/skwp/dotfiles)

```
git clone https://github.com/Sue9104/custom-yadr.git
cd custom-yadr
make install
```

## Usage

### Shortcut

### 跳转

| shortcut                                        | function                   |
| ----------------------------------------------- | -------------------------- |
| 0                                               | first word                 |
| ^                                               | line first                 |
| $                                               | line end                   |
| w                                               | skip to start by word      |
| e                                               | skip to end by word        |
| %                                               | show paird symbol ( {      |
| \*                                              | skip to next same word     |
| #                                               | skip to previous same word |
| \[\[                                            | jump between code block    |
| \{{                                             | jump between code block    |
| ctrl+w+left                                     | jump between windows       |
| <p>ctrl+alt+pageup</p><p>ctrl+alt+fn+pageup</p> | skip between vim tabs      |

### 剪切

| symbol | function                       |
| ------ | ------------------------------ |
| D      | from cursor to line end        |
| dd     | the whole line                 |
| d2w    | from cursor to the next 2 word |

### Buffer

| symbol    | function                                       |
| --------- | ---------------------------------------------- |
| :ls       | list buffer                                    |
| :b \<num> | jump to the nth buffer                         |
| Ctrl+^    | toggle between the current and the last buffer |
| Ctrl+O    | all the jumps you make in your buffers         |
| Ctrl+I    | all the jumps you make in your buffers         |

### 快速插入相同字符

30i#Esc

### 大小写转换

| symbol | function             |
| ------ | -------------------- |
| gU     | convert to uppercase |
| gu     | convert to lowercase |

### 文本对齐

| symbol | function                  |
| ------ | ------------------------- |
| gg=G   | whole script alignment    |
| 3==    | the next 3 line alignment |
| =a{    | alignment in the {} block |

## Editorconfig

```
# EditorConfig is awesome: https://EditorConfig.org

# top-most EditorConfig file
root = true

# Unix-style newlines with a newline ending every file
[*]
indent_style = space
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
indent_size = 2

# Matches multiple files with brace expansion notation
# 4 space indentation
[*.py]
indent_size = 4

# Tab indentation (no size specified)
[Makefile]
indent_style = tab

[*.md]
trim_trailing_whitespace = false

[*.rst]
indent_size = 3
```

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
