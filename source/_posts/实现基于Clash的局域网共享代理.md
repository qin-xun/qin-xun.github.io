---
title: 实现基于Clash的局域网共享代理
date: 2020-07-14 23:15:59
categories: 电脑使用教程
tags:
description: 在激活Oculus Quest设备时，手机需要从Google Play Store安装Oculus。在与Quest配对时，发现无法连接wifi，得知原因是quest要在连接后通过访问oculus.com获得相关服务。
---
# 前言 

在激活Oculus Quest设备时，需要手机安装从Google Play Store安装Oculus。

在与Quest配对时，发现无法连接wifi，得知原因是quest要在连接后通过访问oculus.com获得相关服务，而该网站被魔法，遂上网搜集资料，设置成功。

# 开启移动热点

在windows中设置-网络和Internet-移动热点中开启热点。

# 配置Clash

在Clash中开启 Allow Lan。
![](1.png)

点击clash中的Profiles中服务提供商的配置文件：

![](2.png)

在末尾添加以下代码：

```
dns:
   enable: true
   enhanced-mode: redir-host # 或 fake-ip
   listen: 0.0.0.0:53
   nameserver:
      - 223.5.5.5
experimental:
   interface-name: WLAN # 物理网卡名称
```

# 配置网络适配器
点击 TAP Device，安装tap网卡，在 控制面板\网络和 Internet\网络连接 中会出现TAP开头的网卡：

![](3.png)

点击属性，在【允许其他网络用户通过此计算机的Internet来连接】前面打勾，选择开启热点的网卡。

> 【允许其他网络用户通过此计算机的Internet来连接 】的意思为允许某个网络适配器经过此适配器访问，也就是某个网络适配器的流量可以经过此适配器。

![](4.png)

手机连接笔记本电脑开启的热点就可以使用魔法了~

