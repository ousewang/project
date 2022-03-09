149
##### 一、项目创建和gitlab的托管
1、脚手架3创建

```
vue create superMall 
```
注意：项目名称不能为小写

2、gitlab托管
**问题：将本地的项目和远程的仓库联系起来**
方法1、  
        把地址 http://192.168.1.143:8070/wyq/supermall.git   拷贝,使用 git clone,会拉下来一个空的文件夹(supermall)
        将刚刚用脚手架3创建的项目（supermall1）,复制到拉下来的空项目(supermall)中 

        git add .               工作区=》暂存区
        git commit -m '任务描述' 暂存区=》仓库区   
        git push                仓库区=》远程仓库
方法2、（推荐）
    直接使用指令
```
    git remote add origin git@192.168.1.143:wyq/supermall.git
    git push -u origin master 
```
##### 二、划分目录结构
src目录下
1、删除App.vue中没用的
2、assets   资源，img、css
3、views    大的视图 ，首页之类
4、components   组件 ，公共的组件
    common,不仅当前项目会用到别的项目也会用到 
    content，与当前业务相关的组件
5、router   路由相关的
6、store    状态管理工具的文件夹 vuex
7、network  网络相关
8、common   公共的js文件
    const.js
    utils.js    公共的方法
    mixin.js    混入

##### 三、css文件引入

对不同的标签，进行统一性的规范

assets->css目录下

normalize.css	第三方的初始化样式

base.css	自己



**注意**：在base.css中要引用normalize.css，使用@import；然后再App.vue中引用base.css

项目运行的逻辑

从main.js=》App.vue=》base.css=>normalize.css



**bug**:Parsing error: No Babel config file detected

方法：在package.json	=> eslintConfig中配置

```js
        "parserOptions": {
            "requireConfigFile": false
        },
```



报错

##### 四、配置路径的别名和项目风格

1、根目录文件下 vue.config.js

在脚手架3中，配置别名的时候，@表示的src;	脚手架2，需要写成src

router 	只需要在main.js中引入，不需要配置；而且在所有的文件中都可以通过	this.$router

store		在所有的文件中都可以通过	this.$store

```js
module.exports = {
  configureWebpack: {
    resolve: {
      alias: {
        'components': '@/components',
        'content': 'components/content',
        'common': 'components/common',
        'assets': '@/assets',
        'network': '@/network',
        'views': '@/views',
      }
    }
  }
}
```



2、editorconfig

```js
root = true

[*]
charset = utf-8
indent_style = space
# 缩进尺寸
indent_size = 2
end_of_line = lf
# 插入最后一行
insert_final_newline = true
# 修剪尾随空格
trim_trailing_whitespace = true

```

152

##### 五、tabbar引入和项目划分

1、tabbar	引入到	components->common目录下（导航栏不仅在当前项目可用，别的项目也可以使用）

2、mainTabbar	引入到	components->content目录下（与项目有关）

​	修改mainTabbar	中图片引入的路径

3、

