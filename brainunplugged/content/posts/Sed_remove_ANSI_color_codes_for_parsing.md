+++
date = '2021-04-12T09:00:00+02:00'
draft = false
title = 'Sed remove ANSI color codes for easy parsing'
author = "Peyo"
showToc = false
hidemeta = false
comments = false
description = "Here's how to remove color codes to ease a parsing."
categories = ["linux", "sysadmin", "cheatsheet"]
tags = ["sed", "shell"]
+++
After a software update, a script responsible of triggering email alerts wasn't working as expected.

The reason why was colored output to the log file by the updated application, such as `\033[37m2021-04-09 11:31:13`.

You can remove those ANSI color codes with :
```shell
sed "s/\x1B\[[0-9;]*[a-zA-Z]//g" <inputfile>
```
or with
```shell
sed 's/\x1b\[[0-9;]*m//g' <inputfile>
```
