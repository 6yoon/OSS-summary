## 파일 삭제 rm

### 파일 삭제
리눅스 명령 파일 삭제: $ rm [file]<br>
-> 작업 디렉토리에서 file 삭제<br>
<br>
깃 명령 파일 삭제: $ git rm [file]<br>
-> 작업 디렉토리와 스테이징 영역에서 모두 file 삭제<br>
-> 다음 커밋에서 지정한 file을 삭제하겠다는 의미<br>
-> Tracked 상태의 파일을 제거하여 Untracked 상태로 만듦<br>
<br>
깃 명령 파일 삭제: $ git rm --cached [file]<br>
-> 스테이징 영역에서 file 삭제 → 작업 디렉토리에서는 삭제되지 않음<br>
-> $ git ls -files 결과에서 보이지 않음 → 기본적으로 스테이징 영역의 파일 목록을 표시<br>
<br>

### 작업 디렉토리와 스테이징 영역에서 파일 삭제
현재 상태: 3영역 (WD, SA, GR) 모두에 파일 f, g가 있는 상태<br>
▽<br>
$ git rm g: 작업 디렉토리와 스테이징 영역에서 파일 g 삭제<br>
▽<br>
$ git commit -m ‘Delete g’: 파일 g가 삭제된 상태에서 커밋<br>
<br>

### 스테이징 영역에서만 파일 삭제
현재 상태: WD와 SA에 파일 f가 있는 상태<br>
▽<br>
$ git rm --cached f: 스테이징 영역에서 파일 f 삭제<br>
<br>

### 작업 디렉토리만 파일 삭제
WD에만 파일 f가 있는 상태<br>
▽<br>
$ rm f: 작업 디렉토리에서 파일 f 삭제<br>
<br>

## 파일 복원 restore

### $ git restore [file]
작업 디렉토리의 파일 f를 스테이징 영역의 파일 상태로 복구<br>
-> 작업 디렉토리에 있던 f 내용이 사라지므로 유의<br>
-> 3 영역에서 파일 f가 작업 디렉토리와 스테이징 영역이 같은 상태가 됨<br>
<br>

### $ git restore --staged [file]
깃 저장소의 최신 커밋 상태의 파일 f를 스테이징 영역에 복구<br>
-> 스테이징 영역에 있던 f 내용이 사라지므로 유의<br>
-> 3 영역에서 스테이징 영역의 파일 f가 깃 저장소 영역과 같은 상태가 됨<br>
<br>

### 깃 저장소 내용으로 한번에 모두 복원
깃 저장소의 최신 커밋 상태의 파일 f를 작업 디렉토리와 스테이징 영역에 한번에 복구<br>
-> 파일 f가 현재 커밋 상태의 내용으로 작업 디렉토리와 스테이징 영역 모두 같은 상태가 됨<br>
-> $ git restore --source=HEAD --staged --worktree f<br>
<br>

### HEAD 내용으로 작업 디렉토리 복원
깃 저장소의 최신 커밋 상태의 파일 f를 작업 디렉토리에 복사되어 동일하게 됨<br>
-> $ git restore --source=HEAD f<br>
<br>

### $ git restore --source=HEAD^ --staged [file]
깃 저장소의 이전 커밋 상태의 파일 f를 스테이징 영역에 복구<br>
-> 스테이징 영역에 있던 f 내용이 사라지므로 유의<br>
-> 3 영역에서 스테이징 영역의 파일 f가 깃 저장소 영역과 같은 상태가 됨<br>
<br>
