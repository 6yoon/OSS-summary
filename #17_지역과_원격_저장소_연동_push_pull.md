## 개인 접근 토큰 (Personal Access Token) 생성

### 개인 접근 토큰 인증 개요
- 개인 프로젝트 진행 도중 에러 메세지 발생
  - 2021년 8월 13일 이후부터는 기존의 비밀번호 대신 토큰을 사용하여 접근
    → github에서 Personal Token을 발급 받아 설정해야 함<br>

### Personal Access Tokens
생성된 개인 접근 토큰: 후에 토큰이 표시되지 않기 때문에 잘 보관 해야 함<br>

## 깃허브 원격 저장소 수정 후 pull

### 깃 깃허브 push, pull
- 일상 생활 → 밀기, 끌기
- 깃허브 → 올리기, 내리기

### 원격 저장소 수정 후 지역 저장소에서 pull
- 원격 저장소의 수정을 지역 저장소에 반영 (pull)
- 명령어
  - $ git pull <저장소_별칭><브랜치명>
  - $git pull

### 윈도우 push 중 오류
- 참조 오류 발생 가능
- 인증 오류 발생 가능

## 지역에서 원격 저장소로 push

### 지역 저장소에서 push
쓰기 권한이 있어야 push가 가능
- push
  - 로컬 저장소에 남겨 놓은 코드 변경 이력들이 원격 저장소로 전송
- 명령어
  - $ git push <저장소_별칭><브랜치명>

### 명령 push에서 인자 생략하기
옵션 -u 사용, 최초에 한 번만 저장소명과 브랜치명을 입력하고 그 이후에는 모든 인자를 생략 가능<br>
설정 변수 push.default를 current로 설정<br>
대부분의 경우 로컬 저장소와 원격 저장소에서 동일한 브랜치 이름을 사용하기 때문에 항상 현재 브랜치를 기준으로 git push 명령어가 작동한다면 매우 편리하다 <br>

### git pull = git fetch + git merge 
fetch 명령과 병합하는 merge 명령이 순차적으로 진행<br>
fetch 명령으로 작업한 내용을 먼저 확인 이후 merge 여부를 결정<br>
<br>

### fetch
원격 저장소에서 로컬 저장소로 소스를 가져와 병합을 미수행하는 명령<br>
$ git fetch <remote><br>

### fetch 후 병합
깃허브의 내용을 반영하려면 fetch 후 merge 해야 함<br>
$git merge origin/main <br>

### 원격 브랜치
원격을 포함한 모든 브랜치 파악 
- 지역의 브랜치와 HEAD: main HEAD
- 원격의 브랜치와 HEAD: origin/main origin/HEAD
