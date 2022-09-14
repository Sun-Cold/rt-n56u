本仓库融合~~CV~~了[chongshengB](https://github.com/chongshengB/rt-n56u),[AutoCONFIG](https://github.com/AutoCONFIG/rt-n56u),[xumng123](https://github.com/xumng123/rt-n56u)的源码

### 特点 ###
* 2022年暑假宁理装修顺便对校园网进行了一次**升级**，似乎导致[mentohust](https://github.com/hyrathb/mentohust)失效，因此添加了更新的[minieap](https://github.com/updateing/minieap)插件以对抗万恶的校园网
* 更新了SSR+插件，以支持更多协议，方便平时检索外文资料🤪

### 固件说明 ###
* 默认登陆IP:192.168.2.1 
* 默认用户名/密码:admin/admin
* 默认wifi密码:1234567890
* 集成/取消新增插件请修改此文件: trunk/build_firmware_modify

- 已适配除官方适配外的以下机型
>- MI-R3P(感谢群里emmmm适配,可能led控制有点问题,其它功能正常)
>- 京东云路由(文件来自Lintel) 编译代码: JDC-1
>- 歌华链(感谢群里Heaven适配与测试）编译代码: GHL
>- NEWIFI-D1
>- B70(感谢Untitled提供荒野无灯的适配文件)
>- JCG-AC856M(感谢群里的旅途中的我适配和测试,gpio值还未完全适配，但不影响使用)
>- JCG-AC836M(感谢群里的碧霄客修改和测试)
>- YK-L1(L1、L1C、L1W通刷)
>- PSG712
>- PSG1208
>- PSG1218
>- 5K-W20 (USB)
>- OYE-001 (USB)
>- NEWIFI-MINI (USB)
>- MI-MINI (USB)
>- MI-3 (USB)
>- MI-R3G (USB)
>- HC5661A
>- HC5761A (USB)
>- HC5861B
>- 360P2 (USB)
>- MI-NANO
>- MZ-R13
>- MZ-R13P
>- MZ-R18（USB）
>- RT-AC1200GU (USB)
>- XY-C1 (USB)
>- WR1200JS (USB)
>- NEWIFI3 (USB)
>- B70 (USB)
>- A3004NS (USB)
>- K2P
>- K2P-USB (USB)
>- JCG-836PRO (USB)
>- JCG-AC860M (USB)
>- DIR-882 (USB)
>- DIR-878
>- MR2600 (USB)
>- WDR7300
>- RM2100
>- R2100 
>- E8820V2(USB)
>- MSG1500(USB)

***

### 编译说明 ###

* 安装依赖包

```shell
# Debian/Ubuntu
sudo apt update
sudo apt install unzip libtool-bin curl cmake gperf gawk flex bison nano xxd \
	fakeroot kmod cpio git python-docutils gettext automake autopoint \
	texinfo build-essential help2man pkg-config zlib1g-dev libgmp3-dev \
	libmpc-dev libmpfr-dev libncurses5-dev libltdl-dev wget libc-dev-bin

# Archlinux/Manjaro
sudo pacman -Syu --needed git base-devel cmake gperf ncurses libmpc \
        gmp python-docutils vim rpcsvc-proto fakeroot cpio help2man

# Alpine
sudo apk add make gcc g++ cpio curl wget nano xxd kmod \
	pkgconfig rpcgen fakeroot ncurses bash patch \
	bsd-compat-headers python2 python3 zlib-dev \
	automake gettext gettext-dev autoconf bison \
	flex coreutils cmake git libtool gawk sudo

# CentOS 7
sudo yum update
sudo yum groupinstall "Development Tools"
sudo yum install ncurses-* flex byacc bison zlib-* texinfo gmp-* mpfr-* gettext \
	libtool* libmpc-* gettext-* python-docutils nano help2man fakeroot

# CentOS 8
sudo yum update
sudo yum groupinstall "Development Tools"
sudo yum install ncurses-* flex byacc bison zlib-* gmp-* mpfr-* gettext \
	libtool* libmpc-* gettext-* nano fakeroot

# CentOS 8不能直接通过yum安装texinfo，help2man，python-docutils。请去官网下载发行的安装包编译安装
# 以texinfo为例
# cd /usr/local/src
# sudo wget http://ftp.gnu.org/gnu/texinfo/texinfo-6.7.tar.gz
# sudo tar zxvf texinfo-6.7.tar.gz
# cd texinfo-6.7
# sudo ./configure
# sudo make
# sudo make install

```

* 克隆源码

```shell
git clone --depth=1 https://github.com/chongshengB/rt-n56u.git /opt/rt-n56u
```

* 准备工具链

```shell
cd /opt/rt-n56u/toolchain-mipsel

# （推荐）使用脚本下载预编译的工具链：
sh dl_toolchain.sh

# 或者，也可以从源码编译工具链，这需要一些时间：
./clean_toolchain
./build_toolchain

```

* (可选) 修改机型配置文件

```shell
nano /opt/rt-n56u/trunk/configs/templates/PSG1218.config
```

* 清理代码树并开始编译

```shell
cd /opt/rt-n56u/trunk
./clear_tree
fakeroot ./build_firmware_modify PSG1218
# 脚本第一个参数为路由型号，在trunk/configs/templates/中
# 编译好的固件在trunk/images里
```

***

### 请参阅 ###
- https://www.jianshu.com/p/cb51fb0fb2ac
- https://www.jianshu.com/p/6b8403cdea46

### 特别说明 ###
* hanwckf源码：https://github.com/hanwckf/rt-n56u
* lean源码: https://github.com/coolsnowwolf/lede
* 汉化字典来自：https://github.com/gorden5566/padavan
* hanwckf更新日志：https://www.jianshu.com/p/d76a63a12eae

