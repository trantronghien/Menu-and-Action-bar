# Menu-and-Action-bar

##OverView về Action bar
![actionbar](https://cloud.githubusercontent.com/assets/13708331/17023531/f7098312-4f7d-11e6-9af3-096c2ce15c7d.png)

### Dạng 1 Menu Group

![menu_group](https://cloud.githubusercontent.com/assets/13708331/17023555/12ce519a-4f7e-11e6-822b-9656633bfefc.png)
```
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <!-- với checkableBehavior có những thuộc tính -single => dưới dạng radio button và none-->
    <group
        android:checkableBehavior="all"
        android:menuCategory="secondary"
        >
        <item
        android:id="@+id/menu_item_one"
        android:orderInCategory="1"
        android:showAsAction="never"
        android:title="one" />
        <item
            android:id="@+id/menu_item_two"
            android:orderInCategory="2"
            app:showAsAction="always"
            android:icon="@drawable/menu_item_icon"

            android:title="two" />
        <item
            android:id="@+id/menu_menu_item_three"
            android:orderInCategory="3"
            android:showAsAction="never"
            android:title="three" />
    </group>

    <!--  app:showAsAction="never" ,  android:showAsAction="never" cho phép hiện thi ở action bar -->
    <item
        android:id="@+id/help_info_menu_item"
        android:icon="@android:drawable/ic_menu_help"
        android:menuCategory="secondary"
        app:showAsAction="never"
        android:title="four"
        android:alphabeticShortcut="alphabeticShortcut four" />

    <item
        android:id="@+id/settings"
        android:title="five"
        android:menuCategory="secondary"
        app:showAsAction="never"
        android:alphabeticShortcut="alphabeticShortcut five" />
    <!-- Available if the account specifies a help url -->

</menu>
```
> JAVA CODE
``` 
     // khởi tao giao diện cho menu
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.menu_radiobutton , menu);
        return true;
    }
    // bắt sự kiện cho item trong menu
    @Override
    public boolean onOptionsItemSelected(MenuItem item) {

        switch (item.getItemId()){
            case R.id.menu_item_one:
                if(item.isCheckable())   // kiểm tra check và set check
                    item.setCheckable(true);
                else
                    item.setCheckable(false);
                // set mùa backgroup cho actionbar
                getActionBar().setBackgroundDrawable(new ColorDrawable(Color.parseColor("#f44336")));
                Toast.makeText(MainActivity.this, "Item one", Toast.LENGTH_SHORT).show();
                return true;
            case R.id.menu_item_two:
                if(item.isCheckable()){
                    item.setCheckable(true);
                }else{
                    item.setCheckable(false);
                }
                getActionBar().setBackgroundDrawable(new ColorDrawable(Color.parseColor("#54dc10")));
                Toast.makeText(MainActivity.this, "Item two", Toast.LENGTH_SHORT).show();
                return true;
            case R.id.menu_menu_item_three:
                if(item.isCheckable()){
                    item.setCheckable(true);
                }else{
                    item.setCheckable(false);
                }
                getActionBar().setBackgroundDrawable(new ColorDrawable(Color.parseColor("#1c2ef2")));
                Toast.makeText(MainActivity.this, "Item three", Toast.LENGTH_SHORT).show();
                return true;
            default:
                return super.onOptionsItemSelected(item);
        }

    }
    
    
```
