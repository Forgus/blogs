---
title: 网心容器魔方部署
date: 2022-09-18
catalog: true
tags:
- 网心云
---

挂载移动硬盘

```bash
#查看硬盘
lsblk
fdisk -l
#格式化硬盘
mkfs.ext4 /dev/sda
# 挂载硬盘
mkdir -p /media/wxedge_storage
mount /dev/sda /media/wxedge_storage
# 重启自动挂载
nvim /etc/fstab
/dev/sda /media/wxedge_storage ext4 defaults 0 0
# macOS 下格式化移动硬盘
brew install e2fsprogs
diskutil list
diskutil unmountdisk /dev/disk2
sudo $(brew --prefix e2fsprogs)/sbin/mkfs.ext4 /dev/disk2
diskutil eject /dev/disk2
```

启动容器
```bash
docker run \
--name=wxedge \
--privileged \
--net=host \
--tmpfs /run \
--tmpfs /tmp \
-v /media/wxedge_storage:/storage:rw \
-e LISTEN_ADDR=":18888" \
-e NIC=eth0 \
-e REC=false \
-d \
registry.cn-hangzhou.aliyuncs.com/forgus/wxedge:2.4.0
```
# pi-dashboard

```bash
docker run -d --name docker-pi-dashboard -e 'LISTEN=1024' --net=host --restart=always ecat/docker-pi-dashboard
```

电信首选DNS：202.101.172.35

备选DNS：202.101.172.47

网关：36.24.168.1
