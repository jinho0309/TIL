# 주요태그
## 단락 -p
```HTML
<p></p><!--간격이 고정되어 있음 -->
```
- 단락의 간격을 더 넓히고 싶을때
1. CSS를 이용하여 변경
2. <br>태그를 여러번
## 줄바꿈 -br
```HTML
<br><!--void element--><!--닫는 태그가 없다-->
```
## 이미지 -img
```HTML
<img src="">
```
- 속성
  1. width : 가로
  2. height : 세로
  3. alt : img가 깨졌을 때 alt의 속성값이 표시(대체제)
  4. title : 마우스를 올려놨을 때
## 표 -table
### 기본
```HTML
<table>

    <thead>
      <tr>
          <td>이름</td>
          <td>성별</td>
          <td>주소</td>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>전진호</td>
        <td>남</td>
        <td>강원</td>
      </tr>
    </tbody>

</table>
```
tr : 행  
td : 열

- 속성
  1. border : 테두리
### 구조
```HTML
<html>
<head><meta charset="utf-8"></head>
<body>
<table border="2">
    <thead>
        <tr>
            <th>이름</th>     <th>성별</th>   <th>주소</th> <th>회비</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>최진혁</td>  <td>남</td>      <td >청주</td> <td>1000</td>
        </tr>
        <tr>
            <td>최유빈</td>  <td>여</td>      <td>청주</td> <td>500</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>합계</td>  <td></td>      <td></td> <td>1500</td>
        </tr>
    </tfoot>
</table>
</body>
</html>
```
thead : 표의 머리  
tbody : 표의 본문  
th : 강조  
tfoot : 표의 가장 아래  
### 병합
```HTML
<html>
<head><meta charset="utf-8"></head>
<body>
<table border="2">
    <thead>
        <tr>
            <th>이름</th>     <th>성별</th>   <th>주소</th> <th>회비</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>최진혁</td>  <td>남</td>      <td rowspan="2">청주</td> <td>1000</td>
        </tr>
        <tr>
            <td>최유빈</td>  <td>여</td>      <td>500</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="3">합계</td>      <td>1500</td>
        </tr>
    </tfoot>

</table>
</body>
</html>
```
rowspan : 행 병합(세로)  
colspan : 열 병합(가로)
## 입력양식 -form
```HTML
<html>
<head>
    <meta charset="utf-8">
</head>
<body>
<form action="http://localhost/login.php">
    <p>아이디 : <input type="text" name="id"></p>
    <p>비밀번호 : <input type="password" name="pwd"></p>
    <p>주소 : <input type="text" name="address"></p>
    <input type="submit">
</form>
</body>
</html>
```
1. form
- action : submit했을 때 실행될 동작(ex : 보내질 서버의 주소)
2. input : 입력
- type : 입력받을 값의 종류, submit은 form의 action을 시작함
- name : 각 input의 고유 값
