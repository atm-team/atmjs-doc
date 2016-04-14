# 在html中定位资源

```
<!-- 源码 -->
<img title="百度logo" src="images/logo.gif"/>

<!-- 编译到dev后 -->
<img title="百度logo" src="/node-files/siteName/***/images/logo.gif"/>


<!-- 编译到其他目标后 -->
<img title="百度logo" src="/node-files/siteName/***/images/logo.gif"/>
```