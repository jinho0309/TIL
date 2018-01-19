## 배열
### 배열의 생성
```
<?php
$member = ['egoing', 'k8805', 'sorialgi'];
?>
```
php 5.4 이전 버전에서는 아래와 같은 문법을 사용해야 한다. 따라서 하위 호환성을 위해서는 아래의 형식을 사용하는 것이 권장된다.
```
<?php
$member = array('egoing', 'k8805', 'sorialgi');
?>
```
### 배열의 사용
```
<?php
function get_members(){
    return ['egoing', 'k8805', 'sorialgi'];
}

$members = get_members();

for($i = 0; $i < count($members); $i++){
    echo ucfirst($members[$i]).'<br />';
}

?>
```
PHP는 변수의 자료형을 선언 안하기 때문에 자유롭게 리턴 받을 수 있다.
### 배열의크기
- count(arr)
```
<?php
$l = [1, 2, 3, 4, 5];
echo count($l);
?>
```
### 배열의 추가
- array_push(arr,item) : 마지막에
```
<?php
$arr = ['a', 'b', 'c', 'd', 'e'];
array_push($arr, 'f');
var_dump($arr);
?>
```
- array_merge(arr,[item1,item2]) : 복수의 아이템 추가
```
<?php
$li = ['a', 'b', 'c', 'd', 'e'];
$li = array_merge($li, ['f','g']);
var_dump($li);
?>
```
- array_unshift(arr,item) : 맨앞에 추가
```
<?php
$li = ['a', 'b', 'c', 'd', 'e'];
array_unshift($li,'z');
var_dump($li);
?>
```
- array_splice(arr,idx,num,item) : idx부터 num만큼 제거 후 item 추가
```
<?php
$li = ['a', 'b', 'c', 'd', 'e', 'z'];
array_splice($li, 2, 0, 'B');
var_dump($li);
?>
```
### 배열의 제거
- array_shift(arr) : 맨앞 제거
```
<?php
$li = ['a', 'b', 'c', 'd', 'e', 'z'];
array_shift($li);
var_dump($li);
?>
```
- array_pop(arr) : 맨뒤 제거
```
<?php
$li = ['a', 'b', 'c', 'd', 'e', 'z'];
array_pop($li);
var_dump($li);
```
### 배열의 정렬
- sort(arr) : 오름차순
```
<?php
$li = ['c','e','a','b','d'];
sort($li);
var_dump($li);
?>
```
- rsort(arr) : 내림차순
```
?php
$li = ['c','e','a','b','d'];
rsort($li);
var_dump($li);
?>
```
## 연관배열(Associative Array)
파이썬의 Dic, 자바스크립트의 List같은 느낌
### 연관배열의 생성
```
<?php
$grades = array('egoing'=>10, 'k8805'=>6, 'sorialgi'=>80);
?>
```
```
<?php
$grades = [];
$grades['egoing'] = 10;
$grades['k8805'] = 6;
$grades['sorialgi'] = 80;
var_dump($grades);
?>
```
### 연관배열의 반복
- foreach
```
<?php
foreach($arr2 as $key=>$value)
  echo $key.' '.$value;

echo '</br>';
foreach($arr2 as $value)
  echo $value.' ';
}
?>
```
foreach 문은 $grades 위치의 배열에 담긴 요소의 숫자만큼 반복문을 실행한다. 반복문이 실행될 때마다 요소의 키값을 $key 자리의 변수에 요소의 값을 $value 자리의 변수에 할당  
*as뒤에 value만 쓸수도 있음->key값아닌 value값만 출력, 연관배열 아닌 그냥 배열에서도 foreach쓸 수 있음*
## include와 namespace
- include : 다른 php파일을 삽입
- namespace : 많은 php를 include했을 때 중복을 피하기 위해
### include의 장점
- 자주 사용되는 코드를 별도의 파일로 만들어서 필요할 때마다 재활용할 수 있다.
- 코드를 개선하면 이를 사용하고 있는 모든 애플리케이션의 동작이 개선된다.
- 코드 수정 시에 필요한 로직을 빠르게 찾을 수 있다.
- 필요한 로직만을 로드해서 메모리의 낭비를 줄일 수 있다.
#### greeting.php
```
<?php
function welcome(){
    return 'Hello world';
}
?>
```
#### temp.php
```
<?php
include 'greeting.php';
echo welcome();
?>
```
PHP는 외부의 php 파일을 로드하는 방법으로 4가지 형식을 제공한다.
- include
- include_once
- require
- require_once
include와 require의 차이점은 존재하지 않는 파일의 로드를 시도했을 때 include가 warning를 일으킨다면 require는 fatal error를 일으킨다는 점이다. fatal error는 warning 보다 심각한 에러이기 때문에 require가 include 보다 엄격한 로드 방법.  
`_once`라는 접미사가 붙은 것은 파일을 로드 할 때 단 한번만 로드하면 된다는 의미다.
### namespace
같은 이름을 쓰는 경우가 생길 수 있다. 이런 경우 먼저 로드된 모듈은 나중에 로드된 모듈에 의해서 덮어쓰기 되기 때문에 namespace를 이용하여 중복을 회피한다.*하나의 파일에는 복수의 네임스페이스가 존재 할 수도 있다.*
#### greeting_en.php
```
<?php
namespace eng;
function welcome(){
  echo "Hi</br>";
}
 ?>
```
#### greeting_kor.php
```
<?php
namespace kor;
function welcome(){
  echo "안녕</br>";
}
 ?>
```
#### include_namespace.php
```
<?php
  include 'greeting_kor.php';
  include 'greeting_en.php';
  kor\welcome();
  eng\welcome();
 ?>
```
- 주의사항 : namespace를 설정했을 경우 무조건 namespace를 붙여줘야 한다.
## 파일
### 복사 및 삭제
- copy(filename,newfilename) : 복사
- unlink(filename) : 삭제 (unix계열의 명령어)
### 읽기 및 쓰기
- file_get_contents(file) : 파일의 내용을 반환(URL의 내용도 읽어 올 수 있음.)
- file_put_contents(file,str) : 파일을 쓴다.
### 권한
- is_readable(file) : 읽을 수 있는지
- is_writable(file) : 쓸 수 있는지
- file_exists(file) : 존재하는지
## 디렉토리
### 현재 디렉토리와 디렉토리의 변경
- getcwd() : 현재 디렉토리를 알 수 있다.
- chdir() : 디렉토리를 변경.
### 디렉토리의 탐색
- scandir(dir) : 디렉토리 탐색
- scandir(dir,method_sort) : method_sort가 1이면 정렬결과를 반대로, defalut=0
### 디렉토리의 생성
- mkdir(파일경로,권한,(true/false)) : 세번째 인자의 값으로 true를 지정하면 첫번째 인자로 주어진 경로가 여러개의 디렉토리로 이루어져 있을 때 해당 디렉토리를 한번에 생성하는 기능을 제공.
## 파일업로드
#### file_upload.html
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
</head>
<body>
<form enctype="multipart/form-data" action="upload.php" method="POST">
   <input type="hidden" name="MAX_FILE_SIZE" value="30000" />
   <input name="userfile" type="file" />
   <input type="submit" value="upload" />
</form>
</body>
</html>
```
#### upload.php
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">

  </head>
  <body>
      <?php
      ini_set("display_errors", "1");//php설정을 변경.. 에러를 볼수있도록
      // var_dump($_FILES); Array로 되어있는 걸 확인할 수 있다.
      $uploaddir = '파일경로\\';
      $uploadfile = $uploaddir . basename($_FILES['userfile']['name']);//basename : 경로를 정확하게 하기위해..보안과관련됨
      echo '<pre>';
      if(move_uploaded_file($_FILES['userfile']['tmp_name'], $uploadfile)){
        echo "파일이 유효하고, 성공적으로 업로드\n";
      }else {
        echo "파일 업로드 공격의 가능성이 있습니다.!\n";
      }
      echo '자세한 디버깅 정보입니다:';
      print_r($_FILES);
      print '</pre>';
       ?>
       <img src="file/<?=$_FILES['userfile']['name']?>"/>
  </body>
</html>
```
`$_FILES`로 파일을 받게되면 `연관배열`의 형태로 되어있다.
```
    [userfile] => Array
        (
            [name] => main2.jpg
            [type] =>
            [tmp_name] =>
            [error] => 0
            [size] => 0
        )
```
위와 같은 형태이며 `userfile`은 `html`의 `input`태그의 `name`값이다.  
파일을 업로드 했을 때 파일은 서버에 임시 저장되게 되며 그 파일의 이름은 `tmp_name`이 가지고있다. 이 파일을 `move_uploaded_file($FILES['userfile']['tmp_name'],$uploadfile)`의 함수를 이용하여 `$uploadfile`의 경로로 옮겨온다. 이때 첫번째 인자는 `파일이름`이며 두번째 인자는 파일이름을 포함한 파일경로이다.  
`$uploadfile`에서 파일 이름을 `basename`을 이용하여 가져오는 이유는 보안과 관련된 이유로 `basename`을 이용하면 경로의 마지막 부분을 가져온다.
