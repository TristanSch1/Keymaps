# Tmux

- Commands starting with `$` are commands to type in terminal
- Commands starting with `:` are commands to type in tmux command prompt
- My prefix key is set to `<C-t>`
- Some commands may not correspond to the basic tmux keymap. Here are the commands I chose to modify :

```conf
#### Key bindings

set-window-option -g mode-keys vi

# Reload settings
bind r source-file /opt/homebrew/opt/tmux/share/tmux/tmux.conf \; display "Reloaded!"
# Open current directory
bind o run-shell "open #{pane_current_path}"
bind -r e kill-pane -a

# vim-like pane switching
bind -r k select-pane -U
bind -r j select-pane -D
bind -r h select-pane -L
bind -r l select-pane -R

# Moving window
bind-key -n C-S-Left swap-window -t -1 \; previous-window
bind-key -n C-S-Right swap-window -t +1 \; next-window

# Resizing pane
bind -r C-k resize-pane -U 5
bind -r C-j resize-pane -D 5
bind -r C-h resize-pane -L 5
bind -r C-l resize-pane -R 5
```

## Sessions

| Key                                                                                                                            | Description                                                            |
| ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------- |
| `$ tmux`                                                                                                                       | Start a new session                                                    |
| `$ tmux new -s mysession`                                                                                                      | Start a new session with the name _mysession_                          |
| `$ tmux kill-session -t mysession`                                                                                             | Kill/Delete session _mysession_                                        |
| `$ tmux kill-session -a -t mysession`                                                                                          | Kill/Delete all sessions but _mysession_                               |
| `$ tmux kill-session -a`                                                                                                       | Kill/Delete all sessions but current                                   |
| `<C-b>$`                                                                                                                       | Rename session                                                         |
| `<C-b>d`                                                                                                                       | Detach from session                                                    |
| `: attach -d`                                                                                                                  | Detach others on the session (Maximize window by detach other clients) |
| `$ tmux ls` <br> `$ tmux list-sessions` <br> `<C-b>s`                                                                          | Show all session                                                       |
| `$ tmux a` <br> `$ tmux at` <br> `$ tmux attach` <br> `$ tmux attach-session`                                                  | Attach to last session                                                 |
| `$ tmux a -t mysession`<br> `$ tmux at -t mysession`<br> `$ tmux attach -t mysession`<br> `$ tmux attach-session -t mysession` | Attach to a session with the name _mysession_                          |
| `<C-b>w`                                                                                                                       | Session and Window Preview                                             |
| `<C-b>(`                                                                                                                       | Move to previous session                                               |
| `<C-b>)`                                                                                                                       | Move to next session                                                   |

## Windows

| Key                                   | Description                                                         |
| ------------------------------------- | ------------------------------------------------------------------- |
| `$ tmux new -s mysession -n mywindow` | Start a new session with the name _mysession_ and window _mywindow_ |
| `<C-b>c`                              | Create window                                                       |
| `<C-b>,`                              | Rename current window                                               |
| `<C-b>&`                              | Close current window                                                |
| `<C-b>w`                              | List windows                                                        |
| `<C-b>p`                              | Previous window                                                     |
| `<C-b>n`                              | Next window                                                         |
| `<C-b><0-9>`                          | Switch/select window by number                                      |
| `<C-b>l`                              | Toggle last active window                                           |
| `: swap-window -s 2 -t 1`             | Reorder window, swap window number 2(src) and 1(dst)                |
| `: swap-window -t -1`                 | Move current window to the left by one position                     |

## Panes

| Key                                                             | Description                                                                                  |
| --------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `<C-b>;`                                                        | Toggle last active pane                                                                      |
| `<C-b>"`<br> `: split-window -v`                                | Split the current pane with a horizontal line to create a vertical layout                    |
| `<C-b>%`<br> `: split-window -h`                                | Split the current pane with a vertical line to create a horizontal layout                    |
| `: join-pane -s 2 -t 1`                                         | Join two windows as panes (Merge window 2 to window 1 as panes)                              |
| `: join-pane -s 2.1 -t 1.0`                                     | Move pane from one window to another (Move pane 1 from window 2 to pane after 0 of window 1) |
| `<C-b>{`                                                        | Move the current pane left                                                                   |
| `<C-b>}`                                                        | Move the current pane right                                                                  |
| `<C-b>k`<br> `<C-b>j`<br> `<C-b>h`<br> `<C-b>l`                 | Switch to pane to the direction (Vim-like direction)                                         |
| `: setw synchronise-panes`                                      | Toggle synchronize-panes (send command to all panes)                                         |
| `<C-b>Space`                                                    | Toggle between pane layouts                                                                  |
| `<C-b>o`                                                        | Switch to next pane                                                                          |
| `<C-b>q`                                                        | Show pane numbers                                                                            |
| `<C-b>q<0-9>`                                                   | Switch/Select pane by number                                                                 |
| `<C-b>z`                                                        | Toggle pane zoom                                                                             |
| `<C-b>!`                                                        | Convert pane into a window                                                                   |
| `<C-b><C-k>`<br> `<C-b><C-j>`<br> `<C-b><C-h>`<br> `<C-b><C-l>` | Resize current pane to direction (Vim-like direction)                                        |
| `<C-b>x`                                                        | Close current pane                                                                           |

## Copy Mode

| Key                      | Description                                      |
| ------------------------ | ------------------------------------------------ |
| `: setw -g mode-keys vi` | Use vi keys in buffer                            |
| `<C-b>[`                 | Enter copy mode                                  |
| `<C-b>PgUp`              | Enter copy mode and scroll one page up           |
| `q`                      | Quit mode                                        |
| `g`                      | Go to top line                                   |
| `G`                      | Go to bottom line                                |
| `ArrowUp`                | Scroll up                                        |
| `ArrowDown`              | Scroll down                                      |
| `h`                      | Move cursor left                                 |
| `j`                      | Move cursor down                                 |
| `k`                      | Move cursor top                                  |
| `l`                      | Move cursor right                                |
| `w`                      | Move cursor forward one word at a time           |
| `b`                      | Move cursor backward one word at a time          |
| `/`                      | Search forward                                   |
| `?`                      | Search backward                                  |
| `n`                      | Next keyword occurance                           |
| `N`                      | Previous keyword occurance                       |
| `Space`                  | Start selection                                  |
| `Esc`                    | Clear selection                                  |
| `Enter`                  | Copy selection                                   |
| `<C-b>]`                 | Paste contents of buffer_0                       |
| `: show-buffer`          | Display buffer_0 contents                        |
| `: capture-pane`         | Copy entire visible contents of pane to a buffer |
| `: list-buffers`         | Show all buffers                                 |
| `: choose-buffer`        | Show all buffers and paste selected              |
| `: save-buffer buf.txt`  | Save buffer contents to buf.txt                  |
| `: delete-buffer b 1`    | Delete buffer_1                                  |

## Misc

| Key                | Description                   |
| ------------------ | ----------------------------- |
| `<C-b>:`           | Enter command mode            |
| `: set -g OPTION`  | Set _OPTION_ for all sessions |
| `: setw -g OPTION` | Set _OPTION_ for all windows  |
| `: set mouse on`   | Enable mouse mode             |

## Help

| Key                                               | Description                           |
| ------------------------------------------------- | ------------------------------------- |
| `$ tmux list-keys`<br> `: list-keys`<br> `<C-b>?` | List key bindings (Shortcuts)         |
| `$ tmux-info`                                     | Show every session,window,pane etc... |
