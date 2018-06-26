# how to check the changes in merge commit

## oneway

```bash
git log mergecommit^1..mergecommit^2 --no-merges --oneline
```

## both way

```bash
git log mergecommit^1...mergecommit^2 --no-merges --oneline
```

## pretty

```bash
git log mergecommit^1..mergecommit^2 --no-merges --pretty=format:"%an, %H%n%s%n"
```
