# 什么是SASS，它如何工作

SASS是一个CSS与处理器，是CSS的扩展

当项目过于庞大不好管理，并且重用很低，所以需要SASS

[SASS 文档](https://sass-guidelin.es/zh/)

Sass 存在的关键不是将 CSS 变成一种全功能编程语言，它只是想修复缺陷。正因如此，学习 Sass 如同学习 CSS 一样简单：它只在 CSS 的基础上添加了几个额外功能

# 变量，嵌套的使用

代码使用在线网站codepen.io实现

https://codepen.io/utopia-xxl/pen/ZEvNWgv?editors=1100

主要展示了SASS的变量和嵌套的使用

并且解决了[高度塌陷](https://juejin.cn/post/6844903908456792071)的问题:因为父元素是靠子元素撑开的，当所有的子元素变成 float后就会脱离文档流，因此造成高度塌陷的情况.

```css
nav::after{
    /*可以通过after伪类向元素的最后添加一个空白的块元素，然后对其清除浮动，这样做和添加一个div的原理一样，且不会添加多余的div。*/
    content:"";
    clear:both;
    display: table;
  }
```

# mixin，function，extends

类似多行代码的变量

[mixin](https://sass-guidelin.es/zh/#section-46)

```scss
// 定义类似变量
@mixin clearfix{
  &::after{
    content:"";
    clear:both;
    display: table;
  }
}
```

```scss
// 在需要的地方调用，类似函数一样，也可以设置参数传递
@include clearfix;
```

同样我们也可以自定义函数，接收参数，返回数据等

```scss
// 定义
@function divide($a,$b){
  @return $a / $b;
}
// 调用，并且传递参数
divide(60,2)
```

`@extend` 指令是 Sass 中既强大易于误解的指令。该指令作为一个警示，告知 Sass 对选择器 A 的样式化正好存在与选择器B共通的地方。不用多说，这是书写模块化 CSS 的好助手。

```scss
// 定义
%btn-placeholder{
  padding: 10px;
  display: inline-block;
  text-align: center;
  border-radius: 100px;
  width: $width-button;
  @include style-link-text($color-text-light);
}
//使用
@extend %btn-placeholder;
```

完整代码：https://codepen.io/utopia-xxl/pen/vYpwKOB?editors=1100

 **extend和mixin的区别？**

1. `@extend` 命令不够灵活，不能传递参数。而 `@mixin` 不仅能传递参数，还能传递代码块。
2. 编译的结果不一样。`@extend` 可以生成 `DRY` 格式的代码。

mixin编译后在调用的地方都复制了其代码

而extend并不会额外复制，只会在多个选择器设置一次

参考链接：[extend和mixin的区别](https://juejin.cn/post/7068967683345088519)

# 安装并使用SCSS

1. 官网下载安装 node
2. Nom init 初始化项目
3. 安装node-sass`npm install node-sass --save-dev`
4. 取package.json文件中添加脚本，自动编译scss到css
   1. `"compile:sass": "node-sass sass/main.scss css/style.css"`配置好后执行`npm run compile:sass`即可将scss文件自动编译到配置好路径的css文件
   2. `"compile:sass": "node-sass sass/main.scss css/style.css -w"`添加-w 属性，终端会实时运行监测scss文件一旦保存修改就会自动编译