- [[#명령어 북마크|명령어 북마크]]
- [[#기본 명령어|기본 명령어]]
	- [[#기본 명령어#디렉토리 설정|디렉토리 설정]]
	- [[#기본 명령어#로그 출력|로그 출력]]
	- [[#기본 명령어#브랜치|브랜치]]
	- [[#기본 명령어#병합|병합]]
		- [[#병합#일반 merge (3-way 브랜치)|일반 merge (3-way 브랜치)]]
		- [[#병합#rebase & merge|rebase & merge]]
- [[#필요없는 명령어|필요없는 명령어]]


git bash에서 cd 'C:\Users\Hutosuto\Documents\Obsidian Vault' 하면 저장소 선택돼서 명령 가능

vscode에서 바로 git 사용할 수도 있다

rebase merge 하는 이유 : 간단하고 짧은 브랜치들은 이거 쓰면 깔끔해보임

HEAD : 내 현재 위치

vim 에디터 : i로 입력하고 esc 누르고 :wq로 저장 후 닫기



## 명령어 북마크
<hr>

`git reset --hard origin/main`
: 이 명령어는 로컬 브랜치를 원격 브랜치와 동일하게 만듭니다. 
즉, 로컬 변경 사항을 모두 무시하고 원격 브랜치의 상태로 덮어씁니다.

저장소 경로 들어가서 `rm -rf .git` : Git 저장소 삭제


## 기본 명령어
<hr>

### 디렉토리 설정

`cd 'C:\Users\Hutosuto\Desktop\'` : 바탕화면 디렉토리 설정 (노트북)
`cd 'C:\Users\Hutosuto\Documents\Obsidian Vault'` : 옵시디언 디렉토리 설정 (노트북)

`cd 'C:\Users\bioma\OneDrive\Documents\Obsidian Vault'`

### 로그 출력

`git status` : 현재 작업 디렉토리와 스테이징된 파일의 상태를 보여줌. 파일의 변경, 추가, 삭제 내역을 확인할 수 있음.
- **Untracked files**: Git이 추적하지 않는 파일들.
- **Changes not staged for commit**: 수정되었지만 스테이징되지 않은 파일들.
- **Changes to be committed**: 스테이징되었고 커밋될 준비가 된 파일들.

`git log` : 저장소의 커밋 기록을 보여줌.
- **커밋 해시 (Commit hash)**: 각 커밋을 고유하게 식별하는 SHA-1 해시 값.
- **저자 (Author)**: 커밋을 만든 사람의 이름과 이메일.
- **날짜 (Date)**: 커밋이 만들어진 날짜와 시간.
- **커밋 메시지 (Commit message)**: 커밋에 대한 설명.

### 브랜치

`git branch 브랜치명` : 브랜치 생성
`git switch 브랜치명` : 브랜치로 이동

`git branch -d 브랜치명` : merge 완료된 브랜치 삭제
`git branch -D 브랜치명` : merge 안한 브랜치 삭제

### 병합

`git merge 브랜치명` : 브랜치 병합 (같은 파일 바꿨으면 conflict 일어남. 원하는 코드만 남기고 git add, git commit 하면 merge 완료됨)
`git merge --squash 새브랜치` : sqaush & merge

#### 일반 merge (3-way 브랜치)
1. 중심 브랜치로 이동해서
2. git merge 새로운브랜치명

#### rebase & merge
1. 새로운브랜치로 이동
2. git rebase 중심브랜치명
3. 중심브랜치로 이동
4. git merge 새로운브랜치명


### 파일/커밋 되돌리기

`git resotre 파일명` : 가장 최근 커밋된 버전 기준으로 파일을 되돌림 
`git restore --source 커밋아이디 파일명` : 특정 commit 시점으로 파일 복구

`git restore --staged 파일명` : staging 취소

`git revert 커밋아이디` : commit 취소 (해당 커밋에서 바꿨던거 되돌리는 커밋)
`git revert 커밋아이디1 커밋아이디2` : commit 여러 개 취소
`git revert HEAD` : 최근 commit 취소

`git reset --hard 커밋아이디` : 과거로 모든걸 되돌리기 (협업시엔 사용금지)
`git reset --soft 커밋아이디` : 리셋인데 변동사항 지우지 말고 스테이징 해놓기
`git reset --mixed 커밋아이디` : 리셋인데 변동사항 지우지 말고 unstage 해놓기

### github 관련

`git branch -M main` : 브랜치 이름 변경하는 방법. github.com은 기본 브랜치 이름을 main으로 사용하라고 강요함.
`git push -u 원격저장소주소 main` : -u 붙이면 방금 입력한 주소 기억하라는 뜻. 이후엔 git push만 입력해도 된다.

`git remote add origin 원격저장소주소` : 주소가 필요할 때마다 origin이라는 변수 쓰면 됨
`git remote -v` : 변수 목록 확인

`git clone https://원격저장소주소` : 원격저장소에 있던거 그대로 내려받기

저장소에 올리지 않는 파일들은 .gitignore 파일을 만들어서 명시하면 된다.

git pull은 git fetch + git merge임
git fetch : 원격 저장소 신규 commit 가져오셈
git merge : 내 브랜치에 merge

github 사이트에서 브랜치 생성, 파일 생성, 커밋 등 할 수 있음

로컬에서 브랜치 만들고 git push 하면 그대로 원격 저장소에 브랜치 새로 생성됨


## 필요없는 명령어
<hr>

![](Pasted%20image%2020240517164734.png)

**staging area는 commit을 하기 전에 commit할 파일들을 골라놓는 곳**
**repository는 commit된 파일의 버전들을 모아놓는 곳**

`git add 파일명` 
`git commit -m '아무메세지'`
파일의 현재 상태를 기록할 수 있다.

`git log --graph --oneline --all` : 브랜치마다 commit 내역을 그래프로 보고 싶다.

`git difftool` : vim 에디터에서 최근에 commit한 파일과 현재 파일의 차이점 보여줌
`qa` 입력하면 종료 가능

`git difftool 커밋아이디` : 현재파일 vs 특정커밋 비교 가능
`git difftool 커밋아이디1 커밋아이디2` : 특정커밋 vs 특정커밋 비교 가능

vs code에서 extension 깔면 훨씬 편하게 볼 수 있어서 거의 안 쓴다.


