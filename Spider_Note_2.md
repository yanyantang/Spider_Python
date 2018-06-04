##Unit4   

#Beautiful Soup库的安装 
	pip install beautifulsoup4     
 
#Beautiful Soup库的安装测试   
	from bs4 import BeautifulSoup
	soup = BeautifulSoup(demo,'html.parser')
	print(soup.prettify())      #格式化输出

#BeautifulSoup类的基本元素   
* Tag
* Name 格式：<tag\>.name
* Attributes 格式：<tag\>.attrs
* NavigableString 格式：<tag\>.string
* Comment   
#Beautiful Soup库解释器   
* 'html.parser' 
* 'lxml'
* 'xml'
* 'html5lib'   
#基于bs4库的HTML内容遍历方法   
__下行遍历__      
   
* .contents子节点的列表，将<tag>所有儿子节点存入列表   

* .children子节点的迭代类型，与.contents类似，用于循环遍历儿子节点   
* .descendants子孙节点的迭代类型，包含所有子孙节点，用于循环遍历

  
   
__上行遍历__           

* .parent节点的父亲标签
* .parents节点先辈标签的迭代类型，用于循环遍历先辈节点   

__平行遍历__   

* .next_sibling返回按照HTML文本顺序的下一个平行节点标签    
* .previous_sibling返回按照HTML文本顺序的上一个平行节点标签 
* .next_siblings迭代类型，返回按照HTML文本顺序的后续所有平行节点标签 
* .previous_siblings迭代类型，返回按照HTML文本顺序的前续所有平行节点标签

##Unit5
#XML
	<name> … </name>   
	<name />   
	<!‐‐‐‐>   

#JSON
	“key” :“value”
	“key” :[“value1”,“value2”] 
	“key” : {“subkey” :“subvalue”}
  
#YAML  
	key :value
	key :#Comment 
	‐value1 
	‐value2     
	key :
		subkey:subvalue
#比较
XML 最早的通用信息标记语言，可扩展性好，但繁琐 `Internet上的信息交互与传递`   

JSON 信息有类型，适合程序处理(js)，较XML简洁 `移动应用云端和节点的信息通信，无注释`   

YAML  信息无类型，文本信息比例最高，可读性好 `各类系统的配置文件，有注释易读`

#基于bs4库的HTML内容查找方法
	<>.find_all(name,attrs,recursive, string, **kwargs) #<tag>(..) 等价于<tag>.find_all(..) ，soup(..) 等价于soup.find_all(..)
* name : 对标签名称的检索字符串 
* attrs: 对标签属性值的检索字符串，可标注属性检索 
* recursive: 是否对子孙全部检索，默认True 
* string: <>…</>中字符串区域的检索字符串

__扩展方法__    

* <>.find()搜索且只返回一个结果，同.find_all()参数
* <>.find_parents()在先辈节点中搜索，返回列表类型，同.find_all()参数
* <>.find_parent()在先辈节点中返回一个结果，同.find()参数
* <>.find_next_siblings()在后续平行节点中搜索，返回列表类型，同.find_all()参数
* <>.find_next_sibling()在后续平行节点中返回一个结果，同.find()参数
* <>.find_previous_siblings()在前序平行节点中搜索，返回列表类型，同.find_all()参数
* <>.find_previous_sibling()在前序平行节点中返回一个结果，同.find()参数

 
