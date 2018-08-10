# disable-breakpoint-in-particular-thread

[disable-breakpoint-in-particular-thread](https://stackoverflow.com/questions/37978625/gdb-disable-breakpoint-in-particular-thread#)

```
(gdb) cond (breakpoint_number) $_thread != (thread_number)
```
