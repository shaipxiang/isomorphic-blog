---
title: 「思科模拟器」构建虚拟局域网（VLAN）
date: 2016-06-02 17:40:34
categories: [计算机网络]
tags: [思科,vlan]
---

# 前言
思科模拟器是一款强大的模拟网络环境的软件，但是容量却不大，安装器只有70M左右，这篇文章将为你介绍利用思科模拟器构建VLAN网络。
<!--more-->
# 正文
<img src="http://obu9je6ng.bkt.clouddn.com/FsF1gp7vbtW7SW5-JZIRGB81dKyD?imageslim" alt="ClipboardImage" width="661" height="401" />
如图，操作鼠标搭建如图简单的网络，用到了交换机（端口1-4）-直通线-普通终端。
点击终端图标，进入终端配置界面，点击`Desktop`标签，点击`IP Configuration`，如下图，静态设置IP地址。
<img src="http://obu9je6ng.bkt.clouddn.com/FmNY-emWrMeUVUUfJXSe9-VYLT5y?imageslim" alt="ClipboardImage" width="653" height="576" />
配置完成后，你还可以进入终端的命令行界面`(Command Prompt)`，进行`ping`命令的测试，如下图
<img src="http://obu9je6ng.bkt.clouddn.com/FhjrvRjEl-MdAAEfa0GP_xDVjv9w?imageslim" alt="ClipboardImage" width="653" height="576" />
<img src="http://obu9je6ng.bkt.clouddn.com/FtXX7clqbOS62BDMMsQLRtnrZ236?imageslim" alt="ClipboardImage" width="653" height="576" />
然后，就是对于交换机进行配置了，建立不同的虚拟局域网。点击交换机图片，进入命令行界面，输入如下指令：
```
Switch(config)#vlan 1  #建立Vlan1，默认已经存在
Switch(config-vlan)#exit
Switch(config)#vlan 2  #建立Vlan2
Switch(config-vlan)#exit
Switch(config)#interface f0/1  #对1端口进行配置 
Switch(config-if)#switchport access vlan 1  #将1端口加入vlan1，默认已经存在
Switch(config-if)#interface f0/2
Switch(config-if)#switchport access vlan 1
Switch(config-if)#interface f0/3
Switch(config-if)#switchport access vlan 2
Switch(config-if)#interface f0/4
Switch(config-if)#switchport access vlan 2
```
操作界面如下图所示：
<img src="http://obu9je6ng.bkt.clouddn.com/FilWHzc67CSAsMGe7sVhEaVaOtAD?imageslim" alt="ClipboardImage" width="653" height="576" />
或者你可以利用图形界面进行操作
<img src="http://obu9je6ng.bkt.clouddn.com/Fmdpx-owqvC7VGQVMLmD3YnSxFCD?imageslim" alt="ClipboardImage" width="653" height="576" />
<img src="http://obu9je6ng.bkt.clouddn.com/FndZ6bHcsFfIw7MbqVfN7eB1YW26?imageslim" alt="ClipboardImage" width="653" height="576" />


完成如上步骤后，你就完成了`vlan`的构建，下面进行测试。
进入`ip：192.168.100.11`的终端命令行，进行`ping`指令测试。
如下图，同属于vlan1的`192.168.100.12`能够ping通，但是valn2中的`192.168.200.12`不能够，所以测试正确。
<img src="http://obu9je6ng.bkt.clouddn.com/FpZdc9IqufJCH-s6eAK5Dr9GN4Ln?imageslim" alt="ClipboardImage" width="653" height="576" />

# 总结
初步见识到了思科模拟器的威力，之后还会带来更多的文章教学。