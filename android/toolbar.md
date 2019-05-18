# Android toolbar

## 添加简单toolbar

### 设置App主题为NoActionBar

```xml
<resources>

    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.MaterialComponents.Light.NoActionBar">
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
        <item name="colorAccent">@color/colorAccent</item>
    </style>
</resources>

```

### 新建xml文件并添加toolbar

```xml
<?xml version="1.0" encoding="utf-8"?>

<androidx.appcompat.widget.Toolbar
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_marginTop="30dp" />

```

### 在其他xml文件中引用

```xml
<include
        layout="@layout/toolbar"
        android:id="@+id/info_toolbar" />
```

注：注意添加id，后续将会用到

### 在activity中配置toolbar

```java
Toolbar toolbar;
toolbar = findViewById(R.id.info_toolbar);
setSupportActionBar(toolbar);
```

## 自定义toolbar名称

```java
toolbar.setTitle("我的信息");
```

注：需在setSupportActionBar前使用。

## 添加返回

### 在setSupportActionBar后

```java
getSupportActionBar().setDisplayHomeAsUpEnabled(true);
getSupportActionBar().setHomeButtonEnabled(true);
```

### 在onOptionsItemSelected中添加事件

```java
if (item.getItemId() == android.R.id.home) {
    Log.d(TAG, "onOptionsItemSelected: back");
    finish();
}
```

