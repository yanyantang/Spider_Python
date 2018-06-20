# Scrapy    
Scrapy是一个快速功能强大的网络爬虫框架   
  
# Scrapy的安装小测     

	pip（conda） install scrapy
	scrapy -h

# Scrapy爬虫框架结构   

__“5+2”结构：spiders，engine，scheduler，downloader，item pipelines__      

	数据流的三个路径（1）    
	1 Engine从Spider处获得爬取请求(Request) 
	2 Engine将爬取请求转发给Scheduler，用于调度
	
	数据流的三个路径（2）   
	3 Engine从Scheduler处获得下一个要爬取的请求 
	4 Engine将爬取请求通过中间件发送给Downloader 
	5 爬取网页后，Downloader形成响应（Response） 通过中间件发给Engine 
	6 Engine将收到的响应通过中间件发送给Spider处理

	数据流的三个路径（3）
	7 Spider处理响应后产生爬取项（scraped Item） 和新的爬取请求（Requests）给Engine 
	8 Engine将爬取项发送给Item Pipeline（框架出口） 
	9 Engine将爬取请求发送给Scheduler   

	框架入口：Spider的初始爬取请求 
	框架出口：Item Pipeline	


__结构解析__     

	Engine：(1)控制所有模块之间的数据流 (2)根据条件触发事件  不需要用户修改
	Downloader：根据请求下载网页   不需要用户修改
	Scheduler：对所有爬取请求进行调度管理  不需要用户修改
	Spider：(1)解析Downloader返回的响应（Response） (2)产生爬取项（scraped item） (3)产生额外的爬取请求（Request） 需要用户编写配置代码
	Item Pipelines：(1)以流水线方式处理Spider产生的爬取项 (2)由一组操作顺序组成，类似流水线，每个操 作是一个Item Pipeline类型 (3)可能操作包括：清理、检验和查重爬取项中 的HTML数据、将数据存储到数据库  需要用户编写配置代码

	Downloader Middleware ：目的：实施Engine、Scheduler和Downloader 之间进行用户可配置的控制 功能：修改、丢弃、新增请求或响应  用户可以编写配置代码
	Spider Middleware 目的：对请求和爬取项的再处理 功能：修改、丢弃、新增请求或爬取项  用户可以编写配置代码
   
# Scrapy爬虫常用命令 

	startproject  创建一个新工程  scrapy startproject <name> [dir] 
	genspider  创建一个爬虫  scrapy genspider [options] <name> <domain> 
	settings  获得爬虫配置信息  scrapy settings [options] 
	crawl  运行一个爬虫  scrapy crawl <spider> 
	list  列出工程中所有爬虫  scrapy list
	shell  启动URL调试命令行  scrapy shell [url]   

# yield关键字的使用   

包含yield语句的函数是一个生成器   
生成器每次产生一个值（yield语句），函数被冻结，被唤醒后再产生一个值   
生成器是一个不断产生值的函数   


_生成器相比一次列出所有内容的优势：_      

	1)更节省存储空间 
	2)响应更迅速 
	3)使用更灵活
   
# Scrapy爬虫的使用步骤   
	步骤1：创建一个工程和Spider模板 
	步骤2：编写Spider 
	步骤3：编写Item Pipeline 
	步骤4：优化配置策略  

# Scrapy爬虫的数据类型   
	Request类：Request对象表示一个HTTP请求 由Spider生成，由Downloader执行
	Response类：Response对象表示一个HTTP响应 由Downloader生成，由Spider处理
	Item类：Item对象表示一个从HTML页面中提取的信息内容 由Spider生成，由Item Pipeline处理 Item类似字典类型，可以按照字典类型操作

_Request类_
 
	.url   Request对应的请求URL地址 
	.method   对应的请求方法，'GET''POST'等 
	.headers   字典类型风格的请求头 
	.body   请求内容主体，字符串类型 
	.meta   用户添加的扩展信息，在Scrapy内部模块间传递信息使用 
	.copy()   复制该请求   

_Response类_

	.url   Response对应的URL地址  
	.status   HTTP状态码，默认是200 
	.headers   Response对应的头部信息 
	.body   Response对应的内容信息，字符串类型 
	.flags   一组标记
	.request   产生Response类型对应的Request对象 
	.copy()   复制该响应 

# Scrapy爬虫提取信息的方法   
* Beautiful Soup 
* lxml
* re
* XPath Selector 
* CSS Selector   

__CSS Selector的基本使用__
	
	<HTML>.css('a::attr(href)').extract()
