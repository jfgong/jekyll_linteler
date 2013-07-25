---
layout: post 
title: shell学习笔记 
---

#shell学习笔记#

+用户默认的文件权限模式:umask

+当前目录下查找含有string字符的c文件,且该文件以小写字母开头

	将find文件查找的输出作为grep "string" 的参数
	find ./ -name "[a-z]*.c" | xargs grep "string"

+前台后台进程的切换

	firefox 1>/dev/null 2>&1 &	//后台running
	firefox --> ctrl+z --> bg	//前台running --> 后台stopped

	jobs				//显示后台进程
	fg N				//转到前台running
	bg N				//转到后台running

+重定向

	>  写入
	>> 追加

+输入

	echo -e "your name: \c"
	read name

	cat > file
	content of file<ctrl-d>

+

Posted by randombug @ {{ page.date | date_to_string }}
