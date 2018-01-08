---
title: web前端暑期基础培训课
date: 2017-12-09 22:39:56
tags: [web前端暑期基础培训课,前端]
categories: [菜鸟开讲,CSS]

---
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;第七节课，主要跟大家说了一下响应式网站设计的理念，着重说了一下css3新增的媒体查询的功能，下面我就跟大家大概总结一下：
### 响应式网站设计
#### 概述
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;响应式网站设计(Responsive Webdesign)的理念是：页面的设计与开发应当根据用户行为以及设备环境(系统平台、屏幕尺寸、屏幕定向等)进行相应的响应和调整。具体的实践方式由多方面组成，包括弹性网格和布局、图片、CSS media query的使用等。无论用户正在使用笔记本还是iPad，我们的页面都应该能够自动切换分辨率、图片尺寸及相关脚本功能等，以适应不同设备；换句话说，页面应该有能力去自动响应用户的设备环境。响应式网页设计就是一个网站能够兼容多个终端——而不是为每个终端做一个特定的版本。这样，我们就可以不必为不断到来的新设备做专门的版本设计和开发了。响应式网站设计理念由伊森·马考特于2010年提出，附上原文链接：
        https://alistapart.com/article/responsive-web-design

#### 媒体查询
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;css3的媒体查询功能，使得响应式布局得以实现，其实基本原理还是用css3媒体查询（media/meta）功能查出设备的尺寸，然后写出不同的尺寸写出或者覆盖css样式，使得界面看起来变换了，媒体查询其实就是这么回事，当然，我们追求是让自己的html和css尽可能少的使用媒体查询覆盖css就能很好的适应不同尺寸布局。首先我们在使用Media的时候需要先设置下面这段代码，来兼容移动设备的展示效果：
>     <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
>     这段代码的几个参数解释：
>     width = device-width：宽度等于当前设备的宽度
>     initial-scale：初始的缩放比例（默认设置为1.0）  
>     minimum-scale：允许用户缩放到的最小比例（默认设置为1.0）    
>     maximum-scale：允许用户缩放到的最大比例（默认设置为1.0）   
>     user-scalable：用户是否可以手动缩放（默认设置为no，因为我们不希望用户放大缩小
#### CSS3媒体查询实例
我们先来看下下面这段代码，
>       @media screen and (max-width: 960px){
>       body{
>         background: #000;
>           }
>           }
这个应该算是一个media的一个标准写法，上面这段CSS代码意思是：当页面小于960px的时候执行它下面的CSS。应该有人会发现上面这段代码里面有个screen，他的意思是在告知设备在打印页面时使用的样式。但是目前我发现很多网站都会直接省略screen，因为你的网站可能不需要考虑用户去打印时，你可以直接这样写：当浏览器尺寸小于/等于960px时候

>         @media (max-width: 960px){
>             body{
>                 background: #000;
>             }
>         }
>         当浏览器尺寸大于/等于960px时候的代码了：
>         @media screen and (min-width:960px){
>             body{
>                 background:orange;
>             }
>         }
>         @media screen and (min-width:960px) and (max-width:1200px){
>             body{
>                 background:yellow;
>             }
>         }
以上就是对于CSS3媒体查询的一个简单的介绍，希望大家以后在使用中
慢慢掌握。




