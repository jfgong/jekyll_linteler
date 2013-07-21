---
layout: post
title: adb调试android
---

#配置文件#

断开手机物理连接后重新连上，比较两种条件下的lsusb输出差别：

	Bus 003 Device 003: ID 19d2:1382 ZTE WCDMA Technologies MSM

在\/etc\/udev\/rules.d\/目录下创建配置文件: android\_smartphone.rules

配置参数:

	#ZTE U880
	SUBSYSTEM=="usb", SYSFS{"High Tech Computer Corp."}=="19D2", MODE="0666"

其中的19D2取自lsusb的输出.

设定配置文件的权限

	sudo chmod a+rx /etc/udev/rules.d/android_smartphone.rules
	sudo /etc/init.d/udev restart

#重启adb服务#

	sudo adb kill-server
	sudo adb devices
没配置adb环境变量的话，需要提供adb执行文件的绝对地址


#建立连接#
`adb shell`即可连上android手机
进入手机后权限是$，执行`su`，获得root权限

#拷贝文件#
	adb push Downloads/怒放的生命.mp3 /sdcard/music/
注意是在桌面环境下执行

其他操作：

	The "adb push <local> <remote>" copies a file or folder from the local system to the remote emulator or device.    
	The "adb pull <remote> <local>" copies a file or folder from the remote emulator or device to the local system.    
	The "adb install xx.apk" or "adb push xx.apk /system/app" installs software on connected Android emulator or device.

Reference:
[Linux下Android ADB驱动安装详解](http://blog.csdn.net/zhenwenxian/article/details/5901350)
[adb shell 连接手机使用Root权限，sqlite](http://www.pocketdigi.com/20110409/238.html)
[android adb push 与 adb install的比较(两种安装APK的方法)](http://blog.csdn.net/xuxinshao/article/details/7182002)

Posted by randombug @ {{ page.date | date_to_string }}
