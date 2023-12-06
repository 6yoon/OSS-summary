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

