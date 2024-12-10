
## Introduction

**Tmux** is a terminal multiplexer, allowing you to run multiple terminal sessions within a single window. It also offers session management and persistent terminal sessions.

### Basic Usage

To start **tmux**, run:  
```bash
tmux
```

---

## Common Commands

### Sessions

| Description                       | Command                                                       |
| --------------------------------- | ------------------------------------------------------------- |
| Start a session                   | `tmux`                                                        |
| Attach to the most recent session | `tmux attach` or `tmux a`                                     |
| Attach to a specific session      | `tmux attach -t <session_name>` or `tmux a -t <session_name>` |
| Detach from the current session   | `prefix` + `d`                                                |
| Preview window for each session   | `prefix` + `w`                                                |
| List all sessions                 | `tmux list-session` or `tmux ls`                              |
| Rename a session                  | `tmux rename-session <new_name>` or `prefix` + `$`            |
| Kill all sessions and exit tmux   | `exit`                                                        |

### Windows

| Description                   | Command                                           | re_mapped      |
| ----------------------------- | ------------------------------------------------- | -------------- |
| Create a new window           | `tmux new-window` or `prefix` + `c`               | `prefix` + `n` |
| Switch to the previous window | `prefix` + `p`                                    | `prefix` + `<` |
| Switch to the next window     | `prefix` + `n`                                    | `prefix` + `>` |
| Rename a window               | `tmux rename-window <new_name>` or `prefix` + `,` |                |
| Kill the current window       | `prefix` + `@`                                    | `prefix` + `x` |

### Panes

| Description            | Command              | remapped        |
| ---------------------- | -------------------- | --------------- |
| Vertical split         | `prefix` + `%`       | `prefix` + `/`  |
| Horizontal split       | `prefix` + `"`       | `prefix` + `?`  |
| Move between panes     | `prefix` + arrow key | `prefix` + wsad |
| Close the current pane | `prefix` + `x`       |                 |

### Command Mode

| Description           | Command        |
| --------------------- | -------------- |
| Enter command mode    | `prefix` + `:` |
| List sessions in tmux | `prefix` + `s` |
|                       |                |

### Copy and paste 
`prefix` + `[` to enter into copy mode
`arrow`  to move around
`ctrl` + `Space` key to start selecting
`Alt+W` to copy 

`ctrl` + `shift` + `v`  to paste 

keep this option and make sure `xclip` is installed 
```shell

set-option -g set-clipboard on
setw -g mode-keys vi
bind-key copy-mode-vi Enter send-keys -X copy-pipe "xclip -selection clipboard -i"

```
---

## Configuration

The tmux configuration file is located at:  
```bash
~/.tmux.conf
```

### General Configuration

| To Change             | Syntax                     |
| --------------------- | -------------------------- |
| Change prefix key     | `set-option -g prefix C-j` |
| Turn on mouse support | `set -g mouse on`          |
| Copy                  |                            |

### Key Bindings

#### Splitting Behavior

| Change                          | Syntax                                 |
|---------------------------------|--------------------------------------- |
| Change vertical split binding   | `bind-key v split-window -h`          |
| Change horizontal split binding | `bind-key h split-window -v`          |
### Extra
| Description           | Command        |
| --------------------- | -------------- |
| Zoom a pane           | `prefix` + `z` |
| Turn pane into window | `prefix` + `!` |
#### Pane Navigation (Alt + Arrow Keys)

```bash
bind -n M-left select-pane -L
bind -n M-right select-pane -R
bind -n M-up select-pane -U
bind -n M-down select-pane -D
```

#### Window Switching (Shift + Arrow Keys)

```bash
bind -n S-left previous-window
bind -n S-right next-window
```

#### Window Reordering (Ctrl + Shift + Arrow Keys)

```bash
bind-key -n C-S-Left swap-window -t -1
bind-key -n C-S-Right swap-window -t +1
```

---

## Reloading Configuration

To reload the tmux configuration after making changes, add the following to your `.tmux.conf`:  
```bash
bind-key r source-file ~/.tmux.conf \; display-message "tmux.conf reloaded."
```
