# precautions

## iterm2

profile + text 에 Use Unicode Version 9 Widths 켜면 (업데이트 이후 default 로 켜짐) tmux 깨짐.

## gdb

gdb runs in unexpected way

gdbinit 에 startup-with-shell option 을 끄도록 설정해 주어야 함.

```
$ vi ~/.gdbinit
```

set startup-with-shell off
