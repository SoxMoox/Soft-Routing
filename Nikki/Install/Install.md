# Nikki



在 OpenWrt 上使用 Mihomo 进行透明代理。

## 环境要求



- OpenWrt >= 24.10
- Linux Kernel >= 5.13
- firewall4

## 功能



- 透明代理 (Redirect/TPROXY/TUN, IPv4 和/或 IPv6)
- 访问控制
- 配置文件混入
- 配置文件编辑器
- 定时重启

## 安装和更新



### A. 从软件源安装（推荐）



1. 添加源

```
# 只需运行一次
wget -O - https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/feed.sh | ash
```



1. 安装

```
# 你可以从 shell 执行命令安装或者从 LuCI 的`软件包`菜单安装
# for opkg
opkg install nikki
opkg install luci-app-nikki
opkg install luci-i18n-nikki-zh-cn
# for apk
apk add nikki
apk add luci-app-nikki
apk add luci-i18n-nikki-zh-cn
```



### B. 从发行版安装



```
wget -O - https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/install.sh | ash
```



## 卸载并重置

