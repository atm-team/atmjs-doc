# 在html中定位资源

```
<!-- 源码 -->
<img title="百度logo" src="images/logo.gif"/>

<!-- 编译到dev后大致如下 -->
<img title="百度logo" src="/node-files/siteName/***/images/logo.gif"/>


<!-- 编译到其他目标后大致如下 -->
<img title="百度logo" src="http://hostname/***/images/logo_xxxxxxx.gif"/>
```