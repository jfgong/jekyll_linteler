---
layout: post 
title: 更新照片的文件名
---

这次国庆回去,拍了一些照片,整理的时候,再次碰到纠结的问题,相机的默认命名方式是在独立目录下使用IMG\_1234这种形式,当需要将不同目录下的照片汇总到一起的时候,就会出现重名的现象.这种命名方式几乎想不到有任何的意义,所以准备将之修改为相机中使用时间来命名的方式.


查资料发现`stat`虽然可以查阅文件的访问,修改和状态更新时间,但是并不能获得照片的最原始创建时间即拍摄时间,但是我们在右键属性中却可以看到拍摄的时间,所以可以考虑对照片进行文本处理的方式来获得拍摄信息.


通过`grep -ao`过滤得到照片的创建时间

	#!/bin/sh 
	sourceDir=$1
	destDir=$2
	mkdir $destDir
	filelist=`ls $sourceDir`
	echo $filelist
	echo "total have `ls $sourceDir | wc -l` files, waiting to change name"
	
	#filter keywords like "2013:10:06 18:30:56"
	pattern="[0-9]\{4\}:[0-9]\{2\}:[0-9]\{2\} [0-9]\{2\}:[0-9]\{2\}:[0-9]\{2\}"
	
	for oldName in $filelist
	do
	    echo "Rename $oldName ......"  
	    #cannot use '$pattern'
	    shootTime=`grep -ao "$pattern" $sourceDir/$oldName | sort -u`

	    echo "$sourceDir/$oldName's shoot time is: $shootTime"
	    base=`echo $shootTime | awk -F"[: ]" '{print $1$2$3"_"$4$5$6}'`
	    #sed 's\ \:\g' $shootTime
	    #base=`echo $shootTime | awk -F: '{print $1$2$3"_"$4$5$6}'`

	    suffix=`echo $oldName | awk -F. '{print $NF}'`
	    newName="$base.$suffix"

	    echo "New name is: $destDir/$newName"
	    cp $sourceDir/$oldName $destDir/$newName
	done

上述代码中,简单赘述:

1.`grep -ao`,其中-a将照片视为文本文件来处理,否则只会提示"Binary file * matches",而-o使grep只输出匹配项.

2.其中pattern变量设置的是形如"2013:10:06 18:30:56"类型的关键字模式

3.`awk -F"[: ]"`指定:和空格作为间隔符


Posted by randombug @ {{ page.date | date_to_string }}
