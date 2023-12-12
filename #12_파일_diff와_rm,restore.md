## 파일 비교 diff

### 저장소 생성 1회 커밋
저장소 gfile, 파일 f<br>
<br>
$ git init gfile<br>
$ cd gfile<br>
$ echo aaa > f<br>
$ git commit -m A<br>
$ git log --oneline<br>
<br>

### 파일 수정 후 비교
작업 디렉토리만 다른 상태<br>
<br>
$ echo bbb >> f<br>
$ git status -s<br>
$ git diff<br>
$ git diff --staged<br>
<br>

### 파일 추가 후 비교
깃 저장소만 다른 상태<br>
<br>
$ git add f<br>
$ git status -s<br>
$ git diff<br>
$ git diff --staged<br>
$ git diff HEAD<br>
<br>

### 파일 커밋 비교
3 영역이 모두 동일<br>
$ git commit -m B<br>
$ git log --oneline<br>
$ git status<br>
$ git diff<br>
$ git diff --staged<br>
$ git diff HEAD<br>
<br>

### 버전 간의 파일 비교
HEAD<u>~ </u>와 HEAD 비교<br>
이전 버전과 작업 디렉토리, 스테이징 영역 비교<br>
$ git diff HEAD<u>~ </u>HEAD<br>
$ git diff HEAD HEAD~<br>
$ git diff --staged HEAD~<br>
$ git diff HEAD~<br>
<br>

## 파일 삭제 rm과 복구 restore

### 명령 별칭(git alias) 생성
계속 사용하는 깃 명령을 짧게 다른 이름으로 만드는 방법<br>
$ git config --global alias.ss 'status -s'<br>
다음과 동일하다<br>
$ git status -s<br>
$ git ss<br>
<br>

### 파일 g 생성 후 커밋밋
명령 별칭 ss 생성<br>
$ git config --global alias.ss 'status -s'<br>
$ echo 111 > g<br>
$ git add f g<br>
$ git commit -m 1<br>
$ git log --oneline<br>
$ ls<br>
<br>

### 파일 g 삭제 
파일 g를 WD와 SA에서 함께 삭제<br>
$ git ss<br>
$ git rm g<br>
$ git ss<br>
$ ls <br>
$ ls-files<br>
<br>

### 현재 상태 커밋
파일 g를 삭제한 상태를 커밋<br>
$ git ss<br>
$ git commit -m 'delete g'<br>
$ git ss<br>
$ ls<br>
$ git ls-files<br>
$ git log --oneline<br>
$ git show<br>
<br>

### 스테이징 영역에서 g 파일 복원
파일 g는 HEAD~에 있는 상태
$ git ls-files
$ git restore --source=HEAD<u>~ </u>--staged g
