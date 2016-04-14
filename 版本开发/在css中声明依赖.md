### 在css中声明依赖
* 同项目同模块同版本下的声明，用相对路径

```
// /exports/demo.css

/**
 * @require ./common.css
 */
 ```
<br>

* 同项目不同模块下的声明,可用 {{project}} 占位符

```
// www/index/1.0.0/src/demo.css


/**
 * @require '{{project}}/common:common.css'
 */
 
或

/**
 * @require 'www/common:common.css'
 */
 
```

可以用占位符 {{project}}代替项目名称，这样修改项目名称时不用再修改源码

