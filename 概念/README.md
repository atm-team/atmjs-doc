# 工作原理

每个模块的版本构建后,在对应的构建目录下会生成一个清单文件

用 lib/jquery/1.11.3 和 sys/index/1.0.0 两个模块版本进行说明
###示例json
```json
// lib/jquery/1.11.3的清单文件
{
  "res": {
    "lib/jquery/1.11.3:jquery": {
      "uri": "/lib/jquery/1.11.3/exports/jquery.js",
      "type": "js",
      "deps": [
        "lib/jquery/1.11.3:src/jquery"
      ],
      "pkg": "lib/jquery/1.11.3:p0"
    },
    "lib/jquery/1.11.3:src/jquery": {
      "uri": "/lib/jquery/1.11.3/src/jquery.js",
      "type": "js",
      "pkg": "lib/jquery/1.11.3:p0"
    }
  },
  "pkg": {
    "lib/jquery/1.11.3:p0": {
      "uri": "/lib/jquery/1.11.3/pkg/jquery.js",
      "type": "js",
      "has": [
        "lib/jquery/1.11.3:src/jquery",
        "lib/jquery/1.11.3:jquery"
      ]
    }
  }
}
```

```json
// sys/index/1.0.0模块的清单文件
{
  "res": {
    "sys/index/1.0.0:index": {
      "uri": "/sys/index/1.0.0/exports/index.js",
      "type": "js",
      "deps": [
        "sys/index/1.0.0:src/index"
      ],
      "pkg": "sys/index/1.0.0:p0"
    },
    "sys/index/1.0.0:src/index": {
      "uri": "/sys/index/1.0.0/src/index.js",
      "type": "js",
      "extras": {
        "async": [
          "common/popup/1.0.0:popup"
        ]
      },
      "deps": [
        "lib/jquery/1.11.3:jquery",
        "sys/index/1.0.0:src/index.css"
      ],
      "pkg": "sys/index/1.0.0:p0"
    },
    "sys/index/1.0.0:src/index.css": {
      "uri": "/sys/index/1.0.0/src/index.css",
      "type": "css"
    }
  },
  "pkg": {
    "sys/index/1.0.0:p0": {
      "uri": "/sys/index/1.0.0/pkg/index-1.0.0.js",
      "type": "js",
      "has": [
        "sys/index/1.0.0:src/index",
        "sys/index/1.0.0:index"
      ],
      "deps": [
        "lib/jquery/1.11.3:jquery",
        "sys/index/1.0.0:src/index.css"
      ]
    }
  }
}
```

###示例原理分析
* sys/index/1.0.0:index 依赖 sys/index/1.0.0:src/index
* sys/index/1.0.0:src/index 依赖 lib/jquery/1.11.3:jquery 和 sys/index/1.0.0:src/index.css
* 因为jquery不在当前版本下,因此需要找到lib/jquery/1.11.3下的清单文件继续分析
* lib/jquery/1.11.3:jquery 依赖 lib/jquery/1.11.3:src/jquery
* 因此sys/index/1.0.0:index依赖的全部文件id为

```
lib/jquery/1.11.3:src/jquery
lib/jquery/1.11.3:jquery
sys/index/1.0.0:src/index.css
sys/index/1.0.0:src/index
sys/index/1.0.0:index
```

* 把id对应成文件,然后分析pkg相关信息,则可以得出地图文件数据

```json
{
  "domain": "/node-assets/gcw/dev",
  "active": "1.0.0",
  "siteName": "gcw",
  "port": 2015,
  "https": "dev.gcimg.net:2016",
  "maps": {
    "1.0.0": {
      "sys/index/1.0.0:index": {
        "css": [
          "/sys/index/1.0.0/src/index.css"
        ],
        "loader": "/lib/atm/0.0.1/exports/loader.js",
        "js": [
          "/lib/jquery/1.11.3/pkg/jquery.js",
          "/sys/index/1.0.0/pkg/index-1.0.0.js"
        ],
        "onlyCss": false,
        "async": false,
        "defer": false,
        "init": "{\"baseUrl\":\"/node-assets/gcw/dev\",\"version\":\"1.0.0\",\"alias\":{\"jquery\":\"lib/jquery/1.11.3:jquery\",\"popup\":\"common/popup/1.0.0:popup\"},\"async\":{\"alias\":{\"common/popup/1.0.0:src/popup\":\"/common/popup/1.0.0/pkg/popup-1.0.0.js\",\"common/popup/1.0.0:popup\":\"/common/popup/1.0.0/pkg/popup-1.0.0.js\"},\"deps\":{\"sys/index/1.0.0:src/index\":[\"sys/index/1.0.0:src/index.css\"]},\"exists\":{\"sys/index/1.0.0:src/index.css\":1}}}"
      }
    }
  }
}

```

* 通过后端语言sdk,根据json文件生成依赖的css和js标签

```html
<link data-from="atmjs" type="text/css" rel="stylesheet" href="/node-assets/gcw/dev/sys/index/1.0.0/src/index.css" />


<script id="atmjsnode" data-from="atmjs" type="text/javascript" src="/node-assets/gcw/dev/lib/atm/0.0.1/exports/loader.js"></script>
<script data-from="atmjs" type="text/javascript">
    atmjs.init({
        "baseUrl": "/node-assets/gcw/dev",
        "version": "1.0.0",
        "alias": {
            "jquery": "lib/jquery/1.11.3:jquery",
            "popup": "common/popup/1.0.0:popup"
        },
        "async": {
            "alias": {
                "common/popup/1.0.0:src/popup": "/common/popup/1.0.0/pkg/popup-1.0.0.js",
                "common/popup/1.0.0:popup": "/common/popup/1.0.0/pkg/popup-1.0.0.js"
            },
            "deps": {
                "sys/index/1.0.0:src/index": ["sys/index/1.0.0:src/index.css"]
            },
            "exists": {
                "sys/index/1.0.0:src/index.css": 1
            }
        }
    });
</script>
<script data-from="atmjs" type="text/javascript" src="/node-assets/gcw/dev/lib/jquery/1.11.3/pkg/jquery.js"></script>
<script data-from="atmjs" type="text/javascript" src="/node-assets/gcw/dev/sys/index/1.0.0/pkg/index-1.0.0.js"></script>
<script data-from="atmjs" type="text/javascript">
    atmjs.use("sys/index:index");
</script>

```