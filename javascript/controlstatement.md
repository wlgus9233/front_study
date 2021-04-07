# 제어문
* 조건문, swich~case문, 반복문
## 1. 조건문
* 데이터중복이라도 특정 조건을 허용할때 사용  
조건식에만 맞으면 중복가능
### 1. if문
* if 문
```js
if(조건식){
        실행문;
        } 조건식이 참일경우만 실행문이 실행된다.
```
### 3. 중첩 if문
```js
let score = 72;
    
    if (score >= 90) {
        if (score >= 95) {
            document.write("A+");
        }
        else {
            document.write("A0");
        }
    } 
```
### 3. if ... else 문
*  조건식 만족했을때 if실행문1수행, 그렇지않은(else)경우 실행문2 수행
```js
const myAge = prompt("당신의 나이는?");

    if( myAge >= 20 && myAge < 30){
    document.write("통과" + "<br />");
    }else{ 
        document.write("비통과" + "<br />"); 
    }
```
### 4.if ~ else if문
* 실행문 3개 이상일경우
```js
 const num = prompt("당신의 학점은?");
        if(num >=90){
        document.write("a학점");
        }else if(num >=80){
            document.write("b학점");
        }else if(num >=70){
            document.write("c학점");
        }else if(num >=60){
            document.write("d학점");
        }else{
            document.write("f학점");}
```

## 2. switch ~ case문
* 지정된 변수에 저장된 data와 정확히 일치되는 case가 있는지 검사해서  
일치하는 데이터가 있을때에는 해당 실행문 실행한뒤 마지막 break문으로 반복을 끝낸다.  
일치되는 값이 없으면 default에 해당되는 실행문을 수행한뒤 문장을 마침.
```js
const myArea = prompt("지역을 입력하세요","서울");
    switch(myArea){
        case "서울" :
        areaNum = "02";
        break;
        case "경기" :
        areaNum = "031";
        break;
        case "부산" :
        areaNum = "051";
        break;
    default :
            alert("등록되지 않은 지역입니다.")
    }        
    document.write(myArea + "지역번호는" + areaNum); 
```
## 3. 반복문
*  해당 조건식을 만족하는동안 {}안에 실행문을 반복적 수행 while문과 for문

 ### 1. while문
 * (~하는동안) 특정 조건을 만족하는 동안 실행문을 반복적으로 수행한다.  
 증감식이 반드시있어야한다. 안그럼 계속반복됨.
```js
var i= 초기값;
        while(조건식){
        실행문;
        증감식;
        } 

 //10부터 1까지 내림차순으로 2의배수만 출력
    var i = 10;
    while(i>=1){
            if(i%2 == 0) document.write(i + "<br />");
            i--;
    }
```
### 2. for문
*for문을 많이 쓴다. 반복문은 조건이 거짓이 되어야 빠져나온다.
```js
for(var k=초기값 ; 조건식 ; 증감식등 표현방식){
            실행문; 
            } 

//중첩 2중 for문 두개가 있다.

for(var k=2;k<=9;k++){//1~9곱하기
    document.write("<h1> "+k+" 단</h1>");

for(var m=1; m<=9;m++){//1~9곱하기
    document.write(k + "x"+ m +"=" + (k*m) + "<br />");
    }
}
```
### 3. break문
* 반복문에서 break를 만나면 조건식에 따라서 무조건 반복이 끝나는것 해당 반복문 종료

### 4. continue문
* 반복문이 continue문을 만나면 더이상 실행문을 수행하지 않고 바로 증감식으로 돌아가서 실행문 반복한다.
```js
//i값이 2로나눈 나머지가 1일경우= 홀수 인경우 실행

for(var i=1; i<=10; i++){
    if(i%2==1) continue;  
    //홀수실행하지않고 짝수실행됨
    document.write(i +"<br />");
}
```