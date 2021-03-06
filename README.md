<p>
  <a href="https://developer.android.com/reference/android/os/Build.VERSION_CODES.html#ICE_CREAM_SANDWICH"><img src="https://img.shields.io/badge/API-14%2B-blue.svg?style=flat" alt="API" /></a>
  <a href="javascript:void(0);"><img src="https://img.shields.io/badge/Version-v1.2-brightgreen.svg" alt="Library version" /></a>
  <a href="http://www.methodscount.com/?lib=com.classic.common%3Amultiple-status-view%3A1.2"><img src="https://img.shields.io/badge/Methods count-28-e91e63.svg"/></a>
  <a href="http://www.methodscount.com/?lib=com.classic.common%3Amultiple-status-view%3A1.2"><img src="https://img.shields.io/badge/Size-7 KB-e91e63.svg"/></a>
  <a href="LICENSE.txt"><img src="https://img.shields.io/npm/l/express.svg?maxAge=2592000" alt="License" /></a>
</p>

一个支持多种状态的自定义View,可以方便的切换到：
- 加载中视图
- 错误视图
- 空数据视图
- 网络异常视图
- 内容视图

[apk下载](https://github.com/qyxxjd/MultipleStatusView/blob/master/apk/MultipleStatusView.apk?raw=true)

![](https://github.com/qyxxjd/MultipleStatusView/blob/master/screenshots/demo.gif)

##使用
```gradle
dependencies {
    compile 'com.classic.common:multiple-status-view:1.2'
}
```

##感谢
[LoadingLayout @大头鬼](https://github.com/lzyzsd/LoadingLayout)

##示例
```xml
<com.classic.common.MultipleStatusView
    android:id="@+id/main_multiplestatusview"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:loadingView="@layout/custom_loading_view"
    app:emptyView="@layout/custom_empty_view"
    app:errorView="@layout/custom_error_view"
    app:noNetworkView="@layout/custom_no_network_view"
    app:contentView="@layout/main_content"
    />
```

```java
MultipleStatusView multipleStatusView = (MultipleStatusView) findViewById(R.id.main_multiplestatusview);
//显示加载中视图
multipleStatusView.showLoading();
//显示空视图
multipleStatusView.showEmpty();
//显示错误视图
multipleStatusView.showError();
//显示无网络视图
multipleStatusView.showNoNetwork();
//显示内容视图
multipleStatusView.showContent();
//设置重试视图点击事件
multipleStatusView.setOnRetryClickListener(onRetryClickListener);

/**
* 获取当前view的状态
*      MultipleStatusView.STATUS_LOADING   //当前为加载中视图
*      MultipleStatusView.STATUS_EMPTY     //当前为空视图
*      MultipleStatusView.STATUS_ERROR     //当前为错误视图
*      MultipleStatusView.STATUS_NO_NETWORK//当前为无网络视图
*      MultipleStatusView.STATUS_CONTENT   //当前为内容视图
*/
int viewStatus = multipleStatusView.getViewStatus();

```
MultipleStatusView继承自RelativeLayout，所以内容视图也可以直接写在MultipleStatusView内部
```xml
<com.classic.common.MultipleStatusView
    android:id="@+id/main_multiplestatusview"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:loadingView="@layout/custom_loading_view"
    app:emptyView="@layout/custom_empty_view"
    app:errorView="@layout/custom_error_view"
    app:noNetworkView="@layout/custom_no_network_view"
    >

    <TextView
        android:id="@+id/content_view"
        android:text="内容视图"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:gravity="center"
        android:textSize="20sp"
        />

</com.classic.common.MultipleStatusView>
```

##注意事项
- 加载中视图的id必须为：loading_view
- 空视图的id必须为：empty_view
- 错误视图的id必须为：error_view
- 无网络视图的id必须为：no_network_view
- 内容视图的id必须为：content_view

```xml
<RelativeLayout
    android:id="@+id/loading_view"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    ...

</RelativeLayout>
```

如果需要点击某个view进行重试,可以设置如下id:
- 空视图内对应的view id：empty_retry_view
- 错误视图内对应的view id：error_retry_view
- 无网络视图内对应的view id：no_network_retry_view

```xml
<RelativeLayout
    android:id="@+id/error_view"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <ImageView
        android:id="@+id/error_retry_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:src="@mipmap/ic_error"
        />

    <TextView
        style="@style/MultipleStatusView.Content"
        android:layout_below="@id/error_retry_view"
        android:text="@string/error_view_hint"/>
</RelativeLayout>
```

详细使用见demo示例。

##关于
* Blog: [http://blog.csdn.net/qy1387](http://blog.csdn.net/qy1387)
* Email: [pgliubin@gmail.com](http://mail.qq.com/cgi-bin/qm_share?t=qm_mailme&email=pgliubin@gmail.com)

##License
```
Copyright 2015 classic

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
