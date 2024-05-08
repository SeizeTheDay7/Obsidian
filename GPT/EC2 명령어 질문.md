명령어 `sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 10`는 Linux 시스템에서 `python` 명령어가 기본적으로 `python3`을 가리키도록 설정하는 과정입니다. 각 부분에 대해 자세히 설명해드리겠습니다.

1. **sudo**: `sudo` 명령어는 "superuser do"의 약자로, 일반 사용자가 관리자(슈퍼유저) 권한으로 명령을 실행할 수 있게 해줍니다. 이 명령어를 사용하면 시스템 설정을 변경할 수 있는 등의 권한을 가지게 됩니다.

2. **update-alternatives**: 이는 Debian 계열의 Linux 시스템에서 여러 버전의 프로그램(예: Python)을 관리하고 사용자가 선택할 수 있게 해주는 도구입니다. 사용자가 실행할 때 어떤 프로그램이나 버전이 사용될지를 결정하는 데 사용됩니다.

3. **--install**: `update-alternatives` 도구에게 새로운 대안을 설치하라는 옵션입니다. 이를 통해 특정 명령어(여기서는 `python`)에 대한 대안을 설정할 수 있습니다.

4. **/usr/bin/python**: 이는 `update-alternatives` 도구에 설정할 명령어의 경로입니다. 이 경로에 설치된 명령어를 사용자가 `python`이라고 호출할 때 실제로 실행될 프로그램을 결정합니다.

5. **python**: 이는 대안의 이름입니다. `update-alternatives` 시스템에서 이 이름을 사용하여 여러 대안들을 관리합니다.

6. **/usr/bin/python3**: 이는 실제로 사용자가 `python`을 실행했을 때 대신 호출될 프로그램의 경로입니다. 여기서는 `python3`의 실행 파일 경로를 가리킵니다.

7. **10**: 이는 우선순위입니다. 같은 명령어에 대해 여러 프로그램(대안)이 등록될 수 있는데, 여기서 우선순위가 높은 프로그램이 기본값으로 사용됩니다. 숫자가 클수록 우선순위가 높습니다.

이 명령어를 사용하면, 사용자가 `python`을 입력할 때 시스템은 자동으로 `python3`을 호출하게 되어, Python 3.x 버전이 실행됩니다. 이는 특히 Python 2와 Python 3을 함께 사용하는 시스템에서 Python 3를 기본값으로 설정할 때 유용합니다.

<hr>

여기에 나열된 명령어들은 MongoDB 4.2 버전을 Ubuntu 시스템에 설치하는 과정을 단계별로 설명하고 있습니다. 각 명령어의 기능과 역할을 자세히 설명하겠습니다:

### 1. MongoDB 공개 키 추가
```bash
wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
```
- `wget -qO - URL`은 URL에서 파일을 다운로드하여 표준 출력(stdout)으로 내보내는 명령입니다. `-q`는 조용한 모드로, 진행 상황이나 메시지를 표시하지 않습니다. `-O -`는 다운로드된 데이터를 파일로 저장하지 않고 직접 출력합니다.
- 이 출력은 파이프(`|`)를 통해 `sudo apt-key add -` 명령으로 전달됩니다. `apt-key add`는 GPG 키를 시스템의 APT 키 저장소에 추가합니다. 여기서는 MongoDB의 공개 키를 추가하여 패키지의 무결성을 검증할 수 있도록 합니다.

### 2. MongoDB 저장소 추가
```bash
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
```
- `echo`는 주어진 문자열을 표준 출력으로 내보냅니다. 여기서는 MongoDB의 APT 저장소 설정을 문자열로 출력합니다.
- 이 문자열은 다시 `sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list` 명령으로 전달되어, 해당 경로의 파일로 저장됩니다. `tee` 명령은 입력을 파일로 저장하면서 동시에 표준 출력(stdout)으로도 내보냅니다. 이렇게 함으로써 MongoDB 저장소 설정이 APT의 소스 목록에 추가됩니다.

### 3. 패키지 목록 업데이트
```bash
sudo apt-get update
```
- `sudo apt-get update`는 APT의 패키지 목록을 업데이트합니다. 새로 추가된 MongoDB 저장소에서 패키지 정보를 가져오고, 시스템이 최신 패키지 정보를 알 수 있도록 합니다.

### 4. MongoDB 설치
```bash
sudo apt-get install -y mongodb-org
```
- `sudo apt-get install -y mongodb-org` 명령은 `mongodb-org` 패키지를 설치합니다. `-y` 옵션은 설치 중에 나오는 모든 질문에 자동으로 'yes'를 답하는 옵션으로, 사용자의 입력 없이 설치가 진행됩니다.

이 명령어들을 통해 MongoDB 4.2가 Ubuntu 시스템에 안전하게 설치되며, 이후 MongoDB 서비스를 시작하고 관리할 수 있습니다.