# React 시작하기 - 설치 및 로컬에 샘플 페이지 띄우기

노마드코더(Nomard Corders)에서 **[Django 풀스택] 인스타그램 클론 코딩**을 수강신청했다. $300달러라는 비용이 살짝 부담되긴 했지만 월 $100씩 3개월로 분할해서 결제할 수 있어서 바로 질러버렸다. 그래서 처음 Intro 강의들을 보면서 Django보다는 React가 더 많은 비중을 차지하고 있고, 또 무료 강의들을 먼저 들어야 이해가 편하다고 해서 React 강의를 먼저 듣기로 했다. Django에서는 Variable(변수), Class, Function 개념만 알고 있어도 수월하다고 하기에 Python이나 Django 강의는 따로 듣지 않고 진행할 생각이다. 우선 React를 설치해야한다.

## React 설치

우선 React를 설치하기 위해선 먼저 설치해야할 것들이 있다. Django도 Python, Virtualenv가 먼저 필요했던 것처럼 React도 다음과 같은 것들을 설치해야 한다.

1. Node.js(npm)
2. Yarn

### Node.js 설치

우선 Node.js를 설치해야 한다. React는 기본적으로 Node.js 환경에서 구동되므로 베이스로 설치해야 한다. 또한 **npm은 python의 pip같은 역할**을 하는 것 같다. 둘 다 한번에 설치해보기로 했다.

```bash
sudo apt-get install nodejs npm
```

금방 설치가 된다. 다음 명령어를 통해 정상적으로 설치 되었는지 확인한다.

```bash
node -v
npm -v
```

버전 정보가 정상적으로 나온다면 설치 완료!

### yarn 설치

yarn은 방금 설치한 npm을 이용해서 설치하면 된다. **yarn**이란 <u>페이스북에서 만든 자바스크립트 패키지 매니저라고 하는데  npm보다 더 빠르고 성능이 좋다</u>고 한다. yarn은 [링크](https://yarnpkg.com/en/docs/install#windows-stable)에서 운영체제별로 다운 및 설치하는 방법이 나와있으니 확인하면 된다. 우선 yarn은 기본 repository에 제공하지 않기 때문에 명령어들을 입력해준다.

```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
# curl이 없을 경우
sudo apt-get install curl
```

그리고 다음 명령어로 yarn을 설치해준다.

```bash
sudo apt-get update && sudo apt-get install yarn
```

## React 구동하기

우선 폴더를 만든 후 해당 폴더로 이동했다.

```bash
mkdir react
cd react
```

그리고 create-react-app을 설치해야한다. **create-react-app**은 <u>별도의 설정 없이 곧바로 react 프로젝트를 만들어주는 아주 편리한 것</u>이다.

```bash
sudo npm install -g create-react-app
```

설치가 완료됐다면 create-react-app을 통해서 샘플 프로젝트를 하나 만들어준다. 

```bash
create-react-app (프로젝트명)
```

그럼 프로젝트명으로 폴더가 생성된다. 그리고 해당 폴더로 들어가서 다음 명령어로 프로젝트를 가동해준다.

```bash
yarn start
```

그러면 자동으로 웹브라우저가 열리며 localhost:3000 가 자동으로 접속된다. 

![](https://t1.daumcdn.net/cfile/tistory/9936B2415BF7F5EF0D)

이렇게 화면이 나왔다면 성공!