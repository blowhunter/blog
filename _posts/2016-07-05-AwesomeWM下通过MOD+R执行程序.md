---
layout: post                                                                                                                                                            
title: AwesomeWM下通过MOD+R执行程序
category: Linux
tagline: "Linux"
tags: archlinux awesomeWM 执行 程序 启动
published: true
---
{% include JB/setup %}
### AwesomeWM下通过MOD+R执行程序
---
- 在awesomeWM下通过MOD+R启动程序，有时可能无法启动，并提示“执行子进程“XXXX”失败(没有那个文件或目录)”。<!-- excerpt -->
- 这种情况，我们就需要到"/bin/"下查看是否有对应的可执行文件，如果没有的话就无法通过这种方式运行的。
- **解决方法：**首先，确认你要执行的应用程序已经安装，并且是有界面的应用程序，通常我们可以在需要执行程序的窗口按下MOD+w键，在弹出的Accessories=>Application Finder然后查找对应的应用程序就可以执行了。一般符合规范的应用程序在/bin/下都有对应的可执行文件，你可以看看其对应的可执行文件是不是与安装时的名称不同，或者缩写了。


