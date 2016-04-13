#测试数据
###说明

###测试数据文件规范
* 测试数据文件应创建到版本目录下的/datas目录下
* 支持.html,.json,.xml等文本格式文件
* 对于非开放模块,支持js模块返回数据
* 测试数据对应的uri： 
/node-files/siteName/projectName/moduleName/versionName/datas/fileName.ext
* 支持callback和timeout参数
* atmjs并不建议对数据做复杂的处理,比较atmjs只是一个前端开发系统,真正的数据业务应该在后端去实现

###测试模板与测试数据协同工作实例
```html
<form method="post" action="{{ '/datas/ajax.js' | uri() }}?timeout=1000">
<input type="text" name="test" value="test" />
<input type="submit" />
</form>
```

```javascript
module.exports = function () {
  return {
    status: true,
    message: '操作成功'
  }
}
```
