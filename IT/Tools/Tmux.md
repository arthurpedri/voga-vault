## Leader \<C-space\>
- Prefix for all tmux commands

## Sessions
- `tmux new -s sessionname`
    - `tmux` will create a new unnamed session
- `tmux kill-session -t sessionname`
- `$`: rename session
- `d`: detach from session
- `tmux ls` or `s`: list sessions
- `tmux a`: attach to last session
    - `tmux a -t sessionname`
## Windows
- `c` create window
- `,` rename current window
- `&` close current window
- `p` and `n` previous and next window
- `0 .. 9` switch/select window
## Panes
- `x` close current pane
- `;` toggle last active pane
- `%` split horizontal
- `"` split vertical
- `h j k l` switch to panes
- `space` toggle between pane layouts
- `!` convert pane into a window

## Misc
- `:` command mode
- `?` list key bindings
