# javascript
* JavaScript는 동적으로 컨텐츠를 바꾸는 객체기반스크립트 언어

*복합기.복사해라 == 객체.메서드()*

* 해석형 언어. 따라서 코드가 위에서 아래로 순차적으로 실행되고 그 즉시 결과가 반환.
```js
'use strict';  
//순수바닐라자바스크립트 작성시 선언되지않은 변수는 오류로 뜸.

 console.log('Hello world');
```
#  외부 js /  Script loading

### 1. head 안에 스크립트 포함하는 경우

```html
 <! DOCTYPE html>
 <html lang="en">
  <head>
      <meta charset="UTF-8" />
      <title>Document</title>
      <script src="main.js"></script>
  </head>
  <body>
    <div></div>
  </body>
 <html>

```

* 사용자가 html파일을 다운로드 받았을때  
브라우저가 한줄씩 분석해 css와 병합해 돔요소와 병합하는데,  
parsing HTML 을 하다가 script가 발견되면 멈추고 필요한 js 파일을 서버에 다운받아서 실행한다음 다시 parsing HTML을 거친다.

>**단점** :  js파일 크기가 크고 인터넷이 느리다면, 사용자가 웹사이트를 보는데 많은 시간이 걸린다. (스크립트를 헤드에 포함하는것은 좋은게 아니다.)

 ### 2. body 끝부분에 script를 추가하는 경우

 ```html
 <! DOCTYPE html>
 <html lang="en">
  <head>
      <meta charset="UTF-8" />
      <title>Document</title>
  </head>
  <body>
    <div></div>
    <script src="main.js"></script>
  </body>
 <html>
```
* HTML을 파싱 하고 페이지가 준비될때, 스크립트를 petching (서버로부터 받아온다.) 한후, executing(실행)한다.

>**단점** :사용자가 기본 html을 빨리보는 장점은 있지만, 의미있는 컨텐츠를 보기위해서 js를 이용해서 서버데이터를 받아오거나 돔요소를 꾸며주는등 서버에있는웹사이트가 js에 의존적이라면, 사용자가 정상적인 페이지를 보기까지는 패칭하고 실행하는 시간을 기다려야하는 단점이 있다.

### 3. head안에 async 추가
 ```html
 <! DOCTYPE html>
 <html lang="en">
  <head>
      <meta charset="UTF-8" />
      <title>Document</title>
      <script async src="main.js"></script>
  </head>
  <body>
    <div></div>
  </body>
 <html>
```
* async 는 bull형 옵션갑 선언만으로 true가 설정되어 옵션을 사용할수 있음. 

* html 파싱하다가 스크립트가 발견되면 병렬로 다운받을 명령만 해놓고 파싱을 하다가 다운로드가 완료되면 그때 파싱하는걸 멈추고 다운로드된 js파일을 실행한다. 실행다하고 나서 나머지 html을 파싱하는 방식

>**단점**: 병렬적으로 다운로드 되어 바디끝에 스크립트를 추가 한것보다는 패칭이 파싱하는동안 병렬적으로 일어나기때문에 다운로드 받는시간을 절약할수있다. 하지만 html이 파싱하기전에 일어나기때문에 js가 queryselector이용해 돔요소를 조작한다라면 조작하는시점에 html요소가 아직 정의되어있지 않을수 있다.
파싱하는도중 js실행으로 인해서 언제든 멈출수 있기때문에 사용자가 페이지를 보는데 시간이 걸린다.

 * script가 여러개이면 병렬구조 이기때문에 순서에 관계없이 용량이 작은 js부터 다운받아짐. 순서에 의존적인 script라면 문제가 된다.

### 3. head안에 defer추가
 ```html
 <! DOCTYPE html>
 <html lang="en">
  <head>
      <meta charset="UTF-8" />
      <title>Document</title>
      <script defer="main.js"></script>
  </head>
  <body>
    <div></div>
  </body>
 <html>
```
* html 파싱하다가 스크립트의 defer이 있으면 다운받자! 명령만 시키고 html을 끝까지 파싱한후 다운로드 되어진 js를 실행시킨다. (가장 좋은옵션! 효율적,안전성)

* 필요한 js를 다 다운받아논뒤에 script 순서대로 js를 실행한다.

# html 내부에 js작성

* 내부형스크립트에서는 유효성검사 오류를 막기위해 CDATA선언을 함께작성해야한다.( html태그를 실행문에 사용시 문자형데이터로 인식시켜 바디가 잘 출력되도록 해줌)
```html
<! DOCTYPE html>
 <html lang="en">
  <head>
    <script>
    <[CDATA[
        console.log("hi")
    //]]>
    </script>
  </head>
  <body>
    <div></div>
  </body>
 <html>
```

### 5. html속에 포함한 인라인처리
```html
<button onclick="createParagraph()">Click me!</button>
```
*  button 태그에 onclick속성에 대한 값을 함수이름으로 넣어 버튼이 클릭될 때마다 함수가 실행되도록. 하지만, 이 방법은 효율적이지 않다. 함수를 만들기 위한 모든 버튼 마다 onclick="createParagraph()" 속성을 포함함으로써 html소스가 복잡해질수 있다.
```js
const buttons = document.querySelectorAll('button');
//모든 <button>태그를 List 형태로 buttons 변수에 저장한다.

for (let i = 0; i < buttons.length ; i++) {
  buttons[i].addEventListener('click', createParagraph);
}
//복수이기 때문에 for를 사용해 루프를 돌린다.
```
* 이 코드는 onclick 속성 코드 보다 조금 길어보이지만, 페이지가 많든, 버튼의 수가 많든 적든 상관없이 모든 버튼들이 같은 기능을 할 수 있도록 함.

___
## js = Dynamic Type언어
* c, java 어는 어떤 데이터타입인지 결정해서 타입을 같이 선언
* 선언할때 어떤타입인지 선언하지 않고 프로그램이 동작할때, 할당된 값에 따라서 타입이 변경될수 있는것
>장점 : 갑자기 생각난 좋은아이디어를 빠른 프로토타이핑할수 있다. 브라우저가 바로 이해할수 있어서 실시간으로 연동해서 볼수 있다.

>단점: 다수 엔지니어가 규모가 있는 프로젝트 참여시 데이터타입선언으로 인해 문제발생한다. 보통 변수로 타입을 예상할수 있다. 중간 개발자가 string타입인데 number타입으로 바뀐것을 모르고 text.charAt(0)를 가져온다면 오류가 난다. 그래서 **타입스크립트** 가 나온것.
```js
let text = 'hello';//string
console.log(`value: ${text}, type: ${typeof text}`);
text = 1;  
// 숫자를 할당하면 Number 타입으로 바뀜  
text = '7' + 5;  
 //문자열에 더하기는 문자로 인식 value:75 string
text = '8' / '2';  
//스트링이지만 안에 숫자가 있고 나누기가 있으니 Number타입으로 바뀜 value: 4
```
## TypeScript ?!
* js위에 type이 더 올려진 언어
* 타입스크립트는 브라우저가 이해할수 있는 자바스크립트로 트렌스컴파일러(BABEL)을 해야 볼수 있어서 실시간으로 보기 어렵다.

___


