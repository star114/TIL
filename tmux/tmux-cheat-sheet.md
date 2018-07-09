# tmux-cheat-sheet

* tmux new-session -s {session name}
* ^a c : 현재 경로 - 새 window
* ^a % : 현재 경로 - vertical
* ^a " : 현재 경로 - horizontal split
* ^a C : 세션 실행했던 위치에서 새 윈도우
* ^a | : 세션 실행했던 위치에서 vertical
* ^a - : 세션 실행했던 위치에서 split
* ^a d : 세션 나가기
* tmux list-sessions : 현재 실행중인 세션들
* tmux attach -t {session name}
* ^a () 좌우 세션
* ^a 0-9 : 윈도우 이동
* ^a :rename-session
* ^a :rename-window
* ^a hjkl
* ^a 방향키 -> vertical/horizontal 이동
