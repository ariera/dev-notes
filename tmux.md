### tmux notes
-> actuvate tmux controls: ctrl + b
-> attach: tmux attach
-> detach: ctrl + b + d
-> next window: ctrl + b + n
-> prev window: ctrl + b + p
-> new  window: ctrl + b + c
-> close  window: ctrl + b + &
-> maximaze window: ctrl + b + z
-> split horizontal: ctrl + b + "
-> split vertical: ctrl + b + %
-> switch between predifend split layouts: ctrl + b + <space>
-> remove split: ctrl + b + x
-> move to next split: ctrl + b + <arrowkeys>
-> move to next split: ctrl + b + q --> numbers
-> time: ctrl + b + t


### tmux and iTerm
tmux -CC
tmux -CC attach



### iTemr2 v2 color scheme in tmux profile
* download this file: https://github.com/chriskempson/base16-iterm2/blob/master/base16-default.dark.itermcolors
* enter preferences tmux
* go to profiles
* choose the tmux profile
* colors tab
* there is a "load presets" select box at the bottom
* import the file you downloaded
* and select the installed theme from the "load presets" select box
* bonus: I would suggest changing the background color to something like dark blue that makes instantly realize that you are on a tmux session

remeber that if you just close a iTerm window created by attaching to a tmux session you will close the whole tmux session *to everybody*
the proper way to detach (shortcuts won't work) is to go to the menu `Shell > tmux > detach`

