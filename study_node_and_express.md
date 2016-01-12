从零开始学习node和express
---------------------------

### npm安装包

首先，使用淘宝的npm源加速。

    npm install 包名 --save

在当前项目中安装指定包，并保存配置到packagist.json

    npm install 包名 -g
    
安装到全局，一般用来安装命令行工具。

### underscore

当我浏览一遍express入门教程后，兴冲冲的跑去开始写代码，碰到第一个坑：如何做json合并。

jquery中有$.extend，但express和node都没有内置相关的工具包。

经过一番寻找，发现了一个叫做 `underscore` 的工具包。

安装：
  
    npm install underscore  --save
  
使用：

    var _ = require('underscore');
    var json = _.extend({"a":1},{"b":2});
    console.log(json);
    //得到 {"a":1,"b":2}
  
  
### node-dev

当我每次修改完代码后，都要重启express服务的时候，耐心耗尽了，那么肯定有工具可以监控文件变化并自动重启服务，经过一番搜索，找到了 `node-dev` 。

安装 ： 

    npm install node-dev -g

使用：
express根目录下执行 

    node-dev ./bin/www
  
`npm start` 可以暂时弃用了.

### 关于fs模块路径

fs模块方法所传入的path路径，除非是绝对路径(以 '/' 开头的),其他的都是相对于执行根目录。

举个例子

    fs.exists('config/app.js'); 
    
是取的  `/path/to/project/config/app.js` , 如果要相对于当前目录，有一个变量 `__dirname`

    fs.exists(__dirname + '/app.js')
    
是不是有点像php里的 __DIR__ ？

