# 开启https
* 打开 ~/.atmjs/server.json
* 把证书文件放在自己喜欢的位置，eg: ~/.atmjs/https/ssl.pfx
* 修改https字段
```javascript
{
  "https": {
      "status": false,
      "port": 2016,
      "hostname": "hostname",
      "options": {
          "passphrase": "passphrase",
          //...
      },
      "files": {
          "pfx": "{{homedir}}/.atmjs/https/ssl.pfx"
      }
  }
}
```


