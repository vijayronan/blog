+++
date = 2020-03-16T17:23:17Z
tags = ["tmux"]
title = "Tmux Sheet Cheat"

+++

    # remap prefix from 'C-b' to 'C-a'
    unbind C-b
    set-option -g prefix C-a
    bind-key C-a send-prefix
    
    #setting the delay between prefix and command
    set -s escape-time 1
    
    #Set the base index for windows to 1 instead of 0
    set -g base-index 1
    
    bind r source-file ~/.tmux.conf
    
    #Set the default terminal mode to 256color mode
    set -g default-terminal "screen-256color"
    
    #SET Color for the active window
    setw -g window-status-current-style fg=white,bold,bg=red
    
    #Status line righ side - 31-Oct 13:37
    set -g status-right "#[fg=black]%d %b %R"

    #Update the status line every sixty seconds
    set -g status-interval 60
    
    #set the color of the window list
    setw -g window-status-style fg=cyan,bg=black
    
    #enable vi keys.
    setw -g mode-keys vi

    #enable mouse  
    set -g mouse on
    
    bind Escape copy-mode
    bind-key -T copy-mode-vi v send-keys -X begin-selection
    bind-key -T copy-mode-vi y send-keys -X copy-selection
    bind-key -T copy-mode-vi r send-keys -X rectangle-toggle
    unbind p
    bind p paste-buffer