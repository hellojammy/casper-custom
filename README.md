# Casper-custom
修改自ghost的自带主题，casper
The default theme for [Ghost](http://github.com/tryghost/ghost/).

> 预览地址：

http://hello1010.com

> 新增特性

1、去掉主页的背景图片，主页顶部新增导航栏(使用了headroom.js)

2、主页只显示指定用户的文章（假如要显示此功能，需要把index.hbs底部的{{> "loop_owner"}}改为loop）

3、修改页面底部的显示

4、修改了ghost的node_modules模块中的handlebars，新增了ifCond方法，用来增强handlebars模板引擎的if判断功能，用来比较两个变量是否相等。
主要代码如下：

    instance.registerHelper('ifCond', function(v1, v2, options) {
            if(v1 === v2) {
              return options.fn(this);
            }
            return options.inverse(this);
          });

使用方法：

    {{#ifCond author.name 'hellojammy'}}
        .....
    {{/ifCond}}


需要新增以上代码片段的的文件主要有7个：

    node_modules/express-hbs/node_modules/handlebars/dist/handlebars.amd.js
    node_modules/express-hbs/node_modules/handlebars/dist/handlebars.js
    node_modules/express-hbs/node_modules/handlebars/dist/handlebars_runtime.amd.js
    node_modules/express-hbs/node_modules/handlebars/dist/handlebars.runtime.js
    node_modules/express-hbs/node_modules/handlebars/dist/amd/handlebars/base.js
    node_modules/express-hbs/node_modules/handlebars/dist/cjs/handlebars/base.js
    node_modules/express-hbs/node_modules/handlebars/lib/handlebars/base.js
