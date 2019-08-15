# Terminator

## Install

```
sudo apt-get install terminator
```


## Configure

in /.config/terminator/config

```
[global_config]
  focus = system
  suppress_multiple_term_dialog = True
  title_transmit_bg_color = "#d30102"
[keybindings]
  full_screen = <Primary>Return
  split_horiz = <Alt>d
  split_vert = <Shift><Alt>d
[layouts]
  [[default]]
    [[[child1]]]
      parent = window0
      profile = default
      type = Terminal
    [[[window0]]]
      parent = ""
      type = Window
[plugins]
[profiles]
  [[default]]
    background_color = "#2d2d2d"
    background_darkness = 0.85
    background_image = None
    copy_on_selection = True
    font = Monospace 10.5
    foreground_color = "#eee9e9"
    palette = "#2d2d2d:#f2777a:#99cc99:#ffcc66:#6699cc:#cc99cc:#66cccc:#d3d0c8:#747369:#f2777a:#99cc99:#ffcc66:#6699c
    show_titlebar = False
    use_system_font = False
    cursor_color = "#FF8C00"
    cursor_blink = True[global_config]
  focus = system
  suppress_multiple_term_dialog = True
  title_transmit_bg_color = "#d30102"
[keybindings]
  full_screen = <Primary>Return
  split_horiz = <Alt>d
  split_vert = <Shift><Alt>d
[layouts]
  [[default]]
    [[[child1]]]
      parent = window0
      profile = default
      type = Terminal
    [[[window0]]]
      parent = ""
      type = Window
[plugins]
[profiles]
  [[default]]
    background_color = "#2d2d2d"
    background_darkness = 0.85
    background_image = None
    copy_on_selection = True
    font = Monospace 10.5
    foreground_color = "#eee9e9"
    palette = "#2d2d2d:#f2777a:#99cc99:#ffcc66:#6699cc:#cc99cc:#66cccc:#d3d0c8:#747369:#f2777a:#99cc99:#ffcc66:#6699c
    show_titlebar = False
    use_system_font = False
    cursor_color = "#FF8C00"
    cursor_blink = True```
