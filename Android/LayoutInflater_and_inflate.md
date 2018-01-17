# Inflate란?
안드로이드에서 inflate를 사용하면 xml에 씌어져 있는 view의 정의를 실제 view 객체로 만드는 역할을 한다.  
쉽게설명하면 건물의 설계도(xml)을 그리고 inflate(부풀리다)하면 실제 건물(view)이 나오는 것....
## 기본적인 사용 패턴
1. inflater얻어오기
```java
//1
LayoutInflater inflater=(LayoutInflater)getSystemService(Context.LAYOUT_INFLATER_SERVICE);
//2
LayoutInflater inflater =getLayoutInflater();
//3
LayoutInflater inflater=LayoutInflater.from(this);
```
2. 다음은 xml 이 필요. 이 때 xml 의 root  view 의 type이 무엇인지 알아야 한다. 예를 들어 xml 파일 이름이 example_inflate.xml 이고, root가 LinearLayout 이라면..
```java
LinearLayout linearLayout =(LinearLayout)inflater.inflate(R.layout.example_inflate,null);
```
3. view를 화면에 그린다
```java
setContentView(linearLayout);
```
- 종합
```java
LayoutInflater inflater =getLayoutInflater();
LinearLayout linearLayout = (LinearLayout) inflater.inflate( R.layout.example_inflate, null );
setContentView( linearLayout );  
```
- inflate API
```java
View inflate( int resource, ViewGroup root )
View inflate( XmlPullParser parser, ViewGroup root )
View inflate( XMLPullParser parser, ViewGroup root, boolean attachToRoot )
View inflate( int resource, ViewGroup root, boolean attachToRoot )
```
- resource : view를 만들고 싶은 레이아웃 파일의 id
- root : attachToRoot가 true일경우 생성되는 View가 추가될 부모 뷰, attachToRoot가 false일 경우 LayoutParams값을 설정해주기 위한 상위 뷰, null로 설정할경우 android:layout_xxxxx값들이 무시됨.
- attachToRoot : true일 경우 생성되는 뷰를 root의 자식으로 만든다, flase일 경우 root는 생성되는 View의 LayoutParam을 생성하는데만 사용
