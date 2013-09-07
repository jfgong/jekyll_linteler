---
layout: post 
title: liunx基本概念和操作 
---

#环境变量#
	子进程继承父进程的环境变量
	source ~/.profile	//设置环境变量生效
	/etc/profile		//System login profile
	$HOME/.profile		//User's login profile
	$HOME/.cshrc		//read at beginning of execution by each shell
	~/.bashrc and ~/.cshrc	//针对不同shell的配置文件
	login -> /etc/profile -> ~/.profile
	cat /etc/passwd | grep username //可以查看用户默认使用的shell

#本地变量 环境变量#
	TEST=hello		//本地变量定义
	cat script.sh:
	  echo $SHLVL
	  echo TEST is ${TEST:-not set}
	./script.sh		//子shell不继承本地变量
	source ./script.sh	//在当前shell中已定义
	//导出变量,只适用于当前shell及其子进程,但不能从子进程导出到父进程
	export TEST		//临时添加环境变量
	./script.sh		//子shell继承环境变量
	source ./script.sh	//在当前shell中已定义

#压缩解压#
	tar -zcvf shell.tar.gz	shell/	//压缩成gzip文件
	tar -zxvf shell.tar.gz		//将gzip文件解
	tar -jcvf shell.tar.bz2 shell/	//压缩为bz2文件
	tar -jxvf shell.tar.bz2		//将bz2文件解压

#截屏#
	Alt + Printscreen	//活动窗口
	Shift + Printscreen	//自定义窗口
	Ctrl + Printscreen	//全屏幕拷贝至粘贴板

#编码转换#
	//字幕编码多为gbk，将文件编码转换为utf8
	iconv -f gbk -t utf8 Blood\ Diamond.srt > Blood\ Diamond-utf8.srt

#目录空间#
	du -[ahs]		//a(每个文件)s(总计)h(human)

Posted by randombug @ {{ page.date | date_to_string }}
