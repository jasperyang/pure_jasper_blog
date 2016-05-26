#shell(awk) learning（大白入门）
	这是个十分牛逼的命令，也算的上一门处理文本的语言了。
###原理
	awk就是把文件逐行的读入，以空格为默认分隔符将每行切片，切开的部分再进行各种分析处理
	awk有3个不同版本: awk、nawk和gawk，未作特别说明，一般指gawk，gawk 是 AWK 的 GNU 版本。
###使用方法
	awk '{pattern + action}' {filenames}
###调用awk
	1.命令行方式
	awk [-F  field-separator]  'commands'  input-file(s)
	其中，commands 是真正awk命令，[-F域分隔符]是可选的。 input-file(s) 是待处理的文件。
	在awk中，文件的每一行中，由域分隔符分开的每一项称为一个域。通常，在不指名-F域分隔符的情况下，默	认的域分隔符是空格。

	2.shell脚本方式	
	将所有的awk命令插入一个文件，并使awk程序可执行，然后awk命令解释器作为脚本的首行，一遍通过键入脚	本名称来调用。	
	相当于shell脚本首行的：#!/bin/sh
	可以换成：#!/bin/awk

	3.将所有的awk命令插入一个单独文件，然后调用：
	awk -f awk-script-file input-file(s)
	其中，-f选项加载awk-script-file中的awk脚本，input-file(s)跟上面的是一样的。
###实例
	常用到 awk '{print $1}'
	解释一下，awk后面的格式通常是'{}'里面可以使用一些函数比如print.
	而$1代表的是第一列，
######因此，再看下面：
	ls -l | awk '{print $1}'
	通过管道ls -l的内容传给awk
	
	-rwxr-xr-x   1 jacobtimber  staff  10024 22 Mar 20:48 a.out
	-rw-r--r--   1 jacobtimber  staff    784 22 Mar 20:32 checkright.cpp
	-rwxr-xr-x   1 jacobtimber  staff  20552 22 Mar 15:38 graph
	-rw-r--r--   1 jacobtimber  staff   4356 22 Mar 15:40 graph.cpp
	-rw-r--r--   1 jacobtimber  staff    375 22 Mar 20:48 monkey.cpp
	drwxr-xr-x  31 jacobtimber  staff   1054 22 Mar 12:52 九度oj/
	drwxr-xr-x   9 jacobtimber  staff    306  7 Mar 14:45 北邮oj/
	
	变成---->
	
	total
	-rwxr-xr-x
	-rw-r--r--
	-rwxr-xr-x
	-rw-r--r--
	-rw-r--r--
	drwxr-xr-x
	drwxr-xr-x
	
	懂了吗~？
	
	
根据上面的好好想想下面这个命令
	
	cat /etc/passwd |awk  -F ':'  '{print $1}'  
	
  **没错**  -F 以 ':'分割接着打印出第一列，大家可以试试看~
  
  
  
   如果只是显示/etc/passwd的账户和账户对应的shell,而账户与shell之间以逗号分割,而且在所有行添加列名name,shell,在最后一行添加"blue,/bin/nosh"。
  	
  
  	cat /etc/passwd |awk  -F ':'  'BEGIN {print "name,shell"}  {print $1","$7} END	{print "blue,/bin/nosh"}'
  	
	name,shell
	root,/bin/bash
	daemon,/bin/sh
	bin,/bin/sh
	sys,/bin/sh
	....
	blue,/bin/nosh
	
######搜索支持正则，例如找root开头的: awk -F: '/^root/' /etc/passwd
	# awk -F: '/root/{print $7}' /etc/passwd             
	/bin/bash
	
	