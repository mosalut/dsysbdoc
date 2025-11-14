# dsysb 文档

## 源码和程序
- source code: [__dsysb__ source code](https://github.com/mosalut/dsysb)
- excutable: [__dsysb__](https://github.com/mosalut/dsysb/releases/download/v1.0.0/dsysb_x86_64-1.0.0.rar)
- linux 全家桶 [dist_linux_x86_64-v1.0.0.tar.gz](https://github.com/mosalut/dsysb/releases/download/v1.0.0/dist_linux_x86_64-v1.0.0.tar.gz)
- windows 全家桶 [dist_windows_x86_64-v1.0.0.rar](https://github.com/mosalut/dsysb/releases/download/v1.0.0/dist_windows_x86_64-v1.0.0.rar)

##  运行
假设你已经进入程序所在的目录，可以直接在终端运行 _dsysb_，也可以使用 `&` 在后台运行，例如：

```bash
$ ./dsysb -<connections|http_port|ip|log_file|network_id|port|remote_host>=<value> &
```
后台运行推荐使用[tmux](https://github.com/tmux/tmux/wiki)


## 参数详解

- _\-connections_ 最大P2P连接数量，默认是：32
- _\-http\_port_ 启动HTTP的端口，默认是："20000"
- _\-ip_ 启动P2P的IP，默认是："0.0.0.0"
- _\-log\_file_ 是否将日志写到文件，默认是：false
- _\-network\_id_ 网络ID，0：主网，1-15：不同的测试网，16：开发网，默认是：0
- _\-port_ 启动P2P的IP，默认是：10000
- _\-remote\_host_ 追加一个远程P2P节点的UDP地址


```bash
$ ./dsysb -network_id=1 -remote_host=124.243.173.119:10000
```

在_dsysb_的同目录下, 有一个命名为 _config_ 的文件。其中, remote_hosts 字段 指定了要连接的种子节点的地址，多个地址用逗号分割

例如:
remote_hosts=61.168.100.4:10000,61.168.100.10:10000

注意： _-remote\_host_ 一定不能写本节点自己的地址，否则会有不可预知的错误。如果写了一个已关闭的节点地址，或者不存在的地址，只要格式正确，都可以正常执行下去，只是不会连接到这种不存在的节点。
