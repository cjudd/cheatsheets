# tmux Cheatsheet

## Resources
* http://robots.thoughtbot.com/a-tmux-crash-course
* https://gist.github.com/MohamedAlaa/2961058

## new session
```
tmux new -s <session_name>
```

## attach to session
```
tmux attach -t <session_name>
```

## switch to session
```
tmux switch -t <session_name>
```

## list sessions
```
tmux ls
```
```
tmux list-sessions
```

## detach session
```
tmux detach
```

## kill session
```
tmux kill-session -t <session_name>
```

## kill all sessions
```
tmux ls | grep : | cut -d. -f1 | awk '{print substr($1, 0, length($1)-1)}' | xargs kill
```

## prefix
```
ctrl + b
```

## splits
```
PREFIX %  vertical split
PREFIX "  horizontal split

PREFIX o  swap panes
PREFIX q  show pane numbers
PREFIX x  kill pane
```

## resize
```
PREFIX : resize-pane -D (Resizes the current pane down)
PREFIX : resize-pane -U (Resizes the current pane upward)
PREFIX : resize-pane -L (Resizes the current pane left)
PREFIX : resize-pane -R (Resizes the current pane right)
PREFIX : resize-pane -D 20 (Resizes the current pane down by 20 cells)
PREFIX : resize-pane -U 20 (Resizes the current pane upward by 20 cells)
PREFIX : resize-pane -L 20 (Resizes the current pane left by 20 cells)
PREFIX : resize-pane -R 20 (Resizes the current pane right by 20 cells)
PREFIX : resize-pane -t 2 20 (Resizes the pane with the id of 2 down by 20 cells)
PREFIX : resize-pane -t -L 20 (Resizes the pane with the id of 2 left by 20 cells)
```

## detach
```
PREFIX d
```