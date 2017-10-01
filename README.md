<p align="center">
  <img src="https://github.com/ray00178/RayZhangAlbum/blob/master/RZAlbum_Logo.png" alt="RZAlbum" width="450" height="450" />
</p>

The RZAlbum for android to select the photo library. And usage：<br/>
* Support Single choice、Multiple choice、Preview、Folder switch and take pictures.  
* For __6.0 or later__, The permissions have been handled very well，So don't worry about their own.
* According to your project color, Setting ur StatusBarColor、ToolBarColor.
* According to your preferences / needs, Show the number of fields and select the number of restrictions.
* In Activity or Frangment, Can support the use.
* For __Android7.0 or later, the camera function through the FileProvider do adaptation processing.__<br/>

Screenshots <br/><br/>
![](https://github.com/ray00178/RayZhangAlbum/blob/master/screenshots.jpg)
Gradle
====
```java
compile 'com.rayzhang.android:rzalbum:1.6.0'
```
Maven
====
```java
<dependency>
  <groupId>com.rayzhang.android</groupId>
  <artifactId>rzalbum</artifactId>
  <version>1.6.0</version>
  <type>pom</type>
</dependency>
```
Usage
====
  1.Androidmanifest.xml, Add the following code.
  ```xml
  <!-- android:theme = Set according to your style
  <style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">
      <item name="colorPrimary">@color/colorPrimary</item>
      <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
      <item name="colorAccent">@color/colorAccent</item>
  </style>

  <style name="AppNoActionBar" parent="AppTheme">
      <item name="windowActionBar">false</item>
      <item name="windowNoTitle">true</item>
  </style> -->
  <activity
     android:name="com.rayzhang.android.rzalbum.RZAlbumActivity"
      android:configChanges="orientation|keyboardHidden|screenSize"
     android:screenOrientation="portrait"
      android:theme="@style/AppNoActionBar"
      android:windowSoftInputMode="stateAlwaysHidden|stateHidden"/>
  ```
  2.Androidmanifest.xml, Add the following permissions.
  ```xml
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
  ```
  3.Use RZAlbum. There are many ways to call.
  ```java
  /**
    * @param ofAppName             : (required)
    * @param setLimitCount         : (choose)   (default:5)     
    * @param setSpanCount          : (choose)   (default:3) 
    * @param setStatusBarColor     : (choose)   (default:#ff512da8)
    * @param setToolBarColor       : (choose)   (default:#ff673ab7)
    * @param setToolBarTitle       : (choose)   (default:RZAlbum)
    * @param setPickColor          : (choose)   (default:#ffffc107)
    * @param setPreviewOrientation : (choose)   (default:ORIENTATION_AUTO)
    * @param setDialogIcon         : (choose)
    * @param showCamera            : (choose)   (default:true)
    * @param start                 : (required)
    */
    RZAlbum.ofAppName("RZAlbum")
            .start(this, REQUEST_RZALBUM);
    /**
      * Or Like this
      */
    RZAlbum.ofAppName("RZAlbum")
            .setLimitCount(2)
            .setSpanCount(3)
            .setStatusBarColor(Color.parseColor("#AD1457"))
            .setToolBarColor(Color.parseColor("#D81B60"))
            .setToolBarTitle("Album")
            .setPickColor(Color.argb(255, 153, 51, 255))
            .setDialogIcon(R.drawable.ic_bird_shape_30_3dp)
            .setPreviewOrientation(RZAlbum.ORIENTATION_PORTRATI)
            .showCamera(false)
            .start(this, REQUEST_RZALBUM);
  ```
  4.Override Activity's/Fragment's onActivityResult method.
  ```java
  @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if (resultCode == RESULT_OK) {
            switch (requestCode) {
                case RZALBUM_REQUESTCODE:
                    List<String> paths = RZAlbum.parseResult(data);
                    Log.d("RZAlbum", "GetPath:" + paths);
                    break;
            }
        }
    }
  ```
  5.If you want to customize the Dialog title, description, and button name, please overwrite the following names in strings.xml.
  ```xml
  <string name="rz_album_dia_read_description">(Enter something that u want)</string>
  <string name="rz_album_dia_read_message">(Enter something that u want)</string>
  <string name="rz_album_dia_camera_description">(Enter something that u want)</string>
  <string name="rz_album_dia_camera_message">(Enter something that u want)</string>
  <string name="rz_album_dia_ok">(Enter something that u want)</string>
  <string name="rz_album_dia_cancel">(Enter something that u want)</string>
  ```
Notice
====
  Due to support Material Design style and handle the image cache, So the library references the following categories.
  ```xml
  compile 'com.android.support:design:25.3.1'
  compile 'com.android.support:recyclerview-v7:25.3.1'
  // Glide
  compile 'com.github.bumptech.glide:glide:3.7.0'
  ```
License
====
  ```
MIT License

Copyright (c) [2016] [RZAlbum]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
  ```
Chinese description
====
[中文說明](https://github.com/ray00178/RayZhangAlbum/blob/master/README_zh.md)
