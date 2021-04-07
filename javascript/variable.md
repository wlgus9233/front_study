# 변수

* 변수X에 A를 대입한다고해서 A라는 상자자체를 저장하는것이 아니라.  
변수A에 저장된 값을 복사해서 복사한값을 X에 저장함. 

```js
let X = A
let Y = A + 5 //변수 A저장된 값에 5를 더한값이 변수 Y
```
* 변수명 작성 유의사항   
1. 대-소문자구분
2. 변수명맨앞 영어,_,$f로 시작 (숫자x)
3. 특수문자제외
___

## 변수에도 데이터 타입이 있다.

1. 문자형(String)
```js
const jihyun = 'jihyun'
let txt1 = "문자 큰따옴표";
let txt2 = '숫자문자 작은따옴표';
let txt3 = 'hello' + jihyun;
let txt4 = `hi ${jihyun}!`//템플릿리터럴
```
* 문자열을 합칠때 코트에 넣어서 일일히 + 기호를 넣는것보다 벡틱키를 이용하면 문자열이 그대로 사용된다.
2. 숫자형(Number)

```js
let num = 10; //정수와 실수 따옴표없이
```
3. 논리형(Boolean)
* 불리언(Booleans)은 true 이나  false 라는 값을 가지는 참/거짓을 표현하는 데이터 유형

4. Null  
* 비어있는값이지만 변수에 할당된다. 불리언 연산에서는 거짓을 나타냄.

5. undefined
* 선언되었지만 비었는지 값이 있는지 정해지지않은상태로
let x;도 아무런값이 없는것

```js
null === undefined // false
null  == undefined // true
```
* null 은 값은 값이지만 값으로써 의미없는 특별한 값이 등록되어 있는 것이고, undefined 는 등록이 되어있지 않기 때문에 초기화도 정의되지도 않은 것.
```js
// Number 변수 초기화
let data1 = 0;

// String 변수 초기화
let data2 = "";

// Boolean 변수 초기화
let data3 = false;//초기값이 false 인 것으로 보아 이 변수에는 true 또는 false 가 저장될 것을 알 수 있다.

// Object 변수 초기화
let data4 = null; //깃값으로 null 을 넣어다는 의미는 소스코드 어디에선가 이 변수에 클래스의 인스턴스를 대입할 거
```
6. symbol
* 고유한 식별자가 필요하거나 동시다발적으로 일어날수 있는 코드에서 우선순위를 주고싶을떄
```js
const symboll1 = symbol('id');
const symboll2 = symbol('id');  
//주어지는 string에 상관없이 고유한 식별자 생성
console.log(symbol1 === symbol2); //false

const gsymboll1 = symbol.for('id');
const gsymboll2 = symbol.for('id'); //주어진 스트링에 맞는 심볼을만들어줘
console.log(symbol1 === symbol2); //true 

console.log(`value: ${symbol1.description}`);  
//심볼을 그냥출력하면 에러가 나이떄문에 항상 .description 으로 스트링으로 변환해줘야 한다.

```
## 지역변수와 전역변수
1. block scope
```js
{
let name = 'dog';
consle.log(name);
}
consle.log(name);
//블럭 밖에서 안의 내용을 볼수없다.
```
2. global scope
* 블록을쓰지않고 파일안에 정의하는 변수는 글로벌스콥,어느곳에서나 접근이 가능하다. 
* 블록안이나 밖에서도 출력되는걸 확인할수 있다.
* 앱이 시작하고 끝날때까지 탑재되어있기때문에 최소한으로 쓰는것이 좋다. 가능한 class,for,if,function등으로 정의해서 쓰는것이 좋다.

```js
let globalName = 'global'; 

{
    console.log(global);
}
console.log(global);
```
### ES5 var 쓰지말기...  
* var hoisting : 어디에 선언했냐에 상관없이 항상 젤위로 선언을 끌어올려주는것  
선언순서에 관계없이 작동됨.
* var는 block scope이 없음

> 최신기능을 쓸때는 호환성을 생각해야한다. ES6는 브라우저에 대부분 지원됨. 혹시 익스플로러같은 지원안되는 브라우저는 최신문법으로 개발후 BABEL을 통해 es5로 내리면 된다.
___
### Constant (const)
* 선언함과 동시에 한번 할당하면 값이 바뀌지 않는다.
* 해커들로부터 보안성과 코드를 바꿀때 실수를 줄일수 있고 다양한 프레그가 값을 접근해서 동시에 값을 변경할수 있는데 동시에 값을 변경하는건 위험.
