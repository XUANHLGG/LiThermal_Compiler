# LiThermal 热成像相机编译工具链
用于LiThermal 热成像相机的编译工具链和编译所需的staging_dir文件。  
如果有报错，建议使用Ubuntu 22.04 LTS或以下版本编译。  
## 最新版下载
[![Make project](https://github.com/XUANHLGG/LiThermal_Compiler/actions/workflows/makeProject.yml/badge.svg)](https://github.com/XUANHLGG/LiThermal_Compiler/actions/workflows/makeProject.yml)
**近期发现 GitHub Actions 的二进制文件只有 90 天有效期，因此建议发布新版本到 [Release](https://github.com/XUANHLGG/LiThermal_Compiler/releases)。**
最新构建结果点上面那个 Make Project，打开后打开最新（最上面）那个，在底下`Artifacts`里有个`UDISK.tar`，下载后得到`UDISK.tar.zip`，解压缩2次，直到得到1个文件夹UDISK，里面包含3个文件，把这3个文件复制到相机的MTP设备中（经测试，不需要killall等其它操作），之后长按电源键重启相机。

## 下面内容供开发人员参考，也是旧版说明，如有不一致的地方，以上面的为准

## 编译后的操作
编译完成后，把产生的UDISK文件夹内的**所有文件**复制到USB MTP设备（指的是在热成像相机启动后电脑识别到的USB设备，不是烧录固件后通过TF卡读卡器读出的可见分区）的根目录下。
**注意**：要复制**文件夹内的所有文件**，而不是连带文件夹一起复制过去。
**注意**：如果使用Actions编译的tar文件，则需要先解压出UDISK文件夹。

## [最新代码的 GitHub Actions 编译结果点这里](https://github.com/XUANHLGG/LiThermal_Compiler/actions/workflows/makeProject.yml)

## 手动编译教程
安装依赖
```bash
sudo apt install cmake make
```
拉取代码和编译工具链
```bash
git clone --recursive https://github.com/XUANHLGG/LiThermal_Compiler.git
cd LiThermal_Compiler
```
编译
```bash
./build.sh
```
**注意**：`build.sh`**必须**在本仓库根目录下执行。

**注意**：`build.sh` 会执行 `git submodule update --init --recursive`，不会强制 checkout/pull 上游仓库。
- 如果你修改了 `LiThermal` 子模块源码，请先在子模块内提交到你自己的仓库，并在本仓库更新子模块指针后再编译，否则本地未提交的改动可能会被覆盖。
