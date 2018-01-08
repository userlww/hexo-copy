---
title: web前端暑期基础培训课（二）
date: 2017-12-09 10:53:44
tags: [前端,HTML]
categories: [菜鸟开讲,HTML]

---
&nbsp;&nbsp;&nbsp;&nbsp;第二次课主要跟大家介绍了一下html的标签，第一节课已经说过，HTML(Hypertext Markup Language) 超文本标记语言，是用于描述网页文档的一种标记语言，简单地说就是用一对对标签将开发者要在网页上呈现的内容表现出来。下面我将常见的HTML标签做了一个总结：

|标签名|	含义|	常用属性|	类型|
| ------------- |:-------------------:|:------------------:|
|!DOCTYPE|	声明使用哪种html规范||		
|html|	声明页面的开始和结束|	xmlns:Namespace命名空间|
|head|	页面的头部|	|	
|body|	页面的主体||		
|title|	只能放在head中，用于标明页面的标题||		
|meta|放在head中，用于描述页面的元数据||		
|b|	bold   文本加粗，描述样式Xhtml中已废弃||inline
|strong|	文本加粗，描述语义	xHTML中推荐使用，代替b||	inline
|i|	文本斜体显示，描述样式	XHTML中已废弃||	inline
|em|	文本斜体显示，描述语义	XHTML中推荐使用，代替i||	inline
|sup|	上标字，描述样式||		inline
|sub|	下标字，描述样式||		inline
|u|underline 下划线，描述样式|		inline
|s|	删除线，描述样式	||	inline
|h1,h2....,h6|	标题字，描述语义	注意：在各个浏览器中默认的字体高度和的间距不一致||	block
|span|	行内分区工具，是最简单的内联标签,必须与CSS、JS配合使用，才会有效果||	inline
|a|	锚	href:指定要跳转的url、邮箱、js函数|name:指定可供停靠的锚点名称; target:指定在哪个页面中打开(_self/_blank)|	inline
|img|	通知浏览器此刻要向服务器请求图片资源|	src:指定图片资源的url;       alt:若图片无法显示则显示此文字内容;width:百分比/像素;height:百分比/像素;title|	inline
|input|	输入组件，包含文本框，按钮等类型||inline
|select|	下拉框||	inline
|optgroup|	选项组||	inline
|option|	选项||inline
|textarea|多行文本输入域，只能输入纯文本||inline
|button|按钮||		inline
|label|标签，用于给输入域添加提示文字||	inline
|div|	元素分组工具 ，常用于页面布局、内容分层，是最简单的block元素||		block
|p|	段落标签，描述语义	||	block
|hr|	水平分割线||	block
|pre|	使用源代码中的效果呈现内容||		block
|table|表格||			block
|ul|	无序列表|	|	block
|li|	列表项||		block
|ol|	有序列表||	block
|dl|	自定义列表||		block
|dt|||			block
|dd|||			block

注：inline表示行内元素，block表示块状元素
