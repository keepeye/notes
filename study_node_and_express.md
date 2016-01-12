从零开始学习node和express
---------------------------

### npm安装包

首先，使用淘宝的npm源加速 http://npm.taobao.org/ 

在当前项目中安装指定包，并保存配置到packagist.json

    npm install 包名 --save

安装到全局，一般用来安装命令行工具。

    npm install 包名 -g
    
### 关于require

node中使用 `require()` 来加载模块，模块加载分为两种方式:

1.从node_modules中加载，即通过npm安装的模块。

        var foo = require('foo')
      
2.从自定义路径中加载

        var foo = reuqire('./foo')
        
此种方式会相对于当前脚本所在目录，依次寻找 
    
- ./foo.js
- ./foo.json
- ./foo.node
- ./foo/package.json
- ./foo/index.js
- ./foo/index.json
- ./foo/index.node


模块加载一次后将被缓存，多次require同一个模块不会重复运行模块初始化脚本，即单例模式。

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
    
是不是有点像php里的 `__DIR__` ？

