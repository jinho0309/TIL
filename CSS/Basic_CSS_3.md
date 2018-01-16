## 레이아웃
### 인라인 vs 블럭레벨
- 화면 전체를 사용하는 태그 ```->``` block element
- 화면의 일부를 차지하는 태그 ```->``` inline level element
```HTML
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title></title>
    <style>
        a,
        h1 {
            border: 1px solid red;
        }

        h1 {
            display: inline
        }

        a {
            display: block
        }

    </style>
</head>

<body>
    <h1>Hello world</h1>
    <!--화면 전체사용 (block)-->
    안녕하세요. <a href="http://naver.com">생활코딩입니다.</a>
    <!--자기크기만큼(inline)-->
</body>

</html>
```
*display를 사용하면 변경할 수 있음.*
### 박스모델
```HTML
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title></title>
    <style>
        a,p{
            border: 10px solid red;
            padding : 20px;
            margin : 60px;
            width:120px;/*inline에서는 이 값을 width와 height 무시 */

        }
    </style>
</head>

<body>
    <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Non, minima.
    </p>
    <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Sequi, numquam!
    </p>
    안녕하세요.<a href="https://a.com">전진호</a>입니다.
</body>

</html>
```
박스모델 : 태그의 부피와 태그간의 여백등을 결정.
- 마진 : 태그와 태그 사이의 여백.
- 패딩 : 태그와 태그를 감싸는 테두리 사이의 여백
*인라인 엘리먼트는 width, height 값 무시*
### Box-sizing
box-sizing은 박스의 크기를 화면에 표시하는 방식을 변경하는 속성입니다. width와 height는 엘리먼트의 컨텐츠의 크기를 지정합니다. 따라서 테두리가 있는 경우에는 테두리의 두께로 인해서 원하는 크기를 찾기가 어렵습니다. box-sizing 속성을 border-box로 지정하면  테두리를 포함한 크기를 지정할 수 있기 때문에 예측하기가 더 쉽습니다. 최근엔 모든 엘리먼트에 이 값을 지정하는 경우가 늘고 있습니다.
```HTML
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title></title>
    <style>
        *{
              box-sizing:border-box;/*기본값은 content-gox*/
        }
        div{
            margin:10px;
            width:150px;/*내용의 컨텐트 부분의 길이*/

        }
        #small{
            border:10px solid black;

        }
        #large{
            border:30px solid black;
        }
    </style>
</head>
<body>
    <div id="small">Hello</div>
    <div id="large">Hello</div>
</body>
</html>
```
### 마진겹침 현상
마진겹침(margin-collapsing) 현상은 상하 마진값이 어떤 상황에서 사라지는 현상을 의미합니다.
마진겹침현상 세 가지
1. 위,아래 엘리먼트들의 마진이 겹칠시 둘 중 마진이 큰게 둘 사이의 마진이 된다.
2. 위,아래 엘리먼트들의 마진이 겹치고, 한 엘리먼트의 시각적 요소가 없어지면, 시각적 요소가 없어진 엘리먼트 마진의 top-bottom과/ left-right은 큰값으로 합쳐져 계산된다.
3. 부모,자식 엘리먼트 사이에서 부모의 시각적 요소가 없어지면 부모,자식 마진 중 마진이 큰 쪽이 자식 마진처럼 사용된다.
### 포지션
- static : 이동없이 생성된 위치를 고수한다.(기본값)
- relative : 현재 element위치에서 상대적으로 이동시키는 것.
- absolute :  html태그 위치에서 부터 절대값으로 위치를 지정한다. 단, 부모 element에서 position속성의 값이 static이 아니라면 그 부모 element의 position 위치에서 부터의 절대값 위치로 지정된다.
- fixed : 스크롤과 상관없이 자신의 위치를 고수한다.
absolute와 같이 부모element와 독립되기때문에 witdth와 height값을 다시 입력해주어야한다.
### FLEX
CSS의 flex는 엘리먼트들의 크기나 위치를 쉽게 잡아주는 도구. flex를 이용하면 레이아웃을 매우 효과적으로 표현할 수 있다. **item과 그것을 담을 container가 필요.**
1. 컨테이너에 속성에 display:flex;를 하는 것부터 시작
2. 여러 속성들
- flex-basis : 크기 지정
- flex-grow : 아이템들이 컨테이너를 나눠갖는 비율 결정, flex-shrink : 화면이 작아질 때 줄어드는 비율 결정
- flex-diretion : 컨테이너 방향 결정(row, column)
- flex-wrap : 아이템 크기가 컨테이너 크기보다 크다면 줄바꿈
- align-items : 수직 관련 정렬, justify-items : 수평 관련 정렬,
- align-content : 아이템을 그룹핑해서 정렬
- align-self : 특정 아이템만 크기 다르게
- flex : flex-grow + shrink + basis
- order : 아이템의 순서 바꿈
### media query
media query는 화면의 종류와 크기에 따라서 디자인을 달리 줄 수 있는 CSS의 기능입니다. 특히 최근의 트랜드인 반응형 디자인의 핵심 기술이라고 할 수 있습니다.
- ```@media(max or min-width:...px) {~~~} : max(이하) ...px까지, 혹은 min(이상)...px부터는 ~~~을 적용한다.```
- cascading 주위 : css에서 **나중에 나온것이 먼저 나온 것을 덮어버리기 때문에** 우선순위가 낮은게 먼저 쓰고 높은걸 아래로 써야된다.
### float
Float는 편집 디자인에서 이미지를 삽화로 삽입할 때 사용하는 기법입니다. 또한 레이아웃을 잡을 때도 사용하는 기능이기 때문에 꽤 중요합니다.
```html
   <style>
       img{
           width:300px;
           float:left;
           margin:20px;
       }
       p{
           border:1px solid gray;
       }
    </style>
<img src="img.jpg" alt="">
<p>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Sapiente illo placeat neque cupiditate eius provident saepe dolor hic officiis
</p>
<p style="clear:both;">
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consectetur amet provident similique at assumenda accusantium explicabo autem, culpa, exercitationem tempore, fuga hic eos! Illum magnam minus harum doloremque modi, nobis, itaque enim non
</p>

```
- float : left(right)을 주면 그림의 오른쪽(왼쪽)에 문장이 자연스럽게 들어옴..
- clear : float한 값과 똑같이 주면 float를 없앤다는 의미, both쓰면 알아서.
### 다단(multi column)
```html
<style>
        .column{
            text-align: justify;
            column-count: 4;
            column-width: 200px;
            column-gap:50px;
            column-rule-style : solid;
            column-rule-width: 1px;
            column-rule-color: tomato;
        }
        h1{
            column-span:all;
        }
    </style>
```
- column-count : 다단 갯수
- column-width : 다단 한개의 넓이
- column-gap : 다단과 다단사이의 넓이
- column-rule-style : 다단을 나누는 선
- column-rule-style : 선의 두께
- column-rule-color : 선의 색깔
- column-span : 다단 병합
## 그래픽
### 배경(background)
- background-color : red
- background-image : url("bg.png")
- background-repeat : repeat, no-repeat, repeat-x, repeat-y
- background-attachment : scroll, fixed
- background-position : left top  or x% y% or x y
- background-size : 100px 100px or cover(꽉 채우기) or contain
```html
<style>
        div{

            border:5px solid gray;
/*            background-color: tomato;*/
/*            background-image:url('img.jpg');*/
/*            background-repeat:no-repeat;*/
/*            background-attachment: fixed;*/
/*            background-position: center;*/
            background: tomato url('img.jpg') no-repeat fixed center;
            background-size: 300px 300px;
        }
</style>
```
### 필터(filter)
필터는 이미지에 다양한 효과를 추가하는 방법
```html
<style>
    img{
        transition: all 0.2s;
    }
    img:hover{
        -webkit-filter: grayscale(100%) blur(3px);
        -o-filter:grayscale(0%) blur(3px);
        filter:grayscale(0%) blur(3px);

}
    h1{
    -webkit-filter: grayscale(100%);
        -o-filter:grayscale(0%);
        filter:grayscale(0%);
        filter:blur(3px);
    }
</style>
```
- 참고 : [CSS filter playground](http://bennettfeely.com/filters/)
- 참고 : [CodePen](https://codepen.io/)
### 혼합(blend)
블랜드는 이미지와 이미지를 혼합해서 새로운 이미지를 만들어내는 기법
- background-blend-mod : 배경 그래픽 간이 블랜드 효과
```html
<style>
    .blend {
        height: 400px;
        border: 5px solid;
        background-color: red;
        background-image: url('img.jpg');
        background-blend-mode:screen;
        background-size : cover;
    }
</style>
```
- mix-blend-mode : 컨텐트와 배경 사이의 블랜드 효과
```html
<style>
     body{

         background-image: url('img.jpg');

     }
     .blend{
         font-size:2rem;
         font-weight: bold;
         color:blue;
         mix-blend-mode: darken;
     }
 </style>
```
- 참고 : [CodePen](https://codepen.io/search/pens?q=blend&limit=all&type=type-pens)
### 변형(transform)
transform은 엘리먼트의 크기, 위치, 모양을 변경하는 속성
- 참고 : [hover.css](http://ianlunn.github.io/Hover/)
- 참고 : [CSShake](http://elrumordelaluz.github.io/csshake/#1)
- 참고 : [magic animation](http://www.minimamente.com/example/magic_animations/)
### SVG
svg는 백터(vector) 이미지를 표현하기 위한 포맷으로 w3c에서 만든 백터 이미지 표준입니다. SVG 자체는 CSS가 아닙니다만 CSS를 이용해서 다양한 효과를 줄 때 SVG를 활용하는 경우가 많음.
```html
<!doctype html>
<html>
<body>
  <h1>file</h1>
  <img src="svg_sample.svg" alt="">
  <h1>htmls</h1>
  <svg width="210" height="210">
  <rect x="5" y="5" width="200" height="200" style="fill:red; stroke:black; stroke-width:10px"></rect>
</svg>
</body>
</html>

```
##### svg_sample.svg
```xml
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="210" height="210">
  <rect x="5" y="5" width="200" height="200" style="fill:red; stroke:black; stroke-width:10px"></rect>
</svg>

```
- 참고 : [svg codepen](http://codepen.io/search/pens?q=svg&limit=all&type=type-pens)
