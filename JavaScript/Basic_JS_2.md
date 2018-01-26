## 유효범위
자바스크립트는 함수가 선언된 시점에서의 유효범위를 갖는다. 이러한 유효범위의 방식을 정적 유효범위(static scoping), 혹은 렉시컬(lexical scoping)이라고 한다.  
`->` 조건문이나 반복문에서의 변수선언은 전역변수가 된다.
- 불가피하게 전역변수를 사용해야 하는 경우는 하나의 객체를 전역변수로 만들고 객체의 속성으로 변수를 관리하는 방법을 사용한다.
```javascript
MYAPP = {}
MYAPP.calculator = {
    'left' : null,
    'right' : null
}
MYAPP.coordinate = {
    'left' : null,
    'right' : null
}

MYAPP.calculator.left = 10;
MYAPP.calculator.right = 20;
function sum(){
    return MYAPP.calculator.left + MYAPP.calculator.right;
}
document.write(sum());

```
## 함수 = 값
- JavaScript의 함수가 다른 언어의 함수와 다른 점은 함수가 값이 될 수 있다는 점이다.
```JavaScript
function a(){}
```
위의 예제의 함수 a는 변수 a에 담겨진 값. 함수는 값이기 다른 함수의 인자로 전달 가능.
- 함수는 함수의 리턴 값으로도 사용할 수 있따.
```JavaScript
function cal(mode){
    var funcs = {
        'plus' : function(left, right){return left + right},
        'minus' : function(left, right){return left - right}
    }
    return funcs[mode];
}
alert(cal('plus')(2,1));
alert(cal('minus')(2,1));   
```
- 배열의 값으로도 사용할 수 있음.
```JavaScript
var process = [
    function(input){ return input + 10;},
    function(input){ return input * input;},
    function(input){ return input / 2;}
];
var input = 1;
for(var i = 0; i < process.length; i++){
    input = process[i](input);
}
alert(input);
```
## 콜백
함수가 다른 함수의 인자로 사용됨으로써 그 함수의 내용을 완전히 바꿀 수 있는것.
## 비동기 처리(Ajax)
 시간이 오래걸리는 작업이 있을 때 이 작업이 완료된 후에 처리해야 할 일을 콜백으로 지정하면 해당 작업이 끝났을 때 미리 등록한 작업을 실행하도록 할 수 있다.
## 객체지향
### 생성자와 new
JavaScript에서는 객체를 구성할때도 함수를 이용한다.
```javascript
function Person(name){
    this.name = name;
    this.introduce = function(){
        return 'My name is '+this.name;
    }   
}
var p1 = new Person('egoing');
document.write(p1.introduce()+"<br />");

var p2 = new Person('leezche');
document.write(p2.introduce());
```
### 전역객체
func();와 window.func();는 모두 실행이 된다. 모든 전역변수와 함수는 사실 window 객체의 프로퍼티다. 객체를 명시하지 않으면 암시적으로 window의 프로퍼티로 간주된다.
### 상속
```javascript
var o = {'func':function(){
    alert('Hello?');
}}
o.func();
window.o.func();
```
### 상속
```javascript
function Person(name){
    this.name = name;
}
Person.prototype.name=null;
Person.prototype.introduce = function(){
    return 'My name is '+this.name;
}

function Programmer(name){
    this.name = name;
}
Programmer.prototype = new Person();
Programmer.prototype.coding = function(){
    return "hello world";
}

var p1 = new Programmer('egoing');
document.write(p1.introduce()+"<br />");
document.write(p1.coding()+"<br />");
```
prototpye은 객체의 원형. prototype에 저장된 속성들은 생성자를 통해서 객체가 만들어질 때 객체에 연결된다.
## Core , BOM, DOM
### Core
JavaScript 언어 자체에 정의되어 있는 객체들. 생활코딩의 자바스크립트 수업과 사전에 정의된 객체가 여기에 속한다.  
ex) `Object,Array,Function`
### BOM
Browser Object Model. 웹페이지의 내용을 제외한 브라우저의 각종 요소들을 객체화시킨 것이다. 전역객체 Window의 프로퍼티에 속한 객체들이 이에 속한다.
ex) `navigator`,`screen`,`location`....
### DOM
Document Object Model. 웹페이지의 내용을 제어한다. window의 프로퍼티인 document 프로퍼터에 할당된 Document 객체가 이러한 작업을 담당한다. Document 객체의 프로퍼티는 문서 내의 주요 엘리먼트에 접근할 수 있는 객체를 제공한다.  
ex) `Document`
