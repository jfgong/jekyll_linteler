---
layout: post 
title: liunx基本操作 
---

#压缩解压#
	tar -zcvf shell.tar.gz	shell/	//压缩成gzip文件
	tar -zxvf shell.tar.gz		//将gzip文件解
	tar -jcvf shell.tar.bz2 shell/	//压缩为bz2文件
	tar -jxvf shell.tar.bz2		//将bz2文件解压

#环境变量#
	source .profile		//设置环境变量生效

#截屏#
	Alt + Printscreen	//活动窗口
	Shift + Printscreen	//自定义窗口
	Ctrl + Printscreen	//全屏幕拷贝至粘贴板

Posted by randombug @ {{ page.date | date_to_string }}
