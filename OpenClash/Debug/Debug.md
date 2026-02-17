# OpenWrt-OpenClash

## 安装

- 操作流程：

  1. 网址：https://github.com/vernesong/OpenClash/releases

  2. 型号：[luci-app-openclash_0.46.075_all.ipk](https://github.com/vernesong/OpenClash/releases/download/v0.46.075/luci-app-openclash_0.46.075_all.ipk)[luci-app-openclash_0.46.075_all.ipk](https://github.com/vernesong/OpenClash/releases/download/v0.46.075/luci-app-openclash_0.46.075_all.ipk)

  3. 依赖：打开SSH工具写入

     - 先安装好这些依赖:

     - ```c++
       #iptables
       opkg update
       opkg install bash iptables dnsmasq-full curl ca-bundle ipset ip-full iptables-mod-tproxy iptables-mod-extra ruby ruby-yaml kmod-tun kmod-inet-diag unzip luci-compat luci luci-base
       opkg install /tmp/openclash.ipk
       
       apk update
       apk add bash iptables dnsmasq-full curl ca-bundle ipset ip-full iptables-mod-tproxy iptables-mod-extra ruby ruby-yaml kmod-tun kmod-inet-diag unzip luci-compat luci luci-base
       apk add -q --force-overwrite --clean-protected --allow-untrusted /tmp/openclash.apk
       ```

     - ```
       #nftables
       opkg update
       opkg install bash dnsmasq-full curl ca-bundle ip-full ruby ruby-yaml kmod-tun kmod-inet-diag unzip kmod-nft-tproxy luci-compat luci luci-base
       opkg install /tmp/openclash.ipk
       
       apk update
       apk add bash dnsmasq-full curl ca-bundle ip-full ruby ruby-yaml kmod-tun kmod-inet-diag unzip kmod-nft-tproxy luci-compat luci luci-base
       apk add -q --force-overwrite --clean-protected --allow-untrusted /tmp/openclash.apk
       ```

  4. 上传：将下载好的openclash软件包上传并安装。


## 配置

- 配置流程：
  1. 打开插件设置-版本更新
  2. 检查更新
     - 安装内核
     - 更新软件包
  3. 打开配置管理-上传配置文件（yaml文件）
  4. 应用配置

## 结束
