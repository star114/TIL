# git-reflog

## reflog

```
git reflog
```

HEAD의 변경이력을 모두 볼 수 있다.

## reset

```
git reset --hard HEAD@{1}
```

reflog 에서 나타난 hash 혹은 HEAD@{number} tag 를 사용하면 해당 커밋으로 이동할 수 있다.