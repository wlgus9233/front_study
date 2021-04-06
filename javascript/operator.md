# 연산자
### 1. 산술연산자(=이항연상자)
*  " + ,- , *곱,/나누기, %나머지 "  
```js
let num1 = 10;
let num2 = 50;
let result;

result = 9 * num1; //450
document.write(result);
```
___
### 2. 대입연산자
*  등호 (저장): +=,-=,*=,/=,%=  기존값에다가 얼마씩 계속 더해주는것
```js
let numA = 10;

numA += 5; //15
numA /= 5; //3
numA %= 2;//1
```
___
### 3. 비교연산자 
* 연산자를 통해 Boolean 데이터가 출력된다.
```js

A > B //A크다 (반대 <작다)
A >= B //A가B보다 크거나같다
A == B //데이터형상관없이 같다
A != B //다르다(반대)
A === B //데이터타입일치형 같다
A !== B //데이터타입일치형 불일치로 다르다.

```
___
### 4. 증감 연산자 
* ++ 1씩증가, -- 1씩감소
___

### 5. 논리연산자  
* '&&'(and), '||'(or), '!'(not)
1. ||논리합(or), 

* true ||(더하기) true -> true 컴퓨터는 이진수라 0아니면 1
* true || false -> true 피연산자에 * 트루값이 하나라도 있으면 트루
false ||false -> false

>ex)엄마가 김밥 또는(논리곱) 순대 사오라 심부름을 시켰는데 김밥과 떡볶이 사왔다. 김밥은 참이므로 심부름 한게 맞음= 트루

2. &&논리곱(and)

* true && (곱하기) true 
* true && false -> false  
논리곱연산자에 false값이 하나라도 있으면 false
* false && false -> false 
> 20대여성이면 true 아니면 false결과출력.
```js
let gender = prompt("gender?","girl");
let age = prompt("age?","27");
let result = age >= 20 && age < 30 && gender == "girl";

document.write(result);
```
3. !논리부정(not)
* true참=1 ,false거짓=0  
컴퓨터는 이진수라 변수에 true저장되있으면 false값, false가 저장되있으면 true
```js
var A = 10;
var B = 20;
var C = 30;
var D = 40;

var num1 = A>B;//false
var num2 = C>=D;//false

var a = num1 || num2;
document.write(a + "<br />"); // 거짓더하기 거짓은거짓

var b = num1 && num2;
document.write(b + "<br />");//거짓곱하기 거짓은 거짓

var c = !num1; 
document.write(c + "<br />");//느낌표는 낫 부정의 뜻 펄스의 반대는 트루

var num1 = A>=B; //false
var num2 = C<=D; //true

var d = num1 || num2; //true
document.write(d + "<br />");

var e = num1 && num2; //false
document.write(e + "<br />");

var f = !num1; //true
document.write(f + "<br />");

var num1 = A<=B; //true
var num2 = C<D; //true

var g = num1 || num2; //트루 더하기 트루 트루
document.write(g + "<br />");

var h = num1 && num2; //트루 곱 트루 트루
document.write(h + "<br />");

var i = !num1; //true
document.write(i + "<br />");
```
___
### 6.문자결합 연산자
* 데이터가 1개이상 문자형데이터 가질경우 문자결합연산자로 실행된다. 
* 숫자를 String 함수로 감싸면 문자로 바뀜
* "문자" +"문자" ,"문자" +"숫자" , String(숫자) + 숫자 
```js

let txt1 = "올해는";
let txt2 = '2021';
document.write( txt3 + txt4 + "<br />"); // 올해는 2021

let num1 = 200;
let num2 = 300;
let txt5 = String(num1);

document.write( num1 + num2 + txt5 + "<br />"); //500200
```
___
### 7.조건연산자(삼향 연산자)
* 조건식 ? 실행문1: 실행문2 = 조건식 결과값 참:거짓 실행하는것 

```js
let result =confirm("Do tou like javascript?");
let theText = result ? "good" : "No-good"; // confirm("내용"), 확인-true값반환, 취소-flase값이 반환 
```
* 기타
//지수대입연산자 (2의 10승 **=)
//왼쪽/오른쪽 시프트 대입연산자(<</>>) : 십진수를 이진수로 변경해서 왼쪽/오른쪽으로 한자리씩 이동
//부호없는 시프트 대입연산자 (<<</>>>): 같은비트숫자라도 양의숫자로 반환
//비트 and연산/ or연산 + 대입연산 a&=b === a&b, a|= === a=a|b

