#Custom Toolbar
##styles.xml
-theme변경
'''xml
<style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
'''
-item추가
'''xml
<item name="windowActionBar">false</item>  
<item name="windowNoTitle">true</item>  
'''
##activity_main.xml
-Toolbar추가
'''xml
<android.support.v7.widget.Toolbar  
android:layout_width="match_parent"  
android:layout_height="?attr/actionBarSize"  
android:background="#000"  
android:id="@+id/toolbar"  
android:gravity="center">  
<TextView  
android:layout_width="wrap_content"  
android:layout_height="wrap_content"  
android:text="@string/title"  
android:textColor="#fff"  
/>  
</android.support.v7.widget.Toolbar>  
'''
?attr 지정자를 사용하는 속성 값은 현재 테마에 지정된 값을 사용하라는 의미
##MainActivity.java
'''java
toolbar=(Toolbar)findViewById(R.id.toolbar);  
setSupportActionBar(toolbar);  
'''
setSupportActionBar() 메서드는 인자로 받은 툴바를 액티비티의 액션바로 대체하는 역할
 기본으로 제공되는 액션바 외에 별도로 툴바를 사용하고 싶다면 이 메서드를 호출하지 않고 툴바만 단독으로 사용하는 것도 가능
