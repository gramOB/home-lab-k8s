# must use tmux

```bash
sudo apt install tmux -y
```

add my custom config for keybindings, etc.

```bash
vi ~/.tmux.conf
```

paste my config file I keep handy - created based on many others, tuned during my oscp studies

for bash:

```bash
unbind C-b
set-option -g prefix M-a
bind M-a send-prefix
set -g mouse on
set-option -g history-limit 50000
set -g base-index 1
setw -g pane-base-index 1
set -g renumber-windows on
bind c new-window -c "#{pane_current_path}"
bind % split-window -h -c "#{pane_current_path}"
bind '"' split-window -v -c "#{pane_current_path}"
bind Space last-window
set-option -g default-command bash
set-option -g default-shell /bin/bash

set-option -g status-justify left
set-option -g status-left '#[bg=colour72] #[bg=colour237] #[bg=colour236] #[bg=colour235]#[fg=colour185] #S #[bg=colour236] '
set-option -g status-left-length 16
set-option -g status-bg colour237
set-option -g status-right '#[bg=colour236] #[bg=colour235]#[fg=colour185] %a %R #[bg=colour236]#[fg=colour3] #[bg=colour237] #[bg=colour72] #[]'   
set-option -g status-interval 60

set-option -g pane-active-border-style fg=colour246
set-option -g pane-border-style fg=colour238
set-window-option -g window-status-format '#[bg=colour238]#[fg=colour107] #I #[bg=colour239]#[fg=colour110] #[bg=colour240]#W#[bg=colour239]#[fg=colour195]#F#[bg=colour238] '
set-window-option -g window-status-current-format '#[bg=colour236]#[fg=colour215] #I #[bg=colour235]#[fg=colour167] #[bg=colour234]#W#[bg=colour235]#[fg=colour195]#F#[bg=colour236] '
bind r source-file ~/.tmux.conf \; display "Config reloaded!"

set -g history-file ~/.tmux_history
bind -r Up resize-pane -U 10
bind -r Down resize-pane -D 10

setw -g mode-keys vi

```

for zsh

```bash
unbind C-b
set-option -g prefix M-a
bind M-a send-prefix
set -g mouse on
set-option -g history-limit 50000
set -g base-index 1
setw -g pane-base-index 1
set -g renumber-windows on
bind c new-window -c "#{pane_current_path}"
bind % split-window -h -c "#{pane_current_path}"
bind '"' split-window -v -c "#{pane_current_path}"
bind Space last-window
set-option -g default-command zsh
set-option -g default-shell /bin/zsh

set-option -g status-justify left
set-option -g status-left '#[bg=colour72] #[bg=colour237] #[bg=colour236] #[bg=colour235]#[fg=colour185] #S #[bg=colour236] '
set-option -g status-left-length 16
set-option -g status-bg colour237
set-option -g status-right '#[bg=colour236] #[bg=colour235]#[fg=colour185] %a %R #[bg=colour236]#[fg=colour3] #[bg=colour237] #[bg=colour72] #[]'   
set-option -g status-interval 60

set-option -g pane-active-border-style fg=colour246
set-option -g pane-border-style fg=colour238
set-window-option -g window-status-format '#[bg=colour238]#[fg=colour107] #I #[bg=colour239]#[fg=colour110] #[bg=colour240]#W#[bg=colour239]#[fg=colour195]#F#[bg=colour238] '
set-window-option -g window-status-current-format '#[bg=colour236]#[fg=colour215] #I #[bg=colour235]#[fg=colour167] #[bg=colour234]#W#[bg=colour235]#[fg=colour195]#F#[bg=colour236] '
bind r source-file ~/.tmux.conf \; display "Config reloaded!"

set -g history-file ~/.tmux_history
bind -r Up resize-pane -U 10
bind -r Down resize-pane -D 10

setw -g mode-keys vi

```
