# G-ERP 프론트엔드개발 부트스트랩 프로젝트

G-ERP 프론트엔드 개발을 진행할 수 있도록 개발에 대한 기본 구조를 제공하는 프로젝트입니다.  
 
## 사전 준비 사항

G-ERP 프론트엔드 개발은 순수 HTML 및 JavaScript 를 이용하여 이뤄지나 개발환경 구성을 위하여 Node.js 및 NPM 기반의 기술 
또는 컴포넌트를 사용합니다.  

### Windows

#### NVM-Windows 을 이용한 Node.js 설치

NVM-Windows 다운로드 경로에서 최신 버전의 NVM 설치 파일(nvm-setup.zip)을 받아서 설치해 주세요.

https://github.com/coreybutler/nvm-windows/releases

명령 프롬프트 창을 열어서 NVM 이 설치되어 있는지 확인합니다.

```
> nvm --version
Running version 1.?.?

Usage:
...
```
버전 정보의 확인이 가능하고 사용법이 출력된다면 정상적으로 설치된 것입니다.

명령 프롬프트 창에서 계속해서 Node.js 를 설치합니다.

프로젝트는 Node.js 6.10.0 버전을 기반으로 개발되었으므로 6.10 LTS 이상 버전을 설치하시면 됩니다.

설치 후에는 `nvm use` 를 이용하여 사용할 Node.js 버전을 활성화합니다.

```
> nvm install 6.10.0
...

> nvm use 6.10.0
Now using node v6.10.0 (64-bit)

```

### Mac OS X

#### NVM 을 이용한 Node.js 설치

Mac OS 에서는 **NVM(Node Version Manager)** 을 이용하여 여러가지 버전의 Node.js 를 설치하고 관리할 수 있습니다.

맥 에서 NVM 의 자세한 설치방법과 NVM 관련 정보는 https://github.com/creationix/nvm 에서 확인하실 수 있습니다

터미널 화면을 열고 아래 명령어를 입력하여 `~/.bash_profile` 파일이 있는지 확인합니다

```bash
$ ls -la ~/ | grep .bash_profile
```

파일이 존재하지 않으면 아래 명령어를 실행해 주세요.

```bash
$ touch ~/.bash_profile
```

터미널 화면에서 아래와 같이 입력하여 설치 스트립트를 실행합니다.

```bash
$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash
```

설치 후 아래 명령어를 입력하여 bash 를 재시작합니다.

```bash
$ source ~/.bashrc
```

아래 명령어로 설치가 되었는지 확인할 수 있습니다.

```bash
$ command -v nvm
nvm
$ nvm --version
0.XX.X
```
만일 `nvm: command not found` 라고 나온다면 터미널 창에서 `cmd + Q` 를 이용하여 완전히 종료하신 후 다시 터미널 창을 시작한 이후에 다시 
시도해보세요.

이제 Node.js 를 설치하고 사용할 기본 버전을 설정합니다.

```bash
$ nvm install lts/boron

$ nvm alias default lts/boron

```

Node.js 버전이 제대로 설정되었는지 확인합니다. `v6.10.x` 와 같이 나온다면 성공입니다.

```bash
$ node --version
v6.10.x
```

### Visual Studio Code 설치

비주얼 스튜디어 코드는 무료로 사용할 수 있는 텍스트 에디터로 일반 텍스트 에디터보다는 개발에 편리한 기능
(인텔리센스, 디버깅 등)을 제공합니다.
 
Visual Studio Code 이외에 자신이 사용하는 코드 에디팅 툴이 있다면 이용하셔도 상관없습니다만 Visual Studio Code를 
기반으로 설명을 진행하므로 Visual Studio 코드를 사용하시는 것을 추천드립니다.
 
아래 주소에서 Visual Studio Code 를 받아 설치해 주십시오.
  
https://code.visualstudio.com/

설치가 완료되면 Visual Studio Code 를 실행하고 `ctrl + shift + p` 를 입력하면 `명령 팔레트` 창이 나타나면 아래와 같이 
명령어를 입력하시고 엔터를 입력하십시요.

```
>ext install
```

새로 나타난 확장 창에서 검색 부분에 `EditorConfig` 를 입력하고 `EditorConfig for VS Code` 를 설치합니다.

## 개발 시작하기

### 프로젝트 클론하기

명령 프롬프트나 Git Bash 를 실행하시거나, VS Code 를 실행한 상태에서 `ctrl + ~` 키를 누르거나 `보기 - 통합터미널` 을 
선택해서 명령 프롬프트를 하나 띄워주세요.

프로젝트를 저장할 디렉토리로 이동한 후에 아래 명령을 입력하여 `gerp-front-bootstrap` 프로젝트를 클론합니다.

클론할 때 git 주소 뒤에 자신이 원하는 디렉토리 명을 명기해서 기본 이름인 `gerp-front-bootstrap` 대신 자신이 원하는 이름의 폴더를 이용할 수 있습니다. 

```
$> git clone https://git.comet.duzon.net/front-end-ui/gerp-front-bootstrap.git my_front_project

$> cd my_front_project
```

### 불필요한 파일 제거

프로젝트를 클론해 왔으면 이제 더이상 git 리포지토리 정보는 필요하지 않습니다 아래 명령어를 입력하여 git 리포지토리 정보를 제거합니다.

```bash
# Windows
> rmdir /S /Q .git
  
# Mac OS
$ rm -rf .git
```


### 종속성 설치

설치하기 전에 npm 을 이용한 설치 시 ssl 인증서 관련 오류가 발생하는 것을 방지하기 위해서 아래 명령어를 입력해주세요.
```
$> npm set config set strict-ssl false
```

NPM 을 이용하여 `gerp-main` 프로젝트를 비롯한 개발에 필요한 종속 모듈들을 설치합니다. 
```
$> npm install
```

### 추가적인 설정

로그인을 지정한 서버를 이용하고자 할 경우에는 `accounts.json` 파일을 제거하거나 파일 내의 `use` 를 `false` 로 변경해주시면 됩니다.

사용할 서버 정보를 변경하시려면 `server.json` 파일의 내용을 수정하시면 됩니다.

메뉴를 서버에서 받아오길 원한다면 `api` 디렉토리 내에 있는 `CM/MenuService` 디렉토리를 삭제해주세요

### 실행해보기

`gerp-main` 이 정상적으로 실행되는지 확인하기 위해서 프로젝트를 실행해봅니다.
```
$> npm start
```

실행한 이후 웹 브라우저에서 http://localhost:8000/ 으로 접속시 G-ERP 로그인 화면이 나타나면 정상적으로 동작하는 것입니다.

## 프로젝트 구조

```
-+- api : 서버 요청을 가상화하여 테스트하기 위한 디렉토리
 |  +- CM : 모듈명
 |     +- MenuService : 서비스명
 |        +- FI.json : 요청(/api/MA/MenuService/FI)에 응답에 전달할 가상 데이터가 포함된 json 파일
 +- views : 뷰 화면을 개발하는 디렉토리
 |  +- FI : 모듈명
 |     +- BIMGLM : 서브 모듈 디렉토리
 |        +- BIMGLM00100.html : 업무 화면 HTML 파일
 +- accounts.json : 로그인 테스트를 위한 계정 정보 설정 파일
 +- server.json : 로컬 API 서버를 사용할 지 여부와 원격(개발) 서버 정보 설정 파일 
```

## 프로젝트 업데이트

GERP 프론트엔드 메인에 대한 업데이트를 확인하고 새로운 버전을 설치하고자 할 때는 아래와 같은 명령어를 터미널 화면에 입력하시면 됩니다.

```
$> npm update
```
