### ATMJS是什么

ATMJS是世界工厂网前端团队自主研发出的一套前端一体化开发系统！
### 1.ATMJS与FIS3的关系

> FIS3 是面向前端的工程构建工具。解决前端工程中性能优化、资源加载（异步、同步、按需、预加载、依赖管理、合并、内嵌）、模块化开发、自动化工具、开发规范、代码部署等问题。

评测：正如fis官网上介绍,fis3具备很强大的编译构建能力,但其在一个前端工程的架构与部署方面及前后端协同工作方面存在局限性！


### 2.ATMJS与SPM的关系
我们从SPM身上学到了 site/family/module 的组织结构，但根据我们这几年在使用spm过程中存在的一些问题,又对其结构进行进一步的扩展,把版本引入进来,形成了ATMJS独有的组织架构。(PS:这里的spm只是个人对SPM3之前的版本的一个评测,spm3个人没用过)

###3.ATMJS的特性
|   | 特性列表 |
| -- | -- |
| 1 | ATMJS汲取了FIS3和SPM各自的特长,具备很强的构建能力和结构化的组织架构！ |
| 2 | 不管是FIS3还是SPM,在与后端交互都存在局限性。ATMJS采用标准json交互格式与后端进行协作。 |
| 3 | 无需手动在页面写样式标签和js标签，全部由后段程序根据json文件进行自动生成，使前端开发更灵活。 |
| 4 | 依赖预加载。 |
| 5 | 适用于各种规模的前端项目。|
| 6 | 可视化的操作界面！ |
| 7 | 一体化的开发，无需任何第三方web服务器,即可实现测试数据，模板，文档，公共模块，在线调试等功能 

