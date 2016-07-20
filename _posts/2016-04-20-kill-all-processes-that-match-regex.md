---
layout: post
title: "Kill all processes that match regex"
author: "Alan Lin"
date: 2016-04-20 10:22:10
tags:
- ps
- network
---

```
ps aux | grep -ie syr-mba-sb02 | awk '{print $2}' | xargs kill -9
```

*ps* is a unix program called "process status". I often find myself having to 
track down processes and kill them on our servers and this tool has been very 
handy for that. It's job is to display the currently running processes on 
a machine.

`ps aux` lists every process on the system using BSD syntax (just means you do 
not have to use a dash when grouping the three options a, u, and x). The other 
syntax options are UNIX and GNU. Why is there three? Dunno. Just running `ps` 
by default will only list processes associated with the current user (you).

`grep` is a command line tool that searches bodies of text based on some given 
pattern. The `-i` option tells it to ignore casing and the `-e` option allows 
you to specify a pattern. I think it can be ignored here since it always 
expects a pattern?

`|` is a character that allows you to create a pipeline which are a series of 
series of processes that are connected where the output of one process feeds 
into the input of the next. Kind of analogous to physical pipelines.

`awk` is a text processing tool that takes some body of text as input and 
displays it in some format. `$2` is a built in variable that represents a piece 
of text in some position. Not sure - have to learn awk. In this place, it 
probably grabs the PID.

`xargs` is tool that executes command line tools on some parameter provided 
through stdin. 








