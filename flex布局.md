---
title: flex布局
copyright: false
date: 2018-01-06 00:12:40
tags: [前端,css布局]
categories: [前端,CSS]

---
&nbsp;&nbsp;&nbsp;今天来复习一下css中的一个比较重要的布局方式，flex，传统的css布局依赖于盒模型，依赖于三个重要属性，position，display和flaot，对于一些比较特殊的布局实现起来很不方便，比如，垂直居中。2009年W3c提出了flex布局方案吗，能够非常简便，快捷并且完整的实现各种页面布局而且到现在为止，各个浏览器对它的支持也非常的好。写这篇博客的时候参考了阮一峰大佬的这篇文章[Flex 布局教程：语法篇][1]和一篇纯英文文章[A Complete Guide to Flex][2]


### 简介
&nbsp;&nbsp;&nbsp;Flex即为Flexible Box，意为“弹性布局”，任何一个容器都可以指定它为Flex布局
>        div
      {
         display:flex;
         }

对行内元素设置flex
>            .container
>        {
>         display:inline-flex;
>        }

需要注意的是在webkit内核的浏览器中，必须加上浏览器内核前缀：-webkit-flex;

### 概念
![此处输入图片的描述][3]


  如图中所示，默认在水平方向和竖直方向上各有一条轴线，水平方向上的轴线叫做main axis，最左侧称为main start，最右侧称为main end；竖直方向上的轴线叫做cross axis，最上面叫做cross start，最下面叫做cross end。容器中单个项目所占据的主轴宽度叫做 main size，占据的竖直方向上的宽度叫做cross size

### flex容器属性
&nbsp;&nbsp;&nbsp;flex容器属性有6个
 
####  flex—direction
&nbsp;&nbsp;&nbsp;flex-direction属性决定了项目在主轴方向上的排列方向![此处输入图片的描述][4]
 


属性值
 
 - row（默认值）：在水平方向上从最左端开始排列
 - row-reverse：水平方向上从最右端开始排列
 - column：在竖直方向上从最上端往下排列
 - column-reverse：在竖直方向上从最下端向上排列
 
#### flex-wrap
&nbsp;&nbsp;&nbsp;在未定义该属性的情况下，默认所有项目排列在同一行，Flex-wrap属性值规定当一行放不下时，如何换行属性的取值有三种
 
 - nowrap:不换行，所有项目怕排列在同一行，当项目宽度之和大于容器宽度时，按比例调整，使所有项目都能够排在同一行
 - wrap：换行之后第一行在上面，自上向下行号依次增加
 - wrap-reverse:换行之后，第一行在下面，行号从下往上依次递增
 
#### flex-flow
&nbsp;&nbsp;&nbsp;flex-flow是前两个属性的简写形式
>        .container{
>           flex-flow: <flex-direction>||<flex-flow>
>           }
#### justify-content
&nbsp;&nbsp;&nbsp;justify-content属性定义了项目在主轴方向上的对齐方式
 
 - flex-start:左对齐
 - flex-end: 右对齐
 - center:居中
 - space-between:两端对齐，项目间隔相等
 - space-around:每个项目两侧的间隔相等，项目之间的间隔比项目与边框之间的间隔大一倍。
 ![此处输入图片的描述][5]


  [1]: http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html?utm_source=tuicool
  [2]: https://css-tricks.com/snippets/css/a-guide-to-flexbox/
  [3]: http://i2.bvimg.com/626790/ba613d56db10edf1.png
  [4]: http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071005.png
  [5]: http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071010.png
  
  #### align-item属性
  &nbsp;&nbsp;&nbsp;align-item属性定义项目如何在竖直方向上如何对齐
  
 - flex-start:在交叉轴的起点对齐
 - flex-end:在交叉轴的终点对齐
 - center：在交叉轴的中间对齐
 - baseline：在项目的第一行文字的基线对齐
 - stretch：如果项目未设置高度或设置为auto，将占满整个容器的高度
 
#### align-content
&nbsp;&nbsp;&nbsp;align-content属性定义了多根轴线的对齐方式，如果轴线仅有一根，该属性不起作用

 - flex-start：与交叉轴的起点对齐
 - flex-end: 与交叉轴的终点对齐
 - center：与交叉轴的中间对齐
 - space-between:与交叉轴两端对齐，轴之间的间隔平均分布
 - space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边线之间的间隔大一倍
 - stretch：轴线占满整个交叉轴
 
### 项目的属性
&nbsp;&nbsp;&nbsp;以下6个属性，用来设置在项目上

- order:定义项目排列顺序，数值越小，排列越靠前，默认值为0
- flex-grow:定义项目的放大比例，默认为0，如果所有项目的该属性值都为1，则将剩余空间等分之后分配给各个项目。如果有一个为2.则按照放大倍数的比例分配剩余空间，即该项目分配得到的剩余空间比其他项目大一倍  
- flex-shrink:定义项目的缩小比例，默认比例为1，若空间不足，该项目将缩小
- flex-basis：定义了在多余空间分配之前，项目占据的主轴空间，浏览器根据这个属性，计算主轴是否有多余的空间。它的默认值是auto，就是项目本来的大小
- flex属性是flex-grow，flex-shrink和flex-basis的简写，默认值是0 1 auto，后两个属性可选
- align-self:允许多个项目有与其他项目不一样的对齐方式，可覆盖align-items属性，默认值为auto，表示继承父元素的align-item属性，没有父元素时等同于stretch
  