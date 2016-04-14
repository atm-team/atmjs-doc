### 说明
atmjs系统采用的是[nunjucks模板引擎](http://mozilla.github.io/nunjucks/)(ps:不建议使用相关的异步函数)
### 模板文件规范
1. 模板应创建到版本目录下的/views目录下,其中公共的模板片段（eg：header或footer等）放在版本目录的/layouts目录下
2. 以.html结尾
3. 模板对应的uri： /node-files/siteName/projectName/moduleName/versionName/views/fileName.html

