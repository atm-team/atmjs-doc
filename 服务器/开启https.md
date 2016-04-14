# 开启https
* 打开 ~/.atmjs/server.json
* 把证书文件放在自己喜欢的位置，eg: ~/.atmjs/https/ssl.pfx
* 修改https字段

```javascript
{
  "https": {
      "status": true,            // 默认关闭，需修改为状态设置为true
      "port": 2016,              // https端口
      "hostname": "test.a.com",  // 域名
      "options": {               // 参考[node.js/https的API](https://nodejs.org/api/https.html)
          "passphrase": "***",  
          //...
      },
      "files": {
          "pfx": "{{homedir}}/.atmjs/https/ssl.pfx"    // 证书路径， {{homedir}}变量指向用户目录
      }
  }
}
```


