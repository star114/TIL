# vimdiff-cheat-sheet

## git mergetool

In the middle file (future merged file), you can navigate between conflicts with `]c` and `[c`.

Choose which version you want to keep with `:diffget //2` or `:diffget //3` (the `//2` and `//3` are unique identifiers for the target/master copy and the merge/branch copy file names).

```
        :diffupdate (to remove leftover spacing issues)
        :only (once you’re done reviewing all conflicts, this shows only the middle/merged file)
        :wq (save and quit)
        git add .
        git commit -m “Merge resolved”
```

If you were trying to do a `git pull` when you ran into merge conflicts, type `git rebase –continue`.

## vimdiff commands

```
        ]c :        - next difference
        [c :        - previous difference
        do          - diff obtain
        dp          - diff put
        zo          - open folded text
        zc          - close folded text
        :diffupdate - re-scan the files for differences
```
