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

####请求行             
请求报文起始行 -> 说明要做什么。              
例：GET /gest/hi-there.txt HTTP/1.1              

#### 响应行      
响应报文起始行 -> 说明发生了什么。        
例：HTTP/1.0 200 ok    

#### 方法
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


#### 状态码和原因短语
状态码告知客户端发生了什么。            
原因短语是对状态码的说明。            

100~101 信息提示                      
200~206 成功                   
300~305 重定向                   
400~415 客户端错误                  
500~505 服务器错误             

[状态码大全](http://www.w3school.com.cn/tags/html_ref_httpmessages.asp)

####版本号
将自己遵守的协议告知对方,版本号格式：HTTP/x.y      
HTTP/2.22比HTTP/2.3要高，不按数字来比较            

###3.2.3首部 
首部跟在起始行后面，可以跟零行或多行，每行为一个键值对，他给请求报文和响应报文添加一些附加信息。

<table>
    <tr>
        <td>首部实例</td>
        <td>描述</td>
    </tr>
    <tr>
        <td>Date:Tue,3Oct 1997 02:16:03 GMT</td>
        <td>服务器响应时间</td>
    </tr>
    <tr>
        <td>Content-length:15040</td>
        <td>主体有15040字节</td>
    </tr>
    <tr>
        <td>Content-type:image/gif</td>
        <td>主体是gif图</td>
    </tr>
    <tr>
        <td>Accept:image/gif, image/jpeg, text/html</td>
        <td>客户可接收的文件类型</td>
    </tr>
</table>


###3.2.4 实体的主体部分
主体是HTTP报文要传输的内容，可以承载很多类型的数据，如图片、视频、html文档、软件、电子邮件等。

###3.2.5 版本0.9的报文
求请只有方法和URL，响应只有主体。


###3.3 方法

###3.3.1 方法安全
GET和HEAD方法被认为是安全的方法。

###3.3.2 GET
请求服务器发送资源。

###3.3.3 HEAD
请求服务器发送资源，但只发送首部。
有了首部可以知道资源信息,判断是否存在，是否变化等。


###3.3.4 PUT
向服务器写入文档，服务器一般会要求密码认证。


###3.3.5 POST
向服务器写入数据，如表单提交。


### 3.3.6 TRACE
跟踪请求，可以知道最终发送给出服务器的请求。             
因为请求可能经过防火墙，代理或网关，请求数据可能被修改。              
服务器会在响应报文中加入TRACE响应信息      

TRACE缺点：
* 不提供区分方法机制
* 请求中不能带主体


### 3.3.7 OPTIONS
可以询问服务器，针对什么资源支持什么方法。


### 3.3.8 DELETE
请求服务器删除资源


### 3.3.9(略)

### 3.3.4 状态码
状态码分类5大类：   
100~199 信息提示                      
200~299 成功                   
300~399 重定向                   
400~499 客户端错误                  
500~599 服务器错误   

### 3.4.1 100~199——信息性状态码

<table class="dataintable">
<tbody><tr>
<th style="width:40%;">消息:</th>
<th style="width:60%;">描述:</th>
</tr>
<tr>
<td>100 Continue</td>
<td>服务器仅接收到部分请求，但是一旦服务器并没有拒绝该请求，客户端应该继续发送其余的请求。</td>
</tr>
<tr>
<td>101 Switching Protocols</td>
<td>服务器转换协议：服务器将遵从客户的请求转换到另外一种协议。</td>
</tr>
</tbody>
</table>

### 3.4.2 200~299——成功状态码

<table class="dataintable">
  <tbody><tr>
    <th style="width:40%;">消息:</th>
    <th style="width:60%;">描述:</th>
  </tr>
  <tr>
    <td>200 OK</td>
    <td>请求成功（其后是对GET和POST请求的应答文档。）</td>
  </tr>
  <tr>
    <td>201 Created</td>
    <td>请求被创建完成，同时新的资源被创建。</td>
  </tr>
  <tr>
    <td>202 Accepted</td>
    <td>供处理的请求已被接受，但是处理未完成。</td>
  </tr>
  <tr>
    <td>203 Non-authoritative Information</td>
    <td>文档已经正常地返回，但一些应答头可能不正确，因为使用的是文档的拷贝。</td>
  </tr>
  <tr>
    <td>204 No Content</td>
    <td>没有新文档。浏览器应该继续显示原来的文档。如果用户定期地刷新页面，而Servlet可以确定用户文档足够新，这个状态代码是很有用的。</td>
  </tr>
  <tr>
    <td>205 Reset Content</td>
    <td>没有新文档。但浏览器应该重置它所显示的内容。用来强制浏览器清除表单输入内容。</td>
  </tr>
  <tr>
    <td>206 Partial Content</td>
    <td>客户发送了一个带有Range头的GET请求，服务器完成了它。</td>
  </tr>
</tbody></table>


### 3.4.3 300~399——重定向状态码

<table class="dataintable">
  <tbody><tr>
    <th style="width:40%;">消息:</th>
    <th style="width:60%;">描述:</th>
  </tr>
  <tr>
    <td>300 Multiple Choices</td>
    <td>多重选择。链接列表。用户可以选择某链接到达目的地。最多允许五个地址。</td>
  </tr>
  <tr>
    <td>301 Moved Permanently</td>
    <td>所请求的页面已经转移至新的url。</td>
  </tr>
  <tr>
    <td>302 Found</td>
    <td>所请求的页面已经临时转移至新的url。</td>
  </tr>
  <tr>
    <td>303 See Other</td>
    <td>所请求的页面可在别的url下被找到。</td>
  </tr>
  <tr>
    <td>304 Not Modified</td>
    <td>未按预期修改文档。客户端有缓冲的文档并发出了一个条件性的请求（一般是提供If-Modified-Since头表示客户只想比指定日期更新的文档）。服务器告诉客户，原来缓冲的文档还可以继续使用。</td>
  </tr>
  <tr>
    <td>305 Use Proxy</td>
    <td>客户请求的文档应该通过Location头所指明的代理服务器提取。</td>
  </tr>
  <tr>
    <td>306 <i>Unused</i></td>
    <td>此代码被用于前一版本。目前已不再使用，但是代码依然被保留。</td>
  </tr>
  <tr>
    <td>307 Temporary Redirect</td>
    <td>被请求的页面已经临时移至新的url。</td>
  </tr>
</tbody></table>


### 3.4.4 400~499——客户端错误状态码

<table class="dataintable">
  <tbody><tr>
    <th style="width:40%;">消息:</th>
    <th style="width:60%;">描述:</th>
  </tr>
  <tr>
    <td>400 Bad Request</td>
    <td>服务器未能理解请求。</td>
  </tr>
  <tr>
    <td>401 Unauthorized</td>
    <td>被请求的页面需要用户名和密码。</td>
  </tr>
  <tr>
    <td>402 Payment Required</td>
    <td>此代码尚无法使用。</td>
  </tr>
  <tr>
    <td>403 Forbidden</td>
    <td>对被请求页面的访问被禁止。</td>
  </tr>
  <tr>
    <td>404 Not Found</td>
    <td>服务器无法找到被请求的页面。</td>
  </tr>
  <tr>
    <td>405 Method Not Allowed</td>
    <td>请求中指定的方法不被允许。</td>
  </tr>
  <tr>
    <td>406 Not Acceptable</td>
    <td>服务器生成的响应无法被客户端所接受。</td>
  </tr>
  <tr>
    <td>407 Proxy Authentication Required</td>
    <td>用户必须首先使用代理服务器进行验证，这样请求才会被处理。</td>
  </tr>
  <tr>
    <td>408 Request Timeout</td>
    <td>请求超出了服务器的等待时间。</td>
  </tr>
  <tr>
    <td>409 Conflict</td>
    <td>由于冲突，请求无法被完成。</td>
  </tr>
  <tr>
    <td>410 Gone</td>
    <td>被请求的页面不可用。</td>
  </tr>
  <tr>
    <td>411 Length Required</td>
    <td>"Content-Length" 未被定义。如果无此内容，服务器不会接受请求。</td>
  </tr>
  <tr>
    <td>412 Precondition Failed</td>
    <td>请求中的前提条件被服务器评估为失败。</td>
  </tr>
  <tr>
    <td>413 Request Entity Too Large</td>
    <td>由于所请求的实体的太大，服务器不会接受请求。</td>
  </tr>
  <tr>
    <td>414 Request-url Too Long</td>
    <td>由于url太长，服务器不会接受请求。当post请求被转换为带有很长的查询信息的get请求时，就会发生这种情况。</td>
  </tr>
  <tr>
    <td>415 Unsupported Media Type</td>
    <td>由于媒介类型不被支持，服务器不会接受请求。</td>
  </tr>
  <tr>
    <td>416&nbsp;</td>
    <td>服务器不能满足客户在请求中指定的Range头。</td>
  </tr>
  <tr>
    <td>417 Expectation Failed</td>
    <td>&nbsp;</td>
  </tr>
</tbody></table>


### 3.4.5 500~599——服务器错误状态码

<table class="dataintable">
  <tbody><tr>
    <th style="width:40%;">消息:</th>
    <th style="width:60%;">描述:</th>
  </tr>
  <tr>
    <td>500&nbsp;Internal Server Error</td>
    <td>请求未完成。服务器遇到不可预知的情况。</td>
  </tr>
  <tr>
    <td>501 Not Implemented</td>
    <td>请求未完成。服务器不支持所请求的功能。</td>
  </tr>
  <tr>
    <td>502 Bad Gateway</td>
    <td>请求未完成。服务器从上游服务器收到一个无效的响应。</td>
  </tr>
  <tr>
    <td>503 Service Unavailable</td>
    <td>请求未完成。服务器临时过载或当机。</td>
  </tr>
  <tr>
    <td>504 Gateway Timeout</td>
    <td>网关超时。</td>
  </tr>
  <tr>
    <td>505 HTTP Version Not Supported</td>
    <td>服务器不支持请求中指明的HTTP协议版本。</td>
  </tr>
</tbody></table>


###3.5 首部
首部和方法配合工作，共同决定客户端和服务器能做什么事情。

###3.5.1 通用首部
```
Connection            //允许客户端和服务器指定与请求/响应连接有关的选项

Date                  //提供日期和时间标志，说明报文是什么时间创建的

MIME-Version          //给出了发送端使用的MIME版本

Trailer               //如果报文采用了分块传输编码方式，就可以用这个首部列出位于报文拖挂部分的首部集合

Transfer-Encoding     //告知接收端为了保证报文的可靠传输，对报文采用了什么编码方式

Update                //给出了发送端可能想要”升级”使用的新版本或协议

Via                   //显示报文经过的中间节点（代理，网关）

Cache-Control         //用于随报文传送缓存指示

Pragma                //另一种随报文传送指示的方式，但并不专用于缓存
```

###3.5.2 请求首部
```
Client-IP             //提供了客户端的机器的IP地址

From                  //提供客户端用户的E-mail地址

Host                  //给出了接收请求的服务器的主机名和端口

Refer                 //提供了包含当前请求URI的文档的URL

UA-Color              //提供了客户端像是器的显示颜色有关的信息

UA-CPU                //给出了客户端CPU的类型或制造商

UA-Disp               //提供了客户端显示器(屏幕)能力有关信息

UA-OS                 //给出了运行在客户端机器上的操作系统名称及版本

UA-Pixels             //提供了客户端显示器的像素信息

User-Agent            //将发起请求的应用程序告知服务器

Accept                //告诉服务器能够发送哪些媒体内容

Accept-Charset        //告诉服务器能够发送哪些字符集

Accept-Encoding       //告诉服务器能够发送哪些字符集

Accept-Language       //告诉服务器能够发送哪些语言

TE                    //告诉服务器能够使用哪些扩展传输编码

Expect                //允许客户端列出某种请求所要求的服务器行为

If-Match              //如果实体标记与文档当前的实体标记相匹配，就获取这份文档

If-Modified-Since     //除非在某个指定的日期之后资源被修改过，否则就限制这个请求

If-None-Match         //如果实体提供的实体标记与当前文档的实体标记不相符,就获取这份文档

If-Range              //允许对文档的某个范围进行条件请求

If-Unmodified-Since   //除非在某个指定日期之后资源没有被修改过，否则就限制这个请求

Range                 //如果服务器支持范围请求，就请求资源的指定范围

Authorization         //包含了客户端提供给服务器，以便对其自身进行认证的数据

Cookie                //客户端用它向服务器传送一个令牌——它并不是真正的安全首部，但确实隐含了安全功能

Cookie2               //用来说明请求端支持的cookie版本

Max-Forward           //在通往源端服务器的路径上，将请求转发给其他代理或网关的最大次数——与TRACE方法一同使用

Proxy-Authorization   //与Authorization首部相同，但这个首部在于代理进行认证时使用

Proxy-Connection      //与Connection首部相同，但是这个首部是与代理建立连接时使用
```

###3.5.3 响应首部
```
Age                   //（从最初创建开始）响应持续时间

Public                //服务器为其资源支持的请求方法列表

Retry-After           //如果资源不可用的话,在此日期或时间重试

Server                //服务器应用软件的名称和版本

Title                 //对HTML文档来说，就是HTML文档的源端给出的标题

Warning               //比原因短语中更详细一些的警告报文

Accept-Range          //对此资源来说，服务器可接受的范围类型

Vary                  //服务器查看的其他首部的列表，可能会使响应发生变化；也就是说，这是一个首部列表，服务器会根据这些首部的内容挑选出最适合的资源版本发送给客户端

Proxy-Authenticate    //来自代理的对客户端的质询列表

Set-Cookie            //不是真正的安全首部，但隐含有安全功能;可以在客户端设置一个令牌,以便服务器对客户端进行标识

Set-Cookie2           //与Set-Cookie类似

WWW-Authenticate      //来自服务器的对客户端的质询列表
```

3.5.4 实体首部
```
Allow                 //列出了可以对此实体执行的请求方法

Location              //告知客户端实体实际上位于何处；用于将接收端定向到资源的位置上去

Content-Base          //解析主体中的相对URL时使用的基础URL

Content-Encoding      //对主体执行的任意编码方式

Content-Language      //理解主体时最适宜使用的自然语言

Content-Length        //主体的长度或尺寸

Content-Location      //资源实际所处的位置

Content-MD5           //主体MD5校验和

Content-Range         //在整个资源中此实体表示的字节访问

Content-Type          //这个主体的对象类型

ETag                  //与此实体相关的实体标记

Expires               //实体不再有效，要从原始的源端再次获取此实体的日期和时间

Last-Modified         //这个实体最后一次被修改的日期和时间                
```