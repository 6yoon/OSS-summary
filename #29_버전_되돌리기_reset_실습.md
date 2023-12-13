## 버전 되돌리기 reset

### [실습]

**준비**
$ git init grst
$ cd grst

$ echo 123 > h
$ git add h
$ git commit -m Numeric

$ echo ABC >> h
$ git commit -am Alphabet
$ echo AB12 >> h
$ git commit -am Alphanumeric

$ echo '[1, 2]' >> h
$ git add h
$ echo '{1, 2}' >> h
$ git status

**reset 전 수행**
reset --hard 실행 시 현재 상태가 모두 제거 됨
- $ git stash
    → 현재의 WD와 SA를 임시저장
- $ git stash list
    → 확인하기
- $ git status
    → 현재 상태 확인

**reset 옵션 --hard**

**다시 원래 상태로 복원**
- reset 이전의 커밋 ID를 ORIG_HEAD에 저장

**reset 옵션 --mixed**

**reset 옵션 --soft**

**작업 디렉토리와 스테이징 영역 수정**
- 3회 커밋 이후 다음 상태로 복원
    - WD와 SA를 임시 저장에 저장
    - 임시 저장을 다시 불러온다 → --index 옵션 사용
- $ git stash apply --index
reset 옵션 --soft

## checkout과 reset 비교

### 비교

- **reset → 브랜치의 마지막 커밋을 수정**
- **checkout → HEAD 포인터를 브랜치의 마지막 커밋 이전으로 이동**

### checkout 과거 여행 복습
- 상태가 깔끔해야 checkout 가능
    nothing to commit, working tree clean
