### 使用方法

git clone https://github.com/hechongchong/vue-create-module-cli.git

git checkout master

cd vue-create-module-cli && npm install --save

npm link

### 创建页面及对应路由

autoc create testfile

### 可选单页面或者多页面

single

### 可执行npm publish 打包成npm包


### 参考
vue项目内自动生成页面，zash-cli

https://blog.csdn.net/zwf193071/article/details/107761790



# zash-cli

A simple CLI for generating pages into your projects

> Author：zwf193071

> E-mail: 997131679@qq.com

> date: 2020/07/29
* * *
[![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![npm version](https://badge.fury.io/js/zash-cli.svg)](https://badge.fury.io/js/zash-cli)
[![npm downloads](https://img.shields.io/npm/dm/zash-cli.svg)](https://www.npmjs.com/package/zash-cli)
* * *
## Preface
这些页面都是相似的，为何要反复的拷贝来拷贝去？好不容易拷贝完，还得为新增的页面添加路由、左侧菜单和面包屑导航的功能，555...不甘心将时间浪费在这些细枝末节上，于是擦干眼泪，撸起袖子做了一套自动化生成页面的工具，希望能给后面的读者一些启示。

## Feature
一款为公司内部vue项目特定的CLI工具，亦可基于此进行改造，现支持`create <new-file-name>`命令，可生成单页或带tab的多页面，自动注入新页面功能至路由、面包屑及菜单导航等组件内

## Usage
全局安装zash-cli。`npm install -g zash-cli`

or
```
git clone https://github.com/zwf193071/zash-cli.git

cd zash-cli && npm install

npm link
```

打开terminal或 cmd ，输入`zash` or `zash -h` ，你将看到如下信息:
```
  Usage: zash [options] [command]

  Options:
    -h, --help              output usage information

  Commands:
    create <new-file-name>  create a new file powered by zash-cli

    Run zash <command> --help for detailed usage of given command.

```

在你想生成页面的项目内的根目录下，新建pageConf.js文件，代码如下所示：
```
/**
 * 自动生成文件的相关配置信息
 * @param parentFolderPath 父文件地址，相对于根路径
 * @param routerPath 路由文件地址
 * @param breadPath 面包屑导航地址
 * @param parentName 父菜单名字
 * @param leftMenuPath 左侧菜单文件路径
 * @param author 当前文件的创建者
 * @param title 文件标题，与增删改的提示信息相关
 * @param isDrawer 是否有抽屉，默认为true，表示增删改功能皆有
 * @param getUrl 列表请求接口地址
 * @param addUrl 新增接口地址
 * @param editUrl 编辑接口地址
 * @param deleteUrl 删除接口地址
 * @param childrenValues 子页面的模块名称
 * @param childrenNames 子页面的标题
 * @author zhuwenfang
 * @createtime 2020-07-28
 */
exports.conf = {
    parentFolderPath: 'src/views/Content/SFC',
    routerPath: 'src/router/routes.js',
    breadPath: 'src/components/BreadLink/config.js',
    parentName: '网络服务',
    leftMenuPath: 'src/views/Home/LeftMenu/LeftMenu.config.js',
    author: 'zhuwenfang',
    title: '测试一',
    isDrawer: true,
    getUrl: '',
    addUrl: '',
    editUrl: '',
    deleteUrl: '',
    // 下面针对是多页面的配置
    childrenValues: ['child1', 'child2', 'child3', 'child4'],
    childrenNames: ['子页面1', '子页面2', '子页面3', '子页面4']
};


```

## Commands
### create <new-file-name>
这个命令会创建新页面组件Test.
```
$ zash create Test

```

![image](https://github.com/zwf193071/zash-cli/blob/master/images/1.png)

在你想注入路由的文件内，写上`// $h`和`// $f`，当执行命令成功后，会在该路由文件，根据该注释语句占位符，自动导入`Test`的路由

![image](https://github.com/zwf193071/zash-cli/blob/master/images/2.png)
![image](https://github.com/zwf193071/zash-cli/blob/master/images/3.png)

左侧菜单和面包屑导航亦是根据上述原理自动注入生成

## Thanks to
* [vue-cli](https://github.com/vuejs/vue-cli)

## License
This repo is released under the [MIT](https://opensource.org/licenses/MIT).





