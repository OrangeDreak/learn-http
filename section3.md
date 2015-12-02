#HTTP权威指南读书笔记

###第三章 HTTP报文
HTTP报文是HTTP应用程序之间发送的数据块，在客户端、服务器、代理之间流动。


###3.1.1 报文流入源端服务器
* 客户端 -> 服务器 (流入，inbound)
* 服务器 -> 客户端 (流出，outbound)


###3.1.2 报文向下流动
报文会像河水一样流动，所有报文都向下流(downstream)滚动
* 客户端(上游) -> 请求报文 -> 服务端(下游)
* 服务端(上游) -> 响应报文 -> 客户端(下游)

### 3.2 报文的组成部分
* 起始行 (start line)
* 首　部 (header)
* 主  体 (body)可以为文本、二进制文件或为空
起始行和首部每行都需要行分隔符        
行分隔符由一个回车符 + 一个换行符组成         


### 3.2.1报文语法
请求报文语法：
```
<method/方法> <request-URL/请求URL> <版本>
<headers/首部>

<entity-body/主体>
```

响应报文语法：
```
<version/版本> <status/状态码> <reason-phrase/原因短语>
<headers/首部>

<entity-body/主体>
```


### 3.2.2 起始行

\*请求行\*              
请求报文起始行 -> 说明要做什么。              
例：GET /gest/hi-there.txt HTTP/1.1              

\*响应行\*         
响应报文起始行 -> 说明发生了什么。        
例：HTTP/1.0 200 ok    

\*方法\*
方法告知服务器要做什么，常用的HTTP方法：

<table>
    <tr>
        <td>方法</td>
        <td>描述</td>
        <td>是否包含主体</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>从服务器获取文档</td>
        <td>否</td>
    </tr>
    <tr>
        <td>HEAD</td>
        <td>只从服务器获取文档的首部</td>
        <td>否</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>向服务器发送需要处理的数据</td>
        <td>是</td>
    </tr>
    <tr>
        <td>PUT</td>
        <td>将请求的主体存在服务器</td>
        <td>是</td>
    </tr>
    <tr>
        <td>TRACE</td>
        <td>对可能经过代理服务传送到服务器的报文追踪</td>
        <td>否</td>
    </tr>
    <tr>
        <td>OPTIONS</td>
        <td>决定可以在服务器上执行哪些方法</td>
        <td>否</td>
    </tr>
    <tr>
        <td>DELETE</td>
        <td>从服务器删除文档</td>
        <td>否</td>
    </tr>
</table>


\*状态码和原因短语\*
状态码告知客户端发生了什么。            
原因短语是对状态码的说明。            

100~101 信息提示                      
200~206 成功                   
300~305 重定向                   
400~415 客户端错误                  
500~505 服务器错误             

[状态码大全](http://www.w3school.com.cn/tags/html_ref_httpmessages.asp)

\*版本号\*
将自己遵守的协议告知对方,版本号格式：HTTP/x.y      
HTTP/2.22比HTTP/2.3要高，不按数字来比较            

###3.2.3首部 
起始行可以跟零行或多行首部，每行为一个键值对。
