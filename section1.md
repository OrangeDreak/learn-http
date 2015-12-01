#HTTP权威指南读书笔记

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
![](http://a-402482-80-71883202.www-seoicq-com.anquanbao.cn/uploads/allimg/121206/get-http.png)


###1.6 连接
报文是如何从一个地方搬移到另一个地方的？通过TCP传输控制协议(Transmission Control Protocol)

###1.6.1 TCP/IP
因特网基于TCP/IP，TCP链接传输的报文不会丢失，不会破错，不会错序，保证可靠通信。附http网络协议栈：
* 应用层 - http
* 传输层 - TCP
* 网络层 - IP
* 数据层 - 网络特有的链路接口
* 物理层 - 网络硬件

###1.6.2 连接、IP地址、端口号
TCP链接需要知道服务器的IP和端口号，（就如给别人打电话，需要知道电话号码和分机号）
* http://207.200.83.29:80/index.html (带IP和端口号)
* http://www.netscape.com:80/index.html (IP已经变成的域名，由Domain Name System解析)
* http://www.netscape.com/index.html (默认端口号为80)

###1.6.3 一个使用Telnet的实例
请看书理解。

###1.7 HTTP协议版本
* HTTP/0.9   - 1991年原型版，只支持get，很快被1.0取代
* HTTP/1.0   - 广泛应用最实践，加了版本号，首部和方法
* HTTP/1.0+  - 非正式扩展版，如keep-alive，虚拟主机实现，代理链接支持等
* HTTP/1.1   - 当前使用版本，校正设计，性能优化。
* HTTP/2.0   - 关注性能优化，暂无推广计划。

###1.8 WEB结构组件
* 代理      - 中间实体
* 缓存      - 离客户端近的副本
* 网关      - 链接其他应用程序
* 隧道      - 报文盲发
* Agent代理 - 智能体，自动HTTP请求

###1.8.1 代理
HTTP代理服务器是Web安全，应用集成、性能优化的重要组成模块，代理可以对请求和响应数据进行过滤。

###1.8.2 缓存 (web cache/ proxy cache)
缓存服务器将常用的信息保存起来，客户端从附近缓存下载内容。

###1.8.3 网关 (gateway)
特殊服务器，作为其他服务器的中间实体。
如HTTP/FTP网关对HTTP请求接收FTP URI，通过FTP协议获取文档，封装成HTTP报文，发给客户端。

###1.8.4 隧道 (tunnel)
对原始数据进行盲发，转发时候不会窥探数据。
客户端 -> 隧道起点 -> HTTP链接(加密的SSL流量) -> 隧道终点(80端口) -> SSL连接 -> 服务器(443端口)

###1.8.5Agent代理
用户Agent代理，代表用户发起HTTP请求的客户端程序，如Web浏览器、网络蜘蛛(spiders)、Web机器人(Web robots)等。

###1.9（略）
###1.10(略)