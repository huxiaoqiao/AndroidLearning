### Android官方Demo阅读笔记（一）

####  [Action Bar Compat - Basic](https://github.com/googlesamples/android-ActionBarCompat-Basic/)

* ActionBar上创建Menu

```java
 @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate our menu from the resources by using the menu inflater.
        getMenuInflater().inflate(R.menu.main, menu);

        // It is also possible add items here. Use a generated id from
        // resources (ids.xml) to ensure that all menu ids are distinct.
        MenuItem locationItem = menu.add(0, R.id.menu_location, 0, R.string.menu_location);
        locationItem.setIcon(R.drawable.ic_action_location);

        // Need to use MenuItemCompat methods to call any action item related methods
        MenuItemCompat.setShowAsAction(locationItem, MenuItem.SHOW_AS_ACTION_IF_ROOM);

        return true;
    }
```

* Item点击事件

```java
@Override
    public boolean onOptionsItemSelected(MenuItem item) {
        switch (item.getItemId()) {
            case R.id.menu_refresh:
                // Here we might start a background refresh task
                return true;

            case R.id.menu_location:
                // Here we might call LocationManager.requestLocationUpdates()
                return true;

            case R.id.menu_settings:
                // Here we would open up our settings activity
                return true;
        }

        return super.onOptionsItemSelected(item);
    }
```

* 使用xml设置item,(在res/menu文件中)

  ```xml
  <!--
      As we're using ActionBarCompat, any action item attributes come from ActionBarCompat's XML
      namespace instead of the android namespace. Here we've added a new support namespace added to
      the menu element allowing us to use the 'showAsAction' attribute in a backwards compatible way.
      Any other action item attributes used should be referenced from this namespace too
      (actionProviderClass, actionViewClass, actionLayout).
  -->
  <menu xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:support="http://schemas.android.com/apk/res-auto" >

      <!--
          Here we create an item, setting support:showAsAction to display the item as an action if
          there's room on the compatible Action Bar.
      -->
      <item
          android:id="@+id/menu_refresh"
          android:icon="@drawable/ic_action_refresh"
          android:title="@string/menu_refresh"
          support:showAsAction="ifRoom"/>

      <!-- Location item is added in onCreateOptionsMenu() -->

      <!--
          Here we set the settings item to always be in the overflow menu, by setting
          support:showAsAction to never, so it is never displayed as an action item on the compatible
          Action Bar.
      -->
      <item
          android:id="@+id/menu_settings"
          android:icon="@drawable/ic_action_settings"
          android:title="@string/menu_settings"
          support:showAsAction="never"/>

  </menu>
  ```

  ​

  ​



