---
title: 华为openeuler
date: 2023-03-23 00:10:29
comments: true #是否可评论 
layout: post # 公开文章 
categories:
	- 操作系统
toc: true
coverImg: 
tags: 
- 华为openeuler
- 操作系统
- linux
top: false
cover: true
img: 

---









openEuler目前官方分两种版本：
（1）创新版本：技术、内容较新，如openEuler20.9，通常半年发布一个新的版本，喜欢尝新的朋友可以选择这个版本来安装；
（2）稳定版本（LTS）：LTS是稳定版本，如openEuler LTS 22.03，通常两年发布一个新的版本，生产环境一般选择这个版本；

一、U盘分区
1、清空U盘，最重要的是清除MBR。U盘原来的MBR没有清除，很可能导致安装grub2失败。如果在安装过程中grub2提示“grub-install: warning: Attempting to install GRUB to a disk with multiple partition labels. This is not supported yet… ”，一般就是因为U盘原来的MBR没有清除。清空方法：
（1）组合键win+R 运行 diskpart。
（2）输入list disk，得到目前所有的磁盘。
（3）输入select disk 2 ，定位到U盘。
（4）输入命令clean，清除所有，（MBR，分区和资料）。
diskpart汇总命令如下：
list disk
select disk 1
clean

2、给U盘分区。我的是一个32g的U盘，分了10GB空间来做启动盘，格式为FAT32，因为要兼容UEFI，所以没有选择分区隐藏、删除等保护措施。其余20G格式化为NTFS，存放大于4G的ISO
CREATE PARTITION PRIMARY SIZE=10240
CREATE PARTITION PRIMARY 
list PARTITION
select PARTITION 1
FORMAT FS=FAT32 LABEL=“BOOT_DISK” QUICK
select PARTITION 2
FORMAT FS=NTFS LABEL=“IMG_SET” QUICK
list PARTITION
————————————————
版权声明：本文为CSDN博主「mengyoufengyu」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/mengyoufengyu/article/details/118277379







```
win和linux的系统格式的是不同的 linux下不能格式化win创建的分区 只要将d盘 分区删除了 变回未划分状态 linux下才能识别使用
```



















# Linux（openEuler）没有界面连接互联网方法



前言:

| 系统      | 版本                           |
| --------- | ------------------------------ |
| openEuler | openEuler-22.03-LTS-x86_64-dvd |

我们在安装linux之后，一般都是无界面的情况。大部分情况都是需要自己安装界面的，如果路由器的情况下直接插上网络就好了。下面就开始介绍两种方法进行linxu网络的连接。

注意: 小编是使用的第一种方法进行处理的，第二种试了下没有成功，就果断先放弃了。有时间再研究下。



> **第一种: 使用手机usb热点共享的方式**

- 终端中查看现有网络接口：

```bash
ip addr 或 ifconfig
```

连接好数据线并在手机设置中打开“通过USB共享网络”

再次查看是否将USB识别为新的网络接口，此时没有IP地址。注意新增的网络接口名称，如“usb0”

- 为网络接口分配IP地址：

```bash
dhclient usb0
```

- 再次查看网络接口：

```bash
ip addr 或 ifconfig
```

- 确认已接入互联网：

```bash
ping www.baidu.com
```






> **第二种: nmcli命令**

1 ：废话

​        Nmcli（Network Manager Command Line），是一个用于识别和配置 Internet 连接的常见 Linux 应用程序。许多发行版都有一个用于在桌面环境中使用 NetworkManager 的图形小程序，但如果在 Linux 服务器上，可能将无法访问桌面。通过终端连接 Wi-Fi 的一些方法有点复杂，涉及配置文件和你知道的 PSK 密钥。nmcli 不是这样。假设有一台现代路由器，只需要知道网络的 SSID（Service Set Identifier 要连接的网络的名称）和网络密码（如果有的话）。

2：步骤

- 启用 Wi-Fi 设备

   查看所有网络接口的状态，请使用以下命令：

```bash
nmcli dev status
```



- 获得网络设备列表及其类型、状态和网络连接信息。如果不确定 Wi-Fi 设备是否启用，可以使用如下命令进行检查

```bash
nmcli radio wifi
```


如果输出显示 Wi-Fi 已 禁用，可以使用如下命令启用：

```bash
nmcli radio wifi on
```



-  识别 Wi-Fi 接入点

如果不知道 Wi-Fi 接入点的名称（也称为 SSID），可以通过扫描附近的 Wi-Fi 网络来找到它。

```bash
nmcli dev wifi list
```


注意需要连接的网络的SSID下列出的名称，下一步需要用到它。

- 连接到 Wi-Fi

启用 Wi-Fi 并识别到 SSID 后，可以尝试连接。可以使用一下命令建立连接：

将network-ssid替换为网络名称。

```bash
sudo nmcli dev wifi connect network-ssid
```



如果 Wi-Fi 具有 WEP 或 WPA 安全性，可以在命令中指定网络密码。



```bash
sudo nmcli dev wifi connect network-ssid password "network-password"
```


通过空格分割参数，若SSID参数一个以上，记得用引号括起来


或者，如果不想在屏幕上写出密码，可以使用--ask选项。

```bash
sudo nmcli --ask dev wifi connect network-ssid
```


系统现在将需要输入网络密码，但不会显示。

若设备现在已经连接到互联网，可以用ping www.baidu.com 测试一下。

使用 nmcli 管理网络连接, 可以通过发出以下命令查看所有已保存的连接：

```bash
nmcli con show
```

如果连接到一个网络，但想使用不同的连接，可以通过将连接切换为down来断开连接。需要指定 SSID，或者如果有多个相同 SSID 的连接，请使用 UUID。

```bash
nmcli con down ssid/uuid
```

要连接到另一个保存的连接，只需要在 nmcli 命令中传递 up 选项。确保指定要连接的新网络的 SSID 或 UUID。

```bash
nmcli con up ssid/uuid
```



- 使用图形化连接工具

```bash
sudo nmtui
```









