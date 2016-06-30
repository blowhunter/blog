---
layout: post
title: Archlinux时间调整问题
category: Linux
tagline: "Linux"
tags: linux 时间 time
published: true
---
{% include JB/setup %}
### Archlinux时间调整的问题
---
- 前提：主机的状态是，双系统，办公电脑，一个是win7，一个是archlinux。COMS中的时间是基于本时区时间的接近值进行设置的。
- 出发点：不想变更windows下的设置，而又想避免archlinux设置本地时间导致出问题。所以探求有没有其他的方法，最后在wiki中发现了ntp同步UTC时间的方法。
- Archlinux环境的时间设置是按照wiki上建议的UTC时钟，时区设置为CST-8，如果默认设置不是这样:
 <pre class="prettyprint linenums">
  timedatectl status    #查看当前的时间信息命令</pre>

  返回的信息:
	> Local time: 四 2016-06-30 16:56:07 CST  
	> Universal time: 四 2016-06-30 08:56:07 UTC  
	> RTC time: 四 2016-06-30 16:56:07   
	> Time zone: Asia/Shanghai (CST, +0800)  
	> Network time on: no  
	> NTP synchronized: no  
	> RTC in local TZ: yes  

  可以用如下命令设置
  <pre class="prettyprint linenums">
  ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime #设置默认时区
  hwclock --systohc --utc  #调整时间偏差，设置时间标准为UTC时间</pre>
- 进行ntp时间服务的安装与配置：[参照官方文档](https://wiki.archlinux.org/index.php/Network_Time_Protocol_daemon)
  <pre class="prettyprint linenums">
  sudo pacman -S ntp  #安装ntp包
  sudo systemctl start ntpd.service   #启动ntpd服务
  sudo systemctl enable ntpd.service  #开启启动服务
  ntpq -p                             #稍后运行，查看同步情况</pre>

  返回的信息:  

    | remote      | refid      | st    | t    | when   | poll  | reach | delay | offset    | jitter    |
	| :-------------: | :-------------: |:-------------: |:-------------: |:-------------: |:-------------: |:-------------: |:-------------: |:-------------: |:-------------: |
	|  time4.aliyun.co   |  .STEP.       |  16       |  u     |  47m    |  1024   |  0   |  0.000  |  0.000  |  0.000  |

- 查看同步成功后的时间信息:
  <pre class="prettyprint linenums">
  timedatectl status</pre>

  返回的信息:         
  > local time: 四 2016-06-30 09:39:43 CST  
  > Universal time: 四 2016-06-30 01:39:43 UTC  
  > RTC time: 四 2016-06-30 01:39:43  
  > Time zone: Asia/Shanghai (CST, +0800)  
  > Network time on: no  
  > NTP synchronized: yes  
  > RTC in local TZ: no  

**--本文结束--**            
