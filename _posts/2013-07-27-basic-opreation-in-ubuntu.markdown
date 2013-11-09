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
	Alt + Printscreen		//活动窗口
	Shift + Printscreen		//自定义窗口
	Ctrl + Printscreen		//全屏幕拷贝至粘贴板
	sleep 5; gnome-screenshot	//延迟5秒,及时打开菜单,等待截图程序启动

#编码转换#
	//字幕编码多为gbk，将文件编码转换为utf8
	iconv -f gbk -t utf8 Blood\ Diamond.srt > Blood\ Diamond-utf8.srt

#disk usage#
	du -[ahs]		//a(每个文件)s(总计)h(human)

#几种查找
	find		//针对文件
	locate		//针对文件,在数据库文件中搜索,类似find -m,不搜索具体目录,比find快
	whereis		//针对命令,搜索二进制(-b)man说明文件(-m)源文件(-s)
	which		//针对命令,在$PATH指定的路径中搜索,显示命令的路径
	type		//针对命令,命令由shell自带的，还是由shell外部的独立二进制文件提供

#问题
1.sudo提示command not found

在/bin或者/usr/bin中添加具体command的link


Posted by randombug @ {{ page.date | date_to_string }}
