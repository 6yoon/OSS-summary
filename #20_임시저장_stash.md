## 깃 4 영역과 임시 저장 개요

### 깃 4 영역
→ 깃 3 영역 + stash 영역

### 깃 영역의 가장 단순한 상태
→ Nothing to commit, working tree is clean

### Git Stash
- 사전적 의미 stash
    - 놓다, 남겨두다, 감추다, 안전한 곳에 숨겨두다
    - 커밋할 필요 없이 파일의 변경 사항을 숨기거나 비밀리에 저장할 수 있는 강력한 도구
        - 작업 디렉토리와 스테이징 영역의 원래 내용을 stash 스택에 저장
        - 작업 디렉토리와 스테이징 영역의 값을 깃 저장소의 마지막 커밋 내용으로 복사
    - 따로 안전한 곳에 저장했다가 다시 가져올 수 있는 기능 (저장 내용: WD, SA)

### Stash 저장 구조
- 깃에서 임시 저장소(스택 구조)에 저장
    - Stacks of git stashes (가장 최근의 내용이 가장 위에 저장되는 구조)

### Git stash의 필요성
- 브랜치 이동 또는 이전 커밋으로 이동하려면?
    - $ git switch bname
    - $ git checkout HEAD~
    - 커밋할 게 없고, 작업 트리가 깨끗해야 한다
- 수정한 내용이 있거나 커밋할 게 있는 상황에서 브랜치 이동 또는 이전 커밋으로 이동하려면?
    - 현재 작업 공간의 수정 내용과 인덱스의 내용을 보관해야 함 (나중에 다시 사용하기 위해)

### 임시 저장 영역에 저장되는 내용
- 작업 디렉토리 내용과 스테이징 영역 내용이 stash에 저장 (최신 커밋 자료로 남는다)

## 임시 저장 명령 stash

### 임시 저장 명령 stash
- 작업 폴더와 스테이징 영역을 숨김(stash)에 저장하고 작업 폴더를 정리
    - $ git stash
    - $ git stash -m ‘message’
    - $ git stash save
    - $ git stash save ‘message’
- 옵션
    - --keep-index, -k
        - 스테이징 영역은 제외하고, 작업 폴더만 저장
    - --include-untracked, -u
        - Untracked file도 포함해 저장  ****

### 임시 저장의 최신 저장 내용으로 다시 복원

- 최근 임시 저장 내용을 가져와 반영, stash 목록은 그대로
    - 기본으로 작업 디렉토리 내용만 다시 복사해 활용
        - $ git stash apply
    - 스테이징 영역도 함께 복사하기 위해선 옵션 사용
        - $ git stash apply --index

### 주요 옵션
- 옵션 -k | --keep-index
    - 스테이징 영역은 저장하지 않고 그대로 놔둠
    - 그러므로 checkout 불가능
- 옵션 -u | --include-untracked
    - Untracked file도 포함해 저장
- 옵션 -p | --patch
    - 변경된 모든 사항들을 저장하는 것이 아니며 대화형 프롬프트를 통해 자신이 stash에 저장할 것과 저장하지 않을 것을 지정 가능

### Stash 목록 보기
- $ git stash list
    - stash@{0} → 가장 최신 것이 0
    - stash@{1}
    - stash@{2}
    - …

### 특정 stash 확인
- 해당 stash 항목이 생성되었을 때의 커밋 자료와 최신 stash 항목 간의 차이로 표시**
    - $ git stash show
        - h.txt | 2++
        - 1 file changed, 2 insertion(+) → 변화된 파일과 변화된 수만 표시
    - $ git stash show -p
        - -p: 파일 내용의 차이까지 보여준다
- 해당 stash 항목이 생성되었을 때의 커밋 자료와 해당 stash 항목 간의 차이로 표시
    - $ git stash show stash@{n}
    - $ git stash show stash@{n} -p

### 임시 저장된 stash 반영
- 최근 또는 지정된 임시 저장소 내용을 가져와 반영하고 삭제
    - $ git stash pop
    - $ git stash pop stash@{n}
- 최근 또는 지정된 임시 저장소 내용을 가져와 반영, 작업 디렉토리만 반영, stash 목록은 그대로
    - $ git stash apply
    - $ git stash apply stash@{n}
- 최근 또는 지정된 임시 저장소 내용을 가져와 반영, 작업 디렉토리와 스테이징 영역도 반영, stash 목록은 그대로
    - $ git stash apply --index
    - $ git stash apply --index stash@{n}

### 특정 stash 삭제와 모든 stash 삭제
- 최근 임시 저장 내용을 삭제
    - $ git stash drop
- 지정된 임시 저장 내용을 삭제
    - $ git stash drop stash@{n}
- 모든 stash 목록을 제거
    - $ git stash clear

### Untracked file 삭제
- $ git clean
    - 바로 삭제되지 않음
      fatal: clean.requireForce defaults to true and neither -i, -n, nor -f given; refusing to clean 
- $ git clean -i
    - 물어보고 삭제
- $ git clean -f
    - 무조건 삭제
