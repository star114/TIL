# lsof

You can do both with lsof.

1. To see what processes have a library open or mapped do:

```
$ lsof /path/to/lib.so
```

2. To see what files (including shared libraries) a process has open and/or mapped, do:

```
$ lsof -p <pid>
```
