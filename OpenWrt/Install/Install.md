# OpenWrt

## 下载镜像

下载：

1. 网址：https://firmware-selector.openwrt.org/
2. 型号：Generic x86/64
3. 镜像：COMBINED-EFI (SQUASHFS)
4. 解压：openwrt-24.10.0-x86-64-generic-squashfs-combined-efi.img

## 安装镜像

写盘：

1. 下载Ventoy写入U盘。

1. 下载WE PE工具制作WE-PE ISO镜像文件。

1. 下载IMG写盘工具。

1. 将解压好的IMG镜像、WE PE工具ISO镜像文件、IMG写盘工具文件放入U盘。

1. 插入电脑以U盘启动。

1. 打开WE PE工具，在PE中打开IMG写盘工具将Openwrt镜像写入磁盘。

1. 拔掉U盘，重新启动。

登录：

1. 网线插入网口eth0。

2. 网页打开192.168.1.1。

3. 用户名root，密码为空。

## 配置Openwrt

配置主路由：

配置旁路由：

- 打开网络-接口，编辑lan口：

  - IPv4 地址：x.x.x.x（与主路由同网段）

    IPv4 子网掩码：255.255.255.0

    IPv4 网关：主路由IP地址。

- 高级设置

  - 使用自定义的 DNS 服务器：主路由DNS。

- DHCP服务器

  - 常规设置：忽略此接口。

  - IPv6设置：

    - RA服务 ：禁用

      DHCPv6 服务：禁用

      NDP 代理：禁用

- 网络-DHCP/DNS：

  - 过滤器：勾选过滤 IPv6 AAAA 记录。

- 保存并应用。

## 结束
