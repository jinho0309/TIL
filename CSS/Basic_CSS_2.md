### 부모 자식 선택자
```HTML
<style>
  ul li{/*-- ul 밑에 있는 li모두-->*/
    color : red;
  }
  #lecture>li{/*lecture바로 밑에 있는 li만*/
    border : 1px solid red;
    color : blue;
  }
  ul,ol{/*ul,ol*/
    background-color: powderblue;
  }
</style>
```
1. 조상 자손 선택자
```html
<style>
  ul li{
    color:red
  }
</style>
```
ul밑에 있는 모든 li태그를 선택
2. 부모 자식 선택자
```html
<style>
  #lecture>li{
    color:red
  }
</style>
```
lecture 바로 밑에 있는 li만을 선택
3. 여러 개 선택할 때
```html
<style>
  ul,ol{
    color:red
  }
</style>
```
<<<<<<< HEAD
### 가상 클래스 선택자
가상(pseudo) 클래스 선택자는 클래스 선택자는 아니지만 엘리먼트들의 상태에 따라서 마치 클래스 선택자처럼 여러 엘리먼트를 선택할 수 있다는 점에서 붙은 이름
- link : 방문한 적이 없는 링크
- visited : 방문한 적이 있는 링크
- hover : 마우스를 롤오버 했을 때
- active : 마우스를 클릭했을 때
```HTML
<style>
a:link{/*방문X*/
  color:black;
}
a:visited{/*방문O*,보안상의 이유로 속성이 제한적*/
  color:red;
}
a:hover{/*마우수를 롤오버 했을 때*/
  color:yellow;
}
a:active{/*마우스를 클릭하고 있을 때*/
  color:green;
}
input:focus{/*포커스 될때 색깔, 가장 뒤에 놓는게 조음*/
  background-color: red;
}
/*위에 있는 것이 우선순위가 높음(먼저 적용) active->hover가 실행되면 active를 hover가 덮음*/
</style>
```
*위에 있는 것이 우선순위가 높음(먼저 적용) active->hover가 실행되면 active를 hover가 덮음* **위의 선택자는 순서대로 지정하는 것이 좋다.**
### 중요한 속성들
CSS의 효과 다른 말로 속성(property)는 약 250개 정도.[속성에 대한 통계](https://developer.microsoft.com/en-us/microsoft-edge/platform/usage/)
## 타이포그래피
### font-size
- px : 모니터 상의 화소 하나의 크기에 대응되는 단위. 고정된 값이기 때문에 이해하기 쉽지만, 사용자가 글꼴의 크기를 조정할 수 없기 때문에 가급적 사용을 하지 않는 것이 좋음.
- em : 부모 태그의 영향을 받는 상대적인 크기. 부모의 크기에 영향을 받기 때문에 파악하기가 어렵다. rem이 등장하면서 이 단위 역시 사용이 권장되지 않음.
- **rem** : html 태그에 적용된 font-size의 영향을 받음. html 태그의 폰트 크기에 따라서 상대적으로 크기가 결정되기 때문에 이해하기 쉬움. 가장 바람직한 단위.
```html
<style>
#px{
  font-size:16px;
}
#rem{
  font-size:1rem;
}
</style>
```
### color
- color name
- hex
- rgb
컬러의 다양한 종류는 [W3schools](http://www.w3schools.com/css/css_colors.asp)참고
### text-align
- left
- right
- center
- justify : 왼쪽과 오른쪽이 공평하게
### font-family
font-family는 서체를 지정하는 속성.
- serif(장식이 있는)
- sans-serif(장식이 없는)
- cursive(흘림)
- fantasy
- monospace(고정폭)
```html
<style>
  p{
      font-family:arial, verdana, "Helvetica Nenu";/*앞에 있는 것부터 되는 거*/
  }
</style>
```
### font-weight
폰트의 두께를 나타냄
- bold
### line-height
행과 행 사이의 간격을 지정. 기본 값은 normal로 수치로는 1.2에 해당. 값이 1.2라면 현재 엘리먼트 폰트 크기의 1.2배만큼 간격을 준다는 의미  
*px로 고정할 수 있긴함*
### font
폰트와 관련된 여러 속성을 축약형으로 표현하는 속성. 형식은 아래와 같다. 순서를 지켜서 기술. 이 중에서 font-size와 font-family는 필수로 포함되어야 한다.
font: font-style font-variant font-weight **font-size** /line-height **font-family** |caption|icon|menu|message-box|small-caption|status-bar|initial|inherit;
```HTML
<style>
  #type1{
    font-size:5rem;
    font-family: arial, verdana, "Helvetica Neue", serif;
    font-weight: bold;
    line-height: 2;
  }
  #type2{
    font:bold 5rem/2 arial, verdana, "Helvetica Neue", serif;
  }
</style>
```
- [폰트랭킹](http://www.fontreach.com/#top)
- [국내폰트](http://software.naver.com/software/fontList.nhn?categoryId=I0000000#brandId=)
### 웹폰트
웹폰트는 사용자가 가지고 있지 않은 폰트를 웹페이지에서 사용할 수 있는 방법. 폰트를 서버에서 다운로드하는 방식이라고 할 수 있다.  
[구글폰트](https://fonts.google.com/?authuser=1)  
## 조화
HTML는 중첩된 구조를 가지고 있다. 그렇기 때문에 하나의 엘리먼트는 다양한 요소의 영향을 받게 됨. 그렇기 때문에 여러 효과가 엘리먼트를 두고 대치하고 있을 때 브라우저는 어떤 효과의 손을 들어줘야 하는가에 대한 결정을 해야 합니다. 이를 위한 여러 규칙들이 있습니다. 그 규칙을 이해하지 못하면 CSS 디자인이 다소 혼란스럽게 될 것.
### 상속
상속은 부모 엘리먼트의 속성을 자식 엘리먼트가 물려받는 것을 의미. 상속은 CSS에서 생산성을 높이기 위한 중요한 기능.
```HTML
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title></title>
  <style>
  li{color:blue}
  /*h1{color:blue}*/
  html{color:red}/*html 밑의 모든 color:red가됨 ->상속*/
  body{border:1px solid red;}/*border는 상속X*/
  </style>
</head>
<body>
  <h1>수업내용</h1>
  <ul>
    <li>html</li>
    <li>css</li>
    <li>javascript</li>
  </ul>
</body>
</html>
```
- [상속을 하는 속성과 하지 않는 속성](https://www.w3.org/TR/CSS21/propidx.html)
### 케스케이딩
CSS : **Cascading** Style Sheet  
- 우선순위 : 웹브라우저 ```<``` 사용자 ```<``` 저자
- CSS우선순위의 순서 : 태그선택자 ```<``` class선택자 ```<``` id선택자 ```<``` style속성
- CSS우선순위의 기준 : 포괄적인 규칙, 일반적인 것 ```<```구체적이면서 명시적인 규칙
- !important : 모든 것을 무시하고 우선순위가 가장 높아진다.
## Stylish
stylish는 웹사이트의 디자인을 사용자 마음대로 수정할 수 있는 기능. 이 기능을 이용해서 주어진데로 웹페이지를 소비하는 것이 아니라 자신의 취향을 반영할 수 있음. 또 다른 사람이 만든 디자인을 적용해서 간편하게 사이트의 디자인을 변경할 수도 있음.  
[Stylish](https://userstyles.org/)  
tip. 광고 많은 사이트의 광고도 사라지게 할 수 있다.
=======
>>>>>>> 6be0f432287eb348255a6c5ea65b2a28f1173da2
