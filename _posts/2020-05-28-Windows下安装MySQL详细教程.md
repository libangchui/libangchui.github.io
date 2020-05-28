---
layout:     post
title:      Windows下安装MySQL详细教程
subtitle:   Windows下安装MySQL详细教程
date:       2020-05-28
author:     Twenty-Nine
header-img: img/post-bg-desk.jpg
catalog: 	 true
tags:
    - MySQL
---

# Windows下安装MySQL详细教程

**Windows下安装MySQL详细教程**

　　**1、安装包下载**

　　  **2、安装教程**

　　　　**（1）配置环境变量**

　　　　**（2）生成data文件**

　　　　**（3）安装MySQL**

　　　　**（4）启动服务**

　　　　**（5）登录MySQL**

　　　　**（6）查询用户密码**

　　　　**（7）设置修改用户密码**

　　　　**（8）退出**

　 　**3、解决问题**

　　

> **1、安装包下载。**

下载地址：https://dev.mysql.com/downloads/mysql/

![img](https://images2018.cnblogs.com/blog/1435523/201809/1435523-20180909145941512-769947425.png)

 

点击下载之后，可以选择注册Oracle账号，也可以跳过直接下载。

![img](https://images2018.cnblogs.com/blog/1435523/201809/1435523-20180909150321246-422217249.png)

下载完成后，选择一个磁盘内放置并解压。

 

2020年2月14日，mysql官网进不去了，好吧~那就来个镜像，总没问题了吧。如果官网龟速下载，建议使用下面镜像巨快。相对的~

**Mysql国内镜像：http://mirrors.sohu.com/mysql/MySQL-8.0/**

**![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200214012521294-416245235.png)**

 

 

 下载完成之后，找到下载的路径，解压即可！

![img](https://img2020.cnblogs.com/blog/1302991/202003/1302991-20200324133824383-1822063458.png)

 

 

 

> **2 安装教程**

**（1）配置环境变量**

变量名：MYSQL_HOME

变量值：C:\software

![img](https://img2020.cnblogs.com/blog/1302991/202003/1302991-20200324134052390-1123768702.png)

 

 

 

**（2）生成data文件**

**以管理员身份运行cmd**

进入C:\software\mysql-8.0.19-winx64.zip\mysql-8.0.19-winx64\bin下

![img](https://img2020.cnblogs.com/blog/1302991/202003/1302991-20200324134148878-135182281.png)

 

 ![img](https://img2020.cnblogs.com/blog/1302991/202003/1302991-20200324134235665-1096276433.png)

 

![img](https://img2020.cnblogs.com/blog/1302991/202003/1302991-20200324134317258-794967649.png)

 

 

 

执行命令：mysqld --initialize-insecure --user=mysql  在C:\software\mysql-8.0.19-winx64.zip\mysql-8.0.19-winx64下和bin同级目录生成data目录

 ![img](https://img2020.cnblogs.com/blog/1302991/202003/1302991-20200324134604050-775796161.png)

 

 

**(3) 安装MySQL**

继续执行命令：mysqld -install

 ![img](https://img2020.cnblogs.com/blog/1302991/202003/1302991-20200324134614902-1738135026.png)

 

 

**（4）启动服务**

继续执行命令：net start MySQL

![img](https://img2020.cnblogs.com/blog/1302991/202003/1302991-20200324134710121-934367759.png)

 

 

 

**（5）登录MySQL**

登录mysql:(因为之前没设置密码，所以密码为空，不用输入密码，直接回车即可）

mysql -u root -p

![img](https://img2020.cnblogs.com/blog/1302991/202003/1302991-20200324134859944-327947261.png)

 

 

 

**（6）查询用户密码**

查询用户密码命令：mysql> select host,user,authentication_string from mysql.user;

![img](https://img2020.cnblogs.com/blog/1302991/202003/1302991-20200324135044540-346081321.png)

 

**（7）设置（或修改）root用户密码**

**mysql>** use mysql

![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200213230557388-1983160880.png)

 

**提别注意：下面这个修改密码的方式不正确，可能是因为版本问题。最近解决了。**

**mysql>** update mysql.user set authentication_string=("123456") where user="root"; 

![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200213230625664-67411486.png)

Query OK, 1 row affected, 1 warning (0.00 sec)

Rows matched: 1  Changed: 1  Warnings: 1

**解决方案如下：**

**mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';**

**![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200214005443070-2007166482.png)**

mysql> flush privileges; 

\#作用：相当于保存，执行此命令后，设置才生效，若不执行，还是之前的密码不变

![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200213230706274-1442278651.png)

Query OK, 0 rows affected (0.01 sec) 

**（8）退出**

mysql> quit

Bye

![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200213230730751-12826274.png)

 **（9）再次登录**

**![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200214005517779-28637674.png)**

 

 

 

> **3、解决问题**

**![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200214005803305-1153038646.png)**

 

 

 ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

**关于修改密码再次登录出现ERROR的解决方案：**

首先问题出现的原因在于可能是因为版本不同，命令有所差异。个人认为，其实无所谓了，最终问题解决了就是了。

如果你是按照上面的完整教程安装出现这种问题的解决方案：

1、所有东西都删除，然后重装，按照上面教程再来一遍；部分内容有更正。特别注意！

2、如果你之前装了，报错之后就一直放在那里，现在请严格按照下面步骤进行：

　　**1、打开cmd，切换到mysql的bin目录下，输入命令net stop mysql，停止mysql服务；**

**![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200214010244062-1805443953.png)**

 

 

 　**2、打开mysql的安装目录，找到data文件夹，将其删除！**

**![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200214010329384-1938042208.png)**

　　**3、回到cmd命令窗口，输入mysqld -remove**

**![img](https://img2018.cnblogs.com/i-beta/1435523/202002/1435523-20200214010423973-525837391.png)**

 

 　**4、接下来按照上面教程，从第二步生成data文件开始执行，一定要注意修改密码那里：**

**mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';**

**mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';**

**mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';**