# WEEK1
## Requests库
* Requests库的7个主要方法
   * requests.request() 构造一个请求
   * requests.get()获取HTML网页的主要方法，对应于HTTP的GET
   * requests.head()获取HTML网页头信息的方法，对应于HTTP的HEAD
   * requests.post()向HTML网页提交POST请求，对应于HTTP的POST
   * requests.put()向HTML网页提交Put请求，对应于HTTP的PUT
   * requests.patch()向HTML网页提交局部修改请求，对应于HTTP的PATCH
   * requests.delete()向HTML网页提交删除请求，对应于HTTP的DELETE
   
&nbsp;

* Requests库的2个重要对象
   * Request
   * Response: 包含服务器返回的所有信息，也包含请求的Request信息，其属性有
      * r.status_code HTTP请求的返回状态，200表示成功
      * r.text HTTP响应内容的字符串形式，即url对应的页面内容
      * r.encoding 从HTTP header中猜测的响应内容的编码方式，charset标签
      * r.apparent_encoding 从内容中分析出的响应内容编码方式
      * r.content 响应内容的二进制形式  

&nbsp;

* 理解异常 r.raise_for_status()在方法内部判断r.status_code是否等于200，不需要 增加额外的if语句，该语句便于利用try‐except进行异常处理

&nbsp;

* HTTP协议
   * http://host[:port][path]：host: 合法的Internet主机域名或IP地址； port: 端口号，缺省端口为80； path: 请求资源的路径
   * HTTP协议对资源的操作：  
      * GET请求获取URL位置的资
      *  HEAD请求获取URL位置资源的响应消息报告，即获得该资源的头部信息
      *  POST请求向URL位置的资源后附加新的数据
      *  PUT请求向URL位置存储一个资源，覆盖原URL位置的资源 
      *  PATCH请求局部更新URL位置的资源，即改变该处资源的部分内容 
      *  DELETE请求删除URL位置存储的资源

&nbsp;

* **kwargs: 控制访问的参数，共13个
   * params: 字典或字节序列，作为参数增加到url中
   * data: 字典、字节序列或文件对象，作为Request的内容
   * json: JSON格式的数据，作为Request的内容
   * headers : 字典，HTTP定制头
   * cookies : 字典或CookieJar，Request中的cookie 
   * auth: 元组，支持HTTP认证功能
   * files   : 字典类型，传输文件
   * timeout : 设定超时时间，秒为单位
   * proxies : 字典类型，设定访问代理服务器，可以增加登录认证
   * allow_redirects: True/False，默认为True，重定向开关 
   * stream  : True/False，默认为True，获取内容立即下载开关 
   * verify  : True/False，默认为True，认证SSL证书开关
   * cert    : 本地SSL证书路径


## 网络爬虫的盗亦有道
* 爬虫引发的问题
   * 性能骚扰 
   * 法律风险 
   * 隐私泄露
   
&nbsp;

* 网络爬虫的限制
   * 来源审查： 检查来访HTTP协议头的User‐Agent域，只响应浏览器或友好爬虫的访问
   * Robots协议：告知所有爬虫网站的爬取策略，要求爬虫遵守
      * 在网站根目录下的robots.txt文件 
      * 基本语法：
             ``` # 注释: *代表所有，   /代表根目录    User‐agent: *     Disallow: / ```


## Requests库爬取实例
[实例一](file://D:/Projects/PythonTest/spider1.3.1.py)

[实例二](file://D:/Projects/PythonTest/spider1.3.2.py)

[实例三](file://D:/Projects/PythonTest/spider1.3.3.py)

[实例四](file://D:/Projects/PythonTest/spider1.3.4.py)

[实例五](file://D:/Projects/PythonTest/spider1.3.5.py)