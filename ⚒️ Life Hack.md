- [[#ChatGPT 북마크|ChatGPT 북마크]]
- [[#윈도우 단축키|윈도우 단축키]]
- [[#파일 경로 표기법|파일 경로 표기법]]
- [[#Github Copilot|Github Copilot]]
	- [[#Github Copilot#단축키|단축키]]
	- [[#Github Copilot#명령어|명령어]]
- [[#옵시디언|옵시디언]]


Ctrl+D : 한 줄 전부 삭제

## 윈도우 단축키
<hr>

Ctrl+Shift+V : 서식 없이 붙여넣기
win+D : 바탕화면 바로가기
win+방향키 : 화면 절반으로 정리
Shift+Ins : 붙여넣기


## 파일 경로 표기법
<hr>

**.** : 현재 웹페이지가 소속된 폴더
**..** : 현재 웹페이지의 부모 폴더


## Github Copilot
<hr>

### 단축키
- `Ctrl + I` : 명령 내리기
- `Ctrl + 우측 방향키` : 단어 단위 선택
- `Alt + [, ]` : 코드 추천 고르기
- `Ctrl + Enter` : 한 번에 제안 확인

| 명령어              | Keybinding   |
| ---------------- | ------------ |
| Copilot 활성화/비활성화 | Shift + Q    |
| 설명 요청            | Shift + E    |
| 고치기 요청           | Shift + F    |
| 테스트 생성           | Shift + T    |
| 코드 생성            | Shift + G    |
| 다음 제안으로          | Shift + D    |
| 이전 제안으로          | Shift + A    |
| 제안 전체 보기         | Ctrl + Enter |
| 인라인 제안 생성        | Shift + V    |

### 명령어
- `@workspace /explain` : 이 코드가 어떻게 작동하는지 설명
- 그냥 코드 긁고 `/explain` : 해당 코드 설명
- `@workspace /new` : 새로운 프로젝트를 위해 폴더, 파일 생성
- `/doc` : 설명문 주석으로 달아줌
- `/fix` : 버그 해결책 제안해줌


### 도커 살리기

#### 도커 깨우기

```sh
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
systemctl --user restart docker-desktop
```

#### 컨테이너 살리기

```sh
docker run --restart always --name ubuntu_18.04 -dt ubuntu:18.04 // ubuntu 설치
```

