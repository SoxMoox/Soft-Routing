# **OpenWrt常见问题**

###  一、移除默认的dnsmasq

***openclash默认使用dnsmasq会和clash冲突导致无法安装***

- **SSH命令**：`opkg remove dnsmasq && opkg install dnsmasq-full`

### 二、设置时区

**更换默认时区为上海：Asia/Shanghai**

### 三、更换国内软件源

- ##### 中科大：

  - **SSH命令：**`sed -i 's/downloads.openwrt.org/mirrors.ustc.edu.cn\/openwrt/g' /etc/opkg/distfeeds.conf`

- ##### 清华源：

  - **SSH命令：**`sed -i 's_https\?://downloads.openwrt.org_https://mirrors.tuna.tsinghua.edu.cn/openwrt_' /etc/opkg/distfeeds.conf`

### 四、更换中文语言包

- ##### 中文包:

- **23.5版本：** 包名

  - luci-i18n-base-zh-cn

  - luci-i18n-firewall-zh-cn

  - luci-i18n-opkg-zh-cn

- **24.10版本以后：** 包名

  - luci-i18n-base-zh-cn
  - luci-i18n-firewall-zh-cn
  - luci-i18n-package-manager-zh-cn

### 五、更换Argon主题

 **argon官网：**

​	地址： **[https://github.com/jerrykuku/luci-theme-argon/blob/master/README_ZH.md](https://github.com/jerrykuku/luci-theme-argon/blob/master/README_ZH.md)** 

- **在官方openwrt固件上安装**

  - ```python
    opkg install luci-compat
    opkg install luci-lib-ipkg
    wget --no-check-certificate https://github.soxmoox.com/https://github.com/jerrykuku/luci-theme-argon/releases/download/v2.3.2/luci-theme-argon_2.3.2-r20250207_all.ipk
    opkg install luci-theme-argon*.ipk
    ```

- **argon-config主题设置：**

- **无法安装**

  - 指定文件名
  - SSH命令：`wget --no-check-certificate -O luci-app-argon-config_0.9_all.ipk https://github.com/jerrykuku/luci-app-argon-config/releases/download/v0.9/luci-app-argon-config_0.9_all.ipk`

- **主题设置：**

  - 亮色主题主色调：**#00F5FF**
  - 暗色主题主色调：**#00C5CD**

- **更换背景壁纸、动态壁纸**

  - 手动上传图片、视频到/www/luci-static/argon/background/文件夹下，给755权限。

- **安装argon-config中文包**

  *安装时报错：`/usr/lib/opkg/info/luci-i18n-argon-config-zh-cn.postinst: .: line 2: can't open '/etc/uci-defaults/luci-i18n-argon-config-zh-cn': No such file or directory`*

  解决方案：

  - ```python
    您在安装 luci-i18n-argon-config-zh-cn 时遇到以下错误：
    /usr/lib/opkg/info/luci-i18n-argon-config-zh-cn.postinst: .: line 2: can't open '/etc/uci-defaults/luci-i18n-argon-config-zh-cn': No such file or directory
    此错误通常表示安装脚本尝试执行 /etc/uci-defaults/luci-i18n-argon-config-zh-cn 文件，但该文件不存在。
    
    可能原因：
    
    文件缺失：安装包可能未正确包含所需的默认配置文件。
    
    文件路径或命名不一致：在某些 OpenWrt 版本中，语言文件的命名或路径可能有所更改。例如，在 OpenWrt 21.02 中，语言目录从 zh-cn 更改为 zh_Hans。 
    GITHUB.COM
    
    解决方案：
    
    检查文件是否存在：首先，验证 /etc/uci-defaults/ 目录中是否存在 luci-i18n-argon-config-zh-cn 文件：
    ls /etc/uci-defaults/
    如果文件不存在，可能需要手动创建或从可靠来源获取。
    
    手动创建文件：如果确定文件缺失，您可以手动创建一个空的占位文件，以避免安装脚本报错：
    touch /etc/uci-defaults/luci-i18n-argon-config-zh-cn
    然后，重新配置已安装的包：
    opkg configure luci-i18n-argon-config-zh-cn
    检查语言目录命名：根据 OpenWrt 版本，语言目录可能需要从 zh-cn 更改为 zh_Hans。
    
    导航到语言文件目录：
    cd /usr/lib/lua/luci/i18n/
    创建符号链接：
    ln -s zh-cn/argon-config.po zh_Hans/argon-config.po
    这将确保系统能够找到正确的语言文件。
    
    检查重复条目：在某些情况下，翻译文件中可能存在重复条目，导致安装失败。
    
    编辑翻译文件：
    nano /usr/lib/lua/luci/i18n/zh-cn/argon-config.po
    查找并删除重复的条目。
    
    重新安装插件：如果上述方法未解决问题，考虑从官方或可信来源重新下载并安装 luci-app-argon-config 和其语言包。
    
    下载插件：
    wget https://github.com/jerrykuku/luci-app-argon-config/releases/download/v0.9/luci-app-argon-config_0.9_all.ipk
    安装插件：
    opkg install luci-app-argon-config_0.9_all.ipk
    安装语言包：
    opkg install luci-i18n-argon-config-zh-cn
    ```

  

### 六、安装nikki插件

**Nikki官网**

​	地址：https://github.com/nikkinikki-org/OpenWrt-nikki

- 添加软件源

  - SSH命令：`curl -s -L https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/feed.sh | ash`
- 手动安装：

  - 手动添加地址到系统-软件包-配置opkg-/etc/opkg/customfeeds.conf中
  - 地址：src/gz nikki https://nikkinikki.pages.dev/openwrt-24.10/aarch64_generic/nikki
- 一键安装

  - SSH命令：`curl -s -L https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/install.sh | ash`
- 一键卸载

  - SSH命令：`curl -s -L https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/install.sh | ash`


### 七、安装挂载点

https://www.cnblogs.com/king-77024128/articles/3534832.html

opkg update

opkg install block-mount

### 八、扩容

mkdir -p /tmp/introot

mkdir -p /tmp/extroot

mount --bind / /tmp/introot

mount /dev/mmcblk0p3 /tmp/extroot

tar -C /tmp/introot -cvf - . | tar -C /tmp/extroot -xf -

umount /tmp/introot

umount /tmp/extroot
