---
title: less 笔记
copyright: true
date: 2017-07-03 15:35:10
tags: [前端,CSS,]
categories: [前端,CSS]

---
### 写在前面
&nbsp;&nbsp;&nbsp;今天学习了一下less的语法，这里只是做个笔记，备忘。
### less是什么
&nbsp;&nbsp;&nbsp;less是一门css预处理语言，扩展了css的功能，增加了变量，Mixin以及函数等特性，使得css更加易于维护，方便与制作主题与扩充。
### less部分语法
#### 变量
   &nbsp;&nbsp;&nbsp;例如
   

    @bgcolor:#fff
    #header{
      background:@bgcolor
      }
解析为

    #header{
    background:#fff
          }

&nbsp;&nbsp;&nbsp;今天先写到这里，待更新
