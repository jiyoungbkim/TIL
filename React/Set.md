## Node.js / npm 설치

macOS / Linux 의 경우엔, [nvm](https://github.com/nvm-sh/nvm) 이라는 도구를 사용하여 Node.js 를 설치하시는 것을 권장

나중에 Node.js가 바뀔 때 업그레이드 하기가 쉽다.

### NVM 설치하기

1. Homebrew로 nvm 인스톨

    ```
    brew install nvm
    ```

2. nvm 명령어를 사용하기 위해 .bach_profile 이나 .zshrc 파일을 열어서 편집

    ```
    open -e ~/.zshrc
    ```

3. zshrc 설정파일에 nvm을 연결

    ```
    # NVM
    export NVM_DIR=~/.nvm
    source $(brew --prefix nvm)/nvm.sh
    ```

4. 수정한 .zshrc(.bash_profile)을 반영

    ```
    source ~/.zshrc
    ```

5. nvm 설치 확인

    ```
    nvm -v
    ```

6. Node.js LTS 버전 설치

    ```
    nvm install --lts
    ```

7. node 설치 확인

    ```
    node -v
    ```

## yarn 설치

yarn 설치는 Yarn 공식 홈페이지의 [Install Yarn](https://classic.yarnpkg.com/en/docs/install#mac-stable) 페이지를 참고하세요.

1. Homebrew로 yarn 설치

    ```
    brew install yarn
    ```

2. prefix 값을 yarn에 바로 붙입니다

    ```
    yarn config set prefix ~/.yarn
    ```

3. .zshrc 파일을 열어서 path 설정

    ```
    # yarn
    export PATH="$PATH:`yarn global bin`"
    ```

4. 커맨드로 zsh에 저장

    ```
    source ~/.zshrc
    ```

5. yarn 버전 확인

    ```
    yarn -v
    ```

## VS Code 설치

VS Code 를 설치 할 땐 [VS Code 공식 홈페이지](https://code.visualstudio.com/) 를 참

## VS Code 확장 프로그램 설치

### ESLint

자바스크립트 문법 및 코드 스타일을 검사해 주는 도구

1. VS Code에서 확장 프로그램 인스톨


### Reactjs Code Snippets

리액트 컴포넌트 및 라이프사이클 함수를 작성할 때 단축 단어를 사용하여 간편하게 코드를 자동으로 생성해 낼 수 있는 코드 스니펫 모음

### Prettier-Code formatter

코드 스타일을 자동으로 정리해 주는 도구


## Git 설치

[맥북에 Git 설치하기]

## 새 프로젝트 만들어보기

디렉토리를 새로 만든다.

```
mkdir react-tutorial
cd react-tutorial
```

새로운 리액트 프로젝트 만들기

```
npx create-react-app begin-react
```


예전에 생활코딩 리액트를 글로벌로 만든게 문제였던 것 같아서 지워줬다.

공식 문서에서도 내용을 확인할 수 있다.

[https://create-react-app.dev/docs/getting-started/](https://create-react-app.dev/docs/getting-started/)


yarn을 이용해서 새로운 프로젝트 만들기

```
yarn create react-app my-app
```

마지막에 알려주는대로 입력

```
cd begin-react
yarn start
```

다음과 같은 창이 떠서 확인을 눌러주면 새로운 창이 뜬다


이 명령어를 실행하고 나면 다음과 같이 브라우저에 [http://localhost:3000/](http://localhost:3000/) 이 열리고, 돌아가는 리액트 아이콘이 보일 것입니다. 자동으로 페이지가 열리지 않는다면 브라우저에 주소를 직접 입력하여 들어가세요.


### **VS Code 에서 터미널 띄우기**

VS Code 내부에서 터미널을 띄울 수도 있습니다. VS Code 로 해당 디렉터리를 열은 뒤, 상단 메뉴의 View > Terminal 을 열으세요. (한글 메뉴의 경우 보기 > 터미널).
