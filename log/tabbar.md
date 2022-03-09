

119

##### 一、Tabbar-基本结构的搭建 

1、创建项目，使用的是脚手架2

```
vue init webpack tabbar
```

runtime 



2、思路

TabBar->TabBarItem  

3、body样式

src->assets->css->base.css

```css
body{
	padding:0;
    margin:0;
}
```

注意：main.js一开始渲染的时候渲染的是App.vue,在App.vue中引入相关样式的东西

在js中引入样式，直接import；在style中引入样式，写成@import

```vue
<style>
	@import "./assets/css/base.css"
</style>
```



4、
