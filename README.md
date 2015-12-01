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
URL通常有三部分组成方案、因特网地址、资源      
方案：       http://                
因特网地址:  abc.com              
资源：       /a.gif          

###1.3.4 URN （Uniform Resource Name）- 试验阶段
URN（统一资源名）与资源的位置无关，可以将资源四处搬移，如：urn:ietf:rfc:2141