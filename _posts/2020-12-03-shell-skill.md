---
title: Shell Skill
author: Mrlu
date: 2020-12-03 10:40:00 +0800
categories: [shell]
tags: [shell]
published: true
comments: false
image: /assets/img/sample/shell.jpeg
---

Shell skill 日常 编写shell脚本积累的一些，方式和技巧收录。
以备平时快速开发使用

---

## Shell
Shell 是一个用 C 语言编写的程序，它是用户使用 Linux 的桥梁。Shell 既是一种命令语言，又是一种程序设计语言。

Shell 是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务。

Ken Thompson 的 sh 是第一种 Unix Shell，Windows Explorer 是一个典型的图形界面 Shell。


## header
`#!/bin/sh | #!/bin/bash`

## Set命令 
`set -e # Exit the script if an error happens`
[Linux set命令](https://www.runoob.com/linux/linux-comm-set.html)

## Shell Help

``` shell
# 脚本帮助信息
help() {
cat <<EOF

Desc: 

Tip: 
Usage: sh <ScriptName>.sh <param>  [options]
option:
--param <param>

Example:
sh <ScriptName>.sh <param>  [options]

Parameter:

Author: Mrlu

License: null

EOF
exit 0
}
```

## shell param 截取

``` shell
#这里通过判断$1是否存在判别,也可以通过$#判别
while [[ -n "$1" ]]; do
#statements
case $1 in
-help|--help|-h)
help; break;; # function help is called
-*)
echo "error: no such option $1."; exit 1;;
*) break;;
esac
done
```

`test "${str:a:b}"` 表示提取字bai符du串a开始的zhib个字符
`shift 1;` 位置参数可以用shift命令左移, 比如shift 3表示原来的$4现在变成$1

``` shell
while test "${2:0:1}"; do
case $2 in
--version )
version=$3
shift; shift;;
echo "param is unavailable"
exit 1;;
* )
shift;;
esac
done
```

## Test 命令

*Shell中的 test 命令用于检查某个条件是否成立，它可以进行数值、字符和文件三个方面的测试。* [runoob](https://www.runoob.com/linux/linux-shell-test.html)

## Shell Date
```terminal
today=`date '+%Y-%m-%d.%H-%M-%S'`
```

## For in
```shell 
for url in ${urls[@]}
do
echo "${url}"
done
```

## Shell 脚本封装可执行程序

```terminal
brew install shc
```

>shc [-e date] [-m addr] [-i iopt] [-x cmnd] [-l lopt] [-o outfile] [-rvDSUHCABh] -f script


## Shell Learning

[Shell 教程 | 菜鸟教程](https://www.runoob.com/linux/linux-shell.html)