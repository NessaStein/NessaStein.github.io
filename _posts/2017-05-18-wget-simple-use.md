---
layout: post
title: "wget simple use"
date: <2017-05-18 15:47:53>
tags: wget
description: use wget to download directory
share: 
---

# 使用wget下载目录的三种常用方法
  * Download all file in directory

``` shell  
wget -r --no-parent http://example.com/configs/.vim/
```

  * Edit 1: To avoid downloading the index.html files, use this command:

``` shell  
wget -r --no-parent --reject "index.html*" http://example.com/configs/.vim/
```
  * Edit 2: To avoid downloading the directory structure as well:

``` shell
  wget -r -nH -nd -np -R index.html* http://example.com/configs/.vim/
```



