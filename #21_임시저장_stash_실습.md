## 임시 저장 기초

### 저장소 생성 후 커밋
$ git init gstash<br>
$ cd gstash<br>
$ git add f<br>
$ git stash<br>
$ git commit -m A<br>
$ git lgag1<br>

### 3 영역을 모두 다르게
파일 f가 3 영역이 모두 다르고 추적되지 않은 파일 g도 생성<br>
$ echo 222 >> f<br>
$ git add f<br>
$ echo aaa > g<br>
$ echo 333 >> f<br>
$ git status -s<br>
$ git diff<br>
$ git diff --staged<br>
$ git diff HEAD<br>

### 임시 저장에 저장
옵션 -u가 없으면 untracked file은 그대로 남음<br>
$ git lgag1<br>
$ git status<br>
$ git stash<br>
$ git stash list<br>

### 임시 저장을 다시 작업 디렉토리에 복사
저장에서 삭제되지 않고 복사 (스테이징 영역은 복원 X)<br>
$ git stash apply<br>
$ cat f<br>
$ git diff<br>

### 다시 파일 수정한 후 임시 저장 적용
스테이징 영역도 함께 복원 → 다시 처음 상태가 됨<br>
$ echo 111 > f<br>
$ git status -s<br>
$ git diff<br>
$ git diff --staged<br>
$ git diff HEAD<br>
$ git stash list<br>

## 임시 저장 관련 다양한 명령

### stash save로 저장
- --keep-index, -k → 이미 index(SA)에 추가된 모든 변경 사항은 그대로 유지 됨
  - 스테이징 영역은 제외하고, 작업 디렉토리만 저장, 작업 디렉토리는 스테이징 영역 내용으로
- --include-untracked, -u
  - untracked file도 포함해 저장
  - 
### 임시 저장 복원 시 충돌 발생
- 임시 저장 목록에서 제거되지 않음
- 충돌 시 상태 표시 → Both modified

### ### 충돌 해결
파일 수정 후 add

### 커밋과 임시 저장과의 비교
$ git stash show -p

### 옵션 -m으로 메시지 저장

### 커밋과 임시 저장의 비교
$ git stash show -p

### 임시 저장 목록 삭제
- drop : 최신이나 지정한 임시 저장 삭제
- clear : 모든 임시 저장 삭제

### Untracked file 삭제
새로 생성한 파일 삭제
