- [[#make.md 오류 해결|make.md 오류 해결]]
- [[#명령어 북마크|명령어 북마크]]
- [[#디렉토리 설정|디렉토리 설정]]
- [[#로그 출력|로그 출력]]
- [[#브랜치|브랜치]]
- [[#병합|병합]]
	- [[#병합#일반 merge (3-way 브랜치)|일반 merge (3-way 브랜치)]]
	- [[#병합#rebase & merge|rebase & merge]]
- [[#파일/커밋 되돌리기|파일/커밋 되돌리기]]
- [[#github 관련|github 관련]]
- [[#git 초기 세팅|git 초기 세팅]]
- [[#필요없는 명령어|필요없는 명령어]]

git add -p

git bash에서 cd 'C:\Users\Hutosuto\Documents\Obsidian Vault' 하면 저장소 선택돼서 명령 가능

vscode에서 바로 git 사용할 수도 있다

rebase merge 하는 이유 : 간단하고 짧은 브랜치들은 이거 쓰면 깔끔해보임

HEAD : 내 현재 위치

vim 에디터 : i로 입력하고 esc 누르고 :wq로 저장 후 닫기

conflict 해결
```bash
<<<<<<<<<<<<<< HEAD
[현재 브랜치의 변경 사항]
================== [구분선]
[머지 대상 브랜치의 변경 사항]
>>>>>>>>>>>>>> [대상 브랜치명]
```

충돌을 해결하기 위해서 `<<<<<<<<`와 `=========`와 `>>>>>>>>>`을 모두 제거한 후 선택해야 되는 변경사항을 반영해 깨끗하게 만들면 됨


## make.md 오류 해결
---

```
.makemd/fileCache.mdc
.makemd/superstate.mdc
.obsidian/plugins/make-md/Spaces.mdb
```

이거 .gitignore에 추가


## 명령어 북마크
---

```
git reset --hard origin/main
```
이 명령어는 로컬 브랜치를 원격 브랜치와 동일하게 만듭니다. 
즉, 로컬 변경 사항을 모두 무시하고 원격 브랜치의 상태로 덮어씁니다.

```
rm -rf .git
```
저장소 경로 들어가서 이거 치면 Git 저장소 삭제


## 디렉토리 설정
---

바탕화면 디렉토리 설정 (노트북)
```bash
cd /home/hutosuto/다운로드
```

옵시디언 디렉토리 설정 (노트북)
```bash
cd /home/hutosuto/문서/Obsidian Vault
```

옵시디언 디렉토리 설정 (데스크탑)
```bash
cd 'C:\Users\bioma\OneDrive\Documents\Obsidian Vault'
```

## 로그 출력
---

```bash
git status
```
현재 작업 디렉토리와 스테이징된 파일의 상태를 보여줌. 파일의 변경, 추가, 삭제 내역을 확인할 수 있음.

- **Untracked files**: Git이 추적하지 않는 파일들.
- **Changes not staged for commit**: 수정되었지만 스테이징되지 않은 파일들.
- **Changes to be committed**: 스테이징되었고 커밋될 준비가 된 파일들.

```bash
git log
```
저장소의 커밋 기록을 보여줌.

- **커밋 해시 (Commit hash)**: 각 커밋을 고유하게 식별하는 SHA-1 해시 값.
- **저자 (Author)**: 커밋을 만든 사람의 이름과 이메일.
- **날짜 (Date)**: 커밋이 만들어진 날짜와 시간.
- **커밋 메시지 (Commit message)**: 커밋에 대한 설명.

## 브랜치
---

```bash
git branch 브랜치명
```
브랜치 생성

```bash
git switch 브랜치명
```
브랜치로 이동

```bash
git branch -d 브랜치명
```
merge 완료된 브랜치 삭제

```bash
git branch -D 브랜치명
```
merge 안한 브랜치 삭제

```bash
git pull origin [다른브랜치]
```
다른 branch pull

## 병합
---

```
git merge 브랜치명
```
브랜치 병합 : 같은 파일 바꿨으면 conflict 일어남. 원하는 코드만 남기고 git add, git commit 하면 merge 완료됨

```bash
git merge --squash 새브랜치
```
sqaush & merge

### 일반 merge (3-way 브랜치)

1. 중심 브랜치로 이동해서
2. git merge 새로운브랜치명

### rebase & merge

1. 새로운브랜치로 이동
2. git rebase 중심브랜치명
3. 중심브랜치로 이동
4. git merge 새로운브랜치명


## 파일/커밋 되돌리기
---

```c
git log
git reset --hard (git log 해쉬키)
git push --force
```

git 되돌리기


```bash
git push -f origin "branch name"
```
git 버전 되돌리고 깃허브에도 반영

```bash
git restore 파일명
```
가장 최근 커밋된 버전 기준으로 파일을 되돌림

```bash
git restore --source 커밋아이디 파일명
```
특정 commit 시점으로 파일 복구

```bash
git restore --staged 파일명
```
staging 취소

```bash
git revert 커밋아이디
```
commit 취소 (해당 커밋에서 바꿨던거 되돌리는 커밋)

```bash
git revert 커밋아이디1 커밋아이디2
```
commit 여러 개 취소

```bash
git revert HEAD
```
최근 commit 취소

```bash
git reset --hard 커밋아이디
```
과거로 모든걸 되돌리기 (협업시엔 사용금지)

```bash
git reset --soft 커밋아이디
```
리셋인데 변동사항 지우지 말고 스테이징 해놓기

```bash
git reset --mixed 커밋아이디
```
리셋인데 변동사항 지우지 말고 unstage 해놓기

## github 관련
---

```bash
git branch -M main
```
브랜치 이름 변경하는 방법. github.com은 기본 브랜치 이름을 main으로 사용하라고 강요함.

```bash
git push -u 원격저장소주소 main
```
-u 붙이면 방금 입력한 주소 기억하라는 뜻. 이후엔 git push만 입력해도 된다.

```bash
git remote add origin 원격저장소주소
```
주소가 필요할 때마다 origin이라는 변수 쓰면 됨

```bash
git remote -v
```
변수 목록 확인

```bash
git clone https://원격저장소주소
```
원격저장소에 있던거 그대로 내려받기

저장소에 올리지 않는 파일들은 .gitignore 파일을 만들어서 명시하면 된다.

git pull은 git fetch + git merge임
git fetch : 원격 저장소 신규 commit 가져오셈
git merge : 내 브랜치에 merge

github 사이트에서 브랜치 생성, 파일 생성, 커밋 등 할 수 있음

로컬에서 브랜치 만들고 git push 하면 그대로 원격 저장소에 브랜치 새로 생성됨


## git 초기 세팅
---

0. **git 시작**

```bash
git init
```

1. **원격 저장소 확인**

```bash
git remote -v
```

2. **원격 저장소 추가**

만약 원격 저장소가 설정되어 있지 않다면, 원격 저장소를 추가

```bash
git remote add origin https://github.com/닉네임/리포지터리이름.git
```

3. **원격 저장소 URL 설정 (Personal Access Token)**

그 후 Personal Access Token을 사용하여 원격 저장소 URL을 설정

```bash
git remote set-url origin https://<토큰>@github.com/닉네임/리포지터리이름.git
```


## GitHub 토큰 관리를 위한 gh 설치
---

Ubuntu에서 git을 쓸 때 GitHub login 때문에 복잡해 지지 않도록 GitHub CLI를 설치합니다.  
설치 후 **gh auth login** 명령으로 access token을 생성 혹은 설치합니다.  

```
$ curl -fsSL [https://cli.github.com/packages/githubcli-archive-keyring.gpg](https://cli.github.com/packages/githubcli-archive-keyring.gpg) | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg  
```

```
$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] [https://cli.github.com/packages](https://cli.github.com/packages) stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null  
```
  
```
$ sudo apt update  
$ sudo apt install gh
```
  

## Git duplicate
---

```bash
$ git clone --bare https://github.com/krafton-jungle/rbtree-lab.git
$ cd ${project_name}.git
# 아래 교육생 repository는 GitHub미리 만들어 놓아야 함
$ git push --mirror https://github.com/${교육생ID}/rbtree-lab.git
$ cd ..
$ rm -rf ${project_name}.git
$ git clone https://github.com/${교육생ID}/rbtree-lab.git
```

>아래와 같이 git 명령을 사용하여 GitHub에 있는 [과제](https://jungle-compass.krafton.com/mod/page/view.php?id=3933 "과제")를 다운로드 하고 자신의 git repository로 옮깁니다. 원본 repository에 있는 코드를 개선하기 위해 clone 혹은 fork하는 것이 아니고 자신의 repository로 복제(duplicate) 하는 것임을 명심하십시오

## 필요없는 명령어
---

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


