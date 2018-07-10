# blame-prior-commits

[git blame prior commits - stackoverflow](https://stackoverflow.com/questions/5098256/git-blame-prior-commits#)

## blame the target lines from head 

```
git blame -L10,+1 src/options.cpp
```

## blame the target lines before specific commits

```
git blame -L10,+1 fe25b6d^ -- src/options.cpp
```

## show all logs for the target lines

```
git log -L 10,11:src/options.cpp
```
