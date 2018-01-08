---
title: javascript实现仿射密码加解密
date: 2017-12-16 11:11:44
tags: [密码学,古典密码，仿射密码]
categories: [密码学,古典密码]

---
#### 仿射密码
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;仿射密码是古典密码算法中单表代换密码的一种，所谓单表代换就是指明文中相同的字符在加密过程中使用同一个字符进行代换，而仿射密码的加密算法就是一个线性变换，就是对于任意的明文字符x，对应的密文字符为y≡e(x)≡ax+b(mod26)，a,b为小于26的整数,并且a，必须与26互素。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;注:当a=1，b=3时，这种仿射密码就是著名的凯撒密码。用js实现加密过程的代码如下：
>            var mingwen=document.getElementById("mingwen").value.toLowerCase();//获取明文字符串，将其转换为小写
>            var a=parseInt(document.getElementById("k1").value);//获取a,b;
>            var b=parseInt(document.getElementById("k2").value);
>            var code=new Array(0);
>            var miwen=new Array(0);
>            var j;
>            var str;
>            for(var i=0;i<mingwen.length;i++)
>            {
>                code[i]=((a*(mingwen.charCodeAt(i)-97)+b)%26);//求对应密文字符的Unicode码
>                miwen[i]=String.fromCharCode(code[i]+97);   //解析为对应字符
>            }
>            for( j=1;j<miwen.length;j++)                //将密文串成字符串
>            {
>                miwen[j]=miwen[j-1]+miwen[j];
>            }
>            var result=document.getElementById("miwen");
>            result.innerText=miwen[j-1];
#### 已知密钥解密
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;根据欧拉函数可知0-26之间共有12个与26互素的数字，则密钥空间为12\*26=312。又由a与26互素可知在0-26之间一定存在a的乘法逆元a^-1,使得a\*a^-1≡1(mod26)，在加密函数两侧同时乘以a^-1可得仿射密码的加密函数为：x≡a^-1(e(x)-b)(mod26),其中a^-1可由扩展欧几里得算法求解。以下为已知密钥破解的代码

>             var miwen=document.getElementById("miwen").value.toLowerCase();
>             var result=document.getElementById("mingwenyu");
>             var c=parseInt(document.getElementById("k3").value);    //c的值即为a的逆元
>             var d=parseInt(document.getElementById("k2").value);
>             var mingwen=new Array(0);
>             var code=new Array(0);
>             for(var i=0;i<miwen.length;i++)
>             {
>                 code[i]=(c*(miwen.charCodeAt(i)-97-d+26))%26;
>                 mingwen[i]=String.fromCharCode(code[i]+97);
>             }
>             for(var i=1;i<mingwen.length;i++)
>             {
>                 mingwen[i]=mingwen[i-1]+mingwen[i];
>             }
>             result.value=mingwen[i-1];
#### 暴力破解
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;暴力破解就是尝试所有的可能密钥，得到所有可能的密文，然后从中找出正确的密文

>           var miwen = document.getElementById("miwen").value.toLowerCase();
>           var a = [1, 9, 21, 15, 3, 19, 7, 23, 11, 15, 17, 25];
>           var code = new Array(0);
>           var mingwen = new Array(0);
>           var result=document.getElementById("mingwenyu");
>           for (var j = 0; j < 12; j++)
>               for (var b = 0; b < 26; b++)
>               {
>                   for (var i = 0; i < miwen.length; i++)
>                   {
>                       code[i] = ((a[j] * (miwen.charCodeAt(i) - 97) + b) % 26);
>                       mingwen[i] = String.fromCharCode(code[i] + 97);
>                   }
>                   for (var k = 1; k < miwen.length; k++)
>                   {
>                       mingwen[k] = mingwen[k - 1] + mingwen[k];
>                   }
>                   mingwen[k]=mingwen[k-1]+" \n";
>                   result.value+=mingwen[k];

js代码在浏览器中解析执行，对应的HTML结构如下:
>               <div class="container">
>                   <div class="input">
>                           <div class="input-group input-group-sm">
>                               <span class="input-group-addon" >明文</span>
>                               <input type="text" id="mingwen" class="mingwen form-control">
>                           </div>
>                           <br>
>                           <div class=" k1 input-group">
>                               <span class="words input-group-addon">加密k1</span>
>                               <input type="text"  class="form-control" id="k1">
>                           </div>
>                       <br>
>                           <div class=" k2 input-group">
>                               <span class="input-group-addon">加密k2</span>
>                           <input type="text" class="form-control" id="k2">
>                           </div>
>                       <br>
>                       <div class=" k2 input-group">
>                           <span class="input-group-addon">解密密钥</span>
>                           <input type="text" class="form-control" id="k3">
>                       </div>
>                       <br>
>                       <div class=" output input-group">
>                           <span class="input-group-addon">密文</span>
>                           <textarea id="miwen" class="form-control"></textarea>
>                       </div>
>                       <div class="mingwenyu input-group">
>                           <span class="input-group-addon" >明文</span>
>                           <textarea id="mingwenyu" class="form-control"></textarea>
>                       </div>
>                   </div>
>                   <div class="anniuzu">
>                       <ul>
>                           <li><input type="submit" class="  btn btn-info " value="加密" onclick="jiami()"></li>
>                           <li><input type="submit" class="  btn btn-info "value="求k2"  onclick="qiuk2()"></li>
>                           <li><input type="submit" class="  btn btn-info " value="已知密钥破解"onclick="k2pojie()"></li>
>                           <li><input type="submit" class="  btn btn-info"value="暴力破解"onclick="baopo()"></li>
>                       </ul>
>                   </div>
>               </div>
>               <script src="js/fangshe.js"></script>

样式中引用了bootstrap的ui框架，有需要的可以下载bootstrap并通过以下代码引入：
>          <link rel="stylesheet" href="css/bootstrap.css">
>          <link rel="stylesheet" href="css/bootstrap-theme.css">

自定义CSS
>     body{
>         background-color:bisque;
>     }
>     span{
>         background-color:greenyellow;
>     }
>     
>     .input
>     {
>         position: relative;
>         width:500px;
>         left:200px;
>         top:50px;
>         display: inline-block;
>     }
>     .output{
>         position: relative;
>         top:0px;
>     }
>     .qiumiyao{
>         position: relative;
>         top:40px;
>     }
>     .submit
>     {
>         position: relative;
>         left:100px;
>         top:37px;
>     }
>     .reset
>     {
>         position: relative;
>         left:250px;
>         top:37px;
>     }
>     .jiemi{
>         position: relative;
>         top:50px;
>     }
>     .anniuzu{
>         position: relative;
>         top:-470px;
>         left:725px;
>     }
>     .mingwenyu{
>         position: relative;
>         top: 40px;
>     }
>     #mingwenyu{
>         height: 300px;
>     }
>     ul{
>         list-style: none;
>         float:left;
>         width:200px;
>         height:500px;
>         display: inline-block;
>     }
>     li{
>         width:40px;
>         height:100px;
>     }

![此处输入图片的描述][1]界面效果有一点丑，但是凑合着看吧，毕竟实现算法才是重要的

#### 一点心得
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;之所以不用C++或者PHP是因为相对来说在浏览器中执行相对来说面向用户更加友好，不用python是因为不会,在实现过程中发现用到的API之前都没有用过的，最后通过问大佬解决了问题，中间遇到的问题有一个是取余和取模的区别，这两者在正数处理的时候都是相同的，在处理负数的时候有所不同，请看大佬的解析：http://blog.csdn.net/huasion/article/details/6855900


  [1]: https://s1.ax2x.com/2017/12/17/msyjn.png