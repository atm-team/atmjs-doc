## 服务器配置文件位置
服务器的配置文件: ~/.atmjs/server.json
## 服务器配置项说明

```json
{
    "maps": {
        "atmgui": "{{homedir}}/.atmjs/atmgui",
        "siteName1": "{{homedir}}/path/to"
    },
    "port": 2015,
    "https": {
        "status": true,
        "port": 2016,
        "hostname": "hostname",
        "options": {
            "passphrase": "passphrase",
            //...
        },
        "files": {
            "pfx": "{{homedir}}/.atmjs/https/ssl.pfx"
        }
    },
    "logger": false
}
```
```
其中,maps字段表明的是站点名称与站点路径的关系
路径中可用的占位符 {{homedir}}指向用户目录(即node.js中通过 require('os').homedir() 获取的路径)
maps.atmgui是atmjs的GUI站点，不可被覆盖

https,参考[node.js/https的API](https://nodejs.org/api/https.html)
https.files里面的字段可以把文件转换为字符添加到https.options中

logger设置是否在命令行窗口打印出http请求相关信息
```

##配置修改有下面两种方法
* 打开~/.atmjs/server.json文件直接编辑
* chrome浏览器打开 http://127.0.0.1:2015/ ,点击服务器配置，修改并提交


##注意事项
* 无论哪种修改,都要保证json格式的正确性
* maps字段尽量不要在这里直接修改,而是通过站点管理
* 