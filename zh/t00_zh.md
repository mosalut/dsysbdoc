# DSYSB流程描述
整个 __DSYSB__ 项目，有三个程序：
- _dsysb_，主程序 [dsysb 简体中文](dsysb_zh.md)
- _dsysbminer_，矿工程序 [dsysbminer 简体中文](dsysbminer_zh.md)
- _dsysbcmd_，命令交互程序 [dsysbcmd 简体中文](dsysbcmd_zh.md)


## dsysb
主程序负责读写区块链数据，链上数据会通过 _dsysb_ 写到一个内存数据库，请不要在一个系统中，启动多个 _dsysb_

主程序也负责与其他节点进行交互，使用[q2p](https://github.com/mosalut/q2p)包实现的P2P网络库

这些交互主要是区块的同步和验证

## dsysbminer
矿工程序负责 _PoW_ 挖矿。挖到矿后会将新挖到的区块发送给主程序。主程序会验证新区块。[开始挖矿](t01_zh.md)


## dsysbcmd
这是一个与主程序和矿工程序交互的命令行程序

主要用于查看各类信息，包括钱包地址余额，链的全局状态，查询区块，查询交易等

也可以用来查看和生产钱包地址

还可以用来启动、停止、暂停和恢复挖矿

所有命令详细使用方法，请看[dsysbcmd 简体中文](dsysbcmd_zh.md)


## removedatabase.sh
Linux 下，在打算清空区块数据时，防止误删到钱包数据库，导致钱包私钥丢失，而编写的 _shell_ 文件。执行该文件时，加上 _network\_id_ 作为参数，可以指定清空哪个网络的区块数据，该参数默认为 0：

```bash
./removedatabase.sh 16
```


# 准备工作

## 系统要求：

- 操作系统：Linux (64 位)，Windows 10 (测试不足)。

# 安装配置
- 安装配置 __DSYSB__ 有两种方式：
1. 从源码编译
2. 下载程序包

## 从源码编译 : 使用go语言，[go语言官方文档](https://go.dev/doc/install/source)

```bash
// 加入你的系统中已经安装了go语言的最新版本
// 并且建议开启go mod
// 随便创建进入一个目录，这里用 ~/work
$ mkdir ~/work
$ cd ~/work

// 创建项目目录
$ mkdir ~/dsysb

// 编译 dsysb
$ git clone git@github.com:mosalut/dsysb.git // 拉取 dsysb 源码库
$ cd dsysb // 这个 dsysb 目录是拉去下来的，不是刚才创建的，只不过同名
$ go build -o ~/dsysb/dsysb -ldflags "-w -s" . // 现在编译了一个 dsysb 文件到 ~/dsysb/ 目录下

// 回到 ~/work 目录
$ cd ~/work

// 编译 dsysbminer
$ git clone git@github.com:mosalut/dsysbminer.git // 拉取 dsysbminer 源码库
$ cd dsysb  
$ go build -o ~/dsysb/dsysbminer -ldflags "-w -s" .

// 编译 dsysbcmd
$ git clone git@github.com:mosalut/dsysbcmd.git // 拉取 dsysbcmd 源码库
$ cd dsysb  
$ go build -o ~/dsysb/dsysbcmd -ldflags "-w -s" .

$ cd ~/dsysb/
```

现在你回到了 _~/dsysb/_ 目录，此目录下有你创建的三个可执行文件：dsysb、dsysbminer、dsysbcmd


## 下载程序包
如果你不会编译 _go_ 语言程序，那么可以下载现成的、编译好的程序包

下载完成后，目录的分配可以和以上“从源码编译”部门的目录分配一样

建议使用由开发者发布的程序包

开发者发布的程序可以保证是从源码编译的，可以使用 __md5sum__ 命令来验证

从其他地方下载或者接受，会有被篡改的风险

所以如果你一定要使用其他来源的程序包，请验证其中每个程序的 __MD5__

[dsysb 简体中文](dsysb_zh.md) 中描述了如何运行
