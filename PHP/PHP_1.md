# PHP
PHP는 서버쪽에서 구동되는 언어. 사용자가 업로드한 파일을 서버에 저장하거나, 사용자가 입력한 데이터를 받아서 데이터베이스나 파일에 저장하고, 저장된 정보를 불러와서 HTML을 생성해서 웹브라우저로 전송하는 등의 일을 한다.
- 주로 HTML 코드를 프로그래밍적으로 생성
- 서버쪽에서 실행 되는 프로그래밍 언어
## PHP의 장점
- 웹에 최적화된 언어
- 웹개발에 필요한 수많은 로직들이 함수의 형태로 미리 제공됨
- 크로스플랫폼
- 거의 모든 데이터베이스를 지원
- 가장 많은 공개소프트웨어가 PHP로 만들어짐
- [phpschool](http://phpschool.com/) : php커뮤니티
## PHP설치
Bitnami를 이용해서 Apache, PHP, MySQL (APM)을 설치
## 설정
Configuration. PHP가 동작하는 기본적인 작동방법을 변경하는 것으로, `php.ini` 파일를 통해서 변경 사항을 반영.설정을 변경 한 후에는 웹서버를 리로드(reload) 혹은 재시작(restart) 해야 한다.
### 에러설정
보안과 관련있음. 에러에는 관련된 정보가 들어있어서 운영시에는 에러가 안보이게 해야함.  
`C:\BitNami\wampstack-5.4.20-0\php\php.ini`
- `php.ini-development` : 개발환경에서의 설정 권장사항
- `php.ini-production` : 운영할때의 설정 권장사항
### 운영
```
display_errors = Off
display_startup_errors = Off
error_reporting = E_ALL
log_errors = On
```
### 개발
```
display_errors = On
display_startup_errors = On
error_reporting = -1
log_errors = On
```
## 숫자와 문자
#### number.php
```
<?php
var_dump(6);//자료형 확인
var_dump(6.1);
var_dump('Hi');
?>
```
#### string.php
```
<?php
echo "Hello"." "."world";//문자 + 문자는 PHP에선 .을쓴다.
echo "He says \"blablabla\"";
echo 'He says "blablabla"';
 ?>
```
## 변수와 상수
#### variable1.php
```
<?php
  $a=1;
  echo $a+1;
  echo "<br/>";
  $a=2;
  print $a+1; #echo == print
  echo "<br/>";
  $first = "coding";
  echo $first." "."everyday";
 ?>
```
#### variable2.php
```
<?php
  define('TITLE','PHP Tutorial');//상수 정의
  echo TITLE;
  define('TITLE','PHP Tutorial');//에러(상수는 변경 불가)
 ?>
```
상수를 정의 할 때는 define를 사용한다. define의 첫번째 인자로 상수의 이름이 사용되고, 두번째 인자로 상수의 값이 사용된다. 상수에 저장된 값을 사용하기 위해서는 인용부호가 없이 상수의 이름을 적어주면 된다.  
위의 코드는 한번 정의된 상수의 값은 불변이라는 원칙을 어기고 있기 때문에 PHP에서는 오류를 발생시킨다.
#### variable3.php
```
<?php
$a = 100;
echo gettype($a);//형 반환
settype($a, 'double'); //형 정의
echo '<br />';
echo gettype($a);
?>
```
PHP에서 변수에 담긴 데이터 형을 검사할 때는 gettype과 settype을 사용한다.
- is_ array
- is_ bool
- is_ callable
- is_ double
- is_ float
- is_ int
- is_ integer
- is_ long
- is_ null
- is_ numeric
- is_ object
- is_ real
- is_ resource
- is_ scalar
- is_ string
#### variable4.php
```
<?php
$a = 100;
$a = "test";
$a = array(1,2,3);
?>
```
PHP는 다른 언어들과는 다르게 변수에 담길 값의 데이터 형식을 미리 지정할 필요가 없다.  
이것은 매우 편리 하지만, 변수에 어떠한 형식의 데이터가 담겨있는지를 예측할 수 없기 때문에 오류가 발생할 가능성이 높아지기도 한다.
#### variable5.php(가변변수)
```
<?php
$title = 'subject';
$$title = 'PHP tutorial';
echo $subject;
?>
```
위의 코드를 보면 변수 $title의 값이 subject이다. 그런데 5행에 나타나는 '$$title'에는 '$'가 두번 표시되어 있다. 이것은 문자열 'PHP tutorial'이 변수 $title의 값이 아니라 변수 $subject의 값이라는 의미.
## 입출력,폼과 HTTP
### GET방식
```
<?php
$_GET['value'];
?/
```
### POST방식
```
<?php
$_POST['value'];
?/
```
### GET vs POST
URL에 데이터를 첨부해서 전송하는 방식을 GET 방식이라고 부르고, POST 방식은 HTTP 메시지의 본문에 데이터를 포함해서 전송한다. 이러한 차이로 인해서 GET 방식은 정보에 대한 링크로 많이 사용되고, POST 방식은 사용자의 아이디나 비밀번호와 같은 데이터를 전송하는 방식으로 주로 사용한다.
