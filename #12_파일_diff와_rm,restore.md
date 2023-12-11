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
