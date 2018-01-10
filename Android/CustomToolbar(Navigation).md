# ActionBar에 Navigation 및 Setting 추가
## build.grandle
- support:desgin 추가
```xml
## activity_main.xml
- DrawerLayout으로 변경
```xml

<android.support.v4.widget.DrawerLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/drawer_layout"
    android:orientation="vertical"
    android:background="#fff"
    tools:context="hs8.i_yac.MainActivity"
    >

</android.support.v4.widget.DrawerLayout>
```
DrawerLayout의 id등록 필요
- NavigationView 추가
```xml
<android.support.design.widget.NavigationView
     android:id="@+id/navigation_view"
     android:layout_width="wrap_content"
     android:layout_height="match_parent"
     android:layout_gravity="start"
     app:headerLayout="@layout/drawer_header"
     app:menu="@menu/drawer"/>
```
navigation_view의 id 등록

app:headerLayout <-- navigation의 head부분

app:menu="@menu/drawer" <-- menu폴더에 내가만든 drawer(navigation에 보여지게 될 view)

android:layout_gravity="start" <-- start로 지정하면 시스템 언어 설정에 따라 왼편에서 나오도록 할지, 오른편에서 나오도록 할 지 자동으로 설정

## menu폴더
- res에 menu폴더생성
### drawer.xml
- navigation에 보여질 view를 Custom
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <group >
        <item
            android:id="@+id/item1"
            android:title="item1"
            />
        <item
            android:id="@+id/item2"
            android:title="item2" />
        <item
            android:id="@+id/item3"
            android:title="item3" />
        <item
            android:id="@+id/item4"
            android:title="item4" />

    </group>
            <item
                android:id="@+id/item5"
                android:title="item5" />
</menu>
```
### menu.xml
- setting에 보여질 view를 Custom
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
            <item
                android:id="@+id/setting"
                android:title="setting" />

</menu>
```
## drawer_header.xml(layout)
- navigation의 head부분
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="80dp"
    android:background="#fff"
    android:padding="16dp"
    android:gravity="bottom">
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="메뉴"
        android:textSize="20dp"
        android:textAppearance="@style/TextAppearance.AppCompat.Body1"/>

</LinearLayout>
```
## MainActivity
- Toolbar를 만들고 Navigation등록
```java
Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
toolbar.setNavigationIcon(R.drawable.ic_menu);//toolbar에 navigation추가
setSupportActionBar(toolbar);
```
- Navigation Item의 클릭이벤트
```java
mDrawerLayout = (DrawerLayout)findViewById(R.id.drawer_layout);//activity_main의 DrawerLayout
NavigationView navigationView = (NavigationView)findViewById(R.id.navigation_view);//activity_main의 navigationView
navigationView.setNavigationItemSelectedListener(new NavigationView.OnNavigationItemSelectedListener() {//navigation의 item클릭시 이벤트
            @Override
            public boolean onNavigationItemSelected(@NonNull MenuItem item) {
                mDrawerLayout.closeDrawers();//item 클릭하면 navigation을 닫는다.
                Intent intent;
                int id = item.getItemId();
                switch(id){

                    case R.id.item1 :
                        intent = new Intent(MainActivity.this,item1Activity.class);
                        startActivity(intent);
                        break;
                    case R.id.item2 :
                        intent = new Intent(MainActivity.this,item2Activity.class);
                        startActivity(intent);
                        break;
                    case R.id.item3 :
                        intent = new Intent(MainActivity.this,item3Activity.class);
                        startActivity(intent);
                        break;
                    case R.id.item4:
                        intent = new Intent(MainActivity.this,item4Activity.class);
                        startActivity(intent);
                        break;
                    case R.id.item5:
                        intent = new Intent(MainActivity.this,item5Activity.class);
                        startActivity(intent);
                        break;
                }
                return true;
            }
        });
  }
```
- Toolbar 오른쪽에 Setting메뉴생성
```java
@Override
  public boolean onCreateOptionsMenu(Menu menu) { //오른쪽 옵션을 만들어 줍니다.
      getMenuInflater().inflate(R.menu.menu, menu);//R.menu.menu는 menu폴더의 menu.xml
      return true;
  }
  ```
- Navigation 버튼 및 Setting메뉴의 클릭이벤트
```java
@Override
   public boolean onOptionsItemSelected(MenuItem item) {
       // Handle action bar item clicks here. The action bar will
       // automatically handle clicks on the Home/Up button, so long
       // as you specify a parent activity in AndroidManifest.xml.
       int id = item.getItemId();
       Intent intent;
       switch (id) {
           case android.R.id.home://Navigation 버튼은 R.id.home의 id값을 가짐
               mDrawerLayout.openDrawer(GravityCompat.START);
               break;
           case R.id.setting:
               intent = new Intent(MainActivity.this,settingActivity.class);
               startActivity(intent);
               break;

       }

       return super.onOptionsItemSelected(item);
   }
```
