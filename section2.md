#简学HTTP

##第二章 URL和资源

###2.1 浏览因特网资源
URL是因特网资源的标准化名称，统一资源命名方式。   
URL结构： "方案：//服务器位置/资源路径"
* http://mailto:name@abc.com    (Email帐户)
* ftp://abc.com/a.doc           (word文件)
* rtsp://a.com:554/video        (流媒体)


###2.2 URL语法
secheme://user:password@host:port/path;params?query#frag   
* secheme      - 方案       - 获取资源用哪种方案
* user         - 用户       - 用户名
* password     - 密码       - 密码
* host         - 主机       - 域名或IP地址
* port         - 端口号     - 很多方案有默认端口号(http为80)
* path         - 路径       - 资源服务器上的本地路径
* params       - 参数       - 一些方案会用这这个组件指定输入参数
* query        - 查询       - 如?id=1
* frag         - 片段       - 一部分的资源名称，在客服端使用，如#top

###2.2.1 方案————使用什么协议
告诉服务器用什么协协议解析URL，方案不区分大小写。

###2.2.2 主机和端口
告诉服务器哪台服务器，什么地方找资源。http协议的默认端口号为80

###2.2.3 用户和密码
要求用户名和密码才充许访问资源，如FTP服务器。

###2.2.4 路径
路径说明资源位于服务器什么地方，如/file/index.html

###2.2.5 参数
提供更多的参数来访问资源，如图片有二进制形式和文本形式传输。
如: ftp://abc.com/pub/index.html;type=1

###2.2.6 查询
通过提问来缩小请求资源,如帮助查询数据库
如：http://abc.com/index.html?name=ligang&city=hangzhou

###2.2.7 片段
frag表示一个资源内部的其中一部分，服务器只处理整个对象，片段由客户端使用。





