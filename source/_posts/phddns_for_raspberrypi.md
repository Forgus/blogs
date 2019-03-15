---
title: 为树莓派安装花生壳客户端
catalog: true
tags:
- 树莓派
- 内网穿透
- 建站
---
## 准备
1. 先在本地机器从花生壳官网[下载](https://hsk.oray.com/download)树莓派安装包:`phddns_rapi_3.0.2.armhf.deb`   
2. 通过如下命令将安装包上传到树莓派：  

```
scp ~/Downloads/phddns_rapi_3.0.2.armhf.deb pi@192.168.1.172:~/
```

## 安装
通过ssh命令登陆树莓派。
*   
通过`su`命令切换到root用户之后
输入如下命令进行安装：

```
dpkg -i phddns_rapi_3.0.2.armhf.deb
```
安装成功后，将显示此树莓派的SN码、默认密码以及远程管理地址。

*注意：花生壳安装步骤都需要在管理员（Root）权限下运行。* 
## 命令
查看可用命令列表：**phddns**  
启动：**phddns start**  
停止：**phddns stop**  
重启：**phddns restart**  
查看状态：**phddns status**  
查看版本：**phddns version**  
重置：**phddns reset** 
## 日志
花生壳日志文件存放路径：**/var/log/phddns** 
## 卸载
输入如下命令进行卸载：

```
dpkg -r phddns
```