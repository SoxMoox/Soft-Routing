# ](https://raw.githubusercontent.com/vernesong/OpenClash/dev/img/logo.png) OpenClash 



[![img](https://camo.githubusercontent.com/dada88d8ab77b16ce856084cf65fb523cc2f56a1cb6cfa65ab6bc85832217efd/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f436c6173682d76312e31332e302d626c75652e737667)](https://github.com/Dreamacro/clash/releases/tag/v1.13.0)

本插件是一个可运行在 OpenWrt 上的[ Clash ](https://github.com/Dreamacro/clash)客户端

兼容 Shadowsocks、ShadowsocksR、Vmess、Trojan、Snell 等协议，根据灵活的规则配置实现策略代理

\- 感谢[ frainzy1477 ](https://github.com/frainzy1477)，本插件基于[ Luci For Clash ](https://github.com/frainzy1477/luci-app-clash)进行二次开发 -

## 使用手册



- [Wiki](https://github.com/vernesong/OpenClash/wiki)

## 下载地址



- IPK [前往下载](https://github.com/vernesong/OpenClash/releases)

## 依赖



- luci
- luci-base
- dnsmasq-full
- bash
- curl
- ca-bundle
- ipset
- ip-full
- ruby
- ruby-yaml
- unzip
- iptables(iptables)
- kmod-ipt-nat(iptables)
- iptables-mod-tproxy(iptables)
- iptables-mod-extra(iptables)
- kmod-tun(TUN模式)
- luci-compat(Luci >= 19.07)
- ip6tables-mod-nat(iptables-ipv6)
- kmod-inet-diag(PROCESS-NAME)
- kmod-nft-tproxy(Firewall4)

## 编译



从 OpenWrt 的 [SDK](https://archive.openwrt.org/chaos_calmer/15.05.1/ar71xx/generic/OpenWrt-SDK-15.05.1-ar71xx-generic_gcc-4.8-linaro_uClibc-0.9.33.2.Linux-x86_64.tar.bz2) 编译

```
# 解压下载好的 SDK
curl -SLk --connect-timeout 30 --retry 2 "https://archive.openwrt.org/chaos_calmer/15.05.1/ar71xx/generic/OpenWrt-SDK-15.05.1-ar71xx-generic_gcc-4.8-linaro_uClibc-0.9.33.2.Linux-x86_64.tar.bz2" -o "/tmp/SDK.tar.bz2"
cd \tmp
tar xjf SDK.tar.bz2
cd OpenWrt-SDK-15.05.1-*

# Clone 项目
mkdir package/luci-app-openclash
cd package/luci-app-openclash
git init
git remote add -f origin https://github.com/vernesong/OpenClash.git
git config core.sparsecheckout true
echo "luci-app-openclash" >> .git/info/sparse-checkout
git pull --depth 1 origin master
git branch --set-upstream-to=origin/master master

# 编译 po2lmo (如果有po2lmo可跳过)
pushd luci-app-openclash/tools/po2lmo
make && sudo make install
popd

# 开始编译

# 先回退到SDK主目录
cd ../..
make package/luci-app-openclash/luci-app-openclash/compile V=99

# IPK文件位置
./bin/ar71xx/packages/base/luci-app-openclash_*-beta_all.ipk
```



```
# 同步源码
cd package/luci-app-openclash/luci-app-openclash
git pull

# 您也可以直接拷贝 `luci-app-openclash` 文件夹至其他 `OpenWrt` 项目的 `Package` 目录下随固件编译

make menuconfig
# 选择要编译的包 LuCI -> Applications -> luci-app-openclash
```



## 许可



- [MIT License](https://github.com/vernesong/OpenClash/blob/master/LICENSE)
- 内核 [clash](https://github.com/Dreamacro/clash) by [Dreamacro](https://github.com/Dreamacro)
- 本项目代码基于 [Luci For Clash](https://github.com/frainzy1477/luci-app-clash) by [frainzy1477](https://github.com/frainzy1477)
- GEOIP数据库 [GeoLite2](https://dev.maxmind.com/geoip/geoip2/geolite2/) by [MaxMind](https://www.maxmind.com/)
- IP检查 [MyIP](https://github.com/SukkaW/MyIP) by [SukkaW](https://github.com/SukkaW)
- 控制面板 [clash-dashboard](https://github.com/Dreamacro/clash-dashboard) by [Dreamacro](https://github.com/Dreamacro)
- 控制面板 [yacd](https://github.com/haishanh/yacd) by [haishanh](https://github.com/haishanh)
- lhie1规则 [lhie1-Rules](https://github.com/lhie1/Rules) by [lhie1](https://github.com/lhie1)
- ConnersHua规则 [ConnersHua-Rules](https://github.com/ConnersHua/Profiles/tree/master) by [ConnersHua](https://github.com/ConnersHua)
- 游戏规则 [SSTap-Rule](https://github.com/FQrabbit/SSTap-Rule) by [FQrabbit](https://github.com/FQrabbit)
- 流媒体解锁检测 [RegionRestrictionCheck](https://github.com/lmc999/RegionRestrictionCheck) by [lmc999](https://github.com/lmc999)

## 请作者喝杯咖啡



- PayPal

[![img](https://camo.githubusercontent.com/1fedf764fa06114b797ee53e7506df10880abed6766f854202d758df1707969d/68747470733a2f2f7777772e6b6f2d66692e636f6d2f696d672f676974687562627574746f6e5f736d2e737667)](https://ko-fi.com/vernesong)

- USDT-TRC20

[![img](https://github.com/vernesong/OpenClash/raw/master/img/USDT-Wallet.png)](https://github.com/vernesong/OpenClash/raw/master/img/USDT-Wallet.png)

- 比特币-BTC

[![img](https://github.com/vernesong/OpenClash/raw/master/img/BTC-Wallet.png)](https://github.com/vernesong/OpenClash/raw/master/img/BTC-Wallet.png)

- 以太币-ETH

[![img](https://github.com/vernesong/OpenClash/raw/master/img/ETH-Wallet.png)](https://github.com/vernesong/OpenClash/raw/master/img/ETH-Wallet.png)

## 预览



- 运行状态

[![img](https://github.com/vernesong/OpenClash/raw/master/img/state.png)](https://github.com/vernesong/OpenClash/raw/master/img/state.png)

- 全局设置

[![img](https://github.com/vernesong/OpenClash/raw/master/img/settings.png)](https://github.com/vernesong/OpenClash/raw/master/img/settings.png)

- 服务器&策略组

[![img](https://github.com/vernesong/OpenClash/raw/master/img/servers.png)](https://github.com/vernesong/OpenClash/raw/master/img/servers.png)

- 规则&策略组

[![img](https://github.com/vernesong/OpenClash/raw/master/img/game-settings.png)](https://github.com/vernesong/OpenClash/raw/master/img/game-settings.png)

- 配置文件订阅

[![img](https://github.com/vernesong/OpenClash/raw/master/img/config-subscribe.png)](https://github.com/vernesong/OpenClash/raw/master/img/config-subscribe.png)

- 配置文件管理

[![img](https://github.com/vernesong/OpenClash/raw/master/img/config.png)](https://github.com/vernesong/OpenClash/raw/master/img/config.png)

- 运行日志

[![img](https://github.com/vernesong/OpenClash/raw/master/img/log.png)](https://github.com/vernesong/OpenClash/raw/master/img/log.png)
