---
layout: post
title: "sed insert empty line"
date: <2017-06-06 14:30:38>
tags: sed
description: sed insert empty line
share: false
---

# sed空行

## 添加空行
1. 每行后面添加一行空行:
```
sed G tmp
```

2. 每行前面添加一行空行：

``` shell
sed '{x;p;x;}' tmp
```

3. 每行后面添加两行空行：

``` shell
sed 'G;G' tmp
```

4. 每行前面添加两行空行：

``` shell
sed "{x;p;x;x;p;x;}" tmp
```

5. 每行后面添加三行空行：

``` shell
sed  'G;G;G'  tmp
```

6. 每行前面添加三行空行：

``` shell
sed "{x;p;x;x;p;x;x;p;x}" tmp
```

>依次类推，添加几行空行，就有几个G或者x;p;x


## 若是行后有空行，则删除，然后每行后面添加空行
``` shell
sed "/^$/d;G" tmp
```


## 在匹配行前后添加空行


1. 若是一行里面有shui这个单词，那么在他后面会添加一个空行

``` shell
sed "/shui/G" tmp
```


2. 若是一行里面有shui这个单词，那么在他前后各添加一个空行

``` shell
sed "/shui/{x;p;x;G}" tmp
```


3. 若是一行里面有shui这个单词，那么在他前面添加一个空行

``` shell
sed "/shui/{x;p;x;}" tmp
```


4. 在第一行前面添加空行，想在第几行，号令中的1就改成几

``` shell
sed '1{x;p;x;}' tmp
```


5. 在第一行后面添加空行，想在第几行，号令中的1就改成几

``` shell
sed '1G' tmp
```


## 每几行后面添加一个空行

1. 每两行后面增长一个空行

``` shell
sed "N;/^$/d;G" tmp
```

2. 每两行前面添加一个空行

``` shell
sed "N;/^$/d;{x;p;x;}" tmp
```

3. 每三行后面增长一个空行

``` shell
sed "N;N;/^$/d;G" tmp
```

4. 每三行前面增长一个空行

``` shell
sed "N;N;/^$/d;{x;p;x;}" tmp
```


## 以x为开首或以x为结尾的行前后添加空行


1. 以xi为开首的行后面添加空行

``` shell
sed  "/^xi/G;" tmp
```

2. 以xi为结尾的行前面添加空行

``` shell
sed "/^xi/{x;p;x;}" tmp
```

3. 以xi为结尾的行后面添加空行

``` shell
sed "/xi$/G;" tmp
```

4. 以xi为结尾的行后面添加空行

``` shell
sed "/xi$/{x;p;x;}" tmp
```

