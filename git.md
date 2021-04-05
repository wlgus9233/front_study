# Git & Github

* Git : 버전 컨트롤시스템, 명령어기반. 
1. 많이사용되어지고 무료다.  
2. 오픈소스,빠른동작.  
3. 오프라인가능, 실수수정이 용이.  
4. branching을 이용해서 기능별로 만들어 협업을 효율적으로 한다.

* .git directory에 있는 commit들은 history창고다. 버전별로 나눠관리 할수 있기때문에 앱전체를 commit하기보다 세분화해서 저장하는것이 좋다.

* Github : server와 같은 cloud역활. 서버와 개발자가 동일한 히스토리 정보를 가진다. 서버는 회사가 지닌 private server 와 bitbucket 도 등등 있다.

* git홈페이지에 source tree 등등 GUI도 간편하게 나와있음.

___
## Local (work flow)

1. git init : 초기화 명령어.     로컬저장소를 생성한다. 여기에 깃쓸꺼야!  (working directory)  
2. git add : 변경된파일을 스토리지에 추가한다.(staging area)  
3. git commit : add한 파일을 로컬 디파지토리에 저장한다 (.git directory)  
4. git push : local repository를 remote repository에 업로드
<-> 되돌아가는건 pull

___
## 첫 github 코드 올리기

* 깃허브에 repository생성 > 프로젝트이름/설명 설정

```js
** git을 설치한 후 특별한 설정을 하지 않았다면, Github 이메일 주소 및 비밀번호를 입력하라고 합니다. 입력해야 소스 코드가 Github으로 푸시 **

$ git config --global user.name "wlgus9233"// 내아이디
$ git config --global user.email "wlgus9233@naver.com"// 내 깃허브 이메일

$ git init//git이 추적할 수 있도록 .git 폴더를 생성

(택1)
$ git add 파일이름 //특정파일만 커밋 (추천)
git add . //전체파일 선택들
git add -A
git add *
git add *.파일버전

git config -- global core.autocrlf true/input // 운영체제마다 줄바꿈할때 문자열달라짐을 방지하기위해 window=true,mac=input을 쓴다.window = cariage return + line feed (text\r\n)이기에 git으로 저장할때는 \r을 삭제하고 가져올떄는 \r을 붙힌다. mac은 line feed 하나만 들어가기에(\n) 상태변화가 없지만, 외부이메일을 복사해 붙여넣을때 실수로 \r이 들어가는걸 방지하기위해 input을 넣는것이다. 

$ git commit -m "프로젝트메세지 내용"  
//-m 옵션은 간단하게 한줄로 메시지를 작성하기 위함이며, 긴 메시지 작성이 필요하다면 git commit 명령어만 실행하면 타이틀과설명을 적을수있다.

git remote //현폴더의 레파지토리 확인

$ git remote add origin {remote repository 주소}// origin은 remote repository의 별칭, epository의 주소는 내 github 주소

$ git push origin {브랜치명} //master가 아닌 다른 branch로 push 하고 싶으면, 아래와 같이 master를 특정 브랜치명으로 바꿔서 명령어를 실행하면 됨.

```
___
## 작업진행하며 수정내용 업로드하기

```js
$ git add 특정파일선택

$ git commit -m "두번째 커밋 메시지 내용"

$ git push origin {브랜치명}

```

___
## Branch : 현시점 두미래(평행우주)
* 브랜치란 독립적으로 어떤 작업을 진행하기 위한 개념이다.
* 회사프로젝트와는 다르게 다른시도를 원한다면 파일을 함부로 변경할수 없으니 나만의 브랜치를 만든다.
* 저장소를 처음 만들면, Git은 바로 'master'라는 이름의 브랜치가 생성됨.
```js
 git branch {브랜치이름}
 git branch //생성된 브랜치들을 볼수있음
 git checkout {브랜치이름} //그공간으로 넘어감
 git merge {브랜치명} //다른공간꺼 병합하기
 git log --graph --all --decorate //시각화된 두분기작업 내용을 볼수있다.
```
* merge를 쓰면 여러갈래가 합쳐지고 분기하기 때문에 변경내용이 한줄로 정리 되기 원할때, 
```js
git rebase {브랜치이름}//인라인재배치
git branch -D {브랜치이름} //다쓴브랜치 삭제 
```

___
## 실무에서 자주쓰는 명령어/단축키

```js

cd 폴더이름 //그폴더 안으로 이동

mkdir 폴더명 //새로운 폴더디렉토리생성

ls -al //안에 내용확인 , 폴더나 파일앞에 .닷이 있으면 숨겨진파일.
open 폴더이름 //열기명령어

rm -rf.git //삭제명령어,숨겨진깃을삭제함 삭제하면 더이상 git프로젝트가 아니고 다시초기화 해도됨.

git config --list //모든설정확인

git status //작업내용확인 수정된파일을 확인할수 있다.

git log //커밋된파일의 정보인 해쉬코드, 타이틀, 디스크립션뜸.

echo add >> 파일이름 //파일안에 add 문자추가

git config --h //간단정보 확인

(END)되거나 터미널키 안먹을때 :q 
터미널코드 깨끗이지우기 : command + K


```
___

더자세하게 알고싶다면 [깃허브기초](https://backlog.com/git-tutorial/kr/intro/intro1_1.html)