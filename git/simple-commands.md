# simple-commands

## commands

```
$ git fetch
$ git push origin master
$ git rebase
$ git rebase -i
$ git cherry-pick {commit_number}
$ git revert HEAD
$ git clean -df
```

## git add

Here is table for quick understanding of "add":

Git Version 1.x:

![][image1]

Git Version 2.x:

![][image2]

```
$ git add -A # is equivalent to git add --all
$ git add -u # is equivalent to git add --update
```

## git log

```
$ git reflog
$ git log --decorate
$ git log --author="<authorname>" --oneline --shortstat
```

## git checkout

```
# 워킹트리의 수정된 파일을 index에 있는 것으로 원복
$ git checkout  -- <파일>
# 워킹트리의 수정된 파일을 HEAD에 있는 것으로 원복(이 경우 --는 생략가능)
$ git checkout HEAD -- <파일명>
# 워킹트리의 수정된 파일의 내용을 FETCH_HEAD에 있는 것으로 원복? merge?(이 경우 --는 생략가능)
$ git checkout FETCH_HEAD -- <파일명>
# ??? 워킹트리의 모든 수정된 파일의 내용을 HEAD로 원복.
$ git checkout HEAD .
# 변경된 파일들을 HEAD로 모두 원복(아직 커밋하지 않은 워킹트리와 index 의 수정사항 모두 사라짐. 신규추가 파일 제외)
$ git checkout -f
```

## git reset

```
# 해당 파일을 index에 추가한 것을 취소(unstage). 워킹트리의 변경내용은 보존됨. (--mixed 가 default)
$ git reset -- <파일명>
# 위와 동일
$ git reset HEAD <파일명>
# 최종 커밋을 취소. 워킹트리는 보존됨. (커밋은 했으나 push하지 않은 경우 유용)
$ git reset HEAD^
# 마지막 2개의 커밋을 취소. 워킹트리는 보존됨.
$ git reset HEAD~2
# 마지막 2개의 커밋을 취소. index 및 워킹트리 모두 원복됨.
$ git reset --hard HEAD~2
# 머지한 것을 이미 커밋했을 때,  그 커밋을 취소. (잘못된 머지를 이미 커밋한 경우 유용)
$ git reset --hard ORIG_HEAD
# HEAD에서 변경한 내역을 취소하는 새로운 커밋 발행(undo commit). (커밋을 이미 push 해버린 경우 유용)
# 워킹트리 전체를 마지막 커밋 상태로 되돌림. 마지막 커밋이후의 워킹트리와 index의 수정사항 모두 사라짐. (변경을 커밋하지 않았다면 유용)
$ git reset --hard HEAD
```

## git merge

```
$ git merge --no-ff --no-commit origin/branch
```

## replace word with git grep

```
$ git grep -l 'original_text' | xargs sed -i 's/original_text/new_text/g'
```

## gerrit integration

```
$ git push --receive-pack="git receive-pack" origin {commit SHA-1 or HEAD}:refs/drafts/{branch}
# A general rule to push into gerrit, branch = master:
$ git push origin <a_local_branch_name or specific_commit or HEAD>:refs/for/master
# A general rule to push into gerrit as DRAFT, branch = master:
$ git push origin <a_local_branch_name or specific_commit or HEAD>:refs/drafts/master
```

[image1]: https://cl.ly/pclR/C8AF9FFACA49EA5EB44EDEA7C9AE8876.png
[image2]: https://cl.ly/pcrB/055C90E318D6039A23D4A26EE30F1301.png
