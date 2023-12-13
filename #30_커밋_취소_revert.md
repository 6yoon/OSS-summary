## 커밋 취소 revert

### 커밋 취소 revert
- **=undo와 비슷한 기능**
    - 지정한 특정 커밋을 취소해 바로 이전 상태로 되돌리는 방법
    - reset과 다르게 clean한 상태에서만 수행 가능
        → nothing to commit. working tree clean
    - 커밋해온 모든 변경 사항들을 rollback
    - 이전 커밋 히스토리는 그대로 유지 , 되돌리는 커밋이 그 이후에 추가

### revert 충돌과 해결
**인자가 HEAD~와 같이 HEAD 이전을 취소하면 충돌이 발생할 수 있음**
- 충돌이 발생하지 않으려면?
    - 바로 이전 취소를 여러 번 계속한다
    - Ctrl + z와 비슷

### 명령 revert
- **옵션 --no-edit**
    - 추가되는 커밋 메시지가 자동으로 ‘Revert “이전 커밋 메시지”’로 지정

### 오류가 발생해 revert가 취소
- **nothing to commit, working tree clean이 아니면 오류**
- **해결 방법**
    - 커밋 후 다시 revert (현재 커밋 내용으로)
        → 수정 내용 사라짐
    - $ git reset --hard HEAD~ (이전 커밋 내용으로)
        → 수정 내용 사라지고 현재 커밋 로그도 사라짐

### revert로 HEAD 바로 이전 상태로 돌아가기
- 취소 인자를 HEAD로 사용

### $ git revert HEAD

## reset vs revert 비교

### reset vs revert
- 되돌리기와 취소
- 되돌리기, 재설정 reset
    - 특정 커밋으로 되돌아가고 그 이후의 로그 이력은 제거
- 커밋 취소 revert
    - 특정 커밋을 취소하는 새로운 커밋 생성, 이전 모든 이력은 그대로 남음
