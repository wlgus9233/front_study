# React.JS?

* 재사용 가능한 UI 구성 요소를 구축하기 위한 선언형 JavaScript 라이브러리다.
컴포넌트 기반으로 재사용성이 뛰어나다. 

* 애플리케이션의 뷰 계층만을 담당하는 오픈 소스 구성 요소 기반 프런트 엔드 라이브러리.
프론트와 서버 사이드 모두 제공

* 웹, 웹 앱, SPA등 개발 시 사용.

* Virtual DOM(가상돔)기반으로 가볍다. 이는 전체 새로고침보다 빠르다(필요한 부분만 고침). 앱 속도를 향상시키는 UI(사용자 인터페이스)를 개발하는것이 목적.

* HTML태그 사용.



___
# React Native?
* React-Native는 자바스크립트 오픈소스 모바일 앱 프레임워크

* 크로스 플랫폼 모바일 앱 개발에 사용.웹 개발자에게 모바일 앱 개발을 쉽게 해줌! ios와 Android 동시 개발 가능. (크로스플랫폼에는 플러터도 있다.)

* HTML태그 사용하지 않음.( 예를 들어 View = div 태그와 Text = p태그와 유사합니다.)
```js
mport React, { Component } from 'react';
import { View, Text } from 'react-native';

export default class App extends Component {
  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.intro}>Hello world!</Text>
      </View>
    );
  }
}
```
* 자체 애니메이션 라이브러리를 제공. (css로 작성할 필요 없음)
* 리액트의 Webpack같은 bundler설정이 필요 없음. 이미 가지고 있다.
* 
* 모바일 앱개발시 사용. ndroid에 사용될 수 있고 크로스 플랫폼 모바일 앱을 만들 수 있기
* ES6, 일부 ES7 기능 및 몇 가지 폴리필을 사용하여 첫 번째 네이티브 앱의 코딩을 즉시 시작할 수 있음
___
# React.js Setup/배포

1. 설치
* node.js : Webpack 과 Babel 같은 도구들이  
 자바스크립트 런타임인 Node.js 를 기반으로 만들어져있기 떄문에  
 [node.js](https://nodejs.org/ko/)를 안정적인 버전으로 설치한다.  
리액트는 자바스크립트로 서버운영을 하기때문에 노드환경에서 실행한다.
 ```js
//버전확인
node -v 
npm -v //전세계 자바스크립트 라이브 저장소
npx -g //1회성, 최신노드패키지를 글로벌로 내려받음
```
* Yarn: [Yarn](https://classic.yarnpkg.com/en/docs/install#mac-stable) 은 조금 개선된 버전(더 나은 속도, 더 나은 캐싱 시스템)의 npm.  
npm 은 Node.js 를 설치하게 될 때 같이 딸려오는 package manager.  
프로젝트에서 사용되는 라이브러리를 설치하고 해당 라이브러리들의 버전 관리를 하게 될 때 사용. 
(npm 사용해도 상관없을무) 

* chrom 확장설치 : react developer tool설치해서 리액트아이콘이 활성화된 사이트를 보여줌.
```js
npm install --global yarn
yarn --version
```

> ### Webpack, Babel?  
>
>컴포넌트 를 여러가지 파일로 분리해서 저장 할 것이고,  
 또 이 컴포넌트는 일반 자바스크립트가 아닌 JSX 라는 문법으로 작성한다.  
여러가지의 파일을 한개로 결합하기 위해서 우리는 Webpack 이라는 도구를 사용하고,  
 JSX 를 비롯한 새로운 자바스크립트 문법들을 사용하기 위해서 우리는 Babel 이라는 도구를 사용한다.

2. 리액트 폴더생성  
* 리액트폴더 생성후 터미널에 작성한다.
```js
$ npx create-react-app 폴더명 //라이브러리설치를 돕는 명령어
$ cd 폴더명 //디렉토리이동 명령문
 (둘중 1개 택)
$ npm start//작업한 브라우저창을 확인할수 있다.
 yarn start 
```
3. 작성후 build 하기
```js
npm run build  
// bild폴더가 생성되고 작업한 js,css가 압축되어 생성됨
```
4. package.json 수정

```js
yarn add gh-pages --dev //git 패키지설치
npm install gh-pages

디버그 밑 스크립트추가
"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
-----------------------------------
"predeploy": "npm run build",  
//현재 프로젝트 코드를 빌드한다.
"deploy": "gh-pages -d build"  
// build 디렉토리(-d)에 있는 파일을 GitHub Pages에 업로드

맨밑에 homepage 항목 추가
 },
  "homepage": "http://wlgus9233.github.io/kakao_react"(패키지제이슨맨밑에 http://홈페이지 아이디 + 깃주소 + 프로젝트명)
적는다.
```
5. git-hub페이지 올리기
```js
 git add .
 git commit -m "프로젝트명 업로드"
 git push origin master
 git remote -v

```

6. 빌드 결과물 배포하기
```js
npm run deploy ( = yarn run deploy)  
//내문서나 프로젝트 파일안에 프로젝트폴더 bild됨
```
7. 깃허브사이트에 설정아이콘누름 >  
밑에 내려서 홈페이지 뜨면 눌러서 화면이 나오는지 확인.



