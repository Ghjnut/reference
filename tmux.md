### Window-swap
`swap-window -s 3 -t 1`
to let window number 3 and window number 1 swap their positions.

To swap the current window with the top window, do:

`swap-window -t 0`
In the unlikely case of having no window at index 0, do:

`move-window -t 0`
(if base-index is 0, as it is by default).


`bind-key -n C-S-Left swap-window -t -1`
`bind-key -n C-S-Right swap-window -t +1`


### Panes
#### Splits
`tmux split-window (prefix + ")`
splits the window into two vertical panes

`tmux split-window -h (prefix + %)`
splits the window into two horizontal panes

`tmux swap-pane -[UDLR] (prefix + { or })`
swaps pane with another in the specified direction

`tmux select-pane -[UDLR]`
selects the next pane in the specified direction

`tmux select-pane -t :.+`
selects the next pane in numerical order

#### Joins
The command to do this is join-pane in tmux 1.4.

join-pane [-dhv] [-l size | -p percentage] [-s src-pane] [-t dst-pane]  
    (alias: joinp)
    Like split-window, but instead of splitting dst-pane and creating
    a new pane, split it and move src-pane into the space.  This can
    be used to reverse break-pane.

# pane movement
`bind-key j command-prompt -p "join pane from:"  "join-pane -s '%%'"`
`bind-key s command-prompt -p "send pane to:"  "join-pane -t '%%'"`
The first grabs the pane from the target window and joins it to the current, the second does the reverse.

You can then reload your tmux session by running the following from within the session:

$ tmux source-file ~/.tmux.conf

break-pane [-dP] [-F format] [-t target-pane]
  (alias: breakp)
  Break target-pane off from its containing window to make it the only pane 
  in a new window.  If -d is given, the new window does not become the current
  window.  The -P option prints information about the new window after it has 
  been created.  By default, it uses the format 
  `#{session_name}:#{window_index}' 
  but a different format may be specified with -F.
