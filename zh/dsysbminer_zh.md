# 准备工作

## 系统要求：

- 操作系统：Linux (64 位)，Windows 10 (测试不足)。

# 安装配置
- source code: [__dsysbminer__ source code](https://github.com/mosalut/dsysbminer)
- excutable: [__dsysbminer__](https://github.com/mosalut/dsysbminer/releases/download/v1.0.0/dsysbminer_x86_64-1.0.0.rar)

- 源码编译 : 使用go语言，go语言官方文档 https://go.dev/doc/install/source
- 下载安装包：在linux home目录下创建一个文件夹dsysb,把下载的三个可执行程序都放在这里，启动分别参考[dsysb 中文文档](dsysb_zh.md)，与[dsysbminer 简体中文](dsysbminer_zh.md)。


## 运行
```bash
./dsysbminer [-http_port]
```

可以直接在终端运行矿工程序，也可以使用 `&` 在后台运行，例如：
```bash
./dsysbminer &
```
