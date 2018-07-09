# defaults

## block creation .DS_Store on network drives

```
$ defaults write com.apple.desktopservices DSDontWriteNetworkStores true
```

## showing running apps on Dock

```
$ defaults write com.apple.dock static-only -bool TRUE; killall Dock
```
