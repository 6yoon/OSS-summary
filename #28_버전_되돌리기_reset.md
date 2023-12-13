## 버전 되돌리기 reset과 옵션

### 기능 reset 이해
- 커밋 이력에서 이전 커밋으로 완전히 되돌아가는(roll back) 방법
    - ‘타임 머신’과 같음
    - 이동 되는 해당 커밋 이후의 이력은 모두 사라지므로 주의가 필요
        - 새로운 커밋이 생성되지 않음
    - 깃 저장소는 이전 커밋 내용으로 수정
        - 다만 reset 이전에 있던 WD와 SA의 내용을 어떻게 유지할지 관건
            → 옵션으로 처리
**reset의 3가지 옵션**
- --hard, --mixed, --soft
    - reset 실행 시 무조건 깃 저장소에는 복사, WD와 SA는?

**reset 옵션 --hard**
$ git reset --hard HEAD~
→ 지정된 HEAD~ (커밋 메세지 Alphabet)의 내용으로 WD, SA, GR 모두 복사, 수정 
  (reset 전에 있던 WD, SA 작업 내용이 모두 사라지므로 주의)

**reset 옵션 --mixed**
$ git reset --mixed HEAD~
지정된 HEAD~(커밋 메시지 Alphabet)의 내용으로 SA와 GR 모두 복사 , 수정
→ 커밋 메시지 Alphanumeric의 로그 이력과 함께 당시의 SA, GR 내용 모두 사라짐 
→ 다만 WD의 내용은 그대로 남음 
→ 옵션 --mixed는 옵션이 없는 것과 같음

**reset 옵션 soft**
$ git reset --soft HEAD~
지정된 HEAD~(커밋 메시지 Alphabet)의 내용으로 GR만 복사, 수정
→ 커밋 메시지 Alphanumeric의 로그 이력은 사라짐
→ WD와 SA의 내용 모두 이전 그대로 남음

## reset 정리, checkout과 reset 비교

### reset 3가지 방식
- **--hard**
    - 인자의 커밋 깃 저장소의 내용을 WD와 SA, 그리고 GR에 모두 복사, 수정
- **--mixed**
    - 기본 옵션으로 SA와 GR에 복사, 수정
- **--soft**
    - GR에만 복사, 수정하므로 WD와 SA는 이전 내용이 그대로 남음

### 커밋 되돌리기

- **--soft**
    - 돌아간 후: 인덱스가 그대로(바로 다시 커밋할 수 있는 상태)
        → commit하면 다시 마지막 이전 HEAD로 돌아간다
- **--mixed**
    - 돌아간 후: WD만 그대로
        → add, commit하면 다시 마지막 이전 HEAD로 돌아간다
- **--hard**
    - 돌아간 후: 모두 삭제 됨
        → 파일 수정, add, commit하면 다시 마지막 이전 HEAD로 돌아간다

### reset 후 다시 바로 이전 상태로 되돌아가기
$ git reset --hard ORIG_HEAD

### reset과 checkout 비교
- $ git reset 9033
    - 브랜치의 마지막 커밋을 수정하는 명령
