# JavaScript
JavaScript는 웹페이지를 동적으로, 프로그래밍적으로 제어하기 위해서 고안된 언어.
## 숫자와 문자
- 자바스크립트에서는 큰따옴표나 작은따옴표가 붙지 않은 숫자는 숫자로 인식한다.
```html
<script type="text/javascript">
  alert(1+1);
  alert(1.2 + 1.3);
  alert(2 * 5);
  alert(6 / 2);
  Math.pow(3,2);       // 9,   3의 2승
  Math.round(10.6);    // 11,  10.6을 반올림
  Math.ceil(10.2);     // 11,  10.2를 올림
  Math.floor(10.6);    // 10,  10.6을 내림
  Math.sqrt(9);        // 3,   3의 제곱근
  Math.random();       // 0부터 1.0 사이의 랜덤한 숫자
</script>
```
- 문자는 "(큰 따옴표) 혹은 '(작은 따옴표) 중의 하나로 감싸야 한다.
```html
<script type="text/javascript">
alert("coding everybody");
alert(typeof "1");//데이터형을 출력
alert("안녕하세요.\n생활코딩의 세계에 오신 것을 환영합니다"); //\n:줄바꿈
alert('egoing\'s javascript')// \' : '출력
</script>

```
## 변수
JavaScript에서 변수는 var로 시작한다.
```html
<script type="text/javascript">
var a = 1;
alert(a+1);  //2

var a = 2;
alert(a+1);  //3

var first = "coding";
alert(first+" everybody");

var a = 'coding', b = 'everybody';
alert(a);
alert(b);

</script>
```
## 비교 연산자
- `==`
```html
<script type="text/javascript">
alert(1==2)             //false
alert(1==1)             //true
alert("one"=="two")     //false
alert("one"=="one")     //true

</script>
```
- `===` : 일치 연산자로 === 좌항과 우항이 '정확'하게 같을 때 true 다르면 false가 된다.
```html
<script type="text/javascript">
alert(1=='1');              //true
alert(1==='1');             //false  

alert(null == undefined);       //true
alert(null === undefined);      //false
alert(true == 1);               //true
alert(true === 1);              //false
alert(true == '1');             //true
alert(true === '1');            //false

alert(0 === -0);                //true
alert(NaN === NaN);             //false

</script>
```
 ``===``는 숫자 1과 문자 1을 다르게 인식한다. 반면에 '=='는 양쪽의 값을 같다고 판단한다. 바로 이것이 '정확'의 의미다. 즉 ===는 서로 같은 수를 표현하고 있더라도 데이터 형이 같은 경우에만 같다고 판단하기 때문이다. **== 연산자 대신 === 연산자를 쓰는 것을 강력하게 권한다.**
 - `!=`
 ```html
<script type="text/javascript">
alert(1!=2);            //true
alert(1!=1);            //false
alert("one"!="two");    //true
alert("one"!="one");    //false
</script>
 ```
- `!===`
### 조건문
```html
<script type="text/javascript">
if(id=='egoing'){
            password = prompt('비밀번호를 입력해주세요.');
            if(password==='111111'){
                alert('인증 했습니다.');
            } else {
                alert('인증에 실패 했습니다.');
            }
        } else {
            alert('인증에 실패 했습니다.');
        }

</script>
```
### 반복문
- while
```html
<script type="text/javascript">
var i = 0;
// 종료조건으로 i의 값이 10보다 작다면 true, 같거나 크다면 false가 된다.
while(i < 10){
    // 반복이 실행될 때마다 coding everybody <br />이 출력된다. <br /> 줄바꿈을 의미하는 HTML 태그
    document.write('coding everybody <br />');
    // i의 값이 1씩 증가한다.
    i++
}
//document.write는 웹페이지에 텍스트 출력
</script>
```
- for
```html
<script type="text/javascript">
for(var i = 0; i < 10; i++){
    document.write('coding everybody'+i+'<br />');
}  
</script>
```
- break,continue

### 함수
```html
<script type="text/javascript">
function numbering(){
    i = 0;
    while(i < 10){
        document.write(i);
        i += 1;
    }   
}
numbering();

function get_member1(){
    return 'egoing';
}

function get_member2(){
    return 'k8805';
}
</script>
```
### 배열
```html
<script type="text/javascript">
var member = ['egoing', 'k8805', 'sorialgi']
alert(member[0]);
alert(member[1]);
alert(member[2]);
//////////////////////////////////////////////////////////
function get_members(){
    return ['egoing', 'k8805', 'sorialgi'];
}
members = get_members();
// members.length는 배열에 담긴 값의 숫자를 알려준다.
for(i = 0; i < members.length; i++){
    // members[i].toUpperCase()는 members[i]에 담긴 문자를 대문자로 변환해준다.
    document.write(members[i].toUpperCase());   
    document.write('<br />');
}
//push는 마지막에 추가
var li = ['a', 'b', 'c', 'd', 'e'];
li.push('f');
alert(li);
//concat은 복수의 원소를 추가, 배열형식으로
var li = ['a', 'b', 'c', 'd', 'e'];
li = li.concat(['f', 'g']);// 자기자신에 다시 대입해야됨
alert(li);
//unshift는 맨 앞에 추가
var li = ['a', 'b', 'c', 'd', 'e'];
li.unshift('z');
alert(li);
//splice(index,num,data): index번째부터 num만큼 지우고 data를 삽입
var li = ['a', 'b', 'c', 'd', 'e'];
li.splice(2, 0, 'B');
alert(li);
//shift는 첫번째 제거
var li = ['a', 'b', 'c', 'd', 'e'];
li.shift();
alert(li);
//pop은 마지막 제거
var li = ['a', 'b', 'c', 'd', 'e'];
li.pop();
alert(li);
//sort,reverse(역순)
var li = ['c', 'e', 'a', 'b', 'd'];
li.sort();
alert(li);

var li = ['c', 'e', 'a', 'b', 'd'];
li.reverse();
alert(li);
</script>
```
### 객체
```html
<script type="text/javascript">
var grades = {'egoing': 10, 'k8805': 6, 'sorialgi': 80};
///////////////////
var grades = {};
grades['egoing'] = 10;
grades['k8805'] = 6;
grades['sorialgi'] = 80;
//////////////////
var grades = new Object();
grades['egoing'] = 10;
grades['k8805'] = 6;
grades['sorialgi'] = 80;
////////////////
var grades = {'egoing': 10, 'k8805': 6, 'sorialgi': 80};
alert(grades['sorialgi']);
///////////
alert(grades.sorialgi);
/////// 객체와 반복문
var grades = {'egoing': 10, 'k8805': 6, 'sorialgi': 80};
for(key in grades) {
    document.write("key : "+key+" value : "+grades[key]+"<br />");
}
/////객체지향
var grades = {
    'list': {'egoing': 10, 'k8805': 6, 'sorialgi': 80},
    'show' : function(){
        for(var name in this.list){
            document.write(name+':'+this.list[name]+"<br />");
        }
    }
};
grades.show();

</script>
```
### 모듈
#### greeting.js
```JavaScript
function welcome(){
    return 'Hello world';
}
```
#### main.html
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
    <script src="greeting.js"></script>
</head>
<body>
    <script>
        alert(welcome());
    </script>
</body>
</html>
```
### API
#### 레퍼런스와 튜토리얼
프로그래밍을 공부하기 위한 자료는 크게 레퍼런스(reference)와 tutorial(안내서)가 있다. 통상 튜토리얼은 언어의 문법을 설명하고, 레퍼런스는 명령어의 사전을 의미하다.
#### 자바스크립트 API문서
- [ECMAScript (표준문서)](http://www.ecma-international.org/publications/standards/Ecma-262.htm)
- [자바스크립트 사전 (생활코딩)](http://opentutorials.org/course/50)
- [자바스크립트 레퍼런스 (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)
- [jscript 레퍼런스 (MSDN)](http://msdn.microsoft.com/ko-kr/library/vstudio/z688wt03(v=vs.100))
#### 호스트 환경의 API 문서
- [웹브라우저 API](https://developer.mozilla.org/en-US/docs/Web/API)
- [Node.js API](http://nodejs.org/api/)
- [Google Apps Script API](https://developers.google.com/apps-script/)
