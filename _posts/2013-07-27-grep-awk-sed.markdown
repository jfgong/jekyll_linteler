---
layout: post 
title: grep-awk-sed学习 
---

#元字符--正则表达式#
	[]		//匹配其中任意一个字符
	* ? [!0-9]	//元字符
	* . [^0-9]	//正则表达式
	^$		//开头或结尾
	*,?,+		//0次或更多,0次或1次,1次或更多

#grep搜索#
	-v(排除字符串)
	-i(关闭缺省的大小写敏感)
	-c(统计匹配行数)
	-o(统计匹配次数)
	-E(允许使用扩展模式|&)		//??&是怎么用的?
	-n(显示行号)
	grep -o "string" file | wc -l	//匹配次数
	grep -n "\<string\>" file.in	//精确匹配(忽略标点符号)
	grep 'a\{2,4\}' file.in		//字符a出现2次至4次
	grep -E 'string1|string2' file.in

#awk搜索#
	awk [-F field-separator] 'command' input-file(s)
	记录:	域1 # 域2 # 域3		//使用'{print $n}'抽取域
	-F:				//指定:作为分隔符,缺省空格
	[!]~: awk '$0 ~ /str/' file.in	//目标模式/pattern/,默认输出$0
	awk '{if($6 > $7) print $1}' file.in
	awk 'BEGIN{} {} END{}' file.in
	NF(number field)  NR(number record)

#sed搜索#
	sed [options] 'command' input-file(s)
	sed 's/from/to/[gpwn]' file.in	//将from替换成to
	sed -n '/pattern/p' file.in	//-n取消默认的打印输出
	sed -n '/pattern/=' file.in	//打印匹配模式的行号,d删除匹配行
	sed '/^$/d' file.in		//删除空行
	sed 's/COL\(...\)//g' file.in	//删除COL后的3个字母
	sed 's/Mr/& Bruce/g' file.in	//在Mr后追加Bruce
	sed 's/Mr/Bruce &/g' file.in	//在Mr前追加Bruce
	/pattern/ i\ a\	c\		//i前插a后插,类比vim的insert,c修改行



Posted by randombug @ {{ page.date | date_to_string }}
