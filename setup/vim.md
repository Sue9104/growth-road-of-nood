# Vim

## Configuration

> [https://github.com/skwp/dotfiles](https://github.com/skwp/dotfiles)

```text
git clone https://github.com/Sue9104/custom-yadr.git
cd custom-yadr
make install
```

## Shortcut

### 跳转

<table>
  <thead>
    <tr>
      <th style="text-align:left">shortcut</th>
      <th style="text-align:left">function</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0</td>
      <td style="text-align:left">first word</td>
    </tr>
    <tr>
      <td style="text-align:left">^</td>
      <td style="text-align:left">line first</td>
    </tr>
    <tr>
      <td style="text-align:left">$</td>
      <td style="text-align:left">line end</td>
    </tr>
    <tr>
      <td style="text-align:left">w</td>
      <td style="text-align:left">skip to start by word</td>
    </tr>
    <tr>
      <td style="text-align:left">e</td>
      <td style="text-align:left">skip to end by word</td>
    </tr>
    <tr>
      <td style="text-align:left">%</td>
      <td style="text-align:left">show paird symbol ( {</td>
    </tr>
    <tr>
      <td style="text-align:left">*</td>
      <td style="text-align:left">skip to next same word</td>
    </tr>
    <tr>
      <td style="text-align:left">#</td>
      <td style="text-align:left">skip to previous same word</td>
    </tr>
    <tr>
      <td style="text-align:left">[[</td>
      <td style="text-align:left">jump between code block</td>
    </tr>
    <tr>
      <td style="text-align:left">{{</td>
      <td style="text-align:left">jump between code block</td>
    </tr>
    <tr>
      <td style="text-align:left">ctrl+w+left</td>
      <td style="text-align:left">jump between windows</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>ctrl+alt+pageup</p>
        <p>ctrl+alt+fn+pageup</p>
      </td>
      <td style="text-align:left">skip between vim tabs</td>
    </tr>
  </tbody>
</table>

### 剪切

| symbol | function |
| :--- | :--- |
| D | from cursor to line end |
| dd | the whole line |
| d2w | from cursor to the next 2 word |

### Buffer

| symbol | function |
| :--- | :--- |
| :ls | list buffer |
| :b &lt;num&gt; | jump to the nth buffer |
| Ctrl+^ | toggle between the current and the last buffer |
| Ctrl+O | all the jumps you make in your buffers |
| Ctrl+I | all the jumps you make in your buffers |

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

