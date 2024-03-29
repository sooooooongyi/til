# WEBPACK HANDBOOK

> 해당 페이지는 캡틴판교님의 webpack e-book을 읽고 정리한 글 모음입니다. [웹팩 핸드북](https://joshua1988.github.io/webpack-guide/)

## 웹팩이란?

- 모듈 번들러
  - 웹 애플리케이션을 구성하는 자원을 모두 각각의 모듈로 보고 이를 조합해서 병합된 하나의 결과물을 만드는 도구를 의미
- 모듈 번들링
  - 웹 애플리케이션을 구성하는 몇십, 몇백개의 자원들을 하나의 파일로 병합 및 압축 해주는 동작을 모듈 번들링이라 부른다. (빌드 === 번들링 === 변환 모두 같다!)

## 웹팩의 등장 배경

### 파일 단위의 자바스크립트 모듈 관리

- 복잡하고 큰 웹 애플리케이션을 만들 때 전역적인 변수 범위는 예기치 않은 혼란을 발생시킬 수 있다.
- 모든 변수명을 기억할 수 없다.
- 파일 단위로 관리해 변수 단위로 영역을 설정해 프로그램의 안정성을 높인다.

### 웹 개발 작업 자동화 도구

- 텍스트 편집기에서의 수정을 편하게 할 수 있다.
- 모든 자원들을 압축해서 배포하는 과정을 자동화시킬 수 있다.

### 웹 애플리케이션의 빠른 로딩 속도와 높은 성능

- 웹 사이트의 로딩 속도를 높이기 위해 나중에 필요한 자원들은 나중에 요청하는 레이지 로딩이 등장
- 웹팩의 동작 방식이 레이지 로딩을 따른다.

### 자바스크립트 변수 유효 범위 문제

- 웹팩은 변수 유효 범위의 문제점을 ES6 Modules 문법과 웹팩의 모듈 번들러로 해결

### 브라우저별 HTTP 요청 숫자의 제약

- TCP 스펙에 따라 브라우저에서 한 번에 서버로 보낼 수 있는 HTTP 요청 숫자는 제약되어있다.
  ![스크린샷 2022-07-04 오후 10.19.21.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/05c7c11c-bdb3-4bc6-8551-49bdf81d4a73/스크린샷_2022-07-04_오후_10.19.21.png)
- 웹팩을 이용해 여러 파일을 하나로 합치면 HTTP 요청 숫자 제약을 피할 수 있습니다.
- 게다가, 요청 숫자를 줄임으로써 웹 애플리케이션의 성능을 높이고 사용자의 조작 시간을 앞당길 수 있습니다.

### Dynamic Loading, LazyLoading 미지원

- 웹팩을 사용하지 않으면 라이브러리없이 동적으로 원하는 순간에 모듈을 로딩하는 것이 불가능했습니다.
- 웹팩의 Code Splitting 기능을 이용하여 원하는 모듈을 원하는 타이밍에 로딩할 수 있습니다.

### Node.js

- 브라우저가 아닌 자바스크립트를 실행할 수 있는 환경

### NPM

- 명령어로, 자바스크립트 라이브러리를 설치하고 관리할 수 있는 패키지 매니저
- 자바스크립트 개발자들이 모두 자바스크립트 라이브러리를 공개된 저장소에 올려놓고 npm 명령어로 편하게 다운로드 받을 수 있습니다.
- Node.js 설치 시 함께 설치됩니다.

```jsx
{
  "name": "demo",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

- 기본적인 구조의 package.json

### NPM 지역 설치

- npm install 로 설치하기
- —save-prod 붙이지 않아도 같은 효과
- node_modules 폴더에 라이브러리 파일들이 설치되어있다.

### NPM 전역 설치

- 프로젝트에서 사용할 라이브러리를 불러올 때 사용하는 것이 아니라, 시스템 레벨에서 사용할 자바스크립트 라이브러리를 설치할 때 사용한다.
- —global / -g 를 붙여 설치한다.
- 명렁어 실행 창에 해당 라이브러리 이름을 입력했을 때 명령어를 인식합니다.
- /usr/local/lib/node_modules 해당 경로에 라이브러리 파일들이 설치되어있다.

### 개발용 라이브러리와 배포용 라이브러리 구분하기

- 배포용 라이브러리는 빌드했을 때 최종 애플리케이션 코드 안에 포함된다.
- 화면 로직과 직접적으로 관련된 라이브러리는 배포용으로 설치해야합니다.
- 개발용 라이브러리(-D)의 대표 예시
  - webpack
  - eslint
  - imagemin

### NPM 커스텀 명령어

- NPM 관리 파일에 scripts 속성을 추가할 수있다.
- 커스텀 명령어를 이용해 원하는 동작을 실행할 수 있다.

### 실제 사례

```jsx
"scripts": {
  "dev": "node server.js",
  "build": "webpack --mode=none",
}
```

- dev, build와 같은 명령어로 쉽게 실행 시킬 수 있다.

```jsx
"scripts": {
  "build": "webpack",
  "deploy": "npm run build -- --mode production"
}

npm run deploy
```

- 위 명령어를 실행시키면 webpack 명령어가 실행되면서 명령어 뒤쪽에 붙은 실행 옵션들이 수행된다.
