# 正则表达式    
正则表达式是一种针对字符串表达“简洁”和“特征”思想的工具    
正则表达式可以用来判断某字符串的特征归属   
  
# 正则表达式语法      
正则表达式语法由字符和操作符构成      


__常用操作符__      

	.表示任何单个字符   
	[ ]字符集，对单个字符给出取值范围[abc]表示a、b、c，[a‐z]表示a到z单个字符
	[^ ]非字符集，对单个字符给出排除范围[^abc]表示非a或b或c的单个字符
	*前一个字符0次或无限次扩展abc* 表示ab、abc、abcc、abccc等
	+前一个字符1次或无限次扩展abc+ 表示abc、abcc、abccc等
	?前一个字符0次或1次扩展abc? 表示ab、abc
	|左右表达式任意一个abc|def表示abc、def
	{m}扩展前一个字符m次ab{2}c表示abbc
	{m,n}扩展前一个字符m至n次（含n）ab{1,2}c表示abc、abbc
	^匹配字符串开头^abc表示abc且在一个字符串的开头
	$匹配字符串结尾abc$表示abc且在一个字符串的结尾
	( )分组标记，内部只能使用| 操作符(abc)表示abc，(abc|def)表示abc、def
	\d数字，等价于[0‐9]
	\w单词字符，等价于[A‐Za‐z0‐9_]

__经典正则表达式实例__   

	^[A‐Za‐z]+$ 由26个字母组成的字符串 
	^[A‐Za‐z0‐9]+$ 由26个字母和数字组成的字符串 
	^‐?\d+$ 整数形式的字符串 
	^[0‐9]*[1‐9][0‐9]*$ 正整数形式的字符串 
	[1‐9]\d{5} 中国境内邮政编码，6位 
	[\u4e00‐\u9fa5] 匹配中文字符 
	\d{3}‐\d{8}|\d{4}‐\d{7} 国内电话号码，010‐68913536
	(([1‐9]?\d|1\d{2}|2[0‐4]\d|25[0‐5]).){3}([1‐9]?\d|1\d{2}|2[0‐4]\d|25[0‐5]) IP地址字符串形式的正则表达式（IP地址分4段，每段0‐255）
   
# Re库的基本使用         
Re库是Python的标准库，主要用于字符串匹配 `调用方式：importre`   

re库采用raw string类型表示正则表达式，表示为： `r'text' `

__Re库主要功能函数__   

	re.search(pattern,string,flags=0)在一个字符串中搜索匹配正则表达式的第一个位置，返回match对象
	re.match((pattern,string,flags=0)从一个字符串的开始位置起匹配正则表达式，返回match对象
	re.findall(pattern,string,flags=0)搜索字符串，以列表类型返回全部能匹配的子串
	re.split((pattern,string,maxsplit=0,flags=0)将一个字符串按照正则表达式匹配结果进行分割，返回列表类型
	re.finditer(pattern,string,flags=0)搜索字符串，返回一个匹配结果的迭代类型，每个迭代元素是match对象
	re.sub(pattern,repl, string,count=0,flags=0)在一个字符串中替换所有匹配正则表达式的子串，返回替换后的字符串

	pattern : 正则表达式的字符串或原生字符串表示 
	string : 待匹配字符串 
	flags : 正则表达式使用时的控制标记   
		 re.Ire.IGNORECASE忽略正则表达式的大小写，[A‐Z]能够匹配小写字符 
		 re.Mre.MULTILINE正则表达式中的^操作符能够将给定字符串的每行当作匹配开始 
		 re.Sre.DOTALL正则表达式中的.操作符能够匹配所有字符，默认匹配除换行外的所有字符
	maxsplit: 大分割数，剩余部分作为后一个元素输出 
	repl: 替换匹配字符串的字符串
	count : 匹配的大替换次数 

_函数式用法：一次性操作:_   

	rst=re.search(r'[1‐9]\d{5}', 'BIT 100081')

_面向对象用法：编译后的多次操作:_
 
	pat=re.compile(r'[1‐9]\d{5}') 
	rst=pat.search('BIT 100081')

###### regex = re.compile(pattern,flags=0) 将正则表达式的字符串形式编译成正则表达式对象
###### Re库的另一种等价用法  
	regex.search(string,flags=0)
	regex.match()
	regex.findall()
	regex.split()
	regex.finditer()
	regex.sub()

# Re库的Match对象   
Match对象是一次匹配的结果，包含匹配的很多信息，类型为`<class '_sre.SRE_Match'>`   
_match对象属性_   

	.string待匹配的文本
	.re匹配时使用的patter对象（正则表达式）
	.pos正则表达式搜索文本的开始位置
	.endpos正则表达式搜索文本的结束位置   
_match对象方法_      

	.group(0)获得匹配后的字符串
	.start()匹配字符串在原始字符串的开始位置
	.end()匹配字符串在原始字符串的结束位置
	.span()返回(.start(), .end())
	

# Re库的贪婪匹配和最小匹配   
Re库默认采用贪婪匹配，即输出匹配长的子串   
_最小匹配操作符_    
只要长度输出可能不同的，都可以通过在操作符后增加?变成小匹配  
	
	*?前一个字符0次或无限次扩展，小匹配
	+?前一个字符1次或无限次扩展，小匹配
	??前一个字符0次或1次扩展，小匹配
	{m,n}?扩展前一个字符m至n次（含n），小匹配
		

	  