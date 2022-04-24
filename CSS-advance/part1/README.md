# 总结

这部分实现了网页的第一部分，利用了很多CSS3中的特性，主要涉及到了以下的知识点

## 基本样式

- background-image 添加网页的背景图片，同时使用linear-gradient在图片上设置了一个渐变
  - 关于[linear-gradient](https://www.runoob.com/css3/css3-gradients.html)的更多信息
  - 关于[background](https://www.runoob.com/css3/css3-backgrounds.html)的更多信息
- 通过clip-path: polygon裁剪图片，设计成一个特殊的多边形，顺时针指定多边形的顶点
  - 推荐了一个有用的网站，可以直接生成多种裁剪图形的css代码[clippy](https://bennettfeely.com/clippy/)

## 动画

CSS3 可以创建动画，它可以取代许多网页动画图像、Flash 动画和 JavaScript 实现的效果。

- 利用了@keyframes的方法创建动画，规则内指定一个 CSS 样式和动画将逐步从目前的样式更改为新的样式。
  - 利用transform: translate(), 分阶段来移动位置，实现动画0%{}80%{}100%{}
  - 创建动画后，需要添加带对应的元素上，必须设置 name和duration属性，还有很多，如delay。。。
  - [animation](https://www.runoob.com/css3/css3-animations.html) 为了性能最好只设置两个属性 [opacity](https://www.runoob.com/cssref/css3-pr-opacity.html)透明度（0代表完全透明，1代表完全不透明）和[transform](https://www.runoob.com/cssref/css3-pr-transform.html)

- [transition](https://www.runoob.com/css3/css3-transitions.html) 设置过渡属性来实现动画

- 还利用了[伪类](https://www.runoob.com/css/css-pseudo-classes.html)和[伪元素](https://www.runoob.com/css/css-pseudo-elements.html)，[z-index](https://www.runoob.com/cssref/pr-pos-z-index.html)等来配合实现整个动画

