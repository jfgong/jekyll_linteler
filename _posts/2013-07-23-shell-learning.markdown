---
layout: post 
title: shell学习笔记 
---

#shell学习笔记#

#用户默认的文件权限模式:umask#

#环境变量#
	echo "The PATH is: ${PATH:-not set}"	//判断环境变量是否设置
	echo "The TIME is: ${TIME:=15:37}"	//若未设置,顺便赋值

#变量参数#
	$0 脚本名,应用名        $[1-9]参数
	$# 参数个数
	$$ 进程ID               $? 退出状态,0表示无错误
	$@ 使用""括起每个参数   $* 显示所有参数,可超过9个

#查找#
	#将find输出作为grep "string" 的输入,无xargs,查找的是文件名
	find ./ -name "[a-z]*.c" | xargs grep "string"
	grep "string" file.in
	find ./ -empty -type d          //搜索当前目录下的空目录
	find ./ -empty -type f          //搜索当前目录下的空文件
	find ./ -name "*" -mmin -10	//过去10分钟修改的文件

#前台后台进程的切换#
	firefox 1>/dev/null 2>&1 &	//后台running
	firefox --> ctrl+z --> bg	//前台running --> 后台stopped

	jobs (显示后台进程) -- fg N (转到前台running) -- bg N (转到后台running)

#输入输出#
	#0 标准输入,1 标准输出,2 标准错误
	command file.in <==> command < file.in <==> file.in | command
	echo -e "your name: \c" --> read name
	cat > file --> content of file<ctrl-d>
	cat >> file << EOF		//向file追加内容,以EOF结束

#重定向-管道#
	# >写入 >>追加
	sort < file.in > file.out	//>操作会删除file.out的全部内容
	#标准输出和标准错误都输出到file.out
	command > file.out 2>&1 <==> command >& file.out
	command 1>file.out 2>file.out	//与上述不同,2>会在file.out开始处覆盖写入
	#列出系统中所有的文件系统,注意重定向不会回显,而tee会回显
	df -k | awk '{print $1}' | grep -v "Filesystem" | sed 's/\/dev\///g' | tee file.system
	cat file.system

#命令执行顺序#
	&&  ||
	(command1;command2) 当前shell执行
	{command1;command2} 子shell中执行

#条件判断#
	#注意shell中0为真,其它为假
	test -d file <==> [ -d file ]	//d目录f正规文件L符号链接rwx读写执行
	-a 逻辑与and  -o 逻辑或or  ! 逻辑否

#循环#
	while read LINE - do - done < file.in

#定义shell函数#
	source function.sh	//载入shell,以便在脚本和命令行中调用,set查看
	shift VS getopts	//get options

#调试#
	set -x		//打开shell调试模式,先输出命令,再输出结果
	set +x		//关闭shell调试模式,搭配echo进行调试

Posted by randombug @ {{ page.date | date_to_string }}
