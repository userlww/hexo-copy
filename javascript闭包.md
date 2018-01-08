---
title: javascript闭包
date: 2017-12-27 22:59:09
tags: [前端,javascript,闭包]
categories: [前端,javascript]

---
&nbsp;&nbsp;&nbsp;javascript闭包是JavaScript的一个特色，也是它的难点，许多前端工程师在面试的时候都会被问到闭包相关的问题，我在看书的时候看了一遍是有些不理解的，后来看了一位大佬的博客之后有了有了更好的理解，做了一点整理希望对大家有用。
#### 变量作用域
> &nbsp;&nbsp;&nbsp;&nbsp;要深入理解闭包，首先必须要了解javascript的变量作用域，变量作用域通常分为全局变量和局部变量，JavaScript的特殊之处，就在于函数内部可以直接读取全局变量

>       var n=111;
>       function test1()
>       {
>          alert(n);    //111
>       }
&nbsp;&nbsp;&nbsp;&nbsp;另一方面，函数外部无法读取函数内的局部变量

>       function test1()
>       {
>          var n=111;
>       }
>          alert(n);    //报错  
&nbsp;&nbsp;&nbsp;必须要注意的是,当在函数内部声明局部变量的时候，一定要使用var命令，否则解析引擎会将你声明的变量理解为一个全局变量

>       function test1()
>       {
>         n=1000;
>       }
>       alert(n);      //1000

#### 如何从外部读取局部变量
>&nbsp;&nbsp;&nbsp;有的时候，我们需要访问访问函数内的局部变量，但是前面已经说过，正常情况下，是没有办法做到的，但是为了达到我们的需求，不得不采取一种变通的方法，那就是在函数内部再定义一个函数

>        function test1()
>         {
>            var n=1000;
>            function test2()
>             {
>                alert(n);      //1000
>             }
>         }

>&nbsp;&nbsp;&nbsp;在上面定义的这一段代码中，函数test2被包含在函 test1的内部，那 >test中的局部变量对test2都是可见的，但是test2中定义的变量对test1却是不可见的，这也就是JavaScript>>中>作用域链的一个典型实例，子对象会一级一级向上寻找父对象中的变量，所以父对象的变量对子对象可见>，而子对象的变量对父对象却是不可见的。
&nbsp;&nbsp;&nbsp;既然test2可以读取test1中的局部变量，那么只要把test2座为test1的返回值，我们就可以在test1外部读取它的局部变量。这就是我们接下来要引入的闭包的概念

>         function test1()
>        {
>           var n=1000;
>           function test2()
>            {
>              alert(n);
>            }
>           return test2();
>         }
>          var result=test1();
>          result();

#### 什么是闭包
> &nbsp;&nbsp;&nbsp;MDN上面对闭包的定义是：Closures (闭包)是使用被作用域封闭的变量，函数，闭包等执行的一个函数的作用域。通常我们用和其相应的函数来指代这些作用域。(可以访问独立数据的函数)，根据笔者自己的理解，闭包就是封装在一个函数的另一个子函数，用于返回它所在的父函数中定义的局部变量，以便能够在父函数外部实现对该变量的访问，或者让这个变量的值始终保存在内存之中,请看下面这段代码：

>       function test1()
>       {
>        var n=100;
>        Nadd=function(){
>            n+=1;}
>          function test2()
>          {
>           alert(n);
>          }
>        return test2;
>        }
>        var result=test1();
>         result();         //100
>         Nadd();
>         result（);     //101
>&nbsp;&nbsp;&nbsp;在这段代码中,result就是闭包test2函数，一共执行了两次，第一次值是100，第二次是101，这说明test1中的局部变量n一直保存在内存中，而没有在test1调用后被自动清除。原因就是因为test1是test2的父函数，test2被赋给了一个一个全局变量，导致test2始终存在于内存中，它所依赖的test1也始终在内存中，不会在调用结束后被垃圾回收机制回收。
&nbsp;&nbsp;&nbsp;关于JavaScript闭包就先总结这些，可能有些地方也没有说的特别清楚，这里附上一篇另>外一位大佬对闭包的讲解：

>       https://github.com/mqyqingfeng/Blog/issues/9。