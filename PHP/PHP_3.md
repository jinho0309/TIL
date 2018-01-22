## 데이터베이스
### MySQL?
데이터베이스라는 분류의 제품군에 속한 구체적인 상품으로 ORACLE에 의해서 개발되고 있다. 오픈소스이고, 가장 많은 사용자를 가지고 있는 데이터베이스 시스템에 속한다. MySQL과 같은 분류에 속한 데이터베이스로는 ORACLE, MSSQL 등이 있다.
### MySQL 서버에 접속
- mysql.exe : `mysql -u'유저네임' -p'패스워드' -h'호스트'`
### PDO(PHP Data Objects)
PDO(PHP Data Objects)란 여러가지 데이터베이스를 제어하는 방법을 표준화시킨 것이다.PHP의 (mysql_connect와 같은 함수를 사용할 수 있게 해주는)MySQL 확장은 PHP 5.5 버전부터 지원되지 않을 예정이다. 따라서 새로운 에플리케이션의 개발하는 경우 MySQL 확장을 사용해서는 안된다. 하지만 사용하는 환경이 PDO나 mysqli를 지원하지 않거나 기존의 코드가 MySQL 확장이라면 이것의 사용법을 알아야 한다.  
*MySQL 확장은 레거시(이전의 것)를 위한 공부*
### MySQL 확장
- `mysql_connect(호스트네임,사용자,비밀번호)` : 연결
- `mysql_select_db(DB네임)` : DB선택
- `mysql_query(SQL문)` : SQL문 실행
- `mysql_real_escape_string` : 보안관련, 사용자가 입력한 정보는 꼭 써야됨
- `mysql_fetch_array` : mysql_query문이 반환한 값을 매개변수로 array로 fetch시켜줌(1행 씩 return, 없으면 false를 return)
*cf. header("Location : a.php") : http의 header에 삽입되어 a.php로 이동하게 됨(Redirection)*
*cf. htmlspecialchars : 보안관련,문장 내에 HTML 코드가 들어가는 특수 문자를 포함시켜 입력한 후 화면으로 출력할 때 그 HTML 특수 문자가 HTML 태그로 적용되어 출력되는 것이 아니라, HTML 특수 문자가 일반 문자로 인식되어 그대로 출력되도록 ex)<script></script>하면 javascript가 실행 될 수 있음.*
## 쿠키와 세션
사용자의 상태를 유지시키는 목적.
### 쿠키란?
- 클라이언트(브라우저)에 모든 데이터를 저장, 데이터 유출 될 수 있음
- `setCookie(key,value,time)` : time까지만 유효, 이후에는 삭제
- `$_COOKIE[key]` : 쿠키를 가져옴.
### 세션?
- SID(session ID)를 식별자로 서버에 데이터를 저장
- SID로는 쿠키나 도메인 파라미터를 사용
- `session_start();` 로 항상 시작해줘야함, 스크립트의 최상단에 위치해야 함
- `$_SESSION`
- 데이터는 서버 내에 파일이나 DB에 저장 함
- 주로 사용자 인증시에 사용함
- `session_destroy();` : 세션파괴
## 객체지향프로그래밍
### 클래스와 인스턴스 그리고 메소드
```
class MyClass{
  private $name;
   function __construct($fname){
     $this->name= $fname;
   }
  function show(){
    echo abc;
  }
}
```
- `__construct` : 생성자, 클래스의 변수에 접근제어자 안붙이면 에러..
