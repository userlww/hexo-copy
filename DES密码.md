---
title: DES密码
date: 2017-12-29 14:47:01
tags: [密码学,分组密码,DES]
categories: [密码学,分组密码]

---
### DES算法描述
>#### 概述
&nbsp;&nbsp;&nbsp;明文和密文分组均为64比特，有效密钥56比特，由初始代换，16轮迭代，逆初始置换组成。轮函数结构是Feistel网络，加解密算法相同，只是加密子秘钥和解密子密钥的使用顺序相反。加密过程
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![此处输入图片的描述][1]

### 加密过程详解
>#### E—扩展：32比特扩展为48比特
>&nbsp;&nbsp;&nbsp;E盒扩展方法：每个输入分组的4位作为6位输出分组的中间4位，6位输出分组的第一位和第六位分别由相邻两个4位分组的最外两位扩散进入本分组，第一个分组的左侧相邻分组为最后一个分组![E—扩展][2]
>#### 与子密钥异或：
>&nbsp;&nbsp;&nbsp;将E盒扩展得到的48位输出与子密钥Ki进行异或运算。
>#### 压缩替换S-盒：
>&nbsp;&nbsp;&nbsp;由8个S盒组成，每个S盒都是6比特输入，4比特输出。
>&nbsp;&nbsp;&nbsp;Si(h1h2h3h4h5h6)是对应表Si中（h1h6)行和（h2h3h4h5)列上的值![S-盒的构造][3]


>#### P-置换
>&nbsp;&nbsp;&nbsp;P—置换对8个S-盒的输出进行变换
>&nbsp;&nbsp;&nbsp;下图为P—置换对应的表格

>|16|7|20|21|
|:-------:|:------:|:------:|:-----:|
|29|12|28|17|
|1|15|23|26|
|5|18|31|10|
|2|8|24|14|
|32|27|3|9|
|19|13|20|6|
|22|11|4|25|
>#### DES子密钥的生成
>&nbsp;&nbsp;&nbsp;DES密钥是从初始密钥产生的，初始密钥有64位，其中8位用于奇偶校验，分别位于8,16,24,32,40,48,56,64位，用于检查密钥K在产生和分配以及存储的过程中可能发生的错误，所以说DES密钥实际只有56位。
![此处输入图片的描述][4]


  [1]: http://ww1.sinaimg.cn/large/0060lm7Tly1fmxoj1ie3vj30go0avgm6.jpg
  [2]: http://ww3.sinaimg.cn/large/0060lm7Tly1fmxoutokyhj312j081myy.jpg
  [3]: http://ww3.sinaimg.cn/large/0060lm7Tly1fmxxy9gx1cj30m809d77m.jpg
  [4]: http://ww3.sinaimg.cn/large/0060lm7Tly1fmxyzbu3hzj310v0o87ua.jpg