# Context.js

简体中文|[English](README-en.md)

![image](https://user-images.githubusercontent.com/22728201/147812723-6dd06424-642e-4b0a-94e9-3adbfa09450a.png)

## About

这是一个加强版的右键上下文菜单库，在过去的几年里，[Lsky Pro](https://github.com/wisp-x/lsky-pro)
一直在使用 [jakiestfu/Context.js](https://github.com/jakiestfu/Context.js)  
尽管源库自 2014 就停止更新，但是它依然可以良好的工作。 不过在业务升级时，这个旧版本已经不满足我的需求，所以有了这个版本。    
注意，这个库依赖于 Jquery。

## Features

- 可以与 twitter Bootstrap 一起使用
- 菜单项支持使用 Twitter Bootstrap icons
- 菜单支持点击回调事件
- 支持锚点链接
- 支持设置上下文菜单的头部标题
- 支持设置菜单项分割线
- 递归菜单(无限深度)
- 垂直空间检测(变成一个“下拉列表”)
- 水平空间检测(右侧没有空间时下降到左边而不是右边)
- 支持动态添加/删除菜单
- 甚至适用于<a href="http://google.com" class="inline-menu">内联链接</a>
- 通过在菜单创建期间回调的动态菜单项
- 支持在点击回调中获取被右击元素
- 支持上下文菜单打开前、打开后的回调事件
- 支持通过回调事件动态显示/隐藏菜单项
- 支持自定义菜单项的 class 以及自定义属性

# Use

1. 初始化 contextjs

```js
context.init({
  fadeSpeed: 100,
  filter: function ($obj) {
  },
  above: 'auto',
  preventDoubleContext: true,
  compress: false
});
```
> 配置说明请参考源库

2. 增加右键菜单

```js
context.attach('.item', {
  data: [
    {header: 'this is header'}, // 标题
    {
      text: '打开文件',
      classes: ['open-file'], // 自定义 class，必须是数组
      attributes: { // 自定义标签属性，必须是对象
        'data-operate': 'open-file',
      },
      // 点击菜单项以后的回调
      action: function (item) { // 第一个参数表示 .item 元素
        // 使用 this 可以获取当前点击的菜单项
      },
      visible: function (item) { // 第一个参数表示 .item 元素
        // 在这个回调里，返回 bool 类型的值可以显示/隐藏某个菜单项
      },
    },
    {divider: true}, // 分割线
  ],
  // 鼠标右击后，context menu 打开之前的回调
  beforeOpen: function (item) { // 第一个参数表示 .item 元素
    // 如果你要在这里获取 contextmenu 事件对象，请使用 this 
  },
  // 鼠标右击后，context menu 打开之后的回调
  afterOpen: function (item, dropdown) { // 第一个参数表示 .item 元素，第二个参数表示上下文菜单元素
    // 如果你要在这里获取 contextmenu 事件对象，请使用 this 
  }
});
```