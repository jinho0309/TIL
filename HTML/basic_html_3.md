## 정보로서의 HTML
### 글꼴 -font(퇴출됨)
```html
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    <font size="3" color="red">Hello</font> world
  </body>
</html>
```
사실 font태그는 어떠한 정보(의미)도 가지고 있지 않음, 단지 꾸미기위한 태그
html에서 디자인과 관련된 코드를 쓰면 중복 사용으로 인한 파일 용량 증가, 가독성 저하, 관리 측면에서의 불편함 등의 이유로 현재는 퇴출된 태그  
**CSS를 통해 디자인을 담당하게 함**
- font
  - size : 1~7
### meta
웹페이지에 표현되진 않지만, 웹 페이지를 잘 설명하기 위한 부가 정보들을 담당
```html
<html>
  <head>
    <meta charset="utf-8"><!--디코딩되는 문자형식-->
    <meta name="description" content="html의 공부">
    <meta name="keywords" content="html,jino,study">
    <meta name ="author" content ="jino">
    <meta http-equiv="refresh" content="30">
  </head>
  <body>
    html을 배우고 있습니다.
  </body>
</html>
```
1. charset
  브라우저에 디코딩되는 문자형식을 지정(utf-8은 한글폰트를 정상 출력시켜줌)
2. name
  - description : 검색결과에 대한 요약에 사용됨
  - keywords : 문서를 설명하는 중요 단어(키워드)들
  - author : 저자
3. http-equiv
  - refresh : content로 지정한 시간(초) 마다 웹페이지를 리프레쉬 시켜줌
### semantic
 HTML5에서는 웹페이지에서 통상 많이 사용하는 구조에 의미를 분명히 부여하기 위해서 의미론적 태그(semantic element)를 새롭게 정의해서 제공.
```html
<html>
  <head>
    <title>HTML - 수업소개</title><!-- 웹 페이지 제목 -->
    <meta charset="utf-8">
  </head>
  <body>
    <header>
      <h1><a href="index.html">HTML</a></h1>
    </header>
    <nav><!-- 문서의 네비게이션 항목 -->
      <ol><!-- 그룹화  -->
        <li><a href="1.html">기술소개</a></li>
        <li><a href="2.html">기본문법</a></li>
        <li><a href="3.html">하이퍼텍스트와 속성</a></li>
        <li><a href="4.html">리스트와 태그의 중첩</a></li>
      </ol>
    </nav>
    <section><!--문서의 구획 정의-->
      <article><!--본문-->
        <h2>우주를 줄게, 상상력을 키워주는 아이방인테리어 </h2>
        쉼터이자 놀이터인 집과 함께 성장하는 아이들안녕하세요~ 소통으로 만들어지는 아름다운 생활공간
        1st Avenue : 퍼스트애비뉴 인테리어입니다. 오늘은 새학기가 다가오니까 아이방인테리어에 대해서
        소개해 볼게요~ 아이방을 꾸밀때 가장 중...
      </article>
      <article>
        <h2>프로파간다 (Propaganda Bistro), 호치민 맛집 </h2>
        호치민 맛 집으로 알음알음 소문난 프로파간다 (Propaganda Bistro)
        미리 여행지 정보를 살펴볼 수 없는 상황인지라 일단 첫째 날 들를 맛
        집만 알아보고 호치민으로 갔었거든요. 호텔 체크인 후 짐 정리를 마치고
        미리 알아둔 유일한 곳 프...
      </article>
    </section>
    <footer>
      <ul>
        <li><a href="privacy.html">개인보호정책</a></li>
        <li><a href="about.html">회사소개</a></li>
      </ul>
    </footer>
  </body>
</html>
```
- article 본문
- aside 광고와 같이 페이지의 내용과는 관계가 적은 내용들
- details 기본적으로 표시되지 화면에 표시되지 않는 정보들을 정의
- figure 삽화나 다이어그램과 같은 부가적인 요소를 정의
- footer 화면의 하단에 위치하는 사이트나 문서의 전체적인 정보를 정의
- header 화면의 상단에 위치하는 사이트나 문서의 전체적인 정보를 정의
- main 문서에서 가장 중심이 되는 컨텐츠를 정의
- mark 참조나 하이라이트 표시를 필요로 하는 문자를 정의
- nav 문서의 네비게이션 항목을 정의
- section 문서의 구획들을 정의
- time 시간을 정의
## 검색엔진 최적화(SEO)
HTML코드를 의미론적 태그로 잘 설명하는 것이 기본
1. title 태그를 이용하여 페이지의 제목 나타내기
  - 페이지의 콘텐츠를 정확하게 설명하는 제목
  - 페이지마다 고유한 title 태그 작성
2. description 메타 태그 활용하기
  한 두개의 문장이나 짧은 단락
3. 페이지의 URL 구조를 개선하기
  - HTML의 이름을 콘텐츠의 내용을 잘 표현하는 제목으로
  - 단순 디렉토리 구조 만들기
  - 특정 문서에 도달하기 위한 한가지 형태의 URL을 제공
    - head태그에 *link rel="canonical" href=""*
    - 301 리다이렉션을 설정
4. 사이트 내에서 이동하기 쉽게 만들기
  - 자연스러운 계층 구조
  - 이동경로를 텍스트를 통해
5. 우수한 품질의 콘텐츠와 서비스 제공
  - 검색 엔진을 위한 것이 아닌 사용자를 위한 콘텐츠 작성
6. 보다나은 앵커 텍스트 작성
  - 링크를 눈에 띄기쉽게 표현하기
7. 이미지 사용의 최적화
  - alt속성 이용
  - 보편적인 이미지 파일 포맷의 사용과 이미지를 위한 특정 디렉토리 설정
8. 제목 태그의 적절한 활용
9. robots.txt를 효과적으로 활용하기
### 페이지랭크
검색엔진이 동일한 주제의 웹페이지들에 대해 순위를 매겨 검색 노출 순서를 조정하는 것. 순위가 높은 웹페이지가 우선 노출되며 트래픽이 더 많이 증가한다.
## 모바일 지원 (viewport)
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
기계적으로 넣어주자.....
- width=device-width : 폭을 각 디바이스의 폭으로
- initial-scale=1.0 : 초기화면을 줌 안한 상태로 맞춘다.
## 외부문서삽입 - iframe
```html
<iframe src="http://opentutorials.org" width="500" height="500"></iframe>
```
**but.** 신뢰할 수 없는 사이트에서 악성코드 같은 것을 포함하고 있다면 삽입된 외부소스에서 악성코드가 실행될 수 있기 때문에 보안에 취약. 이런 문제를 해소하기 위해서 HTML의 최신 버전인 HTML5에서는 샌드박스라는 것을 도입  
- sandbox : 아이프래임으로 삽입된 웹페이지에서 자바스크립트 등이 실행되지 않도록 하는 방법
## 비디오 -video(HTML5)
```html
<video width="400" controls>
  <source src="videos/small.mp4"><!--지원형식이 브라우저 마다 다름-->
  <source src="videos/small.ogb">
  </video>
```
- controls : 비디오를 컨트롤할 수 있도록 만듬
- 웹브라우저간 호환성 문제
웹브라우저마다 지원하는 동영상 포멧이 다르므로 여러가지 형태(확장자)의 동영상을 기술하면 웹브라우저는 자신이 지원하는 기능 중 가장 선호하는 형식의 동영상을 선택해서 화면에 표시한다.
## Can I use
새롭게 도입된 기술은 오래된 웹브라우저에서 동작하지 않음. 결국 얼마나 많은 웹브라우저가 이 기술을 사용할 수 있는가에 따라서 신기술의 도입 여부를 결정해야 한다. [Can I use](https://caniuse.com)는 이런 결정을 할 때 도움을 주는 서비스
## HTML5의 입력양식
### input types
- color
- date
- datetime
- datetime-local
- email
- month
- number
- range
- search
- tel
- time
- url
- week
```html
<form action="form.php">
  <input type="number" min="10" max="15"><br><!-- min : 최소값 , max : 최대값 -->
  <input type="date" name="detev"><br>
  <input type="month" name="monthv"><br>
  <input type="week" name="weekv"><br>
  <input type="time" name="timev"><br>
  <input type="email" name="emailv"><br>
  <input type="search" name="searchv"><br>
  <input type="tel" name="telv"><br>
  <input type="url" name="urlv"><br>
  <input type="range" name="rangev" min="0" max="10">
  <input type="submit">
</from>
```
### HTML5 입력양식의 속성들
```html
<form action="login.php" autocomplete="on">
    <input type="text" name="id" placeholder="id를 입력해주세요." autofocus>
    <input type="password" name="password" autocomplete="off" placeholder="비밀번호를 입력해주세요.">
    <input type="submit">
</form>
```
- autocomplete : 자동완성 on/off
  모든 <input>태그들에 동일하게 적용하려면 상위 태그인 <form>태그에 on으로 적용후필요할 경우 특정 <input>태그에만 off로 설정
- placeholder : 입력창에 디폴트값으로 내용을 표시, 사용자가 직접 입력시 해당 내용은 사라짐.
- autofocus : 특정 <input>태그에 입력해두면 사용자가 페이지에 접속시 해당 태그를 오토포커스 해줌.
### HTML5 입력 값 체크
```html
<form action="register.php">
  <input type="text" name="id" placeholder="아이디를 입력해주세요" required
  pattern="[a-zA-Z].+[0-9]"><!--정규 표현식-->
  <input type="email" name="email" placeholder="이메일 입력"><!--알아서 유효성 검사-->
  <input type="submit">
</form>
```
- required : 사용자가 반드시 정보값을 채워야만 제출이 가능해짐.
- pattern : 사용자가 정보값을 입력할 때 특정 양식을 따르도록 강제하는 속성(정규표현식)
