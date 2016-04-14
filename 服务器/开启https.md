# 开启https
* 打开 ~/.atmjs/server.json
* 把证书文件放在自己喜欢的位置，eg: ~/.atmjs/https/ssl.pfx
* 修改https字段
```javascript
{
  "https": {
      "status": true,            // 默认关闭，需修改为状态设置为true
      "port": 2016,              // 
      "hostname": "hostname",
      "options": {
          "passphrase": "***",
          //...
      },
      "files": {
          "pfx": "{{homedir}}/.atmjs/https/ssl.pfx"
      }
  }
}
```


