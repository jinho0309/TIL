# CSS
HTML에서 디자인적 요소가 필요해서 <font>태그와 같은 디자인 담당 태그를 만들었지만 웹이 거대해지면서 난잡해지는 문제가 발생.  
그래서 웹개발자들은 HTML을 정보를 담는 그릇으로서 전념하게 하고 디자인적 요소는 따로 빼내서 하나의 새로운 언어를 만들게 되는데 그것이 **CSS**  
 - CSS를 만들면서 생기는 *장점* : **정보와 디자인의 분리**, HTML의 정보로서의 가치가 올라간다, 중복의 제거
## HTML과 CSS가 만나는법
1. HTML태그내 스타일 지정(Inline Styles)
```HTML
<h1 style="color:red">Hello World</h1><!-- 인라인 -->
```
2. 내부 스타일 시트(Internal Style Sheet)
```html
<head>
  <style>
    h2{
      color:blue
    }
  </style>
</head>
```
3. 외부 스타일 시트(External Style Sheet)
```HTML
<head>
 <link href="파일이름.css" type="text/css" rel="stylesheet"/>
 </head>
 ```
## 선택자
어떤 태그를 디자인하기 위해서는 디자인하려는 태그를
1. 선택하고 (선택자)
2. 선택한 대상에게 효과를 줘야 한다. (선언)
### 선택자의 종류
- 태그 선택자
```HTML
<style>
  li{/*태그 선택자 */
    color:red;
    text-decoration: underline;
  }
</style>
```
- 클래스 선택자
```html
<style>
  .deactive{/*클래스 선택자*/
    text-decoration:line-through;
  }
</style>
```
- 아이디 선택자
```html
<style>
  #select{/*아이디 선택자 */
    font-size:100px;
  }
</style>
```
id 선택자는 같은 주민번호를 가진 사람이 없듯이 **똑같은 id선택자를 여러번 사용하면안된다(단 한번만 사용)**, 클래스 선택자는 grouping의 개념으로 **class로 그룹핑하면 여러번 사용가능**
