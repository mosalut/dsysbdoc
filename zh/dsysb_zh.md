# 准备工作

## 系统要求：

- 操作系统：Linux (64 位)，Windows 10 (测试不足)。

# 安装配置
- 步骤：访问 GitHub 地址 [xxx](#)
## 源码编译 : 使用go语言，go语言官方文档 https://go.dev/doc/install/source
## 下载安装包：在linux home目录下创建一个文件夹dsysb,把下载的三个可执行程序都放在这里，启动分别参考[dsysb 简体中文](dsysb.md)，与[dsysbminer 简体中文](dsysbminer.md)。


##  运行
可以直接在终端运行dsysb，也可以使用 `&` 在后台运行，例如：
```bash
./dsysb -remote_host=<seed address> &
```
后台运行推荐使用[tmux](https://github.com/tmux/tmux/wiki)


此处 _-remote_host_ 参数指定了一个接入dsysb网络(p2p网络)的种子地址，


目前testnet 0.1版本只支持此种方式。


该种子地址可以是一个你已知的节点地址，也可以是本文公布的地址:

a seed address for testnet 0.1: _xxx.xxx.xxx.xxx:ppp_
