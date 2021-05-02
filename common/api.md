# 들어가기전...
 * pc,mobile등등의 client 기기에서 서버에 있는 데이터를 읽고 쓰기 위해서 서버에서 제공하는 web api들을 이용해서 처리할수 있다.  
 네크워크에서 기기간에 의사소통을 해나가는 규격사항을 HTTP(hypertext transfer protocol)라 부른다.  
 이런 webAIP를 어떻게 디자인해서 만들건지 정의하는것이
 과거엔 SOAP(simple object access protocol)라는 모든 네트워크 요청과 반응을  
 HTML처럼 생긴 XML데이터 모맷을 저장해서 주고 받았다면,  현재는 REST(representational state transfer)가 보편적이다.
 > REST 는  Get(read),Post(create),Put(update),Delete(delete) 

 * client는 GET을 이용해서 정보를 요청하면 서버에서 JSON 포맷을 통해 받아 올수 있다.  
 이렇게 서버에서 제공하는 DB를 읽거나 업뎃 하는 Web API 뿐만아니라, Frameworks,Libraries에서 Class나 함수를 API라고 부른다.
 외부에서 가져오는 라이브러리 뿐만아닌,  프로젝트 내부에서 쓰여지고 있는 class나 module이 있다면  
 module calculator에서 제공하는 add,multiply 두가지의 함수를 이용해서 인터페이스를 이용해 api 이용해 사용한다.

 * api는 내부 구현사항을 숨겨두고 외부에서 사용하는 사람이 필요한것만 노출해 두는것을 인터페이스, api라 부르는것.


# API(Application Programming Interface)
프론트엔드에서 1번글을 눌렀을때 백엔드에 1번글을 달라고 요청 (request) 하면,  
백엔드는 자체 DB를 찾아서 1번글에 해당되는 제목과 내용의 정보를 가져와 프론트엔드에 응답(reponse)하여 전달하고  
 프론트엔드는 그 정보를 화면에 보여준다.
이때 프론트엔드가 백엔드에 요청할때 특정규칙에 맞게 요청해야 하는데,  
이런 사용규칙을 제공하는것이
**API** 다.  요약 : 필요한 부분을 요청하여 응답을 받는 서비스간의 다리와 같은 역할

> * front-end : 화면에 보여지는것 ex) 게시판의 제목,내용이 어디있고 색깔,모양이 어떤지  
> * back-end : 서버  ex) 실제 게시판의 제목 , 내용의 데이터를처리

## open API
* 회사 내부에서 공개적으로 오픈한것.
* 백엔드를 만들어놓고 주소와 사용규칙을 공개하는것.  
 백엔드 없이 얼마든지 요청하고 데이터를 가져와서 프론트엔드로 구현할수있다.  
* 공개된 백엔드를 이용하고 프론트엔드만 만들어 쓰는것을 serverless라고 부른다. 
* api 가이드는 api마다 다르지만 공통적으로 요청과 응답에 대한 정보가 나와있다.

ex) 지도(구글,네이버,카카오등),결제(i'mport API등), 채팅(socket.io),AI(cloud vision API) 등등...  
등등의 고급기능들도 공개되어 규칙에 맞게 전송하면 복잡한 기능은  
이미 만들어진 백엔드에서 처리하고 남은 결과만 자바스크립트를 이용해 사용할수 있다.


>### 요청(request)
* 주소: 어디서 정보전달할지 api 서버주소(카카오오픈책검색주소)
* 전송방식 : GET(주소창의 모든정보를 담아 정보전달)/POST(주소창이아닌 내부적으로 정보전송 방식)
* 보낼것 : api 요청에서 필요한 정보들 [query(검색어),sort(정렬방식),target(검색대상)...]
> ### 응답(reponse)
* 형식:JSON
* json응답 의미설명 :[title(도서제목),contents(도서소개),thumbnail(도서표지썸넬url)...]

> ## JSON(javascript object nation)
 중괄호 사이 이름-값 ,콤마 형식
```json
{
    "이름": "홍길순",
    "나이": 27,
    "성별": "여",
    "특기":["도술","검술"],//array => [1,2,3,4]
    "가족관계":{"아버지":"홍판서","어머니":"춘섬"} //objet => {"이름":"홍길동"} 또다른 json의 형태로도 올수있다.
}
```

# Ajax(Asynchronous Javascript And Xml)란?
XMLHttpRequest 객체를 사용해 구현하는 비동기 통신 방법을 의미한다.
>* 동기 방식: 페이지 이동을 하면 페이지전체를 다시 
>* 비동기 방식:페이지 전환 없이 서버에서 값을 가져오는것 (ajex)

>### XMLHttpRequest란?
>초창기 웹은 문서 공유 목적으로 만들어졌기 때문에  동기방식으로 서버에서 넘겨준 데이터를 출력하는 용도로만 동작했다.  
구글 map처럼 설치해서 사용할 프로그램들을 웹으로 만들어 브라우저만 있으면 사용할수 있는 환경을 만들어 웹발전에 영향을 줬다.  
 ( XMLHttpRequest는 브라우저에서 지원하는 객체라 별다른 라이브러리 설치 없이 사용할 수 있다는 장점이 있지만,  
 사용하기 불편하게만들어져 이것을 기반으로 한 jQuery나 axios같은 라이브러리를 설치해서 비동기처리를 한다.)
> 과거에는 프론트 개발시 jQuery에서 제공하는 $.ajax 메소드를 가장 많이 사용했지만 ES5의 promise기반으로 만들어진 axios와 같은 라이브러리를 사용한다.
라이브러리들이 XMLHttpRequest라는 것을 사용하는구나 정도만 알고 넘어가자.

## kakao book API로 정보가져오기
___

1. [jquery cdn](https://code.jquery.com/)에서 jquery cdn을 가져온다.  
 jQuery Core 3.6.0 - uncompressed 를 눌러 script 코드를 복사한 후 마지막<body>태그 바로위에 붙혀넣기.

2. [jquery ajax](https://api.jquery.com/jquery.ajax/)공식사이트에서 예제를 활용해 간단한코드를 작성한다.

3. open api key발급받기  
오픈 api는 api키를 발급받은 사람에게 접근권한을 준다.  
ex) [kakaoDevelopers](https://developers.kakao.com/)로그인 > 메뉴 내 어플리케이션 > 앱만들기(api키 발급받는것)

4. api가이드 참고해서 코드작성하기(요청 => 샘플참고)  

ex) [개발가이드 > 책검색](https://developers.kakao.com/docs/latest/ko/daum-search/dev-guide#search-book)  Request(요청)과Response(응답)의 가이드가 나와있다.

```js
 $.ajax({// 코드상단 = 요청
            method: "GET",//전송방식
            url: "some.php",//전송주소로 api 샘플주소 복붙
            data: { name: "John", location: "Boston" }//전송에 포함될 데이터 정보들(json형식) 필수인것 복붙
        })
          .done(function (msg) {//.done 이후에 요청에 대한 응답이오면
                alert("Data Saved: " + msg);//응답을 가지고 처리하는 코드가 여기에 들어가게 된다.
            }); //control+a 로 전체선택 누르고 control+k+f를 누르면 자동으로 코드 정렬됨
```
> ### http method 를 가이드에 맞게 작성한다.  
>웹 서버는 브라우저에서 무슨 의도로 요청을 보낸것인지 URL과 http method를 통해 파악한다.  
어떤 method를 사용할지는 백엔드 개발자가 결정하는 것.
백엔드 개발자가 알려준 URL과 method로 ajax를 호출하기만 하면 된다.

> method(용도) : GET(조회),POST(저장),PUT(수정),DELETE(삭제)
(과거에는 GET / POST 만 사용하는 경우가 많았지만 URL과 method만으로도 제공하는 API의 기능을 예상할 수 있도록 만들고 있는 추세)

5. 샘플양식에 맞게  headers:{Authorization: "KakaoAK {REST_API_KEY}"}을 작성후 고유키 번호를 넣는다. 
ex) 만든앱 > 내 앱키 > REST API 키

> ### JSON 데이터를 javascriptdp 접근하는법
>json 데이터가 data라는 변수에 담겨있다고 했을때,
>* 홍길순을 가져오려면? data.key값(이름) => value값(홍길순)
>* 단순히 값을 가져오려면? .key이름 => 홍길순
>* 특기의 '도술'값을 가져오려면? data.특기[0] => 도술
>* 또다른 json 속의 어떤값을 가져오려면? data.가족관계.아버지 => 홍판서 ( 똑같은 방식으로 계속 접근하면 된다.)
```json
{
    "이름": "홍길순",//"key":"value"
    "나이": 27,
    "성별": "여",
    "특기":["도술","검술"],
    "가족관계":{"아버지":"홍판서","어머니":"춘섬"} 
}
```

6. 요청에 대한 응답으로 작성한 경고창이 브라우저에 뜨는걸 확인할수 있다.  
alert("Data Saved: " + msg); 를 -->  console.log("msg");로 작성후  
콘솔창에서 먼저 응답받은 json객체 (object)에 대해 마우스 오른쪽 버튼을 눌러 store as global variable (응답받은 json을 console창에서 다루기위해 ) 클릭.  
우리가 응답받은 object가 
json을 저장한 data에 헤당하는게 temp1이 된다.  

7.  document 키값을 배열 0번째 요소에 접근해서,   
0번째 요소에 있는 도서정보중 title과 thumbnail을 가져온다.  
console창에 temp1.documents 를 입력하면 배열이 받아지게 된다.
temp1.documents[0]을 일력해 0번째 요소로 접근하면,  
또 새로운 json이 들어오는데
temp1.documents[0].title
temp1.documents[0].thumbnail 을 입력해 타이틀과 썸네일 이미지 주소를 가져올수 있다.  
코드를 복사해서 응답 에 붙혀넣는다. 그리고 temp1을 msg로 바꿔준다.

8. [jquery add html](https://api.jquery.com/append/)를 통해 코드를 참고해서 body에 p 태그를 추가한후,  
```js
.done(function (msg) {// 응답
                console.log(msg.documents[0].title);
                console.log(msg.documents[0].thumbnail);
                $( "p" ).append( "<strong>"+msg.documents[0].title+"</strong>" );
                $( "p" ).append( "<img src='"+msg.documents[0].thumbnail+"'/>" );
            }); 
```
js값을 넣으면 api를 통해 정보를 가져와서 화면에 표시할수 있다.

* 또한 maps 같은 api 등은 ajax코드를 작성하지 않아도 SDK(software development kit)로 자체적 ajax 요청을 해줘서 사용할수 있는 경우도 있다.
* 얼굴인식 api 경우 html파일에서 ajax요청을 보내게 되면, api 서버자체에서 차단하는 경우가 있기에  node.js에서 자체 front-end 서버를 만들어서 요청하면 올바른 응답이 온다. (보안상 서버를 요구하는 경우로, 이렇게 프론트 엔드만 제공하는것도 Serverless)
___
### 유용한 API 참고 사이트해서 나만의 app을 만들자 !
___
* Giphy 개발툴에서 제공하는 SDK 나 openAPI (gif)
* Sportify (음악)을 이용해 만든 개발자 app을 참고해볼수 있음
* APIMeme Meme Generator
* Public Api
* 깃허브에 정리된 퍼블릭 api