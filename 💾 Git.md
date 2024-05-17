git bash에서 cd 'C:\Users\Hutosuto\Documents\Obsidian Vault' 하면 저장소 선택돼서 명령 가능

vscode에서 바로 git 사용할 수도 있다



`git reset --hard origin/main`
: 이 명령어는 로컬 브랜치를 원격 브랜치와 동일하게 만듭니다. 
즉, 로컬 변경 사항을 모두 무시하고 원격 브랜치의 상태로 덮어씁니다.

## 기본 명령어

`cd 'C:\Users\Hutosuto\Desktop\'` : 바탕화면 디렉토리 설정
`cd 'C:\Users\Hutosuto\Documents\Obsidian Vault'` : 옵시디언 디렉토리 설정

`git status` : 현재 작업 디렉토리와 스테이징된 파일의 상태를 보여줌. 파일의 변경, 추가, 삭제 내역을 확인할 수 있음.
- **Untracked files**: Git이 추적하지 않는 파일들.
- **Changes not staged for commit**: 수정되었지만 스테이징되지 않은 파일들.
- **Changes to be committed**: 스테이징되었고 커밋될 준비가 된 파일들.

`git log` : 저장소의 커밋 기록을 보여줌.
- **커밋 해시 (Commit hash)**: 각 커밋을 고유하게 식별하는 SHA-1 해시 값.
- **저자 (Author)**: 커밋을 만든 사람의 이름과 이메일.
- **날짜 (Date)**: 커밋이 만들어진 날짜와 시간.
- **커밋 메시지 (Commit message)**: 커밋에 대한 설명.

`git branch 브랜치명` : 브랜치 생성
`git switch 브랜치명` : 브랜치로 이동
`git merge 브랜치명` : 브랜치 병합 (같은 파일 바꿨으면 conflict 일어남)

## 필요없는 명령어

![](Pasted%20image%2020240517164734.png)

**staging area는 commit을 하기 전에 commit할 파일들을 골라놓는 곳**
**repository는 commit된 파일의 버전들을 모아놓는 곳**

`git add 파일명` 
`git commit -m '아무메세지'`
파일의 현재 상태를 기록할 수 있다.

`git difftool` : vim 에디터에서 최근에 commit한 파일과 현재 파일의 차이점 보여줌
`qa` 입력하면 종료 가능

`git difftool 커밋아이디` : 현재파일 vs 특정커밋 비교 가능
`git difftool 커밋아이디1 커밋아이디2` : 특정커밋 vs 특정커밋 비교 가능

vs code에서 extension 깔면 훨씬 편하게 볼 수 있어서 거의 안 쓴다.


