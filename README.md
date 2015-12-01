#简学HTTP

##第一章 HTTP概述

###1.1 HTTP——因特网的多媒体信使        
HTTP使用的是可靠的数据传输协议。        

###1.2 Web客户端和服务器
客户端：请将/index.html给我(HTTP请求)           
服务端：好的，这就是，文档是以HTML格式给出，有3150字节(HTTP响应)    

###1.3 资源
WEB服务器放着Web资源，是Web内容的源头。   
资源可以是文本文件，HTML文件，Word文件，JPEG图片，AVI电影等所有内容来源。     

###1.3.1 媒体类型 （Multipurpose Internet Mail Extension）
WEB服务器会给所有对象数据加上MIME类型。   
格式：对象类型/子类型，如：text/html     
[MIME 参考手册](http://www.w3school.com.cn/media/media_mimeref.asp)

###1.3.2 URI （Uniform Resource Identifier） 
每个WEB资源都有统一资源标识符URI，URI有URL和URN两种形式。
URI如：http://www.abc.com/a.gif     
URN如：urn:ietf:rfc:2141 

###1.3.3 URL （Uniform Resource Location）
URL(统一源资定位符)描述资源的特定位置，如：http://abc.com/a.gif    
URL通常有三部分组成方案( http://)、因特网地址(abc.com)、资源(/a.gif)      
      
###1.3.4 URN （Uniform Resource Name）- 试验阶段
URN（统一资源名）与资源的位置无关，可以将资源四处搬移，如：urn:ietf:rfc:2141

###1.4事务
一个HTTP事件由一个请求(客户端)和一个响应(服务器)结果组成。    
请求会包含http方法和URI，响应结果叫响应报文(HTTP message)

###1.4.1 方法
每条HTTP请求都包含方法，告诉服务器要执行什么动作，常见五种方法如下：  
* get           - 服务器向客户端发资源
* put           - 客户端数据存到服务器
* delete        - 服务器删资源
* post          - 客户端数据发送到服务器网关应用程序
* head          - 仅发送资源响应中的HTTP首部

###1.4.2 状态码
每条HTTP响应报文，都会携带一个状态码，告知客户端是否请求成功，举例：    
* 200 - OK.文档正确返回
* 302 - Redirect (重定向)。到其他地方去获取资源
* 404 - Not Found (没找到)

###1.4.3 一个Web页面可以有多个HTTP事务

###1.5 报文
报文都是纯文本，由一行行的简单字符组成的。   
客户端发起的叫请求报文（request message）。服务器返回叫响应报文（response message）   
* 起始行 - 报文的第一行，说明请求什么，响应什么。
* 首部   - 第二开始为首部，可以有多行，如：Content-length: 403
* 主体   - 返回客户端的数据，任意二进制数据或文本