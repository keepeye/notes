从零开始学习node和express
---------------------------

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
