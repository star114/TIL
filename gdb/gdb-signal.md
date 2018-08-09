# gdb-signal

## info

```
info signals
info handle
```
signal 과 signal 에 대한 handle 정보를 출력한다.

## handle

```
catch signal [signal | 'all']
handle signal [keywords..]
```
특정 signal 에 대한 handle 방식을 지정할 수 있다.

### keywords

* nostop
* stop
* noprint
* print
* pass(noignore)
* nopass(ignore)
