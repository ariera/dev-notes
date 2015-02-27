## Hide desktop icons

to hide all icons on the desktop without deleting or moving the files stored in the desktop folder. This first command will remove the icons:

```
defaults write com.apple.finder CreateDesktop -bool false && killall Finder
```

While this second one will restore all the icons:

```
defaults write com.apple.finder CreateDesktop -bool true && killall Finder
```
