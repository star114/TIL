# case-insensitive

[atlassian source tree issue](https://confluence.atlassian.com/sourcetreekb/renaming-a-file-for-case-under-git-source-control-is-not-updated-by-sourcetree-on-mac-os-x-302809301.html)

I experienced it when I cloned the git source tree having the only case renaming history on Mac.

## symptoms

When a file has been renamed and only the case has been modified, git source tree will be broken on Mac. (it has the files cannot be added and upated)

## cause

The default Mac OS filesystem HFS+ is generally case insensitive. ABC.txt and abc.txt are considered the same file, unlike Linux.

## workaround

you can use a temporary file to force the update.

For example if you want to change the case of "kh.png" to "KH.png" you would go to your Git repo from command line and do:

```
mv kh.png temp.png
git add -A
git commit -m "renaming kh.png to KH.png"
mv temp.png KH.png
git add -A
git commit --amend -m "Renamed file.txt to File.txt"
```
