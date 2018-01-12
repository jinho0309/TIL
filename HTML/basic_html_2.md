## 입력양식 -form
### 텍스트 입력
```html
<form action="">
  <p>text : <input type="text" name="id" value="defaultvalue"></p>
  <p>password : <input type="password" name="pwd" value="defaultvalue"></p>
  <p>textarea : <textarea cols="50" rows="2">default value</textarea></p>
</form>
```
1. text,password
  - name : 서버에 전송하기 위한 고유ID(반드시 필요)
  - value : 기본값
2. textarea : 여러줄 입력 가능(텍스트 박스)
  - cols : 열
  - rows : 행
  - defaultvalue는 태그 사이에 삽입
### 선택(Dropdown List)
```html
<select name="color">
      <option value="red">붉은색</option>
      <option value="black">검은색</option>
      <option value="blue">파란색</option>
</select>
<select name="color2" multiple>
      <option value="red">붉은색</option>
      <option value="black">검은색</option>
      <option value="blue">파란색</option>
</select>
```
- 결과(default)
<select name="color">
        <option value="red">붉은색</option>
        <option value="black">검은색</option>
        <option value="blue">파란색</option>
</select>
1. select
  - multiple : 복수개의 정보를 선택할 수 있게 할 수 있음
  - name : 서버에 보낼 ID값
2. option
  - value : html에서 보는 정보는 태그안의 문자지만 서버에 보내질때는 value값이 보내짐
### 선택(RadioButton,CheckBox)
```html
<p>
    <h1>색상(단일선택)</h1>
    붉은색 : <input type="radio" name="color" value="red">
    검은색 : <input type="radio" name="color" value="black" checked>
    파란색 : <input type="radio" name="color" value="blue">
</p>
<p>
    <h1>사이즈(다중선택)</h1>
    95 : <input type="checkbox" name="size" value="95">
    100 : <input type="checkbox" name="size" value="100" checked>
    105 : <input type="checkbox" name="size" value="105" checked>
</p>
```
- 결과
<p>
    <h1>색상(단일선택)</h1>
    붉은색 : <input type="radio" name="color" value="red">
    검은색 : <input type="radio" name="color" value="black" checked>
    파란색 : <input type="radio" name="color" value="blue">
</p>
<p>
    <h1>사이즈(다중선택)</h1>
    95 : <input type="checkbox" name="size" value="95">
    100 : <input type="checkbox" name="size" value="100" checked>
    105 : <input type="checkbox" name="size" value="105" checked>
</p>
1. radio
  - name : name값이 같아야 여러 라디오버튼 중 한개만 선택가능
  - checked : 초기에 선택되있는 상태로 변경
2. checkbox
  - name : 같은 name을 가진 여러개를 선택 가능(복수의 것을 같은 이름으로 서버에 전송가능)
  - checked
### 버튼
```html
<input type="text">
<input type="submit" value="전송">
<input type="button" value="버튼" onclick="alert('hello world')">
<input type="reset">
```
1. button : javascript와 연계해서 사용성이 높음
  - onclick : 버튼 클릭시 이벤트
2. reset : 입력한 모든 정보가 초기화됨
### 데이터 전송 -hidden
눈에 보이지 않음, 서버로 전송해야 되는데 UI가 필요없거나 몰래 서버로 전송하는 내용을 위해
```html
<input type="text" name="id">
<input type="hidden" name="hide" value="egoing">
<input type="submit">
```
### 컨트롤의 제목 -label
- 특별한 기능이라기 보다는 정보의 이름을 붙여주는 태그(이름표)
- 눈으로 보이는 차이는 없음
```html
<p>
  <label for="id_txt">text :</label>
  <input id="id_txt" type="text" name="id" value="default value"></p>
<p>
  <label for="password">password :</label>
  <input id="password" type="password" name="pwd" value="default value"></p>
<p>
  <label>textarea :
  <textarea cols="50" rows="2">default value</textarea></label>
</p>
<p>
  <label>
     <input type="checkbox" name="color" value="red">붉은색
</label>
</p>
```
- 사용방법
  1. label for="exp" : exp라는 id를 가진 태그의 Label이 됨
  2. ```<label></label>```
### method
서버로 전송하는 방식(GET,POST)
1. GET방식(default) : URL에 보내지는 값이 보여짐(URL을 통해 값 전송)
2. POST방식 : 보내지는 값이 숨겨짐
```html
<form action="http://localhost/method.php" method="post">
            <input type="text" name="id">
            <input type="password" name="pwd">
            <input type="submit">
</form>
```
어떤 방식으로 보낼지는 서버 엔지니어의 선택
### 파일 업로드
서버에서 할일이 더 많음
```html
<form action="http://localhost/upload.php" method="post" enctype="multipart/form-data">
         <input type="file" name="profile">
         <input type="submit">
</form>
```
*method="post" enctype="multipart/form=data"* 를 **반드시** 추가
- enctype : 전송되는 데이터 형식을 설정
  1. application/www-form-urlencoded : 디폴트값이다. 폼데이터는 서버로 전송되기 전에 URL-Encode 된다.
  2. multipart/form-data : 파일이나 이미지를 서버로 전송할 경우 이 방식을 사용한다.
  3. text/plain : 이 형식은 인코딩을 하지 않은 문자 상태로 전송한다.
